##Platform Module
###Platform.OS
Platform.OS has two value: `ios` and `android`
Use this property to change something at runtime
    
    if(Platform.OS==='ios'){
    
    }
###Platform.select
This method takes an object as input :
    
    {
        ios:Any,
        android:Any
    }
You can use it in style creation or instantiate different component on specific platform
    
    var ComIOS
    var ComAndroid
    var Com =  Platfrom.select(
        {
            ios:ComIOS,
            android:ComAndroid
        }
        )

---
##specific file extension
Add a platform before `.js`, the system will automatically load the proper file.
    