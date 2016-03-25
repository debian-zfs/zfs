# Quick build instructions

- create build directory

  ```
export VERSION=0.6.5.6
mkdir build-$VERSION
cd build-$VERSION
  ```

- build spl

  ```
wget https://github.com/debian-zfs/spl/archive/pkg-$VERSION.zip -O spl-pkg-$VERSION.zip
unzip spl-pkg-$VERSION.zip
cd spl-pkg-$VERSION/
dpkg-checkbuilddeps
  ```

  If you see any build prequisite missing, install it with ``apt-get install``

  ```
dpkg-buildpackage -b
cd ..
  ```

- install spl

  ```
dpkg -i spl_$VERSION*.deb spl-dkms_$VERSION*.deb
  ```

- build zfs

  ```
wget https://github.com/debian-zfs/zfs/archive/pkg-$VERSION.zip -O zfs-pkg-$VERSION.zip
unzip zfs-pkg-$VERSION.zip
cd zfs-pkg-$VERSION/
dpkg-checkbuilddeps
  ```

  If you see any build prequisite missing, install it with ``apt-get install``

  ```
dpkg-buildpackage -b
cd ..
  ```

- install zfs

  ```
dpkg -i libnvpair1_$VERSION*.deb libuutil1_$VERSION*.deb libzfs2_$VERSION*.deb libzpool2_$VERSION*.deb zfs-dkms_$VERSION*.deb zfsutils_*.deb
  ```

- install ``zfs-initramfs`` as well if you use zfs root

  ```
dpkg -i zfs-initramfs_$VERSION*.deb
  ```
