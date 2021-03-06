
# 系统简介

> 可以将车间的工作流程应用控制中心的功能一一展现出来，方便人们不用进入车间便可以了解车间的具体结构， 方便管理者对车间的架构进行调控，更利于车间的管理
![The Vue Instance Lifecycle](/images/springBootVUE.png)
# 工艺流程

>功能包括BOM管理，工艺流程版本和路径管理，工序管理，资源管理，工序绘制关联关系等。将原来表格文档化的内容管理转为可视化管理。 将逻辑性较强的关系数据转为可视化数据管理，结构清晰，层次分明。计划应用在生产单位的工艺流程管理系统中。
![The Vue Instance Lifecycle](/images/technologyTree.png)
# 生产计划

## 生产计划
生产计划是对应生产系统所做的一系列计划，可以在不同的生产计划上做多个版本的修改，可以实时的进行报工，对其完成的数量也可以进行实时的监控
![The Vue Instance Lifecycle](/images/plan.png)

## 计划版本
生产计划版本管理
1)	添加/编辑：录入数据包括部门【数据来自部门管理】、产品【数据来自产品管理】、开始时间、结束时间。
2)	版本复制：复制直接版本，主要用于版本修改。
3)	发布版本：将确定版本发布，计划数据推送到“部门管理”里的“任务分配管理”中，用于做为部门任务分配管理的基础数据，以及报工数据的统计依据。
![The Vue Instance Lifecycle](/images/planVersion.png)

## 版本明细
版本明细
统计数据为：交付需求、交付需求累计、生产计划、完成数量、累计完成数量、需要结转量【生产量与需求生产量有出入，需要制定下一个生产计划完成此数据，现程序为新建生产计划时，选择需要承接某一个生产计划】、报工统计【用于显示除上述数据外的其他数据信息。现程序中没有此模块】。此模块中的数据，现程序部分数据为人工输入，以后报工完成后，数据来源应该来自报工数据。
![The Vue Instance Lifecycle](/images/planVersionDetail.png)

# 质量管理

## 工艺树
工序和检验需求是属于一一对应的关系，检验需求内涵检验需求类别的属性，检验需求对应对个检验项，检验项包含检验标准，检验类别和检验单位属性 工序下包含多条工序任务，可以根据工序对应的检验需求和检验项对应生成多个检验任务和检验项，将检验需求作为一个模板去使用。在执行检验任务时，真正检测时又分为实测和观感两种方式
![The Vue Instance Lifecycle](/images/technologyTree.png)

该树是由产品—工件—工艺—工序组成，打开树可以看见产品------工序树中的每一个节点的显示，仅作为显示， 只有最后一层的工序才可以进行点击。
## 质量检查

### 任务管理
![The Vue Instance Lifecycle](/images/checkTaskTree.png)
该任务树是由产品，工件，工艺，工序和工序任务组成，每一层都可以点击，完整的诠释了产品------工序任务的每一个节点，可以直观的看出该树的架构和每个节点的名称，但是只有最后一个节点可进行点击。
创建检验任务—派发检验任务—执行检验任务—生成该检验任务的结论并进行查看

### 检验任务
![The Vue Instance Lifecycle](/images/checkTaskList.png)
派发的检验任务规则：
1.	检验任务必须有检验人
2.	计划的开始时间和结束时间不能为空且：当前时间<计划开始时间<计划结束时间
3.	检验任务下的检验项的检验人不能为空，这样派发后才会有具体人执行
符合以上条件后，点击右侧的派发按钮，该检验任务就派发到指定的检验员

### 检验数据反馈
![The Vue Instance Lifecycle](/images/checkTaskInsert.png)
数据录入分为两大类：
实测类
进入检验任务列表—检验项列表，选择自己检验的检验项，进入数据录入界面，
实测类在添加数据的同时，直接生成检验结果（判定结论是根据上下公差和实际值）得出的。
观感类
添加观感描述，根据观感测量人为判断是否合格

### 检验数据管理
![The Vue Instance Lifecycle](/images/lookCheckTask.png)
该树总共分为7层，由产品，工件，工艺，工序，工序任务，检验任务和检验项组成，点击每一个节点都会该节点所对应的的列表数据，可以用于领导观看进度和总体架构。
### 统计图分析
![The Vue Instance Lifecycle](/images/statistics.png)

## 数据字典

### 单位管理
![The Vue Instance Lifecycle](/images/unit.png)

### 检验标准
![The Vue Instance Lifecycle](/images/standard.png)

### 检验类型
![The Vue Instance Lifecycle](/images/type.png)

# 控制中心

本系统可以将制造系统的软硬件结合起来使用，实现真正的智能制造，内涵看板，站位任务等多个模块 可以给操作人员提供更多的便捷
![The Vue Instance Lifecycle](/images/controlcenter.png)

# 物料

## 物料管理
物料管理是指将新入库的物料分配货架进行管理，以及该物料的合并入库，分批出库等操作将物料分别放入不同的位置 在该过程中也可以对该物料进行出线和上报异常。
1.已有实际物料展示界面
主要是展示库存和在制品信息，物料种类，数量，位置
2.物料需求信息展示界面
以人物师徒展示每道工序需要展示需要物料的种类、数量、时间.
3.物料需求满足界面
以物料所在部门/区域的物料管理角色，展示该部门/区域物料的需求信息。然后对需求进行匹配，需求与已有库存进行匹配，并给出物料需求满足状态，具体物料/满足多少/缺货等信息
4.物料配送任务界面
依据物料需求的满足信息，依据物料的原始地和目的地，生成对应的物料配送任务界面，主要包括物料的种类数量，运转箱、原始地、目的地。
5.任务反馈的物料信息录入界面
在任务开始加工前，通过配送过来的物料编码，录入到任务的消耗物料列表中。

### 物料类型
![The Vue Instance Lifecycle](/images/materialType.png)

### 物料管理
![The Vue Instance Lifecycle](/images/materialInfo.png)

### 产品-任务
![The Vue Instance Lifecycle](/images/productTask.png)

### 站位任务
![The Vue Instance Lifecycle](/images/siteTask.png)


# 工艺流程
功能包括BOM管理，工艺流程版本和路径管理，工序管理，资源管理，工序绘制关联关系等。将原来表格文档化的内容管理转为可视化管理。 将逻辑性较强的关系数据转为可视化数据管理，结构清晰，层次分明。计划应用在生产单位的工艺流程管理系统中。
![The Vue Instance Lifecycle](/images/technology.png)

