# تحلیل پوششی داده ها

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)<br>

در اینجا ما عمدتاً از چند مثال برای نشان دادن نحوه استفاده از Python-Gurobi برای ساخت یک ماژول تحلیل پوششی داده (Data-Envelopment-Analysis، DEA) استفاده می کنیم.

### § الزامات

-   پایتون 3.6

-   gurobipy 6.5.2 یا بالاتر

### § مدل های DEA

مقالات در این زمینه عمدتاً مدل‌های DEA زیر را معرفی می‌کنند و فرآیند مدل‌سازی Python-Gurobi را توضیح می‌دهند:

-   CRS (بازگشت ثابت به مقیاس؛ ورودی محور): بازگشت ثابت به مقیاس مدل ورودی محور

-   VRS (بازگشت متغیر به مقیاس؛ ورودی محور): بازگشت متغیر به مقیاس مدل ورودی گرا

-   مدل DEA شبکه رابطه ای: مدل DEA شبکه رابطه ای

| زمان به روز رسانی | مقاله                                                                                         |
| ----------------- | --------------------------------------------------------------------------------------------- |
| 2018-01-29        | [مدل CRS](https://github.com/wurmen/DEA/blob/master/CRS_Model/CRS%20model.md)                 |
| 2018-02-05        | [مدل VRS](https://github.com/wurmen/DEA/blob/master/VAS_Model/VRS%20model.md)                 |
| 2018-01-30        | [مدل DEA شبکه رابطه ای](https://github.com/wurmen/DEA/blob/master/Network_DEA/network_dea.md) |

### § توابع مدل های DEA

چندین تابع توسعه ساده DEA برای مدل DEA فوق ساخته شده است، به طوری که کاربران می توانند به راحتی از این توابع DEA برای انجام تجزیه و تحلیل کارایی استفاده کنند، یا می توانند این توابع از قبل ساخته شده را گسترش دهند.<br>

لینک های زیر مربوط به مقاله های توضیحی، نمونه مقالات، پوشه کد و فایل هر مبحث (که شامل تمامی منابع موضوع می باشد) می باشد که می توانید با توجه به مقاله های توضیحی دانلود و آموزش ببینید.

| زمان به روز رسانی | مقاله                                    | ربط دادن                                                                                                                                                                                                                                                                                                                                                                                                        |
| ----------------- | ---------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2018-03-23        | دستورالعمل توابع DEA                     | [مستندات](https://github.com/wurmen/DEA/blob/master/Functions/user's%20guide.md)                                                                                                                                                                                                                                                                                                                                |
| 2018-03-23        | خواندن توابع داده برای مدل های اساسی DEA | [مستندات](https://github.com/wurmen/DEA/blob/master/Functions/read_data_function.md)/[مثال](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/read_data_example.ipynb)/[کد](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/DEA.py)/[پوشه](https://github.com/wurmen/DEA/tree/master/Functions/basic_DEA_data%26code)                                         |
| 2018-03-23        | توابع اساسی DEA                          | [مستندات](https://github.com/wurmen/DEA/blob/master/Functions/basic_dea_functions.md)/[مثال](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/basic_DEA_function.ipynb)/[کد](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/DEA.py)/[پوشه](https://github.com/wurmen/DEA/tree/master/Functions/basic_DEA_data%26code)                                       |
| 2018-03-23        | خواندن تابع داده برای شبکه DEA           | [مستندات](https://github.com/wurmen/DEA/blob/master/Functions/read_data_for_networkDEA.md)/[مثال](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/Read_data_for_network_DEA_function%20example.ipynb)/[کد](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/network_function.py)/[پوشه](https://github.com/wurmen/DEA/tree/master/Functions/network_data%26code) |
| 2018-03-23        | تابع DEA شبکه رابطه ای                   | [مستندات](https://github.com/wurmen/DEA/blob/master/Functions/network_DEA_function.md)/[مثال](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/Network_DEA_function_example.ipynb)/[کد](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/network_function.py)/[پوشه](https://github.com/wurmen/DEA/tree/master/Functions/network_data%26code)                     |

* * *

### منابع مرجع (Python-Gurobi)

اگر با مدل سازی پایتون-گوروبی آشنایی ندارید می توانید به منابع زیر مراجعه کنید~

-   [آموزش نصب و راه اندازی محیطی](https://github.com/wurmen/Gurobi-Python/blob/master/Installation/%E5%AE%89%E8%A3%9D%E6%95%99%E5%AD%B8.md)
-   [معماری پایه پایتون + گوروبی](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python+Gurobi%E5%9F%BA%E6%9C%AC%E6%9E%B6%E6%A7%8B.md)<br>
-   [مدل سازی پایتون + گوروبی](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python+Gurobi%E5%BB%BA%E6%A8%A1.md)<br>
-   [ساختار داده ویژه Python+Gurobi](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python%2BGurobi%E7%89%B9%E6%AE%8A%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B.ipynb)
