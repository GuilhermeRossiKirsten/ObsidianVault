 Atenção: a compilação demorou mais de 50 minutos (precisa também de 8 GB de disco livre) na minha máquina virtual, você foi avisado :-D

Esses passos foram achados no artigo: [https://www.dedicatedcore.com/blog/install-gcc-compiler-ubuntu/](https://www.dedicatedcore.com/blog/install-gcc-compiler-ubuntu/) que você pode ler para ter acesso a mais detalhes.

```bash
sudo apt install build-essential
sudo apt install libmpfr-dev libgmp3-dev libmpc-dev -y
wget http://ftp.gnu.org/gnu/gcc/gcc-13.2.0/gcc-13.2.0.tar.gz
tar -xf gcc-13.2.0.tar.gz
cd gcc-13.2.0
./configure -v --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu --prefix=/usr/local/gcc-13.2.0 --enable-checking=release --enable-languages=c,c++ --disable-multilib --program-suffix=-13.2.0
make -j3
sudo make install
/usr/local/gcc-13.2.0/bin/gcc-13.2.0 --version
```


A linha `make -j3` pode ser adaptada para um número maior, caso você tenha vários processadores. Veja que usamos sudo em várias partes, ou seja, você precisa ser o root do sistema para poder instalar novos pacotes.

No final, teste o novo compilador com:

```bash
/usr/local/gcc-13.2.0/bin/gcc-13.2.0 --version
```


que deve resultar em:

```console
$ /usr/local/gcc-13.2.0/bin/gcc-13.2.0 --version
gcc-13.2.0 (GCC) 13.2.0
Copyright (C) 2023 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```


Para ficar mais fácil de usar, digite:

```console
sudo ln -s /usr/local/gcc-13.2.0/bin/gcc-13.2.0 /usr/bin/gcc-13.2.0
```


que cria um link para o /usr/bin, desta forma, você poderá chamar o compilador apenas com:

```console
$ gcc-13.2.0 --version
gcc-13.2.0 (GCC) 13.2.0
Copyright (C) 2023 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```