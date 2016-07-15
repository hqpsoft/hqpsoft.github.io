# 工具集合
* [tfs迁移到git的工具](http://git-tfs.com/)


# 疑难杂症solution
* 关于msbuild发布长度超过256的问题
```
C:\Program Files (x86)\MSBuild\14.0\Bin\Microsoft.Common.targets
在 <Otherwise>
 <PropertyGroup>下添加<IntermediateOutputPath>D:\Temp</IntermediateOutputPath>
 或者直接在项目的csproj的<PropertyGroup>添加也可以
 ```

           
