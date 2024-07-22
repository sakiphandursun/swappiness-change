
# Swappiness Ayarını Değiştirme

Bu doküman, Linux sunucunuzda `swappiness` ayarını 40 olarak kalıcı bir şekilde değiştirme adımlarını içermektedir.

## Adımlar

### 1. Geçici Olarak `swappiness` Değerini Değiştirme

`swappiness` ayarını geçici olarak değiştirmek için aşağıdaki komutu kullanın. Bu değişiklik, sistem yeniden başlatılana kadar geçerli olacaktır.

```sh
sudo sysctl vm.swappiness=40
```

### 2. Kalıcı Olarak `swappiness` Değerini Değiştirme

`swappiness` ayarını kalıcı hale getirmek için `/etc/sysctl.conf` dosyasına ekleme yapmanız gerekmektedir:

```sh
sudo nano /etc/sysctl.conf
```

Dosyanın sonuna şu satırı ekleyin:

```sh
vm.swappiness=40
```

Değişiklikleri kaydetmek ve dosyadan çıkmak için:

- `Ctrl + O` tuşlarına basın ve `Enter` tuşuna basarak kaydedin.
- `Ctrl + X` tuşlarına basarak çıkın.

### 3. Değişiklikleri Uygulama

Yeni `sysctl` ayarlarını uygulamak için aşağıdaki komutu çalıştırın:

```sh
sudo sysctl -p
```

Bu komut, `sysctl.conf` dosyasındaki tüm ayarları tekrar yükler ve yeni `swappiness` değeri hemen geçerli olur.

### 4. Mevcut Swap Durumunu Kontrol Etme

Swap alanınızı ve bellek kullanımınızı kontrol etmek için aşağıdaki komutları kullanabilirsiniz:

```sh
sudo swapon --show
free -h
```

### Örnek Çıktılar

- `sudo swapon --show` komutunun örnek çıktısı:

```sh
NAME      TYPE SIZE USED PRIO
/swap.img file  12G 6.4G   -2
```

- `free -h` komutunun örnek çıktısı:

```sh
               total        used        free      shared  buff/cache   available
Mem:           7.8Gi       3.4Gi       274Mi       165Mi       4.1Gi       3.9Gi
Swap:           11Gi       6.4Gi       5.6Gi
```
