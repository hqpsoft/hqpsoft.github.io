# automapper的使用
```
1:5.0版本的初始化配置改成如下方式了
Mapper.Initialize(cfg =>
           {
               cfg.CreateMap<User, UserDto>();
           })

2:在做查询的时候可以直接使用ProjectTo<UserDto>()映射
```

# EF提升查询效率的Tips
```
1:查询使用AsNoTracking(),意思是查询出来的数据just显示用.

2:
```