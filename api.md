# 问答社区接口文档

## 一、用户部分
### 1. 验证
#### header
```http
POST  https://wx.idsbllp.cn/api/verify
Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "data": {
        "stuNum": "2016210xxx",
        "name": "李吉",
        "college": "通信与信息工程学院",
        "class": "01041602班",
        "classNum": "01041602",
        "gender": "男",
        "major": "0104",
        "grade": "2016",
        "idNum": "xxxxx"
    }
}
```

### 2. 获取用户信息
#### header
```http
POST  https://wx.idsbllp.cn/cyxbsMobile/index.php/Home/Person/search
Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "state": 200,
    "data": {
        "id": 2828,
        "stunum": "2016210xxx",
        "introduction": "An Android Developer",
        "username": "李吉",
        "nickname": "Jay",
        "gender": "男",
        "photo_thumbnail_src": "http://wx.idsbllp.cn/cyxbsMobile/Public/photo/thumbnail/1520430636_1133226083.png",
        "photo_src": "http://wx.idsbllp.cn/cyxbsMobile/Public/photo/1520430636_1133226083.png",
        "updated_time": "2018-05-05 23:15:35",
        "phone": "159235xxxxx",
        "qq": "14325xxxxx"
    }
}
```

## 二、问题部分
### 1. 提新问题
#### header
```http
POST  https://wx.idsbllp.cn/springtest/cyxbsMobile/index.php/QA/Question/add
Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |
| title | 这个代码太难写了 | 问题标题 |
| description | 代码是真的难 | 问题描述 |
| is_anonymous | 0 | 0不匿名,1匿名 |
| kind | 其他 | 问题类型,填写学习/情感/其他等几个大标题 |
| tags | PHP | 标签 |
| reward | 2 | 奖励分数,最低为1 |
| disappear_time | 2018-02-27 01:11:20 | 消失时间,yyyy-mm-dd HH:mm:ss形式 |

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "data": {
        "id": 53
    }
}
```

### 2. 首页问题列表
#### header
```http
POST  https://wx.idsbllp.cn/springtest/cyxbsMobile/index.php/QA/Question/getQuestionList
Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| page | 0 | 分页页码.0,1为第一页,不填默认为第一页 |
| size | 6 | 每页问题数,可以不填,不填为6个 |
| kind | 其他 | 填写大的类型,学习/情感/其他 |

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "data": [
        {
            "title": "又在写bug\\\\ue056",
            "description": "bug是真的多",
            "kind": "其他",
            "tags": "PHP",
            "reward": 2,
            "answer_num": 0,
            "disappear_at": "2019-02-27 01:11:20",
            "created_at": "2018-05-19 17:35:14",
            "is_anonymous": 0,
            "id": 52,
            "photo_thumbnail_src": "",
            "nickname": "。",
            "gender": "女"
        }
    ]
}
```

### 3. 取消提问
#### header
```http
POST  https://wx.idsbllp.cn/springtest/cyxbsMobile/index.php/QA/Question/cancelQuestion
Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |
| question_id | 6 | 问题id,填写返回字段里面的id |

#### response-body
```json
{
    "status": 200,
    "info": "success"
}
```

### 4. 问题详细页面
#### header
```http
POST  https://wx.idsbllp.cn/springtest/cyxbsMobile/index.php/QA/Question/getDetailedInfo
Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |
| question_id | 19 | 填写问题id |

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "data": {
        "is_self": 0,
        "title": "这个代码太难写了\\\\ue056",
        "description": "代码是真的难",
        "reward": "2",
        "disappear_at": "2018-04-27 02:22:22",
        "tags": "PHP",
        "kind": "其他",
        "photo_urls": [],
        "questioner_nickname": "。",
        "questioner_photo_thumbnail_src": "",
        "questioner_gender": "女",
        "answers": [
            {
                "id": "10",
                "nickname": "Jay",
                "photo_thumbnail_src": "http://wx.idsbllp.cn/cyxbsMobile/Public/photo/thumbnail/1503374869_593154551.png",
                "gender": "男",
                "content": "菜",
                "created_at": "2018-04-22 14:08:50",
                "praise_num": "0",
                "comment_num": "0",
                "is_adopted": "0",
                "is_praised": 0,
                "photo_url": []
            }
        ]
    }
}
```
> 注：此接口默认只会返回6个回答，更多的回答通过回答部分的接口获取

### 5. 问题图片上传
#### header
```http
POST  https://wx.idsbllp.cn/springtest/cyxbsMobile/index.php/QA/Question/uploadPicture
Content-Type: multipart/form-data
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |
| question_id | 5 | 问题id |
| photo1 | image file | 图片上传, 多图片上传时, 直接把参数改成photo2 photo3 ,切记此处文件参数只能为photo+数字格式,后端做了正则校验 |
| photo2 | image file | 图片上传, 多图片上传时, 直接把参数改成photo2 photo3 ,切记此处文件参数只能为photo+数字格式,后端做了正则校验 |

> 注：图片最多上传三张

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "data": [
        "https://wx.idsbllp.cn/springtest/cyxbsMobile/Public/QA/Question/5b0410a7e49de.jpg"
    ]
}
```

## 三、答案部分
### 1. 回答问题
#### header
```http
POST  https://wx.idsbllp.cn/springtest/cyxbsMobile/index.php/QA/Answer/add
Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |
| content | 测试 | 回答内容 |
| question_id | 7 | 所回答的问题 |

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "data": "12"    //成功返回问题id
}
```
> 注：同一个人同一个问题只能回答一次

### 2. 回答列表补充
#### header
```http
POST  https://wx.idsbllp.cn/springtest/cyxbsMobile/index.php/QA/Answer/getAnswerlist
Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |
| page | 0 | 分页页码.0,1为第一页,不填默认为第一页 |
| size | 6 | 每页问题数,可以不填,不填为6个 |
| question_id | 5 | 问题id |

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "data": [
        {
            "id": "12",
            "user_id": "17",
            "content": "测试",
            "created_at": "2018-05-22 20:45:37",
            "praise_num": "0",
            "comment_num": "0",
            "is_adopted": "0",
            "photo_url": "https://wx.idsbllp.cn/springtest/cyxbsMobile",
            "photo_thumbnail_src": "http://wx.idsbllp.cn/cyxbsMobile/Public/photo/thumbnail/1465723329_1200486922.png",
            "nickname": "Camesa",
            "gender": "女"
        }
    ]
}
```

### 3. 点赞
#### header
```http
POST  https://wx.idsbllp.cn/springtest/cyxbsMobile/index.php/QA/Answer/praise
Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |
| answer_id | 7 | 答案id |

#### response-body
```json
{
    "status": 200,
    "info": "success"
}
```

### 4. 取消点赞
#### header
```http
POST  https://wx.idsbllp.cn/springtest/cyxbsMobile/index.php/QA/Answer/cancelPraise
Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |
| answer_id | 7 | 答案id |

#### response-body
```json
{
    "status": 200,
    "info": "success"
}
```
### 5. 获取评论列表
#### header
```http
POST  https://wx.idsbllp.cn/springtest/cyxbsMobile/index.php/QA/Answer/getRemarkList
Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |
| answer_id | 7 | 填写答案id |

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "data": [
        {
            "content": "测试",
            "created_at": "2018-02-24 01:45:56",
            "nickname": "溟\\\\n濛",
            "photo_thumbnail_src": "http://wx.idsbllp.cn/cyxbsMobile/Public/photo/thumbnail/1503374918_2132490885.png",
            "gender": "男"
        },
        {
            "content": "测试2",
            "created_at": "2018-02-24 01:48:42",
            "nickname": "溟\\\\n濛",
            "photo_thumbnail_src": "http://wx.idsbllp.cn/cyxbsMobile/Public/photo/thumbnail/1503374918_2132490885.png",
            "gender": "男"
        }
    ]
}
```

### 6. 评论答案
#### header
```http
POST  https://wx.idsbllp.cn/springtest/cyxbsMobile/index.php/QA/Answer/remark
Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |
| answer_id | 5 | 答案id |
| content | 测试3 | 评论内容 |

#### response-body
```json
{
    "status": 200,
    "info": "success"
}
```

### 7. 采纳答案
#### header
```http
POST  https://wx.idsbllp.cn/springtest/cyxbsMobile/index.php/QA/Answer/adopt
Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |
| answer_id | 4 | 答案id |
| question_id | 7 | 问题id |

#### response-body
```json
{
    "status": 200,
    "info": "success"
}
```

### 8. 答案图片上传
#### header
```http
POST  https://wx.idsbllp.cn/springtest/cyxbsMobile/index.php/QA/Answer/uploadPicture
Content-Type: multipart/form-data
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 认证字段,填用户学号 |
| idNum | 2xxxxx | 同上,填用户身份证后六位 |
| answer_id | 3 | 答案id |
| photo1 | image file | 图片上传, 多图片上传时, 直接把参数改成photo2 photo3 ,切记此处文件参数只能为photo+数字格式,后端做了正则校验 |
| photo2 | image file | 图片上传, 多图片上传时, 直接把参数改成photo2 photo3 ,切记此处文件参数只能为photo+数字格式,后端做了正则校验 |

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "data": [
        "https://wx.idsbllp.cn/springtest/cyxbsMobile/Public/QA/Answer/5b0412fddd938.jpg"
    ]
}
```

## 四、课表部分
### 1. 个人课表查询
#### header
```http
POST  https://wx.idsbllp.cn/api/kebiao
Content-Type: Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stu_num | 201621xxxx | 用户学号 |
| forceFetch | true or false | 可选参数，值为true时强制从教务在线拉取课表（数据较慢），false时从服务器拉取课表缓存数据 |

#### response-body
```json
{
    "status": 200,
    "version": "16.9.4",
    "term": "2017-2018学年第2学期",
    "stuNum": "2016210xxx",
    "cachedTimestamp": 1527003165462,
    "outOfDateTimestamp": 1527607965462,
    "data": [
        {
            "hash_day": 0,      //day的数值表示
            "hash_lesson": 0,   //lesson的数值表示
            "begin_lesson": 1,
            "day": "星期一",
            "lesson": "一二节",
            "course": "通信软件开发与应用(1)",
            "teacher": "罗文丰",
            "classroom": "4403",
            "rawWeek": "1-16周",
            "weekModel": "all", //all, single(单周) or double（双周）
            "weekBegin": 1,
            "weekEnd": 16,
            "type": "必修",
            "period": 2,
            "_id": "5b04381de0800855200fd7fb",
            "week": [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16]
        }
    ],
    "nowWeek": 12
}
```

### 2. 获取备忘
#### header
```http
POST  https://wx.idsbllp.cn/cyxbsMobile/index.php/Home/Person/getTransaction
Content-Type: Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 用户学号 |
| idNum | 1xxxxx | 用户身份证后6位 |

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "state": 200,
    "term": 201720182,
    "stuNum": "2016210xxx",
    "data": [
        {
            "id": 15270450378678627,
            "time": 5,  //remind time
            "title": "this is a title",
            "content": "this is a content",
            "updated_time": "2018-05-23 11:10:38",
            "date": [
                {
                    "class": 0, //1、2节
                    "day": 5,   //周六
                    "week": [
                        12
                    ]
                }
            ]
        }
    ]
}
```

### 3. 添加备忘
#### header
```http
POST  https://wx.idsbllp.cn/cyxbsMobile/index.php/Home/Person/addTransaction
Content-Type: Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 用户学号 |
| idNum | 1xxxxx | 用户身份证后6位 |
| time | 5 | 提前几分钟提醒 |
| title | title | 标题 |
| content | content | 内容 |
| id | 15270450378678628 | 备忘的唯一标识，生成规则：`System.currentTimeMillis() + "" + (new Random().nextInt(9999 - 1000 + 1) + 1000)` |
| date | `[{"day":1,"week":1,"class":"1"},{"day":1,"week":"1,2","class":"2"}]` | 参照获取备忘接口的date字段 |

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "state": 200,
    "id": 15270450378678628
}
```

### 3. 编辑备忘
#### header
```http
POST  https://wx.idsbllp.cn/cyxbsMobile/index.php/Home/Person/addTransaction
Content-Type: Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 用户学号 |
| idNum | 1xxxxx | 用户身份证后6位 |
| time | 5 | 提前几分钟提醒 |
| title | title | 标题 |
| content | content | 内容 |
| id | 15270450378678628 | 需要修改的备忘id |
| date | `[{"day":1,"week":1,"class":"1"},{"day":1,"week":"1,2","class":"2"}]` | 参照获取备忘接口的date字段 |

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "state": 200
}
```

### 4. 删除备忘
#### header
```http
POST  https://wx.idsbllp.cn/cyxbsMobile/index.php/Home/Person/deleteTransaction
Content-Type: Content-Type: application/x-www-form-urlencoded
```

#### request-body
| key | value | description |
| --- | ----- | ----------- |
| stuNum | 201621xxxx | 用户学号 |
| idNum | 1xxxxx | 用户身份证后6位 |
| id | 15270450378678628 | 需要删除的备忘id |

#### response-body
```json
{
    "status": 200,
    "info": "success",
    "state": 200
}
```