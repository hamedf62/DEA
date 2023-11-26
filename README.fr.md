# Analyse d'enveloppement des données

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)<br>

Ici, nous utilisons principalement quelques exemples pour illustrer comment utiliser Python-Gurobi pour créer un module d'analyse d'enveloppement de données (Data-Envelopment-Analysis, DEA).

### § Exigences

-   python 3.6

-   gurobipy 6.5.2 ou supérieur

### § Modèles DEA

Les articles de ce domaine présentent principalement les modèles DEA suivants et expliquent le processus de modélisation de Python-Gurobi :

-   CRS(constant return to scale; input-oriented) ：固定規模報酬投入導向模型

-   VRS (retour d'échelle variable ; orienté entrées) : modèle à retour d'échelle variable orienté entrées

-   Modèle DEA de réseau relationnel : Modèle DEA de réseau relationnel

| Temps de mise à jour | article                                                                                               |
| -------------------- | ----------------------------------------------------------------------------------------------------- |
| 2018-01-29           | [Modèle CRS](https://github.com/wurmen/DEA/blob/master/CRS_Model/CRS%20model.md)                      |
| 2018-02-05           | [Modèle VRS](https://github.com/wurmen/DEA/blob/master/VAS_Model/VRS%20model.md)                      |
| 2018-01-30           | [Réseau relationnel Modèle DEA](https://github.com/wurmen/DEA/blob/master/Network_DEA/network_dea.md) |

### § Fonctions des modèles DEA

Plusieurs fonctions d'extension DEA simples sont construites pour le modèle DEA ci-dessus, afin que les utilisateurs puissent utiliser plus facilement ces fonctions DEA pour effectuer une analyse d'efficacité, ou qu'ils puissent étendre ces fonctions déjà construites.<br>

Les liens suivants correspondent aux articles d'explication, aux exemples d'articles, aux dossiers de code et de fichiers de chaque sujet (qui contiennent toutes les ressources du sujet).Vous pouvez télécharger et apprendre en fonction des articles d'explication.

| Temps de mise à jour | article                                                      | Mise en relation                                                                                                                                                                                                                                                                                                                                                                                                              |
| -------------------- | ------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2018-03-23           | Instructions pour les fonctions DEA                          | [Documentation](https://github.com/wurmen/DEA/blob/master/Functions/user's%20guide.md)                                                                                                                                                                                                                                                                                                                                        |
| 2018-03-23           | Fonctions de lecture de données pour les modèles DEA de base | [Documentation](https://github.com/wurmen/DEA/blob/master/Functions/read_data_function.md)/[Exemple](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/read_data_example.ipynb)/[Code](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/DEA.py)/[Dossier](https://github.com/wurmen/DEA/tree/master/Functions/basic_DEA_data%26code)                                         |
| 2018-03-23           | Fonctions DEA de base                                        | [Documentation](https://github.com/wurmen/DEA/blob/master/Functions/basic_dea_functions.md)/[Exemple](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/basic_DEA_function.ipynb)/[Code](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/DEA.py)/[Dossier](https://github.com/wurmen/DEA/tree/master/Functions/basic_DEA_data%26code)                                       |
| 2018-03-23           | Fonction de lecture de données pour le réseau DEA            | [Documentation](https://github.com/wurmen/DEA/blob/master/Functions/read_data_for_networkDEA.md)/[Exemple](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/Read_data_for_network_DEA_function%20example.ipynb)/[Code](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/network_function.py)/[Dossier](https://github.com/wurmen/DEA/tree/master/Functions/network_data%26code) |
| 2018-03-23           | Fonction DEA du réseau relationnel                           | [Documentation](https://github.com/wurmen/DEA/blob/master/Functions/network_DEA_function.md)/[Exemple](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/Network_DEA_function_example.ipynb)/[Code](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/network_function.py)/[Dossier](https://github.com/wurmen/DEA/tree/master/Functions/network_data%26code)                     |

* * *

### Ressources de référence (Python-Gurobi)

Si vous n'êtes pas familier avec la modélisation python-gurobi, vous pouvez vous référer aux ressources suivantes~

-   [Enseignement des installations environnementales](https://github.com/wurmen/Gurobi-Python/blob/master/Installation/%E5%AE%89%E8%A3%9D%E6%95%99%E5%AD%B8.md)
-   [Architecture de base Python+Gurobi](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python+Gurobi%E5%9F%BA%E6%9C%AC%E6%9E%B6%E6%A7%8B.md)<br>
-   [Modélisation Python+Gurobi](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python+Gurobi%E5%BB%BA%E6%A8%A1.md)<br>
-   [Python+Gurobi特殊資料結構](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python%2BGurobi%E7%89%B9%E6%AE%8A%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B.ipynb)
