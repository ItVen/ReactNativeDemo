# ReactNativeDemo
在原生adnroid上集成RN的Demo

#android 集成RN填坑

###添加依赖库时编译异常
错误提示 ： 

		  Warning:Conflict with dependency 'com.google.code.findbugs:jsr305'. Resolved versions for app (3.0.1) and test app (2.0.1) differ. See http://g.co/androidstudio/app-test-app-conflict for details.

	解决方案：

		android {
			...
		    configurations.all {
		        resolutionStrategy.force 'com.google.code.findbugs:jsr305:1.3.9'
		    }
		}
		
### 编写好RactActivityh后运行android程序会报错
错误提示：

		Caused by: java.lang.UnsatisfiedLinkError: could find DSO to load: libreactnativejni.so

解决办法，集成ndk

	android {
	    ...
	    defaultConfig {
	       ...
	        ndk {
	            abiFilters "armeabi-v7a", "x86"
	        }
	    }
    }
  
 这两个坑填完了就可以开启package 玩儿啦。
	
	react-native start
	
再在AS上启动应用 效果如下
![这里写图片描述](http://img.blog.csdn.net/20170823164025479?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMjc2MjM1MjE=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
