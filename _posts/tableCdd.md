## Army Content
+ admin:**虹西**
+ date: **2018/05/07**

## Main Content
### 1. Sit
#### 2 get type
    {
       "result": 1,                      // 
       "seat":3,                         //
       "detail": Array<User>,            //UserArray JSONObject        
       "data": "sit",
       "command": "msg_cdd"           
    }


### 2. Leave
#### 1 send type
    {
       "card": [0],                      
       "detail":0,                                            
       "data": "leave",
       "command": "msg_cdd"           
    }

#### 2 get type
    {
       "result": 1, 
       "seat":3,
       "detail": 1,                  // 1-nomalLeave  2-halfLeave                      
       "data": "leave",
       "command": "msg_cdd"           
    }


### 3. Ready
#### 1 send type
    {
       "card": [0],
       "detail":0,                          
       "data": "ready",
       "command": "msg_cdd"           
    }

#### 2 get type
    {
       "result": 1,                 // 0-failed 1-success
       "seat":3,  
       "detail": [2,2,0,0],         // ready arr                       
       "data": "ready",
       "command": "msg_cdd"           
    }


### 4. FaPai
#### 2 get type
    {
       "result": 1,                 // 0-failed 1-success
       "seat":3,                    //  
       "detail": [1,2,3..,13],      //count=13                                        
       "data": "fapai",
       "command": "msg_cdd"           
    }


### 5. Status
#### 1 send type
    {
       "card": [0],
       "detail":0,                          
       "data": "status",
       "command": "msg_cdd"           
    }

#### 2 get type
    {   
    }


### 6. DaPai
#### 1 send type
    {
       "card": [5],                 //cards                      
       "detail":0,                  //         
       "data": "call",              //call,follow,pass,switch           
       "command": "msg_cdd"           
    }
#### 2 get type
    {
       "result": 1,                 
       "seat":3,                    //seat
       "detail": [5],               //cards
       "data": "gang",              //call,follow,pass,switch
       "command": "msg_cdd"           
    }

### 6. multiples
#### get type