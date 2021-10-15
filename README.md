## ERPNext Chinese

ERPNext中文汉化，简化，优化

本项目解决标准控件翻译问题参考学习了破匣求禅/EBCLocal，源项目地址 https://gitee.com/petel_zhang/EBCLocal，
在此特别感谢

主要功能（本项目主要针对13版，理论上也适用于低版本)

界面汉化

1.1 维护translations目录下的zh.csv 覆盖标准frappe与erpnext目录下zh.csv翻译内容

1.2 维护translations目录下的zh_global.csv，类似界面上的用户翻译，会在每个页面加载，用以解决标准功未能获取相关页面待翻译文本，而无法翻译的问题。

1.3 修正标准系统中以下自带控件不能翻译中文的问题

 1.3.1 日历控件

 1.3.2 甘特图控件

 1.3.3 表单视图顶部热力图控件

 1.3.4 数据表格控件标题列下拉菜单：排序、移除列菜单项

 1.3.5 链接字段下拉框是中文，选择择值之后也显示为中文

 1.3.6 筛选器中多选字段（包括),下拉框及显示值均支持中文

 1.3.7 数据面板及工作区中的数据卡

 1.3.8 数据面板视图标题

 1.3.9 统计图表标题及日期过滤按钮与下拉选单

初始化（setup wizard）步骤简化

2.1 设置默认语言为中文，默认地区(国家)为中国

2.2 导入中国会计科目表（已添加公司表单上所需默认科目与临时开账科目）

2.3 为公司分派默认科目

2.4 为默认仓库分派默认库存科目

2.5 为默认物料组分派默认费用科目

2.6.新建税种（内销、外销、小规模纳税、一般纳税）

2.7 新建销售及采购税费模板（13%， 0%， 1%）以及税费模板分派规则

2.8 修改一词多义字段标签（如采购、销售税费明细中的税率）

2.9 隐藏本地化不适用字段，如供应商与客户主数据中的pan(印度企业实体纳税登记号） ，物料主数据中物料商场hub相关字段

2.10 修改默认系统流水码前缀-改短

标准功能优化

3.1 修复bug 3.1.1 防止因网络超时无法创建有首选邮箱的联络人，取消从国外用户图像网站获取用户图像

 3.1.2 防止因SQL写入语句超二十万条被系统自动终止，避免将select语句计算在内

 3.1.3 全局智能搜索框对检索出的单据进行权限检查

 3.1.4 表单表格控件
    3.1.4.1 因复制的内容最后一行是空行，进度条走不完
    3.1.4.2 文本编辑器字段内容中保留回车换行
    
3.2 功能完善

 3.2.1 角色权限管理：用户角色及单据类型下拉框变更为下拉框变更为智能输入下拉框，支持按中文与英文关键字检索

 3.2.2 全局智能搜索框支持按中、英文检索单据类型、报表、模块等界面对象

 3.2.3 单据类型、用户角色、报表下拉框支持按中、英文关键字检索

 3.2.4 单据打印时显示制单人与审批人姓名， 在打印格式自定义html字段中 使用 {{ doc.get_owner_username() }} 和 {{ doc.get_submit_username() }}

 3.2.5 导入功能导出模板字段标题为中文，导入模板支持中文字段标题，导入主从表时连续行主表字段值相同会被自动识别为同一个单据，不需要再在Excel中通过
 工具将相同单据第一行以后的主表字段清空
 
本人在discuss.erpnext.com及github.com官网帐号是szufisher

使用方法

先决条件

进入 bench 工作台目录；

1.新安装
1.1、获取对应版本APP

bench get-app https://gitee.com/yuzelin/erpnext_chinese.git

1.2、安装APP(有多个站点且未设默认站点的请加--site参数）

bench install-app erpnext_chinese

升级
2.1、bench update 命令

bench update --apps erpnext_chinese --pull --reset

2.2 重新编译JS等资源文件

bench build --app erpnext_chinese --force

2.3 通过本应用中的插件机制向打印格式单据类型中新增两个字段(同步，新安装时不需要这一步，也可运行标准的bench migrate 命令，会对所有app作升级后同步数据库表处理)
bench console
In [6]: from frappe.utils.fixtures import sync_fixtures

In [7]: sync_fixtures('erpnext_chinese')

卸载
3.1 从站点卸载 

bench uninstall-app erpnext_chinese

3.2 从整个bench环境卸载,移除整个应用目录

bench remove-app erpnext_chinese

欢迎提交问题和反馈建议。


#### License

MIT