---
layout: post
title: IdentityServer3 SSO使用记录
category : 技术分享
tagline: "Supporting tagline"
tags : [SSO]
---
{% include JB/setup %}

# IdentityServer3 SSO使用记录
---
* ### Ids3项目介绍
* ### Ids3的SSO基本使用
* ### Ids3使用中遇到的问题
***
## Ids3项目介绍:

> IdentityServer3是github上.net平台下,算下比较不错一个关于OpenId,Oauth开源项目,作者在这方面有多年的研究经验,版本也来到了V3;SSO是这个项目的一个附属功能,与Asp.Net集成得很友好,目前在工作中正好使用这个idead来解决公司内部系统之间的SSO,So记录下开发总结

## Ids3的SSO基本使用:
官方教程已经有MVC+WebApi的[教程](https://identityserver.github.io/Documentation/docsv2/overview/mvcGettingStarted.html),按照这个来很快就能让你的项目集成SSO,认证,授权功能

## Ids3使用中遇到的问题:
1. **在webforms下如何判断是否认证:** 只需要在`Page_Load`事件如下判断:  
```
if (!Request.IsAuthenticated)
        {
            HttpContext.Current.GetOwinContext().Authentication.Challenge(
                new AuthenticationProperties
                {
                    RedirectUri = Request.Url.AbsoluteUri
                },
                OpenIdConnectAuthenticationDefaults.AuthenticationType);
        }
```
2. **基于以上判断产生的另外一个问题:**由于webforms事件机制实现原因,以上这样判断还是会继续执行其他事件,不会立即跳转到SSO登录页面,目前我们采用的方法是在`if`里面加`Response.End();return;`
