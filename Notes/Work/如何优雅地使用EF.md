# automapper的使用

* 5.0版本的初始化配置改成如下方式了
Mapper.Initialize(cfg =>
           {
               cfg.CreateMap<User, UserDto>();
           })

* 在做查询的时候可以直接使用ProjectTo<UserDto>()映射


# EF提升查询效率的Tips

* 查询使用AsNoTracking(),意思是查询出来的数据just显示用.不过如果在查询的时候,
进行了投影操作, 且不包含实体(select里面投缘)的话, 也是进行了AsNoTracking(),官方解释如下:  
![](http://hqpsoft.github.io/images/asNoTracking.png)

