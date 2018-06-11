## Army Content
+ admin:**虹西**
+ date: **2018/05/07**

> #### create
> #### join


## Main Content

### 1. Create
#### 1 get type
    {
       "result": 666666,                //0-failed  209976-roomId
       "detail":"create success"        //explain
       "data": "create",
       "command": "hall_room"           
    }

#### 2 send type
##### 1 send type[Maj]
    {
        "type": "maj",                //maj/cdd/ssz/nn...             
        "detail": {
                "di": "50",         //50,300
                "tai": "20",        //20,100
                "round": "1",       //1,4,8,16
                "pwd": "",          //""  "password"
                
                "time":"2",         //2,3,5,7                
                "ting":"",          //true,false-限听
                "zimo":"",          //true,false-限自摸
                "bao":"",           //true,false-宝牌
                "men":""            //true,false-门骰加倍
                  },
        "data": "create",
        "command": "hall_room"
    }

##### 2 send type[Cdd]
    {
        "type": "cdd",             
        "detail": {
                "di": "50",         //50,200,500
                "time": "20",       //4,6,10
                "round": "1",       //1,4,8,16
                "pwd": "",          //""  "password"
                  },
        "data": "create",
        "command": "hall_room"
    }


### 2. Join
#### 1 send type
    {
      "type": "",                       //pwd
      "detail": 666666,                 //roomId
      "data": "join",
      "command": "hall_room"
    }

#### 2 get type
    {
       "result": 666666,                //0-no room 1-success 2-started 3-no seat 4-wrong
       "detail":"join success"          //0-no room 1-success 2-started 3-no seat 4-wrong
       "data": "join",                  
       "command": "hall_room"
    }
result code->
0       ->Send(agent, Msg(resultJoin,"no room","join","hall_room"))
1       ->Send(agent, Msg(resultJoin,"success","join","hall_room"))
2       ->Send(agent, Msg(resultJoin,"game started","join","hall_room"))
3       ->Send(agent, Msg(resultJoin,"no seat","join","hall_room"))
4       ->Send(agent, Msg(resultJoin,"wrong","join","hall_room"))
5       ->Send(agent, Msg(resultJoin,"wrong pwd","join","hall_room"))

### 3. List
#### 1 send type
##### 1 send type[maj]
    {
      "type": "maj",                                
      "detail":{
               "di": "50",              //0,50,300       
               "tai": "20",             //0,20,100
               "round": "1",            //1,4,8,16...
               },
      "data": "list",
      "command": "hall_room"
    }
##### 2 send type[cdd]
    {
      "type": "cdd",                                
      "detail":{
               "di": "50",              //50,200,500       
               "time": "20",            //4,6,10
               "round": "1",       
               },
      "data": "list",
      "command": "hall_room"
    }    
    
#### 2 get type
    {
      "result": 2,                      //room's number
      "detail": [
        362772,                         //rid Arrays
        682705
      ],
      "data": "list",
      "command": "hall_room"
    }

### 4. Current  (==old.hall_user_room)
#### 1 send type
    {
        "type": "",
        "detail": 0,
        "data": "current",
        "command": "hall_room"
    }
#### 2 get type
    {
        "result": 2,                      //room's number,0==null
        "detail": [
            362772,                       //rid Arrays[maj's rid,ssz's rid]
            682705
        ],
        "data": "current",
        "command": "hall_room"
    }
