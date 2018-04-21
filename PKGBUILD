# Script generated with Bloom
pkgdesc="ROS - Python Multiprocess Management Framework, based on ZeroMQ communication"


pkgname='ros-kinetic-pyzmp'
pkgver='0.0.15_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('python2-pytest'
'python2-pyzmq'
'ros-kinetic-catkin-pip>=0.2.0'
'ros-kinetic-catkin>=0.6.18'
)

depends=('python2-pyzmq'
)

conflicts=()
replaces=()

_dir=pyzmp
source=()
md5sums=()

prepare() {
    cp -R $startdir/pyzmp $srcdir/pyzmp
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

