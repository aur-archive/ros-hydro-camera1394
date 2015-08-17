# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - ROS driver for devices supporting the IEEE 1394 Digital Camera (IIDC) protocol."
url='http://www.ros.org/'

pkgname='ros-hydro-camera1394'
pkgver='1.9.4'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('LGPL')

ros_makedepends=(ros-hydro-camera-info-manager
  ros-hydro-sensor-msgs
  ros-hydro-nodelet
  ros-hydro-diagnostic-updater
  ros-hydro-image-transport
  ros-hydro-roscpp
  ros-hydro-catkin
  ros-hydro-tf
  ros-hydro-dynamic-reconfigure
  ros-hydro-driver-base
  ros-hydro-rostest)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]}
  boost
  libdc1394)

ros_depends=(ros-hydro-sensor-msgs
  ros-hydro-nodelet
  ros-hydro-diagnostic-updater
  ros-hydro-image-transport
  ros-hydro-roscpp
  ros-hydro-tf
  ros-hydro-dynamic-reconfigure
  ros-hydro-camera-info-manager)
depends=(${ros_depends[@]}
  boost
  libdc1394)

_tag=release/hydro/camera1394/${pkgver}-${_pkgver_patch}
_dir=camera1394
source=("${_dir}"::"git+https://github.com/ros-drivers-gbp/camera1394-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
