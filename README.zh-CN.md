# 数据包络分析

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)<br>

在此主要透过一些范例来说明如何利用Python-Gurobi来建构资料包络分析模组(Data-Envelopment-Analysis, DEA)

### § 要求

-   蟒蛇3.6

-   gurobipy 6.5.2 以上版本

### § DEA 模型

此区文章主要针对以下DEA模型进行简介，并说明Python-Gurobi的建模流程：

-   CRS(constant return to scale; input-oriented) ：固定规模报酬投入导向模型

-   VRS(variable return to scale; input-oriented) ：变动规模报酬投入导向模型

-   Relational network DEA Model ：关联网络DEA模型

| 更新时间       | 文章                                                                                |
| ---------- | --------------------------------------------------------------------------------- |
| 2018-01-29 | [CRS模型](https://github.com/wurmen/DEA/blob/master/CRS_Model/CRS%20model.md)       |
| 2018-02-05 | [VRS模型](https://github.com/wurmen/DEA/blob/master/VAS_Model/VRS%20model.md)       |
| 2018-01-30 | [关系网络DEA模型](https://github.com/wurmen/DEA/blob/master/Network_DEA/network_dea.md) |

### § DEA 模型函数

针对上述DEA模型建构几个简单的DEA扩充函数，让使用者能够更轻松的利用这些DEA函数来进行效率分析，或者可由这些已建好的函数去做延伸。<br>

以下连结分别对应到每个主题的说明文章、范例文章、程式码以及档案资料夹(内部包含该主题的所有资源)，可根据说明文章自行下载操作学习。

| 更新时间       | 文章               | 连结                                                                                                                                                                                                                                                                                                                                                                                                      |
| ---------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2018-03-23 | DEA 函数说明         | [文档](https://github.com/wurmen/DEA/blob/master/Functions/user's%20guide.md)                                                                                                                                                                                                                                                                                                                             |
| 2018-03-23 | 基本 DEA 模型的读取数据函数 | [文档](https://github.com/wurmen/DEA/blob/master/Functions/read_data_function.md)/[例子](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/read_data_example.ipynb)/[代码](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/DEA.py)/[文件夹](https://github.com/wurmen/DEA/tree/master/Functions/basic_DEA_data%26code)                                         |
| 2018-03-23 | DEA 基本函数         | [文档](https://github.com/wurmen/DEA/blob/master/Functions/basic_dea_functions.md)/[例子](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/basic_DEA_function.ipynb)/[代码](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/DEA.py)/[文件夹](https://github.com/wurmen/DEA/tree/master/Functions/basic_DEA_data%26code)                                       |
| 2018-03-23 | 网络DEA读取数据功能      | [文档](https://github.com/wurmen/DEA/blob/master/Functions/read_data_for_networkDEA.md)/[例子](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/Read_data_for_network_DEA_function%20example.ipynb)/[代码](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/network_function.py)/[文件夹](https://github.com/wurmen/DEA/tree/master/Functions/network_data%26code) |
| 2018-03-23 | 关系网络DEA函数        | [文档](https://github.com/wurmen/DEA/blob/master/Functions/network_DEA_function.md)/[例子](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/Network_DEA_function_example.ipynb)/[代码](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/network_function.py)/[文件夹](https://github.com/wurmen/DEA/tree/master/Functions/network_data%26code)                     |

* * *

### 参考资源(Python-Gurobi)

若对python-gurobi的建模较不熟悉，可参考下面资源~

-   [环境安装教学](https://github.com/wurmen/Gurobi-Python/blob/master/Installation/%E5%AE%89%E8%A3%9D%E6%95%99%E5%AD%B8.md)
-   [Python+Gurobi基本架构](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python+Gurobi%E5%9F%BA%E6%9C%AC%E6%9E%B6%E6%A7%8B.md)<br>
-   [Python+Gurobi建模](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python+Gurobi%E5%BB%BA%E6%A8%A1.md)<br>
-   [Python+Gurobi特殊资料结构](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python%2BGurobi%E7%89%B9%E6%AE%8A%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B.ipynb)
