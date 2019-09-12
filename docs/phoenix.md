### download

[APACHE-PHOENIX](https://mirrors.tuna.tsinghua.edu.cn/apache/phoenix/apache-phoenix-4.14.0-cdh5.14.2/parcels/APACHE_PHOENIX-4.14.0-cdh5.14.2.p0.3-el7.parcel)



### 安装

```bash
#在hadoop1机器进行此操作
#用root用户将其上传至/opt/cloudera/parcel-repo/下
cd /opt/cloudera/parcel-repo/
rz 
#APACHE_PHOENIX-4.13.2-cdh5.11.2.p0.0-el7.parcel

#在hadoop1机器进行此操作
vim APACHE_PHOENIX-4.14.0-cdh5.14.2.p0.3-el7.parcel.sha
#输入以下内容并保存
5aebefdeb239a9dc7a042b891e2aac98336a25bc


#在hadoop1机器进行此操作
#修改manifest.json文件，并保存
vim manifest.json
#在"parcels"节点的最下面追加以下内容
{
    "hash": "5aebefdeb239a9dc7a042b891e2aac98336a25bc",
            "depends": "CDH (>= 5.14.0), CDH (<= 5.14.999)",
            "parcelName": "APACHE_PHOENIX-4.14.0-cdh5.14.2.p0.3-el7.parcel",
            "components": [
                {
                    "pkg_version": "4.14.0+cdh5.14.2+3",
                    "version": "4.14.0-cdh5.14.2",
                    "name": "phoenix",
                    "pkg_release": "cdh5.14.2.p0.3"
                }
            ]
 }
```

