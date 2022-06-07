# 销售模块：需求规格说明
**（文档中略去信息缺失部分以及其他模块内容）**

### 分工

| 学号      | 姓名   | 工作内容                     |
| --------- | ------ |--------------------------|
| 201250172 | 熊丘桓 | 完成"客户管理需求"部分             |
| 201250127 | 蔡之恒 | 其他部分的评审，并完成文档框架          |
| 201250185 | 王福森 | 完成"查询成交额最大客户"部分和"单据审批"部分 |
| 201250181 | 孙立帆 | 完成"进退货单生成"部分和"商品销售"部分    |

## 1. 引言
### 1.1 目的
本文档描述了 ERP 系统的功能需求和非功能需求。开发小组的软件系统实现与验证工作都以此文档为依据。

除特殊说明外，本文档所包含的需求都是高优先级需求。

### 1.2 范围
ERP 系统是为 XXX 公司开发的业务系统，开发的目标是帮助该公司处理日常的重点业务，包括库存管理、销售管理、财务管理、人事管理和企业经营管理。

通过该系统的应用，期望为 XXX 公司减少积压的库存，增加销售额，提高财务人员和人力资源人员工作效率，为经理的决策做支持。

### 1.3 参考文献
- IEEE 标准。
- ERP 系统用例描述。
- ERP 系统项目需求。
## 2. 总体描述
### 2.1 商品前景
#### 2.1.1 背景与机遇

一民营企业专业从事灯具开关行业，是某著名开关品牌的南京地区总代理，主要在南京 负责品牌的推广及项目的落地销售、分销的批发等工作，服务对象包括项目业主、施工单位、 分销商、设计院、终端用户等。
现公司规模扩大，企业业务量、办公场所、员工数都发生增长，为适应新的环境，提高 工作效率和用户满意度， 该公司聘南鲸软件科技公司开发一套 ERP 系统。该系统主要包括 库存管理、销售管理、财务管理、人事管理和企业经营管理。

#### 2.1.2 业务需求
略

### 2.2 商品功能
略

### 2.3 用户特征
**仅保留有关销售模块的用户**

| 用户     | 描述                                                                               |
|--------|----------------------------------------------------------------------------------|
| 进货销售人员 | 有 4～8 名进货销售人员，他们重复大量机械的工作，负责基本的销售并填写单据。进货销售人员分为销售员和销售经理。他们对新系统持积极的态度，不希望增加现有工作量。 |
| 总经理    | 有总经理 2 名，负责生产的管理、单据的审批，有权决定优惠的额度。他们能够熟练使用办公信息化系统，对新系统持积极态度。                      |                                                                  |

### 2.4 约束

略

### 2.5 假设和依赖
略

## 3. 详细需求描述
### 3.1 对外接口需求
略

### 3.2 功能需求

#### 3.2.1 客户管理：增加客户
##### 3.2.1.1 特性描述

在收到增加客户操作请求时，完成录入客户信息、客户信息保存。

优先级=高

##### 3.2.1.2 刺激/响应序列

刺激：进货销售人员提交增加客户任务请求

响应：系统自动生成客户编号，系统引导进货销售人员输入客户分类、级别、姓名、电话、地址、邮编、电子邮箱、应收额度、应收、应付、默认业务员

刺激：进货销售人员取消增加客户任务

响应：系统完成增加客户任务

刺激：进货销售人员确认增加客户任务

响应：系统检查用户信息完整性并保存用户信息

##### 3.2.1.3 相关功能需求

| ID                      | 描述                                                         |
| ----------------------- | ------------------------------------------------------------ |
| AddClient.Input         | 系统应该允许进货销售人员在增加客户任务中进行键盘输入         |
| AddClient.Input.Save    | 系统能够在进货销售人员输入客户信息符合要求时提醒销售管理人员确认保存客户信息，参见AddClient.Save |
| AddClient.Input.Invalid | 系统能够在进货销售人员输入客户信息不符合要求时发出警告并拒绝保存客户信息 |
| AddClient.Input.Cancel  | 系统能够在进货销售人员取消增加客户任务时完成当前增加客户任务 |
| AddClient.Save          | 系统能够在销售管理人员确认客户信息后保存客户信息             |

#### 3.2.2 客户管理：删除客户
##### 3.2.2.1 特性描述

在收到增加删除操作请求时，输入客户编号，删除客户信息。

优先级=高

##### 3.2.2.2 刺激/响应序列

刺激：进货销售人员输入客户编号

响应：系统自动查询相应编号的客户，显示客户信息，提醒进货销售人员确认客户信息

刺激：进货销售人员确认删除客户

响应：系统完成删除客户

刺激：进货销售人员完成删除客户任务

响应：系统完成删除客户

##### 3.2.2.3 相关功能需求

| ID                         | 描述                                                         |
| :------------------------- | ------------------------------------------------------------ |
| DeleteClient.Input         | 系统应该允许进货销售人员在删除客户任务中进行键盘输入         |
| DeleteClient.Input.Display | 系统能够在进货销售人员输入客户编号时显示客户信息             |
| DeleteClient.Input.Invalid | 系统能够在进货销售人员输入客户编号不存在时拒绝发出警告并拒绝删除客户 |
| DeleteClient.Input.Cancel  | 系统能够在进货销售人员取消删除客户任务时完成当前删除客户任务 |
| DeleteClient.Delete        | 系统能够在销售管理人员确认删除客户后删除客户信息             |

#### 3.2.3 客户管理：修改客户信息
##### 3.2.3.1 特性描述

在收到修改客户信息操作请求时，输入客户编号，修改客户信息。

优先级=高

##### 3.2.3.2 刺激/响应序列

刺激：进货销售人员输入客户编号

响应：系统自动查询客户编号，显示客户信息，提醒进货销售人员修改客户信息

刺激：进货销售人员修改客户信息

响应：系统提醒进货销售人员确认修改客户信息

刺激：进货销售人员确认修改客户信息

响应：系统完成修改客户信息

刺激：进货销售人员取消修改客户信息任务

响应：系统完成修改客户信息任务

##### 3.2.3.3 相关功能需求

| ID                         | 描述                                                         |
| :------------------------- | ------------------------------------------------------------ |
| UpdateClient.Input         | 系统应该允许进货销售人员在修改客户信息任务中进行键盘输入     |
| UpdateClient.Input.Display | 系统能够在进货销售人员输入客户编号时显示客户信息             |
| UpdateClient.Input.Invalid | 系统能够在进货销售人员输入客户编号不存在时拒绝发出警告并拒绝删除客户 |
| UpdateClient.Input.Cancel  | 系统能够在进货销售人员取消修改客户信息任务时完成当前删除客户任务 |
| UpdateClient.Update        | 系统能够在销售管理人员确认修改客户信息后完成修改客户信息     |

#### 3.2.4 客户管理：查询客户信息
##### 3.2.4.1 特性描述

在收到查询客户信息操作请求时，输入客户编号，修改客户信息。

优先级=高

##### 3.2.4.2 刺激/响应序列

刺激：进货销售人员发出查询客户信息请求

响应：系统提醒进货销售人员选择查询信息项并输入查询信息值

刺激：进货销售人员选择查询信息项、输入查询信息值

响应：系统提醒进货销售人员确认查询信息

刺激：进货销售人员确认查询信息

响应：系统显示所有查询信息项为对应查询信息值的客户信息，并按照客户编号排序

刺激：进货销售人员取消查询客户信息任务

响应：系统完成查询客户信息任务

##### 3.2.4.3 相关功能需求

| ID                       | 描述                                                         |
| :----------------------- | ------------------------------------------------------------ |
| QueryClient.Input        | 系统应该允许进货销售人员在查询客户信息任务中进行键盘输入     |
| QueryClient.Display      | 系统能够在进货销售人员确认查询信息后显示客户信息             |
| QueryClient.Invalid      | 系统能够在查询结果为空时提醒进货销售人员确认输入的客户信息   |
| QueryClient.Input.Cancel | 系统能够在进货销售人员取消查询客户信息任务时完成当前查询客户信息任务 |

#### 3.2.5 查询成交额最大客户

##### 3.2.5.1特性描述

在了解大客户包含哪些人时，进货销售人员根据开始时间、结束时间、销售人员编号查询该销售人员在这个时间段成交金额或订单数最大的客户的信息（包括编号、分类、级别、姓名、电话、地址、邮编、电子邮箱、应收额度、应收、应付、默认业务员）。

优先级=高

##### 3.2.5.2刺激/响应序列

刺激：进货销售人员输入开始时间、结束时间、销售人员编号、衡量标准（包括成交金额、订单数）。

响应：系统显示该销售人员在该时间段成交金额最大的客户的信息（包括编号、分类、级别、姓名、电话、地址、邮编、电子邮箱、应收额度、应收、应付、默认业务员）。

##### 3.2.5.3相关功能需求

| ID                            | 描述                                                         |
| ----------------------------- | ------------------------------------------------------------ |
| FindBigClient.Input           | 系统应该允许进货销售人员在查询大客户信息时进行键盘输入       |
| FindBigClient.Input.Condition | 在进货销售人员输入选择条件（开始时间、结束时间、销售人员编号、衡量标准），系统要搜索并展示在该销售人员在该时间段成交金额最大的客户的信息 |
| FindBigClient.Input.Invaild   | 在进货销售人员输入条件有误时，系统显示错误原因（开始时间大于结束时间、销售人员编号不存在）、保存原本的输入 |



#### 3.2.6 单据审批

##### 3.2.6.1特性描述

当进货销售人员提交了进货单、进货退货单、销售单、销售退货单后，销售经理开始对提交的单据进行一级审批，总经理对一级审批通过的单据进行二级审批。

优先级=高

##### 3.2.6.2刺激/响应序列

刺激：销售经理输入需要审批的单据类型（包括：进货单、进货退货单、销售单、销售退货单）。

响应：系统显示对应类型且状态为提交状态的单据列表，列表的每个条目显示该单据的类型和编号。

刺激：销售经理选择一个条目进行处理。

响应：系统显示该单据的详细信息（各个单据的详细信息详见制定单据的需求规格说明）。

刺激：销售经理选择通过该单据的审批。

响应：系统将该单据的状态修改为通过一级审批，页面停留5秒后回到与该单据类型相同且状态为提交状态的单据列表。

刺激：销售经理取消该单据的审批。

响应：系统显示与该单据类型相同且状态为提交状态的单据列表。

刺激：销售经理拒绝通过该单据的审批。

响应：系统将该单据的状态修改为未通过一级审批，页面停留5秒后回到与该单据类型相同且状态为提交状态的单据列表。

刺激：总经理输入需要审批的单据类型（包括：进货单、进货退货单、销售单、销售退货单）。

响应：系统显示对应类型且状态为通过一级审批的单据列表，列表的每个条目显示该单据的类型和编号。

刺激：总经理选择一个条目进行处理。

响应：系统显示该单据的详细信息（各个单据的详细信息详见制定单据的需求规格说明）。

刺激：总经理选择通过该单据的审批。

响应：系统将该单据的状态修改为通过二级审批，根据单据的详细信息修改库存数据和客户的应收应付数据，页面停留5秒后回到与该单据类型相同且状态为通过一级审批的单据列表。

刺激：总经理取消该单据的审批。

响应：系统显示与该单据类型相同且状态为提交状态的单据列表。

刺激：总经理拒绝通过该单据的审批。

响应：系统将该单据的状态修改为未通过二级审批，页面停留5秒后回到与该单据类型相同且状态为通过一级审批的单据列表。

刺激：总经理修改该单据的内容。

响应：系统进入单据修改页面。

刺激：总经理保存修改内容。

响应：系统保存修改后的单据内容，将该单据的状态修改为通过二级审批，根据单据的详细信息修改库存数据和客户的应收应付数据，页面停留5秒后回到与该单据类型相同且状态为通过一级审批的单据列表。

##### 3.2.6.3相关功能需求

| ID                              | 描述                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| SalesManager.Input              | 系统应该允许销售经理在单据一级审批任务中经行键盘输入         |
| SalesManager.Input.Type         | 在销售经理输入审批单据的类型后，系统要显示对应类型且状态为提交状态的单据列表 |
| SalesManager.EntryList          | 系统显示特定类型且状态为提交状态的单据列表                   |
| SalesManager.EntryList.Select   | 在销售经理选择单据列表中的某一个条目后，系统显示该单据条目的详细信息 |
| SalesManager.Entry              | 系统显示某一个单据条目的详细信息                             |
| SalesManager.Entry.Approval     | 在销售经理选择通过该单据的审批后，系统将该单据的状态修改为通过一级审批，页面停留5秒后回到与该单据类型相同且状态为提交状态的单据列表。 |
| SalesManager.Entry.Cancel       | 在销售经理选择取消该单据的审批后，系统退出该单据条目页面，并且显示与该单据类型相同且状态为提交状态的单据列表 |
| SalesManager.Entry.Reject       | 在销售经理拒绝通过该单据的审批后，系统将该单据的状态修改为未通过一级审批，页面停留5秒后回到与该单据类型相同且状态为提交状态的单据列表 |
| GeneralManager.Input            | 系统应该允许总经理在单据二级审批任务中经行键盘输入           |
| GeneralManager.Input.Type       | 在总经理输入审批单据的类型后，系统要显示对应类型且状态为通过一级审批的单据列表 |
| GeneralManager.EntryList        | 系统显示特定类型且状态为通过一级审批的单据列表               |
| GeneralManager.EntryList.Select | 在总经理选择单据列表中的某一个条目后，系统显示该单据条目的详细信息 |
| GeneralManager.Entry            | 系统显示某一个单据条目的详细信息                             |
| GeneralManager.Entry.Approval   | 在总经理选择通过该单据的审批后，系统将该单据的状态修改为通过二级审批，根据单据的详细信息修改库存数据和客户的应收应付数据，页面停留5秒后回到与该单据类型相同且状态为通过一级审批的单据列表 |
| GeneralManager.Entry.Cancel     | 在总经理取消该单据的审批后，系统退出该单据条目页面，并且显示与该单据类型相同且状态为提交状态的单据列表 |
| GeneralManager.Entry.Reject     | 在总经理拒绝通过该单据的审批后，系统将该单据的状态修改为未通过二级审批，页面停留5秒后回到与该单据类型相同且状态为通过一级审批的单据列表 |
| GeneralManager.Entry.Alter      | 在总经理请求修改该单据的内容时，系统进入单据修改页面         |
| GeneralManager.Entry.Save       | 在总经理保存修改内容后，系统保存修改后的单据内容，将该单据的状态修改为通过二级审批，根据单据的详细信息修改库存数据和客户的应收应付数据，页面停留5秒后回到与该单据类型相同且状态为通过一级审批的单据列表 |



#### 3.2.7 进退货单生成

##### 3.2.7.1 特性描述

进货人员需要打印进/退货单时，经过验证后由系统生成进货/退货单。(包括：单据编号，供应商，仓库，
操作员，入库商品列表，备注，总额合计。)

优先级=高

##### 3.2.7.2 刺激/响应序列

刺激 : 进货人员新建一份进/退货单。

响应 :  系统提示进货人员从商品列表中选择商品名称，并输入商品数量、商品单价、备注。

刺激 : 进货人员从商品列表中选择商品名称，并输入商品数量、商品单价、备注。

响应 : 系统根据输入的信息填充其他字段并显示进/退货单，并提示进货人员确认。

刺激 : 进货人员输入不合法的输入(商品数量 $\leq$ 0 / 商品单价 $\leq$ 0 / 字段未填写)。

响应 : 系统弹出错误提示，提示进货人员重新输入。

刺激 : 进货人员重新选择商品名称并输入商品数量、商品单价、备注。

响应 : 系统根据新输入的信息重新填充其他字段并显示进/退货单，并提示进货人员确认。

刺激 : 进货人员取消进/退货单生成。

响应 : 系统结束本次进/退货单生成。

刺激 : 进货人员确认进/退货单。

响应 : 系统结束本次进/退货单生成，提交审批，开始等待下一次任务。

##### 3.2.7.3 相关功能需求

| ID                               | 描述                                                         |
| :------------------------------- | ------------------------------------------------------------ |
| Restock/Return.Create            | 系统应该允许进货人员通过鼠标点击新建按钮新建一份进/退货单    |
| Restock/Return.Input             | 系统应该允许进货人员通过鼠标和键盘输入进/退货信息            |
| Restock/Return.Input.ProductName | 系统应该允许进货人员通过鼠标点击在商品列表中选择商品名称     |
| Restock/Return.Input.ProductNum  | 在进货人员输入商品数量后，系统要进行检查是否合法(大于零的整数) |
| Restock/Return.Input.Price       | 在进货人员输入商品单价后，系统要检查是否合法(大于零的实数, 保留到 2 位小数) |
| Restock/Return.Input.Comment     | 系统应该允许进货人员用键盘输入 100 字以内的备注信息          |
| Restock/Return.Input.Invalid     | 在进货人员输入不合法时，系统弹出错误信息,并重新读取输入      |
| Restock/Return.AutoFill          | 进货人员填写了需要手动填写的信息后，系统自动填写其他字段     |
| Restock/Return.Check.Prompt      | 完成其他字段的自动填充后，系统应该弹出确认提示，提示进货人员确认 |
| Restock/Return.Check.Confirm     | 进货人员确认显示的进/退货单据信息后，系统结束本次生成任务，并提交审批 |
| Restock/Return.Check.Cancel      | 进货人员请求取消本次进退货单生成任务后，系统结束本次生成任务 |

#### 3.2.8 商品销售

##### 3.2.8.1 特性描述

在销售人员需要生成销售出/退货单时，在验证后由系统生成销售出/退货单。（包括：单据编号，客户，业务员，操作员，仓库，出货商品清单，折让前总额，折让，使用代金卷金额，折让后总额，备注）。

优先级=高

##### 3.2.8.2 刺激/响应序列

刺激 :  销售人员新建一个销售出/退货单。

响应 : 系统提示销售人员在商品界面中选择商品名称，并输入数量、单价、备注。

刺激 : 销售人员选择商品名称，并输入数量、单价、备注。

响应 : 系统弹出确认提示，请求销售人员确认填写的信息。

刺激 : 销售人员输入了不合法的信息 (商品数量 $\leq$ 0 / 单价 $\leq$ 0 / 或字段漏填)。

响应 : 系统弹出错误提示，提示销售人员重新输入信息。

刺激 : 销售人员选择取消本次销售单据生成。

响应 : 系统结束本次销售单据生成任务。

刺激 : 销售人员选择确认本次填写的信息。

响应 : 系统自动填写其他字段，生成单据并提交审批，结束本次事务，等待下一次事务。

##### 3.2.8.3 相关功能需求

| ID                     | 描述                                                         |
| :--------------------- | ------------------------------------------------------------ |
| Sale.Create            | 系统应该允许销售人员通过鼠标点击新建按钮新建一份销售出/退货单 |
| Sale.Input             | 系统应该允许销售人员通过鼠标和键盘输入商品出/退货信息        |
| Sale.Input.ProductName | 系统应该允许销售人员通过鼠标点击在商品列表中选择商品名称     |
| Sale.Input.ProductNum  | 在销售人员输入商品数量后，系统要进行检查是否合法(大于零的整数) |
| Sale.Input.Price       | 在销售人员输入商品单价后，系统要检查是否合法(大于零的实数, 保留到 2 位小数) |
| Sale.Input.Comment     | 系统应该允许销售人员用键盘输入 100 字以内的备注信息          |
| Sale.Input.Invalid     | 在销售人员输入不合法时，系统弹出错误信息,并重新读取输入      |
| Sale.AutoFill          | 销售人员输入手动输入的字段后，系统自动填充其他字段           |
| Sale.Check.Prompt      | 完成其他字段的自动填充后，系统应该弹出确认提示，提示销售人员确认 |
| Sale.Check.Confirm     | 销售人员确认显示的销售出/退货单据信息后，系统结束本次生成任务，并提交审批 |
| Sale.Check.Cancel      | 销售人员请求取消本次进出/退单生成任务后，系统结束本次生成任务 |

### 3.3 非功能需求

略

### 3.4 数据需求
略

### 3.5 其他需求
略