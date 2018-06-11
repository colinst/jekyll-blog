## DataBase
+ admin:**虹西**
+ date: **2018/03/21**

#### SHMUser
#### army
#### friends
#### goods
#### usergoods

### 1 User

#### 1.1 Key Columns

    uid,nickname,realname,avatar,hash,
    mail,phone,accounttype(google,yahoo,facebook),
    sex,level,viplevel,exp,expfashion,medal(0,1,2),
    coin,gem,bank,
    rid,aid,
    regiestertime,logintime,

#### 1.2 Create Table

### 2 Army
#### 2.1 Create Table
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
#### 2.2 Base Info
The table included 2 kinds of messages:  
&ensp;&ensp;    1.One is the army base infomation,the row's all attributes will almostly be filled;(like name,level,date,announcement...);   
&ensp;&ensp;    2.The other is the relatonship between army and users(message 1 can be look as the relationship between army and the army's leader);  
&ensp;&ensp;    2.1 Base messages2 generally filled three attributes include(aid,status,members).