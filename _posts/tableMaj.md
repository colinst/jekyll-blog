## Army Content
+ admin:**虹西**
+ date: **2018/05/07**

+ online: 判断是否在线关键值为：mapSeesion
+ inRoom: 判断是否在房间关键值为：arrSeats
+ halfRoom: 判断是否有其他房间关键值为：mapHalfRoom

## Main Content

### 1. Sit
#### 2 get type
    {
       "result": 1,                      // 
       "seat":3,                         //
       "detail": Array<User>,            //UserArray JSONObject        
       "data": "sit",
       "command": "msg_maj"           
    }


### 2. Leave
#### 1 send type
    {
       "card": 0,                      
       "detail":0,                                            
       "data": "leave",
       "command": "msg_maj"           
    }

#### 2 get type
    {
       "result": 1,                 // 
       "seat":3,                         //
       "detail": 1                  // 1-nomalLeave  2-halfLeave                      
       "data": "leave",
       "command": "msg_maj"           
    }


### 3. Ready
#### 1 send type
    {
       "card": 0,                   // 0
       "detail":0,                  // 0                          
       "data": "ready",
       "command": "msg_maj"           
    }

#### 2 get type
    {
       "result": 1,                 // 0-failed 1-success
       "seat":3,                         //  
       "detail": Array<User>,                 // ready arr                       
       "data": "ready",
       "command": "msg_maj"           
    }


### 4. FaPai
#### 2 get type
    {
       "result": 1,                 // 0-failed 1-success
       "seat":3,                    //  
       "detail": JSONObject<        //
                    Array<start>,
                    Array<arr>,
                    Array<flower>   //4 Array
                    >,                                        
       "data": "fapai",
       "command": "msg_maj"           
    }


### 5. MoPai
#### 2 get type
    {
       "result": 1,                 //always=1
       "seat":3,                    //
       "detail": 0x37,               //pai
       "data": "mo",                //mo/hua
       "command": "msg_maj"           
    }
    {
       "result": 1,                 //always=1
       "seat":3,                    //
       "detail": 0x48,              //pai
       "data": "hua",
       "command": "msg_maj"           
    }


### 6. DaPai
#### 1 send type
    {
       "card": 0x05,                    //card number                      
       "detail":0,                      //when chi,chi's index         
       "data": "da",                    //da,chi,peng,gang,hu,pass,ting
       "command": "msg_maj"           
    }
#### 2 get type
    {
       "result": 1,                 
       "seat":3,                    //seat
       "detail": 0x37,              //card
       "data": "gang",              //da,chi,peng,gang,hu,pass,ting，hold
       "command": "msg_maj"           
    }

### 5. multiples
#### get type
    {
        "result": 1,                 //1
        "seat":3,                    //seatHu
        "detail": {
        
            "roundCur":1,
            "numTai":6,
            "taiTypes":["zimo","yise3shun"],
            "meansChange":[-180,0,0,180],
            "cardHand0":[3,34,54,37,33,4,23,7,51,18,17,7,8,38,21,3,20,0,0,0,0,0],
            "cardHand1":[17,6,6,3,49,37,22,53,2,1,20,5,24,36,37,8,0,0,0,0,0,0],
            "cardHand2":[1,5,50,39,52,5,21,52,20,19,49,51,41,18,9,40,0,0,0,0,0,0],
            "cardHand3":[39,22,41,2,9,53,33,8,23,52,39,19,25,19,34,51,0,0,0,0,0,0],
            "cardFlower0":[53,0,0,0,0,0,0,0],
            "cardFlower1":[0,0,0,0,0,0,0,0],
            "cardFlower2":[0,0,0,0,0,0,0,0],
            "cardFlower3":[55,0,0,0,0,0,0,0],
        },
        "data": "multiples",         //
        "command": "msg_maj"   
    }

    taiMapper= mapOf(
    
                "da4xi" to 24,
                "da3yuan" to 12,
                "xiao4xi" to 12,
                "xiao3yuan" to 6,
                "3yuantai"  to 2,
    
                "qing1se" to 12,
                "hun1se" to 6,
                "zi1se" to 16,
    
                "8xianguolai" to 16,
                "hua1" to 1, "hua2" to 2, "hua3" to 3,
                "hua4" to 4, "hua5" to 5, "hua6" to 6, "hua7" to 7,
                "wuziwuhua" to 2,
    
                "qinglaotou" to 16,
                "duanyao9" to 4,
                "hunlaotou" to 8,
                "3setongke" to 4,
                "3setongshun" to 4,
                "1qitongguan" to 4,
                "1sesanshun" to 6,
    
                "3angang" to 12,
                "4lianke" to 7,
                "5lianke" to 12,
    
                "5anke" to 12,
                "4anke" to 7,
                "3anke" to 3,
    
                "chunquandaiyao" to 8,
                "hunquandaiyao" to 4,
    
                "menqing" to 2,
                "zimo" to 2,
                "menqingzimo" to 5,
                "quanqiuren" to 3,
    
                "duting" to 2,
                "1fa"   to 1,
                "qianggang" to 2,
                "haidilaoyue" to 2,
                "hedilaoyu" to 2,
                "baopai" to 1
        )










## Member detail 
### 1. value 
    
    

### 2. function  
 

    fun OnUserSit(user: User)
    
    override fun SendData(seat: Int, msg: String) 
#### getNumPlayers
获取arrPlayers中null值的数量  
若为null, numNull++  
如果不为null,则检查对应arrSeats值是否为0，若为0改为1

    fun getNumPlayers():Int{
    
            var numNull=0
            for ((i,u) in arrPlayers.withIndex()){
                if (u==null){
                    numNull++
                }else{
                    if (arrSeats[i]==0)
                        arrSeats[i]=1
                }
            }
            return 4-numNull
    }

### 3. Logic
#### Legal Hu
    
* 步进分拆法：（注意：不带鬼牌）

1、将牌按连续性进行拆分，拆出的组合为3*n 或 3*n + 2，如果有例外，则不能胡。
2、检查数量为3*n的连续段是否满足胡牌条件，如果都能满足，再用方法3检查3*n+2  
3、在连续的牌中，牌张数为3*n + 2的张数拆出可能的将牌  
4、扣除将牌后，分别检查各连续的段是否满足胡牌

检查段的思路：  
   例：连续段为 1筒1筒1筒2筒3筒3筒4筒4筒5筒  
       数字表示为 31221  

   a、取3位数为key，从下表查询，如果有结果则扣除这个数字。  
      312取到结果330，则余下数字为1221  
   b、如果a步骤没有结果，则取2位数为key  
   c、如果b步骤没有结果，则取1位数为key  
   如果c失败，则不能胡  

   31221拆分全步骤：  
   312 = 300 余 1221  
   122 = 111 余 111  
   111 = 111 全部拆分完毕，能胡  

拆分表：  
local t = {  
    [3] = 3, [4] = 3,  
    [31] = 30, [32] = 30, 33 = 33, 34 = 33, 44 = 33,  
    [111] = 111, [112] = 111, [113] = 111, [114] = 114,  
    [122] = 111, [123] = 111, [124] = 111,  
    [133] = 111, [134] = 111,  
    [141] = 141, [142] = 141, [143] = 141, [144] = 144,  
    [222] = 222, [223] = 222, [224] = 222,  
    [233] = 222, [234] = 222,  
    [244] = 222,  
    [311] = 300, [312] = 300, [313] = 300, [314] = 300,  
    [322] = 300, [323] = 300, [324] = 300,  
    [331] = 330, [332] = 330, [333] = 333, [334] = 333,  
    [341] = 330, [342] = 330, [343] = 330, [344] = 333,  
    [411] = 411, [412] = 411, [413] = 411, [414] = 414,  
    [422] = 411, [423] = 411, [424] = 411,  
    [433] = 411, [434] = 411,  
    [441] = 441, [442] = 441, [443] = 441, [444] = 444  
}  

表格生成思路：

1、从边上取牌的数量  
2、如果是1，则取111  
3、如果是2，则取222  
4、如果是3，则取3  
5、如果是4，则取411  