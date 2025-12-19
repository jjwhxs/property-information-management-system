### 系统介绍

基于SpringBoot实现的物业信息管理系统采用前后端一体化的架构方式，实现了系统登录、档案管理、计费管理、抄表管理、应收管理、收费管理、报表中心、系统管理、客户服务、个人中心等功能模块。

### 技术选型

开发工具：idea2020.3+Webstorm2020.3

运行环境：jdk1.8+maven3.6.3+MySQL8.0

服务端技术：springboot+mybatis-plus+fastjson

前端技术：html+css+ajax+jquery+layui

### 成果展示

系统登录 输入图片说明

档案管理->客户档案 输入图片说明

计费管理->收费项目 输入图片说明

抄表管理->抄表费用 输入图片说明

应收管理->应收账单 输入图片说明

收费管理->缴费结账 输入图片说明

报表中心->应收区域汇总 输入图片说明

系统管理->权限管理 输入图片说明

客户服务->投诉建议 输入图片说明

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

输入图片说明

4、项目结构展示

输入图片说明

5、运行步骤

1）创建数据库、导入sql脚本

2）修改application.yml中的数据库配置文件，启动服务端，访问链接

### 获取方式(可远程调试)

访问链接(在浏览器中手动输入下图中的地址)：

输入图片说明

若资源获取失败，可添加happy35596339(vx)或1204901965(qq)进行交流
