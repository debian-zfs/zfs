# Quick build instructions

- create build directory

  ```
mkdir build-0.6.5.5
cd build-0.6.5.5
  ```

- build spl

  ```
wget https://github.com/debian-zfs/spl/archive/pkg-0.6.5.5.zip -O spl-pkg-0.6.5.5.zip
unzip spl-pkg-0.6.5.5.zip
cd spl-pkg-0.6.5.5/
dpkg-checkbuilddeps
  ```

  If you see any build prequisite missing, install it with ``apt-get install``

  ```
dpkg-buildpackage -b
cd ..
  ```

- install spl

  ```
dpkg -i spl_*.deb spl-dkms_*.deb
  ```

- build zfs

  ```
wget https://github.com/debian-zfs/zfs/archive/pkg-0.6.5.5.zip -O zfs-pkg-0.6.5.5.zip
unzip zfs-pkg-0.6.5.5.zip
cd zfs-pkg-0.6.5.5/
dpkg-checkbuilddeps
  ```

  If you see any build prequisite missing, install it with ``apt-get install``

  ```
dpkg-buildpackage -b
cd ..
  ```

- install zfs

  ```
dpkg -i libnvpair1_*.deb libuutil1_*.deb libzfs2_*.deb libzpool2_*.deb zfs-dkms_*.deb zfsutils_*.deb
  ```

- install ``zfs-initramfs`` as well if you use zfs root

  ```
dpkg -i zfs-initramfs_*.deb
  ```
