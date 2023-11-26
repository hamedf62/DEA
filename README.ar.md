# تحليل مغلف البيانات

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)<br>

نستخدم هنا بشكل أساسي بعض الأمثلة لتوضيح كيفية استخدام Python-Gurobi لبناء وحدة تحليل مغلف البيانات (تحليل مغلف البيانات، DEA).

### § متطلبات

-   بيثون 3.6

-   جوروبيبي 6.5.2 أو أعلى

### § نماذج DEA

تقدم المقالات في هذا المجال بشكل أساسي نماذج DEA التالية وتشرح عملية نمذجة Python-Gurobi:

-   CRS (العودة الثابتة إلى المقياس؛ موجه نحو الإدخال): نموذج العودة الثابتة إلى المقياس الموجه نحو الإدخال

-   VRS (العودة المتغيرة إلى المقياس؛ موجه نحو الإدخال): نموذج العودة المتغيرة إلى المقياس الموجه نحو الإدخال

-   نموذج الشبكة العلائقية DEA: نموذج الشبكة العلائقية DEA

| تحديث الوقت | شرط                                                                                                |
| ----------- | -------------------------------------------------------------------------------------------------- |
| ٢٠١٨-٠١-٢٩  | [نموذج CRS](https://github.com/wurmen/DEA/blob/master/CRS_Model/CRS%20model.md)                    |
| ٢٠١٨-٠٢-٠٥  | [نموذج VRS](https://github.com/wurmen/DEA/blob/master/VAS_Model/VRS%20model.md)                    |
| ٢٠١٨-٠١-٣٠  | [نموذج DEA للشبكة العلائقية](https://github.com/wurmen/DEA/blob/master/Network_DEA/network_dea.md) |

### § وظائف نماذج DEA

تم إنشاء العديد من وظائف تمديد DEA البسيطة لنموذج DEA أعلاه، بحيث يمكن للمستخدمين استخدام وظائف DEA هذه بسهولة أكبر لإجراء تحليل الكفاءة، أو يمكنهم توسيع هذه الوظائف المبنية بالفعل.<br>

الروابط التالية تتوافق مع المقالات التوضيحية ونماذج المقالات والأكواد ومجلدات الملفات الخاصة بكل موضوع (والتي تحتوي على جميع موارد الموضوع)، ويمكنك التنزيل والتعلم وفقًا لمقالات الشرح.

| تحديث الوقت | شرط                                      | الربط                                                                                                                                                                                                                                                                                                                                                                                                           |
| ----------- | ---------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ٢٠١٨-٠٣-٢٣  | تعليمات وظائف DEA                        | [توثيق](https://github.com/wurmen/DEA/blob/master/Functions/user's%20guide.md)                                                                                                                                                                                                                                                                                                                                  |
| ٢٠١٨-٠٣-٢٣  | قراءة وظائف البيانات لنماذج DEA الأساسية | [توثيق](https://github.com/wurmen/DEA/blob/master/Functions/read_data_function.md)/[Example](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/read_data_example.ipynb)/[شفرة](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/DEA.py)/[مجلد](https://github.com/wurmen/DEA/tree/master/Functions/basic_DEA_data%26code)                                      |
| ٢٠١٨-٠٣-٢٣  | وظائف DEA الأساسية                       | [توثيق](https://github.com/wurmen/DEA/blob/master/Functions/basic_dea_functions.md)/[مثال](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/basic_DEA_function.ipynb)/[شفرة](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/DEA.py)/[مجلد](https://github.com/wurmen/DEA/tree/master/Functions/basic_DEA_data%26code)                                       |
| ٢٠١٨-٠٣-٢٣  | قراءة وظيفة البيانات لشبكة DEA           | [توثيق](https://github.com/wurmen/DEA/blob/master/Functions/read_data_for_networkDEA.md)/[مثال](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/Read_data_for_network_DEA_function%20example.ipynb)/[Code](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/network_function.py)/[مجلد](https://github.com/wurmen/DEA/tree/master/Functions/network_data%26code) |
| ٢٠١٨-٠٣-٢٣  | وظيفة DEA للشبكة العلائقية               | [توثيق](https://github.com/wurmen/DEA/blob/master/Functions/network_DEA_function.md)/[مثال](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/Network_DEA_function_example.ipynb)/[شفرة](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/network_function.py)/[مجلد](https://github.com/wurmen/DEA/tree/master/Functions/network_data%26code)                     |

* * *

### الموارد المرجعية (بايثون-جوروبي)

إذا لم تكن على دراية بنمذجة python-gurobi، فيمكنك الرجوع إلى الموارد التالية~

-   [تعليم التركيب البيئي](https://github.com/wurmen/Gurobi-Python/blob/master/Installation/%E5%AE%89%E8%A3%9D%E6%95%99%E5%AD%B8.md)
-   [بنية بايثون + جوروبي الأساسية](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python+Gurobi%E5%9F%BA%E6%9C%AC%E6%9E%B6%E6%A7%8B.md)<br>
-   [نمذجة بايثون + جوروبي](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python+Gurobi%E5%BB%BA%E6%A8%A1.md)<br>
-   [بنية البيانات الخاصة بـ Python+Gurobi](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python%2BGurobi%E7%89%B9%E6%AE%8A%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B.ipynb)
