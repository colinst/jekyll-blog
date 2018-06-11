## Army Content
+ admin:**虹西**
+ date: **2018/04/20**

> #### RealName
> #### Avatars
> #### DaySign
    
## Main Content

### 1. Real Name
#### 1 Send msg
    {
        "uid": 4936,
        "data": "name",     
        "time": 1506421419,
        "command": "hall_updaterealname"
    }
#### 2 Recevie msg
    {
       "result": 0,                     //0-failed  1-success 
       "data": "name",     
       "detail": "detail messages",     //sometimes the detail will cotains more json objects(army object)
       "command": "hall_updaterealname"
    } 

### 2. Avatars
#### 1 Send msg
    {
        "uid": 4936,
        "data": "avatar",     
        "time": 1506421419,
        "command": "hall_update_avatar"
    }
#### 2 Recevie msg
    {
       "result": 0,                     //0-failed  1-success 
       "data": "avatar",     
       "detail": "detail messages",     //sometimes the detail will cotains more json objects(army object)
       "command": "hall_update_avatar"
    } 
  

### 3. DaySign
#### 1 Send msg
    {
        "uid": 4936,     
        "time": 1506421419,
        "command": "hall_daysign"
    }
#### 2 Recevie msg
    {
       "result": 0,                     //0-failed  1-success 
       "data": "times",     
       "detail": "detail messages",     //detial
       "command": "hall_daysign"
    }