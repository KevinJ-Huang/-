#### 在pychram里找不到自己文件的库，但是在命令行中找不到
&emsp;&emsp; 在pycharm中可以找到自己文件下的库，在命令行中找不到，需要在自己相应的python文件里添加项目的根目录，如下所示：
```python
sys.path.append("/home/ustc-ee-huangjie/video-practice/hdrnet")
```
&emsp;&emsp; 这样就能在命令行里找到了。

#### undefined symbol：_ZN10tensorflow7strings6StrCatB5cxx11ERKNS0_8AlphaNumE、
一般认为是编译器g++不匹配造成的，添加下面的话到makefile里
```cmd
# Use flag -D _GLIBCXX_USE_CXX11_ABI=0 for gcc > 5
# Use flag -undefined dynamic_lookup for OSX
CFLAGS = -fPIC -I$(TF_INC) -O2
LDFLAGS = -L$(CUDA_HOME)/lib64 -lcudart
# Use flag -D _GLIBCXX_USE_CXX11_ABI=0 for gcc > 5
NVFLAGS = -DGOOGLE_CUDA=1 -x cu -Xcompiler -fPIC -I $(TF_INC) \
					-expt-relaxed-constexpr -Wno-deprecated-gpu-targets -ftz=true
```
或者
```
D_GLIBCXX_USE_CXX11_ABI=0
```
