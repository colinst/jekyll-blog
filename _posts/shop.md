## Army Content
+ admin:**虹西**
+ date: **2018/04/20**

> #### table
> #### else..

    
## Main Content
### 1. Think
#### 1.1 goods kind
    
    装扮-
        
        戒指（7天，永久）
        套装（7天，永久）
        花纹（7天，永久）
    
    货币-
    
        金币，钻石，mycard点数
        
    货币-礼物-
        
        别墅，钢琴，
        玛莎拉蒂，兰博基尼，
        包，香水，戒指，黑钻，水晶鞋
        

    道具卡-    [1天，7天]
    
        积分卡，金币卡，（加倍）
        补签卡，改名卡，
        
    箱子-

    
    非卖-
        碎片-
            季节-
            踏青春枝[]
            愚人节彩蛋[]
            新年吉子符[]
            童年棒棒冰[]
            
            影视特殊--
            中分裤头[红中]
            恶鬼上身符[]
            黄金万碎片[]
            战略露牌[]
            窥牌雷达[]
            布谷鸟，呖咕呖咕[]
            雀神的米粒[攒米粒，获得特殊道具]
                                    
        限定-
            5月限定周末卷-  
                
#### 1.2 group num id

    00000-
    110000-金币
    120000-钻石
    
    200000-道具
    210000-功能卡
    210001-改名卡
    210002-补签卡
    
    220000-加倍卡
    220001-双倍金币卡(1天)
    220007-双倍金币卡(7天)
    220011-双倍经验卡(1天)
    220017-双倍经验卡(7天)
    
    
    300000-装扮
    300000+发型
    300001-黑长直
    300002-波兰卷
    
    320000+上衣
    320001-燕尾服
    320002-羽绒服
    
    340000+裤子
    340001-灯笼裤
    340002-7分短
    
    360000+鞋子
    360001-水晶鞋
    360002-阿迪达斯
    
    380000+饰品
    380001-墨镜
    380002-蝴蝶结
    380003-兔耳朵
    380004-手镯
    
    400000-礼物
    400001-别墅
    400002-钢琴
    400003-玛莎拉蒂
    400004-兰博基尼
    
    500000-箱子
    500001-将神宝箱
    500002-麻神宝箱
    500003-雀神宝箱
    
    600000-非卖-特殊-任务
    600001-黄金骰碎片
    600002-幺鸡含枝
    
    660000-场景
    660001-苏伊士庄园
    660002-巴黎大教堂
    
### 1.3 tables
    
    goods           //商品表
    store           //仓库表
    fmcc            //加倍表（经验卡到期时间）
    historyShop     //购买历史

#### 1.3.1 goods
    
    gid,name,type,num,detial,status,
    price,unit,
    outdate,createDate,createUser,
    
#### 1.3.2 store

    uid,goods1,goods2.goods3...
       
#### 1.3.3 fmcc(Fast Moving Consumer Goods)

    uid,card1,card2,card3...

#### 1.3.4 shophistory
    
    id,uid,date,gid,
    price,num,total,currency,
    teget,type(购买/赠送)
    
### 2.work flow
#### 1. main functions

1.addGoods  
    GoodsMapper.goodsAdd(goods)  
    StoreMapper.goodsAdd(goods.gid)  
    &nbsp;if(goods.type=card)  
    cardsOutMapper.cardsAdd(goods.gid)  
    
2.getGoods
    GoodsMapper.goodsGet
    
3.getStore
    StoreMapper.storeGet

4.useGoods

#### 2. when user sign  
insert into store(uid) values uid
insert into fmcc(uid) values uid

#### 3. main goods detail
    
    礼物-
    兰博基尼，玛莎拉蒂，
    黑钻，戒指，
    波兰卷，蝴蝶结
       
    400001  "玛莎拉蒂"  "gift"     -1   8000
    400002  "兰博基尼"  "gift"     -1   7000
    400003  "黑钻"      "gift"     -1    500  
    400004  "戒指"      "gift"     -1    100
    300001  "波兰卷"    "hair"     -1
    380001  "蝴蝶结"    "wears"    -1
    
    //=================================
    110000 金币 
    120000 钻石       means
    200000 道具       funprop
    300000-装扮
    
    300000+发型       hair
    320000+上衣       clothes
    340000+裤子       trousers
    
    360000+鞋子       shoes
    380000+饰品       wears
        
    400000-礼物       gift
   
    500000-箱子       box
    
    600000-非卖-任务  mission 
    600001-黄金骰碎片
    
    660000-场景       scene