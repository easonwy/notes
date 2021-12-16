# C端接口文档

## 1. API V1 接口说明

- 接口基准地址：`http://wuyi276.cn.utools.club/api/`
- 服务端已开启 CORS 跨域支持
- API V1 认证统一使用 Token 认证
- 需要授权的 API ，必须在请求头中使用 `token` 字段提供 `token` 令牌
- 使用 HTTP Status Code 标识状态
- 数据返回格式统一使用 JSON

### 1.1. 支持的请求方法

- GET（SELECT）：从服务器取出资源（一项或多项）。
- POST（CREATE）：在服务器新建一个资源。
- PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）。
- PATCH（UPDATE）：在服务器更新资源（客户端提供改变的属性）。
- DELETE（DELETE）：从服务器删除资源。
- HEAD：获取资源的元数据。
- OPTIONS：获取信息，关于资源的哪些属性是客户端可以改变的。

### 1.2. 通用返回状态说明

| *状态码* | *含义*                | *说明*   |
| -------- | --------------------- | -------- |
| 0        | OK                    | 请求成功 |
| 500      | INTERNAL SERVER ERROR | 内部错误 |
| 400      |                       |          |

### 1.3. 统一响应模型

| 返回字段 | 字段类型     | 说明                       |
| :------- | :----------- | :------------------------- |
| code     | int          | 返回状态码                 |
| msg      | string       | 返回消息。失败返回失败原因 |
| data     | object/array | 返回数据                   |

### 1.4. 分页字段说明

| 返回字段   | 字段类型 | 说明       |
| :--------- | :------- | :--------- |
| total | int      | 总记录数   |
| pageSize   | int      | 每页记录数 |
| totalPage  | int      | 总页数     |
| pageNum | int      | 当前页数   |
| list       | ?        | 列表数据   |

### 1.5. 统一请求Header

| 参数  | 必选 | 类型   | 位置   | 说明                |
| :---- | :--- | :----- | ------ | ------------------- |
| token | true | string | header | 登录之后拿到的token |

## 2. 登录相关

### 2.1. 获取手机验证码

###### 接口功能
> 获取手机验证码，绑定手机号用。有效期10分钟，过期后重新获取。 

###### URL
> [http://wuyi276.cn.utools.club/api/h5/auth/phone/verifyCode](http://wuyi276.cn.utools.club/api/h5/auth/phone/verifyCode)

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
> | 参数  | 必选 | 类型   | 位置 | 说明   |
> | :---- | :--- | :----- | ---- | ------ |
> | mobile | true | string | URL  | 手机号 |

###### 返回字段
> | 返回字段 | 字段类型 | 说明                       |
> | :------- | :------- | :------------------------- |
> | code     | int      | 返回状态码                 |
> | msg      | string   | 返回消息。失败返回失败原因 |
> | data     | boolean  | 是否发送成功               |

###### 接口示例
> 地址：[http://wuyi276.cn.utools.club/api/h5/auth/phone/verifyCode](http://wuyi276.cn.utools.club/api/h5/auth/phone/verifyCode)
``` javascript
{
    "code": 0,
    "msg": "sucess",
    "data": true
}
```

### 2.2. 绑定手机号

###### 接口功能
> 提交手机号绑定请求

###### URL
> [http://wuyi276.cn.utools.club/api/h5/auth/phone/confirm](http://wuyi276.cn.utools.club/api/h5/auth/phone/confirm)

###### 支持格式
> JSON

###### HTTP请求方式
> POST

###### 请求参数
> | 参数       | 必选 | 类型   | 说明           |
> | :--------- | :--- | :----- | -------------- |
> | mobile     | ture | string | 待绑定的手机号 |
> | verifyCode | true | string | 验证码         |

###### 返回字段
> | 返回字段 | 字段类型 | 说明                       |
> | :------- | :------- | :------------------------- |
> | code     | int      | 返回状态码                 |
> | msg      | string   | 返回消息。失败返回失败原因 |
> | data     | boolean  | 是否绑定成功               |

###### 接口示例
> 地址：[http://wuyi276.cn.utools.club/api/h5/auth/phone/confirm](http://wuyi276.cn.utools.club/api/h5/auth/phone/confirm)
``` javascript
{
    "code": 0,
    "msg": "绑定成功",
    "data": true
}
```

### 2.3. 获取微信登录授权页面URL

###### 接口功能
> 获取微信登录授权页面URL，此接口会自动跳转到微信授权登录页面
> 参考文档：
>
> - https://blog.csdn.net/BThinker/article/details/81153686

###### URL
> [http://wuyi276.cn.utools.club/api/h5/wxAuth/auth](http://wuyi276.cn.utools.club/api/h5/wxAuth/auth)

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
> N/A

###### 返回字段
> N/A

###### 接口示例
> 地址：[http://wuyi276.cn.utools.club/api/h5/wxAuth/auth](http://wuyi276.cn.utools.club/api/h5/wxAuth/auth)

### 2.4. 微信登录回调接口

###### 接口功能
> 微信公众号登录系统， 授权登录成功后，微信会回调词接口传回登录相关的信息(code, state), 然后调用微信接口或者access_token, 成功后返回用户的相关基本信息。 并进行业务登录，成功后跳转到登录后的默认页面。
>
> 参考文档：
>
> - https://blog.csdn.net/BThinker/article/details/81153686

###### URL
> [http://wuyi276.cn.utools.club/api/h5/wxAuth/callback](http://wuyi276.cn.utools.club/api/h5/wxAuth/callback)

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
> | 参数     | 必选 | 类型   | 说明       |
> | :------- | :--- | :----- | ---------- |
> | state | ture | string |  |
> | code | ture | string |      |

###### 返回字段
> N/A

###### 接口示例
> 地址：[[http://wuyi276.cn.utools.club/api/h5/wxAuth/callback](http://wuyi276.cn.utools.club/api/h5/wxAuth/callback)]

## 3. 首页

### 3.1. 职位搜索

###### 接口功能
> 搜索职位列表

###### URL
> [http://wuyi276.cn.utools.club/api/h5/job/search](http://wuyi276.cn.utools.club/api/h5/job/search)

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
> | 参数     | 必选  | 类型   | 说明               |
> | :------- | :---- | :----- | ------------------ |
> | keywords | ture  | string | 职位关键字         |
> | pageSize | false | number | 每页大小。默认为20 |
> | pageNum  | false | number | 当前页码           |

###### 返回字段
> | 返回字段        | 字段类型  | 说明           |
> | :-------------- | :-------- | :------------- |
> | jobId           | string    | 职位ID         |
> | title           | string    | 职位标题       |
> | salaryRange     | string    | 薪资范围       |
> | tags            | string[]  | 职位标签       |
> | tagIds          | integer[] | 职位标签ID集合 |
> | unitPrice       | string    | 单价           |
> | travelAllowance | string    | 7天车贴金额    |
> | bannerUrl       | string    | banner图片URL  |
> | publishTime     | string    | 发布时间       |

###### 接口示例
> 地址：[http://wuyi276.cn.utools.club/api/h5/job/search](http://wuyi276.cn.utools.club/api/h5/job/search)
``` javascript
{
    "code": 0,
    "msg": "success",
    "data": {
        "total": 200,
        "pageSize": 10,
        "totalPage": 20,
        "pageNum": 1,
        "list": [
            {
                "jobId": "123131",
                "title": "昆山城南富士康小时工B",
                "salaryRange": "6000-7000",
                "tags": [
                    "18-45岁",
                    "坐班多",
                    "不做厂车"
                ],
                "tagIds": [
                    600,
                    3,
                    4
                ],
                "unitPrice": "20每小时",
                "travelAllowance": "7/100",
                "bannerUrl": "https://cos.liangdaidai.com/company/fastdfs/10323bb0-6a9e-411a-84d3-95122f786deb-1503244501094.jpg",
                "publishTime": "2021-05-01 12:00:00"
            }
        ]
    }
}
```

###  3.2. 职位列表查询

###### 接口功能
> 获取职位列表

###### URL
> http://wuyi276.cn.utools.club/api/h5/job/list

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
> | 参数 | 必选 | 类型 | 说明                                             |
> | :--- | :--- | :--- | ------------------------------------------------ |
> | type | true | int  | 请求项目的类型。1：全部；2：领周薪 3：报销路费。 |
> | pageSize | false | number | 每页大小。默认为20 |
> | pageNum | false | number | 当前页码           |

###### 返回字段
> | 返回字段        | 字段类型 | 说明          |
> | :-------------- | :------- | :------------ |
> | jobId           | string   | 职位ID        |
> | title           | string   | 职位标题      |
> | salaryRange     | string   | 薪资范围      |
> | tags            | string[] | 职位标签      |
> | unitPrice       | string   | 单价          |
> | travelAllowance | string   | 7天车贴金额   |
> | bannerUrl       | string   | banner图片URL |
> | publishTime     | string   | 发布时间      |

###### 接口示例
> 地址：http://wuyi276.cn.utools.club/api/h5/job/list
``` javascript
{
    "code": 0,
    "msg": "success",
    "data": {
        "total": 200,
        "pageSize": 10,
        "totalPage": 20,
        "pageNum": 1,
        "list": [
            {
                "jobId": "123131",
                "title": "昆山城南富士康小时工B",
                "salaryRange": "6000-7000",
                "tags": [
                    "18-45岁",
                    "坐班多",
                    "不做厂车"
                ],
                "tagIds": [
                    600,
                    3,
                    4
                ],
                "unitPrice": "20每小时",
                "travelAllowance": "7/100",
                "bannerUrl": "https://cos.liangdaidai.com/company/fastdfs/10323bb0-6a9e-411a-84d3-95122f786deb-1503244501094.jpg",
                "publishTime": "2021-05-01 12:00:00"
            }
        ]
    }
}
```

## 4. 职位详情页

### 4.1. 通过jobID获取详情

###### 接口功能
> 通过JobID获取职位的详情信息，展示在详情页

###### URL
> [http://wuyi276.cn.utools.club/api/h5/job/get]()

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
> | 参数  | 必选 | 类型   | 说明   |
> | :---- | :--- | :----- | ------ |
> | jobId | ture | string | 职位ID |

###### 返回字段
> | 返回字段           | 字段类型  | 字段类型 | 说明                               |
> | :----------------- | :-------- | -------- | :--------------------------------- |
> | jobId              | number    |          | 职位ID                             |
> | bannerUrls         | string[]  |          | banner图片URL集合                  |
> | companyName        | string    |          | 公司名称                           |
> | jobTags            | string[]  |          | 职位标签     e.g.  18-45岁, 坐班多 |
> | priceTagTitle      | string    |          | 薪资标签.      e.g. 厂发工资       |
> | priceTagAmount     | string    |          | 薪资金额标签   e.g. 同工同酬       |
> | subsidy            | object    |          | 补贴信息                           |
> |                    | title     | string   | 标题                               |
> |                    | remark    | string   | 备注                               |
> |                    | amount    | string   | 金额                               |
> |                    | unit      | string   | 单位                               |
> |                    | priceTag  | string   | 截止时间                           |
> |                    | payDate   | string   | 获取补贴日期                       |
> | reimbursement      | object    |          | 车补信息                           |
> |                    | title     | string   | 标题                               |
> |                    | desc      | string   | 描述                               |
> |                    | remark    | string   | 备注                               |
> | applyUserCount     | string    | string   | 报名人数                           |
> | jobRateInfo        | object    |          | 职位推荐信息                       |
> |                    | rateScore | string   | 推荐分数                           |
> |                    | rateTotal | string   | 推荐总分                           |
> |                    | rateTitle | string   | 推荐描述                           |
> | jobDescription     | string    |          | 岗位介绍                           |
> | jobRequirement     | string    |          | 录用条件                           |
> | jobSalaryBenefits  | string    |          | 薪资福利                           |
> | companyDescription | string    |          | 公司介绍                           |
> | interviewAddress   | string    |          | 面试地址                           |
> | hotline            | string    |          | 热线电话 400-10080912131           |
> | followFlag         | number    |          | 关注状态。 1: 已关注, 0: 未关注    |

###### 接口示例
> 地址：[http://wuyi276.cn.utools.club/api/h5/job/get]()
``` javascript
{
  "msg": "success",
  "code": 0,
  "data": {
    "jobId": 1,
    "bannerUrls": [
      "https://cos.niuzhigongzuo.com/company/fastdfs/df07963e-1a4d-4e66-9df0-a05cf341bd3d-1503244561371.jpg",
      "https://cos.niuzhigongzuo.com/company/fastdfs/5007316e-3916-412b-8c38-8c78903ad10f-1503244561817.jpg",
      "https://cos.niuzhigongzuo.com/company/fastdfs/c121743d-26a3-473a-9fb0-d40c8be7bb91-1503244561542.jpg"
    ],
    "companyName": "郑州富士康科技集团",
    "jobTags": [
      "吃住在厂",
      "工时高",
      "18-42岁",
      "5月3日面试"
    ],
    "priceTagTitle": "厂发薪资",
    "priceTagAmount": "同工同酬",
    "applyUserCount": "1",
    "jobDescription": "1. 班制及优势: 两班倒，8:00-20:00，有坐有站，恒温车间\r\n\r\n2. 主要工作内容: 主要从事苹果手机生产及苹果零部件生产\r\n\r\n3. 合同签署: 与企业指定的人力资源公司签订，转正后与企业签订\r\n\r\n4. 面试时间: 下午16：00\r\n\r\n5. 接站点: 郑州八大街富士康经开人才市场接待中心\r\n\r\n6. 乘车路线: 1、火车站B17路到航海路第七大街下车 2、高铁东站，座129路到经纬北二路与第八大街下车",
    "jobRequirement": "1. 年龄及性别比例: 18—48周岁，男女不限\r\n\r\n2. 身份证要求: 只接收有磁二代身份证原件，不接受临时身份证及其他证件\r\n\r\n3. 体检说明: 体检费50元先交，下个月补发到工资卡\r\n\r\n4. 文化水平: 会写自己名字及简单文字，不要求字母\r\n\r\n5. 纹身烟疤: 纹身烟疤不超过身份证大小的可以接收\r\n\r\n6. 案底: 查案底，有案底不接收\r\n\r\n7. 色盲色弱: 色盲色弱可以接收\r\n\r\n8. 体内有金属: 过安检门，体内金属不可以，金属牙不可以\r\n\r\n9. 人脸识别: 要求\r\n\r\n10. 离职再进: 正常离职满30天可以再进，自离满30天可以再进，黑名单不录用，其它富士康离职系统显示不在职可以再进，港区IPEBG离职满15天后可以再进。\r\n\r\n11. 发薪银行: 统一办理银行卡\r\n\r\n12. 进厂前费用: 除体检费无其他费用\r\n\r\n13. 进厂准备材料: 黑色中性笔一支，身份证复印件5张，一寸照片张\r\n\r\n14. 其他要求: 少数民族需要提前报备，确认是否可接收，接受本地户籍，四大民族已满（回族，藏族，维吾尔族，彝族），境外、港/澳/台、山东青岛市，以上轨迹途径或到访不予接收。面试前请提供户籍所在地的绿码。",
    "jobSalaryBenefits": "薪资说明:\r\n\r\n工资发放日期: 7号发上月（1—31号）工资\r\n\r\n薪资说明: 补足至32.00元/小时，企业先按同工同酬发工资，拿补贴不在职上月同工同酬无补贴,企业每月25号会补足到28元到工资卡里面，如果当月有请假，旷工，打款会延迟，员工拿到补贴后再申请离职，含税5%; 培训期间按照同工同酬。下产线计算工时\r\n\r\n注意事项: 需要正常办理离职手续\r\n\r\n食宿介绍:\r\n\r\n住宿: 有3个住宿厂区，随机分配，走路10分钟左右，150元/月（含水电），宿舍有空调\r\n\r\n伙食: 自己充钱吃饭，无餐补\r\n\r\n保险说明: 商保50元/月",
    "companyDescription": "富士康完成郑州富士康科技园投资22亿元，建成95条生产线，实现销售收入200亿美元，富士康郑州科技园主要生产计算机、通讯、手机、消费性电子等零组件、机构件及系统软件等，厂房建设面积约140万平方米，2015年底入住员工总数达30万人。富士康科技集团在郑州有三个厂区，分别是郑州航空港厂区，经开区厂区，中牟县厂区。详情请查看郑州富士康招聘简章 企业地址：郑州新郑综合保税区厂区",
    "interviewAddress": "中国河南省郑州市管城回族区经北二路",
    "subsidy": {
      "title": "补贴",
      "remark": "补足至",
      "amount": "32",
      "unit": "元/小时",
      "priceTag": "截止至2021年05月31日",
      "payDate": "10号 ~ 16号"
    },
    "reimbursement": {
      "title": "车补",
      "desc": "7天补100元",
      "remark": "(入职不满50天扣回100元)"
    },
    "jobRateInfo": {
      "rateScore": "4.5",
      "rateTotal": "5.0",
      "rateTitle": "推荐指数"
    },
    "followFlag": 1,
    "hotline": "4008-1231-1231"
  }
}
```

### 4.2. 关注职位

###### 接口功能
> 关注特定职位

###### URL
> [http://wuyi276.cn.utools.club/api/h5/job/follow]()

###### 支持格式
> JSON

###### HTTP请求方式
> POST

###### 请求参数
> | 参数  | 必选 | 类型   | 说明   |
> | :---- | :--- | :----- | ------ |
> | jobId | ture | string | 职位ID |

###### 返回字段
> | 返回字段 | 字段类型 | 说明           |
> | :------- | :------- | :------------- |
> | code     | int      | 返回结果状态码 |
> | msg      | string   | 返回消息       |
> | data     | boolean  | 返回数据       |

###### 接口示例
> 地址：http://wuyi276.cn.utools.club/api/h5/job/follow
``` javascript
{
    "code": 0,
    "msg": "关注成功",
    "data": true
}
```

### 4.3. 取消职位关注

###### 接口功能
> 取消职位关注

###### URL
> http://wuyi276.cn.utools.club/api/h5/job/unfollow

###### 支持格式
> JSON

###### HTTP请求方式
> POST

###### 请求参数
> | 参数  | 必选 | 类型   | 说明         |
> | :---- | :--- | :----- | ------------ |
> | jobId | ture | string | 请求的项目名 |

###### 返回字段
> | 返回字段 | 字段类型 | 说明           |
> | :------- | :------- | :------------- |
> | code     | int      | 返回结果状态码 |
> | msg      | string   | 返回消息       |
> | data     | boolean  | 返回数据       |

###### 接口示例
> 地址：http://wuyi276.cn.utools.club/api/h5/job/unfollow
``` javascript
{
    "code": 0,
    "msg": "取消关注成功",
    "data": true
}
```

### 4.4. 获取猜你喜欢列表

###### 接口功能
> 获取猜你喜欢模块的数据列表

###### URL
> http://wuyi276.cn.utools.club/api/h5/job/related/list

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
> | 参数  | 必选 | 类型   | 说明   |
> | :---- | :--- | :----- | ------ |
> | jobId | ture | string | 职位ID |

###### 返回字段
> | 返回字段        | 字段类型  | 说明           |
> | :-------------- | :-------- | :------------- |
> | jobId           | string    | 职位ID         |
> | title           | string    | 职位标题       |
> | salaryRange     | string    | 薪资范围       |
> | tags            | string[]  | 职位标签集合   |
> | tagIds          | integer[] | 职位标签ID集合 |
> | unitPrice       | string    | 单价           |
> | travelAllowance | string    | 7天车贴金额    |
> | bannerUrl       | string    | banner图片URL  |
> | publishTime     | string    | 发布时间       |

###### 接口示例
> 地址：http://wuyi276.cn.utools.club/api/h5/job/related/list
``` javascript
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "jobId": "123131",
            "title": "昆山城南富士康小时工B",
            "salaryRange": "6000-7000",
            "tags": [
                "18-45岁",
                "坐班多",
                "不做厂车"
            ],
            "tagIds": [
                600,
                3,
                4
            ],
            "unitPrice": "20每小时",
            "travelAllowance": "7/100",
            "bannerUrl": "https://cos.liangdaidai.com/company/fastdfs/10323bb0-6a9e-411a-84d3-95122f786deb-1503244501094.jpg",
            "publishTime": "2021-05-01 12:00:00"
        }
    ]
}
```

### 4.5. 立即报名

###### 接口功能
> 立即报名某个职位

###### URL
> http://wuyi276.cn.utools.club/api/h5/job/apply

###### 支持格式
> JSON

###### HTTP请求方式
> POST

###### 请求参数
> | 参数  | 必选 | 类型   | 说明   |
> | :---- | :--- | :----- | ------ |
> | jobId | ture | string | 职位ID |

###### 返回字段
> | 返回字段 | 字段类型 | 说明           |
> | :------- | :------- | :------------- |
> | code     | int      | 返回结果状态码 |
> | msg      | string   | 返回消息       |
> | data     | boolean  | 返回数据       |

###### 接口示例
> 地址：http://wuyi276.cn.utools.club/api/h5/job/apply
``` javascript
{
    "code": 0,
    "msg": "报名成功",
    "data": true
}
```

## 5. 个人中心

### 5.1. 获取个人基本信息（根据用户ID）

###### 接口功能
> 获取个人基本信息

###### URL
> http://wuyi276.cn.utools.club/api/h5/profile/get

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
> N/A

###### 返回字段
> | 返回字段         | 字段类型 | 说明                                                         |
> | :--------------- | :------- | :----------------------------------------------------------- |
> | name             | string   | 姓名                                                         |
> | nickname         | string   | 昵称                                                         |
> | mobile           | string   | 手机号                                                       |
> | nation           | string   | 民族                                                         |
> | sex              | integer  | 性别 0：未知性别， 1: 男, 2: 女, 9: 未说明的性别             |
> | birthday         | string   | 生日                                                         |
> | startWorkingDate | string   | 开始工作日期                                                 |
> | residenceAddress | string   | 现居住地                                                     |
> | domicileAddress  | string   | 户籍地                                                       |
> | politicalStatus  | integer  | 政治面貌   1: 党员  2: 团员  3: 群众                         |
> | jobStatus        | integer  | 求职状态.  0:  求职中   1: 已离职， 2：在职看机会,   3: 在职不看机会 |
> | avatarUrl        | string   | 头像URL                                                      |
> | openId           | string   | 微信openId                                                   |
> | userId           | string   | 用户ID                                                       |

###### 接口示例
> 地址：http://wuyi276.cn.utools.club/api/h5/profile/get
``` javascript
{
    "code": 0,
    "data": {
        "name": "张三",
        "nation": "汉",
        "nickname": "昵称",
        "mobile": "18930804525"
        "sex": "1",
        "birthday": "1984-11-28",
        "startWorkingDate": "2008-11-28",
        "residenceAddress": "1",
        "domicileAddress": "1",
        "politicalStatus": "1",
        "jobStatus": "1",
        "avatarUrl": "https://cos.niuzhigongzuo.com/company/fastdfs/2251d8e6-5a4c-412e-8a8a-09503c18708c-1503244502168.jpg",
        "openId": "123131321",
        "userId": "1"
    },
    "msg": "可口可乐"
}
```

### 5.2. 获取已投递(报名)列表

###### 接口功能
> 个人中心获取已经报名的职位列表

###### URL
> http://wuyi276.cn.utools.club/api/h5/job/apply/list

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
> | 参数  | 必选 | 类型   | 说明   |
> | :---- | :--- | :----- | ------ |
> | pageSize | false | number | 每页大小。默认为20 |
> | pageNum | false | number | 当前页码           |

###### 返回字段
> | 返回字段        | 字段类型  | 说明           |
> | :-------------- | :-------- | :------------- |
> | jobId           | string    | 职位ID         |
> | title           | string    | 职位标题       |
> | salaryRange     | string    | 薪资范围       |
> | tags            | string[]  | 职位标签集合   |
> | tagIds          | integer[] | 职位标签ID集合 |
> | unitPrice       | string    | 单价           |
> | travelAllowance | string    | 7天车贴金额    |
> | bannerUrl       | string    | banner图片URL  |
> | publishTime     | string    | 发布时间       |

###### 接口示例
> 地址：http://wuyi276.cn.utools.club/api/h5/job/apply/list
``` javascript
{
    "code": 0,
    "msg": "success",
    "data": {
        "total": 200,
        "pageSize": 10,
        "totalPage": 20,
        "pageNum": 1,
        "list": [
            {
                "jobId": "123131",
                "title": "",
                "salaryRange": "6000-7000",
                "tags": [
                    "18-45岁",
                    "坐班多",
                    "不做厂车"
                ],
                "tagIds": [
                    600,
                    3,
                    4
                ],
                "unitPrice": "20每小时",
                "travelAllowance": "7/100",
                "bannerUrl": "https://cos.liangdaidai.com/company/fastdfs/10323bb0-6a9e-411a-84d3-95122f786deb-1503244501094.jpg",
                "publishTime": "2021-05-01 12:00:00"
            }
        ]
    }
}
```

### 5.3. 获取已关注列表

###### 接口功能
> 获取用户已关注的职位列表

###### URL
> http://wuyi276.cn.utools.club/api/h5/job/follow/list

###### 支持格式
> JSON

###### HTTP请求方式
> GET

###### 请求参数
> | 参数 | 必选 | 类型   | 说明                                    |
> | :--- | :--- | :----- | --------------------------------------- |
> | pageSize | false | number | 每页大小。默认为20 |
> | pageNum | false | number | 当前页码           |

###### 返回字段
> | 返回字段        | 字段类型  | 说明           |
> | :-------------- | :-------- | :------------- |
> | jobId           | string    | 职位ID         |
> | title           | string    | 职位标题       |
> | salaryRange     | string    | 薪资范围       |
> | tags            | string[]  | 职位标签集合   |
> | tagIds          | integer[] | 职位标签ID集合 |
> | unitPrice       | string    | 单价           |
> | travelAllowance | string    | 7天车贴金额    |
> | bannerUrl       | string    | banner图片URL  |
> | publishTime     | string    | 发布时间       |
> |                 |           |                |

###### 接口示例
> 地址：http://wuyi276.cn.utools.club/api/h5/job/follow/list
``` javascript
{
    "code": 0,
    "msg": "success",
    "data": {
        "total": 200,
        "pageSize": 10,
        "totalPage": 20,
        "pageNum": 1,
        "list": [
            {
                "jobId": "123131",
                "title": "",
                "salaryRange": "6000-7000",
                "tags": [
                    "18-45岁",
                    "坐班多",
                    "不做厂车"
                ],
                "tagIds": [
                    600,
                    3,
                    4
                ],
                "unitPrice": "20每小时",
                "travelAllowance": "7/100",
                "bannerUrl": "https://cos.liangdaidai.com/company/fastdfs/10323bb0-6a9e-411a-84d3-95122f786deb-1503244501094.jpg",
                "publishTime": "2021-05-01 12:00:00"
            }
        ]
    }
}
```

### 5.4. 提交举报投诉

###### 接口功能
> 提交举报投诉信息

###### URL
> http://wuyi276.cn.utools.club/api/h5/report/complaints

###### 支持格式
> JSON

###### HTTP请求方式
> POST

###### 请求参数
> | 参数    | 必选 | 类型   | 说明     |
> | :------ | :--- | :----- | -------- |
> | content | ture | string | 举报内容 |

###### 返回字段
> | 返回字段 | 字段类型 | 说明           |
> | :------- | :------- | :------------- |
> | code     | int      | 返回结果状态码 |
> | msg      | string   | 返回消息       |
> | data     | boolean  | 返回数据       |

###### 接口示例
> 地址：http://wuyi276.cn.utools.club/api/h5/report/complaints
``` javascript
{
    "code": 0,
    "msg": "success",
    "data": true,
}
```

### 5.5. 编辑简历（个人基本信息）

###### 接口功能
> 编辑更新个人基本信息

###### URL
> http://wuyi276.cn.utools.club/api/h5/profile/update

###### 支持格式
> JSON

###### HTTP请求方式
> POST

###### 请求参数
> | 返回字段         | 必选 | 字段类型 | 说明                                                         |
> | :--------------- | ---- | :------- | :----------------------------------------------------------- |
> | name             |      | string   | 姓名                                                         |
> | nickname         |      | string   | 昵称                                                         |
> | nation           |      | string   | 民族                                                         |
> | sex              |      | integer  | 性别 0：未知性别， 1: 男, 2: 女, 9: 未说明的性别             |
> | birthday         |      | string   | 生日                                                         |
> | startWorkingDate |      | string   | 开始工作日期                                                 |
> | residenceAddress |      | string   | 现居住地                                                     |
> | domicileAddress  |      | string   | 户籍地                                                       |
> | politicalStatus  |      | integer  | 政治面貌   1: 党员  2: 团员  3: 群众                         |
> | jobStatus        |      | integer  | 求职状态.  0:  求职中   1: 已离职， 2：在职看机会,   3: 在职不看机会 |
> | avatarUrl        |      | string   | 头像URL                                                      |

###### 请求示例

```json
{
    "name": "张三",
    "nation": "汉",
    "nickname": "昵称",
    "sex": "1",
    "birthday": "1984-11-28",
    "startWorkingDate": "2008-11-28",
    "residenceAddress": "1",
    "domicileAddress": "1",
    "politicalStatus": "1",
    "jobStatus": "1",
    "avatarUrl": "https://cos.niuzhigongzuo.com/company/fastdfs/2251d8e6-5a4c-412e-8a8a-09503c18708c-1503244502168.jpg",
    "openId": "123131321",
    "userId": "1"
}
```



###### 返回字段

> | 返回字段 | 字段类型 | 说明           |
> | :------- | :------- | :------------- |
> | code     | int      | 返回结果状态码 |
> | msg      | string   | 返回消息       |
> | data     | boolean  | 返回数据       |

###### 接口示例
> 地址：http://wuyi276.cn.utools.club/api/h5/profile/update
``` javascript
{
    "code": 0,
    "msg": "success",
    "data": true,
}
```

### 5.6. 头像上传

###### 接口功能
> 单图像文件上传

###### URL
> http://wuyi276.cn.utools.club/api/h5/photo/upload

###### 支持格式
> JSON

###### HTTP请求方式
> POST

###### 请求参数
> | 参数 | 必选 | 类型           | 说明         |
> | :--- | :--- | :------------- | ------------ |
> | file | ture | multipart/file | 图片文件信息 |

###### 返回字段
> | 返回字段 | 字段类型 | 说明                 |
> | :------- | :------- | :------------------- |
> | code     | int      | 返回结果状态码       |
> | msg      | string   | 返回消息             |
> | data     | string   | 返回上传图片访问地址 |

###### 接口示例
> 地址：http://wuyi276.cn.utools.club/api/h5/photo/upload
``` javascript
{
    "code": 0,
    "msg": "success",
    "data": "https://cos.liangdaidai.com/company/fastdfs/10323bb0-6a9e-411a-84d3-95122f786deb-1503244501094.jpg",
}
```

