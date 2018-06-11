---
layout: post
title:  "Army test!"
date:   2017-06-12 17:05:13 +0000
categories: jekyll update2
---


## Army Content
+ admin:**虹西**
+ date: **2018/03/09**

> #### database
> #### maintype
> #### hall
> #### admin
> #### members
> #### else..

## DataBase Table
### 0. All Columns
#### 0.1 Create Table
    -- auto-generated definition
    DROP TABLE ninedt_army;
    CREATE TABLE ninedt_army
    (
      id           INT(64) AUTO_INCREMENT
      COMMENT '序列id'
        PRIMARY KEY,
      aid          INT                     NOT NULL
      COMMENT 'army_id',
      adminid      INT                     NULL
      COMMENT '管理员id',
      level        INT                     NULL
      COMMENT '等级_未定义',
      num          INT DEFAULT '1'         NULL
      COMMENT '军团数量 ',
      status       INT                     NOT NULL
      COMMENT '关系状态 0-解散/未成立/清除 1-成立 2-主动加入 3-被动邀请',
      name         VARCHAR(64) DEFAULT ''  NULL
      COMMENT '军团名称',
      date         VARCHAR(20) DEFAULT ''  NULL
      COMMENT '创建日期',
      announcement VARCHAR(255) DEFAULT '' NULL
      COMMENT '宣言',
      store        INT(64) DEFAULT '0'     NULL
      COMMENT '军团商店-未定义',
      donate       INT(64) DEFAULT '0'     NULL
      COMMENT '捐赠-未定义',
      donatecoin   INT(64) DEFAULT '0'     NULL
      COMMENT '捐赠金币',
      donategem    INT(64) DEFAULT '0'     NULL
      COMMENT '捐赠钻石',
      competcoin   INT(64) DEFAULT '0'     NULL
      COMMENT '军团赛获得金币',
      competgem    INT(64) DEFAULT '0'     NULL
      COMMENT '军团赛获得钻石',
      grain        INT(64) DEFAULT '0'     NULL
      COMMENT '军粮',
      experience   INT(64) DEFAULT '0'     NULL
      COMMENT '经验/积分',
      members      INT(64)                 NOT NULL
      COMMENT '成员ID',
      expcenter    INT(64) DEFAULT '0'     NULL
      COMMENT '军团中心',
      expstore     INT(64) DEFAULT '0'     NULL
      COMMENT '军团商店',
      expbattle    INT(64) DEFAULT '0'     NULL
      COMMENT '军团战',
      expmill      INT(64) DEFAULT '0'     NULL
      COMMENT '军团作坊',
      exptree      INT(64) DEFAULT '0'     NULL
      COMMENT '科技树',
      avatars      INT(64) DEFAULT '0'     NULL
    );
#### 0.2 Base Info
The table included 2 kinds of messages:  
&ensp;&ensp;    1.One is the army base infomation,the row's all attributes will almostly be filled;(like name,level,date,announcement...);   
&ensp;&ensp;    2.The other is the relatonship between army and users(message 1 can be look as the relationship between army and the army's leader);  
&ensp;&ensp;    2.1 Base messages2 generally filled three attributes include(aid,status,members).
#### 0.3 Functions
##### 0.3.1 Army number
Count the rows where aid is the id and status=1.

     UPDATE ninedt_army SET num= (  SELECT a.*FROM(SELECT count(*)FROM ninedt_army WHERE status = 1 AND aid = 400371) a)WHERE members=adminid and aid=400371
##### 0.3.2 Authority
Haven't do.
The mind is make the attribute 'adminid' to distinguish leader and lowleader

##### 0.3.3 Level
Update the donatecoin and donategem,and Front-End Divide every level section
##### 0.3.4 Infrastructure
expcenter    INT(64) DEFAULT '0'     NULL COMMENT '军团中心',  
expstore     INT(64) DEFAULT '0'     NULL COMMENT '军团商店',  
expbattle    INT(64) DEFAULT '0'     NULL COMMENT '军团战',  
expmill      INT(64) DEFAULT '0'     NULL COMMENT '军团作坊',
exptree      INT(64) DEFAULT '0'     NULL COMMENT '科技树',  
avatars      INT(64) DEFAULT '0'     NULL  

&ensp;&ensp;Count the five attributes to collect.
##### 0.3.5 Army Competition
Haven't do.
&ensp;&ensp;Count and update the experience
##### 0.3.5 else


## FRONT-END
## Main Content
### 1. Main type
#### 1.1 send type
    {
        "uid": 4936,
        "data": "trycreate|0|avatarid|name|announcement",     
        "time": 1506421419,
        "command": "hall_army_msg"
    }
#### 1.2 get type
    {
       "result": 1,                     //0-failed  1-success 
       "data": "trycreate",     
       "detail": "trycreate success",   //sometimes the detail will cotains more json objects(army object)
       "command": "hall_army_msg"
    }
    
### 2. Hall
#### 2.1 recommend
    "data": "recommend|0|0",      
#### 2.2 getArmys
#### 2.3 getrank
     "data": "getrank|0|0",

### 3. Admin
#### 3.1 trycreate
    "data": "trycreate|0|avatarid|name|announcement",       //(int)avatarid,(String)name-announcement         
#### 3.2 trydissolve
    "data": "trydissolve|0|aid",      //(int)aid         
#### 3.3 tryinvite
    "data": "tryinvite|fuid|aid",     //(int)fuid-aid    
#### 3.4 agreejoin
    "data": "agreejoin|fuid|aid",     //(int)fuid-aid
#### 3.5 refusejoin
    "data": "refusejoin|fuid|aid",     //(int)fuid-aid
#### 3.6 tryremove
    "data": "tryremove|fuid|aid",     //(int)fuid-aid
#### 3.7 watch
    "data": "watch|0|aid",     //(int)aid


#### 3.5 trylevelup
#### 3.5 tryleveldown

### 4. Member
#### 4.1 tryjoin
    "data": "tryjoin|0|aid",          //(int)aid
#### 4.2 agreeinvite
    "data": "agreeinvite|0|aid",      //(int)aid
#### 4.21 refuseinvite
    "data": "refuseinvite|0|aid",      //(int)aid
#### 4.3 leave
    "data": "leave|0|aid",            //(int)aid
#### 4.4 default
    "data": "default|0|0",                
#### 4.5 info
    "data": "info|0|aid",                //(int)aid
#### 4.6 members
    "data": "members|0|aid",                //(int)aid
    
