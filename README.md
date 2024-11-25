# Gemma2-MNN
## Download
```bash
git clone https://github.com/Russyyds/Gemma2-MNN.git
cd Gemma2-MNN/
git submodule update --init --recursive --depth=1
```
## Build
### Linux
```bash
mkdir build
cd build
cmake .. 
make -j16
```

### Android
CPU
```bash
mkdir build
cd build
cmake .. -DBUILD_FOR_ANDROID=ON \
-DCMAKE_TOOLCHAIN_FILE=/path/to/ndk/build/cmake/android.toolchain.cmake \
-DANDROID_ABI="arm64-v8a" \
-DANDROID_STL=c++_static \

make -j16
```
OpenCL
```bash
mkdir build
cd build
cmake .. -DBUILD_FOR_ANDROID=ON \
-DCMAKE_TOOLCHAIN_FILE=/home/jmtang/Workspace/android-ndk-r27/build/cmake/android.toolchain.cmake \
-DMNN_OPENCL=ON \
-DANDROID_ABI="arm64-v8a" \
-DANDROID_STL=c++_static \

make -j16
```

# Run
## Linux
```bash
./cli_demo ./Gemma-MNN/config.json 
```
## Android
```bash
cd build
adb push ./MNN/OFF/arm64-v8a/libMNN.so /data/local/tmp
adb push ./MNN/express/OFF/arm64-v8a/libMNN_Express.so /data/local/tmp
adb push ./MNN/source/backend/opencl/OFF/arm64-v8a/libMNN_CL.so /data/local/tmp
adb push ./libllm.so ./cli_demo /data/local/tmp
adb push Gemma-MNN /data/local/tmp

adb shell
cd data/local/tmp
export LD_LIBRARY_PATH=.
./cli_demo ./Gemma-MNN/config.json 
```
# Ref
[mnn-llm](https://github.com/wangzhaode/mnn-llm)

[MNN](https://github.com/alibaba/MNN)