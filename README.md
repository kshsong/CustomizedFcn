# CustomizedFcn
**use a custom transfer/activation function in NN fitting in matlab**

**将matlab神经网络工具箱中的激活函数改为自定义函数**

## 修改步骤如下


1. 将MATLAB自带的激活函数**tansig**函数文件和目录拷贝到自己的工作目录
   ```
   cd  /you_path/matlab-xx-version/toolbox/nnet/nnet/transfer/
   cp -fr transig.m +tansig/  /your_destination_path/
   chown -R your_group:your_name tansig.m +tansig/
   ```
2. 修改 **tansig.m** 为 **自定义函数名**，并同时修改 **+tansig** 为 **+自定义函数名/**，例如 **myfcn**
    ```
    mv tansig.m myfcn.m
    mv +tansig +myfcn
    ```
3. 修改 **myfcn.m** 以及 **+myfcn/** 里的 **xx.m** 文件

   3.1 修改 **myfcn.m**
   
       ```
       sed -i "s/tansig/myfcn/g" tansig.m
       ```
   
   3.2 进入 **+myfcn** 目录，根据需要修改里面的 **.m** 文件
   
      **将apply.m中的函数改为自定义函数(required)**

      **修改ActiveInputRange.m中函数的输入范围(required)**

      **修改outputRange.m中函数输出范围(required)**

      **修改backprop.m中反向传播的函数，即自定义函数对变量的导数(required)**

      **修改forwardprop.m中正向传播的函数(required)**

      **修改da_dn.m中的导函数定义(required)**

      **修改discontinuity.m中判断函数连续性(option)**
   
   **其他函数一般不需要修改**

   **本教程适用于Linux平台，Windows平台请参考Ref[1].**
   


## Reference
[1] [如何在matlab工具箱中自定义激活函数及其使用](https://blog.csdn.net/qq_42052630/article/details/132744143) 

[2] [How to use a custom transfer function in neural net training](https://ww2.mathworks.cn/matlabcentral/answers/56137-how-to-use-a-custom-transfer-function-in-neural-net-training)

[3] [How to customize Neural Networks' activation function](https://ww2.mathworks.cn/matlabcentral/answers/312900-how-to-customize-neural-networks-activation-function)
