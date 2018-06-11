## Army Content
+ admin:**虹西**
+ date: **2018/04/20**

> #### sign
> #### login
> #### resign
> #### relogin


## Main Content

### 1. Sign
#### 1 send type
    {
          "account": "colinst@qq.com",  //email (^([a-z0-9A-Z]+[-|\.]?)+[a-z0-9A-Z]@([a-z0-9A-Z]+(-[a-z0-9A-Z]+)?\.)+[a-zA-Z]{2,}$)
          "hash": "01234567890123456789012345678901",             
                                        //length=32
          "device": "dsfa56lgio56346h", //devicecode
          "hardware": "android",        //android,ios
          "data": "email",              //1.email
                                        //2.1234567  (when return result=1,data=1,command=hall_sign)
          "nick": "nick",               //nick
          "command": "hall_sign"
    }
#### 2 get type
    {
       "result": 0,                     //0-failed  1==code had send 
       "data": 2,
                                        //0- wrong mail form
                                        //1-code had send                        
                                        //2-mail is sgined/nick has been used
                                        //3-time out
                                        //4-illegal request
                                        //5-wrong mailcode
                                        //6-sign data msg wrong
       "detail": "detail messages",     //sometimes the detail will cotains more json objects(army object)
       "command": "hall_sign"           //hall_sign,hall_sign_in(is login)
    }



### 2.Login
#### 1 send type
    {
      "account": "colinst@qq.com",      //fast->("*******"),email->("**@**.com"),google->("accountGG"),facebook->("accountFB"),yahoo->("accountYH")
      "hash": "123123",                 //email=hash fast=************
      "device": "dfgd2l54j2lk345k2j",   //must cotain !
      "hardware": "android",            //android and ios !
      "data": "email",                  //fast,email,google,facebook,yahoo
      "command": "hall_login"
    }
#### 2 get type
    {
       "result": 4900,                  //0-failed  else==uid 
       "data": "commend",               //0- wrong input
                                        //4- illegal request
                                        //user JSONObject
       "detail": "detail messages",     //some examplain
       "command": "hall_sign_in"
    }

   
   
### 3.ReSign
#### 1 send type
    {
      "account": "colinst@qq.com",      //email
      "hash": "0123456789
               0123456789
               0123456789
               01",                     //new hash
      "device": "dfgd2l54j2lk345k2j",   //
      "hardware": "android",            //name's
      "data": "email",                  //email or 1234567
      "command": "hall_resign"
    }
#### 2 get type
    {
       "result": 0,                     //0-failed  1-success  2-mailCode had sent
       "data": 0,                       
                                        //0- no this mail
                                        //3-time out
                                        //4-illegal request
                                        //5-wrong mailcode
                                        //7-have not fill realname
                                        //8-wrong name
                                        //9-dba wrong
       "detail": "detail messages",     //
       "command": "hall_resign"         //
    }

### 4.Relogin
#### get type
    {
        "result": 0,                    // just close client
        "data": 0,                                                               
        "detail": "relogin",                
        "command": "hall_relogin"       //There has reloginTest in sign,resign,loginF
    }

