# Pontos de Montagem, Discos e `/etc/fstab`

## Pontos de montagem no Linux

No Linux, um **ponto de montagem** é um diretório usado para acessar o conteúdo de uma partição, disco, pendrive, HD externo, SSD, compartilhamento de rede ou outro sistema de arquivos.

Diferente do Windows, que usa letras como `C:`, `D:` e `E:`, o Linux integra tudo dentro da árvore principal de diretórios, iniciada em:

```bash
/
```

Exemplos de pontos de montagem:

```bash
/mnt/hdexterno
/media/douglas/PENDRIVE
/home
/boot/efi
/var/lib/docker
```

---

### 1. O que significa montar um disco

Montar um disco significa conectar uma partição a uma pasta do sistema.

```bash
sudo mount /dev/sdb1 /mnt/hdexterno
```

| Parte | Significado |
|---|---|
| `/dev/sdb1` | Partição que será montada |
| `/mnt/hdexterno` | Diretório onde o conteúdo ficará acessível |
| `mount` | Comando usado para montar |
| `sudo` | Executa com permissão administrativa |

Após a montagem, os arquivos da partição ficam acessíveis em:

```bash
/mnt/hdexterno
```

---

### 2. Diretórios comuns usados como pontos de montagem

| Diretório | Uso principal |
|---|---|
| `/mnt` | Montagens manuais, temporárias ou configuradas pelo administrador |
| `/media` | Montagens automáticas feitas pela interface gráfica |
| `/home` | Pode ser usado como partição separada para arquivos dos usuários |
| `/boot` | Pode armazenar arquivos de inicialização em partição separada |
| `/boot/efi` | Ponto de montagem da partição EFI em sistemas UEFI |
| `/var` | Pode ser partição separada em servidores, pois armazena logs, caches e dados |
| `/var/lib/docker` | Local comum de dados do Docker |
| `/srv` | Dados servidos por serviços, como sites ou FTP |

---

### 3. Como ver os pontos de montagem atuais

### Listar discos, partições e pontos de montagem

```bash
lsblk
```

A coluna mais importante é:

```bash
MOUNTPOINTS
```

---

### Ver espaço usado e disponível

```bash
df -h
```

---

### Ver árvore de montagens

```bash
findmnt
```

Consultar um ponto específico:

```bash
findmnt /mnt/hdexterno
```

---

### Ver montagens ativas

```bash
mount
```

Filtrar uma montagem específica:

```bash
mount | grep sdb1
```

---

### 4. Como identificar discos e partições

### Listar discos

```bash
lsblk
```

### Ver UUID e tipo do sistema de arquivos

```bash
sudo blkid
```

Exemplo de saída:

```bash
/dev/sdb1: UUID="A1B2-C3D4" TYPE="exfat" PARTUUID="12345678-01"
```

| Campo | Significado |
|---|---|
| `/dev/sdb1` | Nome da partição |
| `UUID` | Identificador único da partição |
| `TYPE` | Tipo do sistema de arquivos |
| `PARTUUID` | Identificador da partição na tabela de partições |

---

### 5. Como criar um ponto de montagem

Crie uma pasta para servir como ponto de montagem:

```bash
sudo mkdir -p /mnt/hdexterno
```

Monte a partição:

```bash
sudo mount /dev/sdb1 /mnt/hdexterno
```

Acesse os arquivos:

```bash
cd /mnt/hdexterno
ls -la
```

---

### 6. Como desmontar uma partição

Desmontar pelo ponto de montagem:

```bash
sudo umount /mnt/hdexterno
```

Ou pelo dispositivo:

```bash
sudo umount /dev/sdb1
```

Se aparecer erro de alvo ocupado:

```bash
umount: /mnt/hdexterno: target is busy
```

Verifique quem está usando o diretório:

```bash
sudo lsof +f -- /mnt/hdexterno
```

ou:

```bash
sudo fuser -vm /mnt/hdexterno
```

Depois, feche arquivos, terminais ou programas que estejam usando o disco.

---

### 7. Montagem por tipo de sistema de arquivos

| Sistema de arquivos | Comando |
|---|---|
| `ext4` | `sudo mount -t ext4 /dev/sdb1 /mnt/dados` |
| `ntfs` | `sudo mount -t ntfs3 /dev/sdb1 /mnt/windows` |
| `exfat` | `sudo mount -t exfat /dev/sdb1 /mnt/hdexterno` |
| `vfat` | `sudo mount -t vfat /dev/sdb1 /mnt/pendrive` |

---

### 8. Permissões em pontos de montagem

### Sistemas Linux, como `ext4`

```bash
sudo chown -R $USER:$USER /mnt/hdexterno
```

Ou para um usuário específico:

```bash
sudo chown -R douglas:douglas /mnt/hdexterno
```

---

### Sistemas `ntfs`, `exfat` ou `vfat`

Esses sistemas não usam permissões Linux da mesma forma que `ext4`. Normalmente, as permissões são definidas no momento da montagem.

Exemplo com `ntfs`:

```bash
sudo mount -t ntfs3 -o uid=$(id -u),gid=$(id -g),umask=022 /dev/sdb1 /mnt/hdexterno
```

Permissão mais aberta:

```bash
sudo mount -t ntfs3 -o uid=$(id -u),gid=$(id -g),umask=000 /dev/sdb1 /mnt/hdexterno
```

---

### 9. Montagem automática com `/etc/fstab`

O arquivo `/etc/fstab` define quais partições serão montadas automaticamente durante a inicialização do sistema.

Antes de editar, faça backup:

```bash
sudo cp /etc/fstab /etc/fstab.bkp
```

Editar o arquivo:

```bash
sudo nano /etc/fstab
```

---

### Exemplo para `ext4`

```bash
UUID=xxxx-xxxx /mnt/dados ext4 defaults 0 2
```

### Exemplo para `ntfs`

```bash
UUID=xxxx-xxxx /mnt/windows ntfs3 defaults,uid=1000,gid=1000,umask=022 0 0
```

### Exemplo para `exfat`

```bash
UUID=xxxx-xxxx /mnt/hdexterno exfat defaults,uid=1000,gid=1000,umask=022,nofail 0 0
```

### Exemplo para EFI

```bash
UUID=xxxx-xxxx /boot/efi vfat umask=0077 0 1
```

---

### 10. Testar o `/etc/fstab`

Após editar o `/etc/fstab`, teste sem reiniciar:

```bash
sudo mount -a
```

Se não aparecer erro, a configuração está válida.

Verifique a montagem:

```bash
lsblk
df -h
findmnt
```

---

### 11. Opções comuns no `/etc/fstab`

| Opção | Função |
|---|---|
| `defaults` | Usa opções padrão de montagem |
| `auto` | Monta automaticamente |
| `noauto` | Não monta automaticamente no boot |
| `rw` | Monta com leitura e escrita |
| `ro` | Monta somente leitura |
| `user` | Permite que usuário comum monte |
| `users` | Permite que qualquer usuário monte/desmonte |
| `uid=1000` | Define o dono dos arquivos montados |
| `gid=1000` | Define o grupo dos arquivos montados |
| `umask=022` | Define permissões padrão mais restritas |
| `umask=000` | Define permissões abertas para todos |
| `nofail` | Não impede o boot se o disco estiver ausente |

---

### 12. Exemplo prático de montagem manual

### 1. Listar discos

```bash
lsblk
```

### 2. Verificar UUID e tipo

```bash
sudo blkid /dev/sdb1
```

### 3. Criar ponto de montagem

```bash
sudo mkdir -p /mnt/hdexterno
```

### 4. Montar partição

```bash
sudo mount -t exfat /dev/sdb1 /mnt/hdexterno
```

### 5. Acessar arquivos

```bash
cd /mnt/hdexterno
ls -la
```

### 6. Desmontar

```bash
sudo umount /mnt/hdexterno
```

---

### 13. Exemplo prático de montagem automática

### 1. Criar ponto de montagem

```bash
sudo mkdir -p /mnt/hdexterno
```

### 2. Descobrir UUID

```bash
sudo blkid /dev/sdb1
```

### 3. Editar `/etc/fstab`

```bash
sudo nano /etc/fstab
```

Adicionar linha:

```bash
UUID=A1B2-C3D4 /mnt/hdexterno exfat defaults,uid=1000,gid=1000,umask=022,nofail 0 0
```

### 4. Testar

```bash
sudo mount -a
```

### 5. Verificar

```bash
df -h
lsblk
```

---

### 14. Comandos mais usados

| Comando | Função |
|---|---|
| `lsblk` | Lista discos, partições e pontos de montagem |
| `df -h` | Mostra espaço usado e disponível |
| `sudo blkid` | Mostra UUID e tipo das partições |
| `findmnt` | Mostra árvore de montagens |
| `mount` | Mostra ou realiza montagens |
| `sudo mount /dev/sdb1 /mnt/hdexterno` | Monta uma partição |
| `sudo umount /mnt/hdexterno` | Desmonta uma partição |
| `sudo mkdir -p /mnt/hdexterno` | Cria ponto de montagem |
| `sudo nano /etc/fstab` | Edita montagens automáticas |
| `sudo mount -a` | Testa e aplica o `/etc/fstab` |

---

### 15. Observações importantes

- Faça backup do `/etc/fstab` antes de editar.
- Prefira usar `UUID` no `/etc/fstab`, pois nomes como `/dev/sdb1` podem mudar.
- Use `/mnt` para montagens manuais.
- Use `/media` para dispositivos montados automaticamente pela interface gráfica.
- Para `ntfs`, `exfat` e `vfat`, configure `uid`, `gid` e `umask` quando precisar controlar permissões.
- Use `nofail` em discos externos para evitar problemas de inicialização caso o disco não esteja conectado.
