# 一:EF7
## (1)数据迁移命令
* 先执行`dnx ef migrations add Describe` 然后再执行`dnx ef database update`.Describe会生成yyyy-MM-dd_Describe的类,方便管理每次迁移记录


## (2)EF上下文注册:在`Startup`启动类的`ConfigureServices`方法中添加如下:
<pre><code>
services.AddEntityFramework()
                .AddSqlServer()
                .AddDbContext<VNextContext>(options => options.UseSqlServer(connection));
</code></pre>
然后可以通过构造函数注入方式使用 e.g.
<pre><code>
public class HomeController : Controller
    {
        private VNextContext _context;
        public HomeController(VNextContext context)
        {
            _context = context;
        }
    }
</code></pre>

## (3)依赖注入:在`Startup`启动类的`ConfigureServices`方法中直接注入` services.AddTransient<IUserSvc, UserSvc>();`
默认有4种生命周期类型:
> Instance	任何时间都只能使用特定的实例对象，开发人员需要负责该对象的初始化工作。  
Transient	每次都重新创建一个实例。  
Singleton	创建一个单例，以后每次调用的时候都返回该单例对象。  
Scoped	    在当前作用域内，不管调用多少次，都是一个实例，换了作用域就会再次创建实例，类似于特定作用内的单例。  