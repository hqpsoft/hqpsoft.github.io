# 工具集合
* [tfs迁移到git的工具](http://git-tfs.com/)


# 疑难杂症solution
* 关于msbuild发布提示文件路径长度超过256的问题
```
修改C:\Program Files (x86)\MSBuild\14.0\Bin\Microsoft.Common.targets
在 
<Otherwise>
 <PropertyGroup>
 下添加<IntermediateOutputPath>D:\Temp</IntermediateOutputPath>
 或者直接在项目的csproj的<PropertyGroup>添加也可以
 ```

* 关于CI发版, webconfig transfer转换与本地vs预览效果不一致的问题
```
关于这个问题, 通过排查找到的原因是site下的其他文件夹还有webconfig文件导致转换失败
```

* 关于CI部署的时候出现`Not possible to fast-forward, aborting`的问题
```
这个问题是pre分支和dev分支滞后了,2种解决方案:
1:删除pre,重新从master从创建分支,然后dev合并到pre
2:本地用命令执行下在dev分支下执行merge(git merge oringin/pre)
```

* 关于部署出现`The OutputPath property is not set for project "xxxx"问题`.
```
这个问题是webconfig transfer配置导致, 要配置成全局的
```

