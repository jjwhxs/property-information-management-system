### 系统介绍

基于SpringBoot实现的物业信息管理系统采用前后端一体化的架构方式，实现了系统登录、档案管理、计费管理、抄表管理、应收管理、收费管理、报表中心、系统管理、客户服务、个人中心等功能模块。

### 技术选型

开发工具：idea2020.3+Webstorm2020.3

运行环境：jdk1.8+maven3.6.3+MySQL8.0

服务端技术：springboot+mybatis-plus+fastjson

前端技术：html+css+ajax+jquery+layui

### 成果展示

系统登录
<img width="1920" height="990" alt="系统登录" src="https://github.com/user-attachments/assets/e0083b44-83ec-4549-9af7-e4bff2568795" />

档案管理->客户档案
<img width="1920" height="931" alt="档案管理-客户档案" src="https://github.com/user-attachments/assets/2ca6b708-c31e-4358-b74b-1614f72b553a" />

计费管理->收费项目
<img width="1920" height="932" alt="计费管理-收费项目" src="https://github.com/user-attachments/assets/faf4952c-31cb-4484-8728-9c004f05d3d8" />

抄表管理->抄表费用
<img width="1920" height="932" alt="抄表管理-抄表费用" src="https://github.com/user-attachments/assets/91b531bb-433c-4904-a739-0172a7a0d1ea" />

应收管理->应收账单
<img width="1920" height="931" alt="应收管理-应收账单" src="https://github.com/user-attachments/assets/a8babe37-9c97-4754-a911-6bd43f516b55" />

收费管理->缴费结账
<img width="1920" height="931" alt="收费管理-缴费结账" src="https://github.com/user-attachments/assets/622f7a35-95ef-46dd-b9c3-b299ca0fbfce" />

报表中心->应收区域汇总
<img width="1920" height="932" alt="报表中心-应收区域汇总" src="https://github.com/user-attachments/assets/d33a2e32-2b79-49e2-a227-1b1a6df640c8" />

系统管理->权限管理
<img width="1920" height="931" alt="系统管理-权限管理" src="https://github.com/user-attachments/assets/b62cd4c9-a8fb-482a-83a4-61808bdf6220" />

客户服务->投诉建议
<img width="1920" height="931" alt="客户服务-投诉建议" src="https://github.com/user-attachments/assets/61cd1910-be34-4cf8-b1ef-d728075c76fc" />

### 源码展示

@RequiresPermissions("sys:role:list")

@PostMapping("list")

@ResponseBody

public PageData list(@RequestParam(value = "page",defaultValue = "1")Integer page, @RequestParam(value = "limit",defaultValue = "10")Integer limit, ServletRequest request){

    Map map = WebUtils.getParametersStartingWith(request, "s_");
    PageData<Role> rolePageData = new PageData<>();
    QueryWrapper<Role> roleWrapper = new QueryWrapper<>();
    roleWrapper.eq("del_flag",false);
    if(!map.isEmpty()){
        String keys = (String) map.get("key");
        if(StringUtils.isNotBlank(keys)) {
            roleWrapper.like("name", keys);
        }
    }
    IPage<Role> rolePage = roleService.page(new Page<>(page,limit),roleWrapper);
    rolePageData.setCount(rolePage.getTotal());
    rolePageData.setData(setUserToRole(rolePage.getRecords()));
    return rolePageData;
    
}

### 账号地址及其它说明

1、地址说明

登录页：localhost:8080

2、账号说明

管理员：admin/123456

3、目录结构展示

<img width="462" height="175" alt="目录结构展示" src="https://github.com/user-attachments/assets/065b6625-8932-44ed-8606-bf0a2644e203" />

4、项目结构展示

<img width="1775" height="977" alt="项目结构展示" src="https://github.com/user-attachments/assets/bd10ce96-f9eb-4b1e-a06c-f9bce676ebaa" />

5、运行步骤

1）创建数据库、导入sql脚本

2）修改application.yml中的数据库配置文件，启动服务端，访问链接

### 获取方式(可远程调试)

访问链接(在浏览器中手动输入下图中的地址)：

<img width="1075" height="123" alt="链接" src="https://github.com/user-attachments/assets/ad3e2c90-ef34-4b90-8029-5ddb0275f66f" />

若资源获取失败，可添加happy35596339(vx)或1204901965(qq)进行交流
