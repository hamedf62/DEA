# Data-Envelopment-Analysis

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)<br>

Here we mainly use some examples to illustrate how to use Python-Gurobi to build a data-envelopment-Analysis module (Data-Envelopment-Analysis, DEA).

### § Requirements

-   python 3.6

-   gurobipy 6.5.2 or above

### § DEA Models

The articles in this area mainly introduce the following DEA models and explain the modeling process of Python-Gurobi:

-   CRS (constant return to scale; input-oriented): fixed return to scale input-oriented model

-   VRS (variable return to scale; input-oriented): Variable return to scale input-oriented model

-   Relational network DEA Model: Relational network DEA model

| Update time | article                                                                                              |
| ----------- | ---------------------------------------------------------------------------------------------------- |
| 2018-01-29  | [CRS Model](https://github.com/wurmen/DEA/blob/master/CRS_Model/CRS%20model.md)                      |
| 2018-02-05  | [VRS Model](https://github.com/wurmen/DEA/blob/master/VAS_Model/VRS%20model.md)                      |
| 2018-01-30  | [Relational network DEA Model](https://github.com/wurmen/DEA/blob/master/Network_DEA/network_dea.md) |

### § DEA Models Functions

Several simple DEA extension functions are constructed for the above DEA model, so that users can more easily use these DEA functions to conduct efficiency analysis, or they can extend these already built functions.<br>

The following links correspond to the explanation articles, sample articles, code and file folders of each topic (which contain all the resources of the topic). You can download and learn according to the explanation articles.

| Update time | article                                  | Linking                                                                                                                                                                                                                                                                                                                                                                                                                      |
| ----------- | ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2018-03-23  | DEA Functions Instructions               | [Documentation](https://github.com/wurmen/DEA/blob/master/Functions/user's%20guide.md)                                                                                                                                                                                                                                                                                                                                       |
| 2018-03-23  | Read data functions for basic DEA models | [Documentation](https://github.com/wurmen/DEA/blob/master/Functions/read_data_function.md)/[Example](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/read_data_example.ipynb)/[Code](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/DEA.py)/[Folder](https://github.com/wurmen/DEA/tree/master/Functions/basic_DEA_data%26code)                                         |
| 2018-03-23  | Basic DEA functions                      | [Documentation](https://github.com/wurmen/DEA/blob/master/Functions/basic_dea_functions.md)/[Example](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/basic_DEA_function.ipynb)/[Code](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/DEA.py)/[Folder](https://github.com/wurmen/DEA/tree/master/Functions/basic_DEA_data%26code)                                       |
| 2018-03-23  | Read data function for network DEA       | [Documentation](https://github.com/wurmen/DEA/blob/master/Functions/read_data_for_networkDEA.md)/[Example](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/Read_data_for_network_DEA_function%20example.ipynb)/[Code](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/network_function.py)/[Folder](https://github.com/wurmen/DEA/tree/master/Functions/network_data%26code) |
| 2018-03-23  | Relational network DEA function          | [Documentation](https://github.com/wurmen/DEA/blob/master/Functions/network_DEA_function.md)/[Example](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/Network_DEA_function_example.ipynb)/[Code](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/network_function.py)/[Folder](https://github.com/wurmen/DEA/tree/master/Functions/network_data%26code)                     |

* * *

### Reference resources (Python-Gurobi)

If you are not familiar with python-gurobi modeling, you can refer to the following resources~

-   [Environmental installation teaching](https://github.com/wurmen/Gurobi-Python/blob/master/Installation/%E5%AE%89%E8%A3%9D%E6%95%99%E5%AD%B8.md)
-   [Python+Gurobi basic architecture](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python+Gurobi%E5%9F%BA%E6%9C%AC%E6%9E%B6%E6%A7%8B.md)<br>
-   [Python+Gurobi modeling](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python+Gurobi%E5%BB%BA%E6%A8%A1.md)<br>
-   [Python+Gurobi special data structure](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python%2BGurobi%E7%89%B9%E6%AE%8A%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B.ipynb)
