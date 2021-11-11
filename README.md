# Servers API
本文档介绍对华为云ECS服务器的增、删、查询

---
### 创建云服务器（按需）
 POST servers/
 
 - 请求
 
 | 请求体参数 | 类型 |  描述  |
 |  :---:  |  :---: |  :---:  |
 | flavor_level | string | 服务器规格, l1, l2, l3 (选传参数, 不传则取配置文件的默认值) |
 | count | int | 待创建云服务器的数量 (选传参数, 不传则默认为1) |
 
 - 返回
 
 | 响应结果 | 状态码 |  返回值示例  |
 |  :---:  |  :---: |  :---:  |
 | 成功 | 201 | [{"name": "obs-worker1636612382", "ip": "172.1.16.xxx", "server_id": "xxx", "flavorRef": "c6.4xlarge.4"}] |
 | 失败 | 400 | {"error": {"message": "vpc id[sdf] is not uuid.", "code": "Ecs.0005"}} |

--- 
### 删除云服务器
 DELETE server/{str:server_id}/

 - 请求

 | params参数 | 类型 |  描述  |
 |  :---:  |  :---: |  :---:  |
 | server_id | string | 服务器ID |

 - 返回
 
 | 响应结果 | 状态码 |  返回值示例  |
 |  :---:  |  :---: |  :---:  |
 | 成功 | 204 | {"code": 204, "msg": "Delete successfully"} |
 | 失败 | 400 | {"error": {"message": "some of the id in request are illegal uuid.", "code": "Ecs.0005"}} |

---
### 查询云服务器
 GET server/{str:server_id}/

 - 返回
 
 | 响应结果 | 状态码 |  返回值示例  |
 |  :---:  |  :---: |  :---:  |
 | 成功 | 200 | {"name": "obs-worker1636612382", "ip": "172.1.16.xxx", "server_id": "xxx", "flavorRef": "c6.4xlarge.4"} |
 | 失败 | 400 | {"error": {"message": "Not exist", "code": "400"}} |

---
### 查询云服务器列表
 GET serverslist/

 - 返回
 
 | 响应结果 | 状态码 |  返回值示例  |
 |  :---:  |  :---: |  :---:  |
 | 成功 | 200 | [{"name": "obs-worker1636612382", "ip": "172.1.16.xxx", "server_id": "xxx", "flavorRef": "c6.4xlarge.4""}, {}, {}...] |
 
