# आकड़ा लपेटना विश्लेषण

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)<br>

यहां हम मुख्य रूप से यह बताने के लिए कुछ उदाहरणों का उपयोग करते हैं कि डेटा-एनवेलपमेंट-विश्लेषण मॉड्यूल (डेटा-एनवेलपमेंट-एनालिसिस, डीईए) बनाने के लिए पायथन-गुरोबी का उपयोग कैसे करें।

### § आवश्यकताएं

-   पायथन 3.6

-   गुरुबिपी 6.5.2 या इससे ऊपर

### § डीईए मॉडल

इस क्षेत्र के लेख मुख्य रूप से निम्नलिखित डीईए मॉडल पेश करते हैं और पायथन-गुरोबी की मॉडलिंग प्रक्रिया की व्याख्या करते हैं:

-   सीआरएस (स्केल पर निरंतर रिटर्न; इनपुट-ओरिएंटेड): स्केल इनपुट-ओरिएंटेड मॉडल पर निश्चित रिटर्न

-   वीआरएस (वेरिएबल रिटर्न टू स्केल; इनपुट-ओरिएंटेड): वेरिएबल रिटर्न टू स्केल इनपुट-ओरिएंटेड मॉडल

-   रिलेशनल नेटवर्क डीईए मॉडल: रिलेशनल नेटवर्क डीईए मॉडल

| समय सुधारें | लेख                                                                                               |
| ----------- | ------------------------------------------------------------------------------------------------- |
| 2018-01-29  | [सीआरएस मॉडल](https://github.com/wurmen/DEA/blob/master/CRS_Model/CRS%20model.md)                 |
| 2018-02-05  | [वीआरएस मॉडल](https://github.com/wurmen/DEA/blob/master/VAS_Model/VRS%20model.md)                 |
| 2018-01-30  | [रिलेशनल नेटवर्क डीईए मॉडल](https://github.com/wurmen/DEA/blob/master/Network_DEA/network_dea.md) |

### § डीईए मॉडल फ़ंक्शंस

उपरोक्त DEA मॉडल के लिए कई सरल DEA एक्सटेंशन फ़ंक्शंस का निर्माण किया गया है, ताकि उपयोगकर्ता दक्षता विश्लेषण करने के लिए इन DEA फ़ंक्शंस का अधिक आसानी से उपयोग कर सकें, या वे इन पहले से निर्मित फ़ंक्शंस का विस्तार कर सकें।<br>

निम्नलिखित लिंक प्रत्येक विषय के स्पष्टीकरण लेख, नमूना लेख, कोड और फ़ाइल फ़ोल्डरों से मेल खाते हैं (जिसमें विषय के सभी संसाधन शामिल हैं)। आप स्पष्टीकरण लेखों के अनुसार डाउनलोड और सीख सकते हैं।

| समय सुधारें | लेख                                          | लिंक करना                                                                                                                                                                                                                                                                                                                                                                                                             |
| ----------- | -------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2018-03-23  | डीईए कार्य निर्देश                           | [प्रलेखन](https://github.com/wurmen/DEA/blob/master/Functions/user's%20guide.md)                                                                                                                                                                                                                                                                                                                                      |
| 2018-03-23  | बुनियादी डीईए मॉडल के लिए डेटा फ़ंक्शन पढ़ें | [प्रलेखन](https://github.com/wurmen/DEA/blob/master/Functions/read_data_function.md)/[उदाहरण](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/read_data_example.ipynb)/[कोड](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/DEA.py)/[फ़ोल्डर](https://github.com/wurmen/DEA/tree/master/Functions/basic_DEA_data%26code)                                         |
| 2018-03-23  | बुनियादी डीईए कार्य                          | [प्रलेखन](https://github.com/wurmen/DEA/blob/master/Functions/basic_dea_functions.md)/[उदाहरण](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/basic_DEA_function.ipynb)/[कोड](https://github.com/wurmen/DEA/blob/master/Functions/basic_DEA_data%26code/DEA.py)/[फ़ोल्डर](https://github.com/wurmen/DEA/tree/master/Functions/basic_DEA_data%26code)                                       |
| 2018-03-23  | नेटवर्क डीईए के लिए डेटा फ़ंक्शन पढ़ें       | [प्रलेखन](https://github.com/wurmen/DEA/blob/master/Functions/read_data_for_networkDEA.md)/[उदाहरण](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/Read_data_for_network_DEA_function%20example.ipynb)/[कोड](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/network_function.py)/[फ़ोल्डर](https://github.com/wurmen/DEA/tree/master/Functions/network_data%26code) |
| 2018-03-23  | रिलेशनल नेटवर्क डीईए फ़ंक्शन                 | [प्रलेखन](https://github.com/wurmen/DEA/blob/master/Functions/network_DEA_function.md)/[उदाहरण](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/Network_DEA_function_example.ipynb)/[कोड](https://github.com/wurmen/DEA/blob/master/Functions/network_data%26code/network_function.py)/[फ़ोल्डर](https://github.com/wurmen/DEA/tree/master/Functions/network_data%26code)                     |

* * *

### संदर्भ संसाधन (पायथन-गुरोबी)

यदि आप पायथन-गुरोबी मॉडलिंग से परिचित नहीं हैं, तो आप निम्नलिखित संसाधनों का संदर्भ ले सकते हैं~

-   [पर्यावरण स्थापना शिक्षण](https://github.com/wurmen/Gurobi-Python/blob/master/Installation/%E5%AE%89%E8%A3%9D%E6%95%99%E5%AD%B8.md)
-   [पायथन+गुरोबी बुनियादी वास्तुकला](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python+Gurobi%E5%9F%BA%E6%9C%AC%E6%9E%B6%E6%A7%8B.md)<br>
-   [पायथन+गुरोबी मॉडलिंग](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python+Gurobi%E5%BB%BA%E6%A8%A1.md)<br>
-   [पायथन+गुरोबी विशेष डेटा संरचना](https://github.com/wurmen/Gurobi-Python/blob/master/python-gurobi%20%20model/Python%2BGurobi%E7%89%B9%E6%AE%8A%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B.ipynb)
