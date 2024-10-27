# Gemma2-MNN
## Build
### Linux
```bash
mkdir build
cd build
cmake .. 
make -j16
```

### Android
```bash
mkdir build
cd build
cmake .. -DBUILD_FOR_ANDROID=ON -DCMAKE_TOOLCHAIN_FILE=/path/to/ndk/build/cmake/android.toolchain.cmake
make -j16
```

# Ref
[mnn-llm](https://github.com/wangzhaode/mnn-llm)
[MNN](https://github.com/alibaba/MNN)