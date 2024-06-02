## Django 关于静态文件的那点儿事

Django 在关于静态文件方面主要阐述了两点，大家可以参考官网，官网说得很详细，但是我觉得有些地方还不够明确，以下记录下我的理解

一、如何管理静态文件（如图片、JavaScript、CSS）
二、如何部署静态文件

有关这方面的内容，我先贴下我的主要配置

1. settings.py

```python

    DEBUG = False
    
    STATIC_URL = '/static/' #
    
    STATICFILES_DIRS = [
        BASE_DIR / 'static',
    ]
    
    STATIC_ROOT = BASE_DIR / 'public'
    
    MEDIA_ROOT = BASE_DIR / "uploads"
    
    MEDIA_URL = "uploads/"

```

2. 我的linux服务器 nginx 配置

```nginx

	#引用反向代理规则，注释后配置的反向代理将无效

	include /www/server/panel/vhost/nginx/proxy/***/*.conf;



    location ^~ /static {
        
        #此处地址为 `python manage.py collectstatic` 静态文件收集地址，即 `STATIC_ROOT` 配置地址
        alias /www/wwwroot/txmabc/public;

    }

    location ^~ /uploads {
        #同上，配置好媒体文件所在地址
        alias /www/wwwroot/txmabc/uploads;
    }

```

