# RKSampleCommon
Rockchip media sampling library.

## Build 
isp3.x is build with Rockchip SDK V1.4.0 (sololinker). Cmake configuration:
```
toolchain=/SDK/tools/linux/toolchain/arm-rockchip830-linux-uclibcgnueabihf
sysroot=${toolchain}/arm-rockchip830-linux-uclibcgnueabihf/sysroot
cxx_compiler=${toolchain}/bin/arm-rockchip830-linux-uclibcgnueabihf-g++
c_compiler=${toolchain}/bin/arm-rockchip830-linux-uclibcgnueabihf-gcc
rk_media_include_dir=/SDK/media/out/include/

# cmake -DCMAKE_SYSROOT=${sysroot}\
cmake -DRKMEDIA_INCLUDE_DIR=${rk_media_include_dir} \
    -DCMAKE_CXX_COMPILER=${cxx_compiler} \
    -DCMAKE_C_COMPILER=${c_compiler} \
    -DCMAKE_BUILD_TYPE=Release \
    -DBUILD_ISP_3=ON \
    -S . -B build
```

isp2.x is built with official Rockchip SDK V1.1.0. Cmake configuration:
```
toolchain=/SDK/buildroot/output/rockchip_rv1126_owl_50emmc_ipc/host
sysroot=${toolchain}/arm-buildroot-linux-gnueabihf/sysroot
cxx_compiler=${toolchain}/usr/bin/arm-linux-gnueabihf-g++
c_compiler=${toolchain}/usr/bin/arm-linux-gnueabihf-gcc
rk_media_include_dir=/SDK/buildroot/output/rockchip_rv1126_owl_50emmc_ipc/host/arm-buildroot-linux-gnueabihf/sysroot/usr/include

# cmake -DCMAKE_SYSROOT=${sysroot}\
cmake -DRKMEDIA_INCLUDE_DIR=${rk_media_include_dir} \
    -DCMAKE_CXX_COMPILER=${cxx_compiler} \
    -DCMAKE_C_COMPILER=${c_compiler} \
    -DCMAKE_BUILD_TYPE=Release \
    -DBUILD_ISP_2=ON \
    -S . -B build
```

Build targets:
```
cd build && make -j24 install
```