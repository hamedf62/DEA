# شبکه

_جبهه_<br>_2017/01/30_<br>[【بازگشت به صفحه اصلی](https://github.com/wurmen/DEA)<br>

#### ※_مرجع_

_این مقاله به طور عمده به آن اشاره دارد[پروفسور گائو کیانگ](http://www.iim.ncku.edu.tw/files/11-1407-20368.php?Lang=zh-tw)مقاله منتشر شده در سال 2007:[تجزیه کارآیی در تجزیه و تحلیل پاکت داده های شبکه: یک مدل رابطه ای](https://www.sciencedirect.com/science/article/pii/S0377221707010077)_

## (一)前言

هنگام اندازه گیری کارآیی در DEA مشترک ، کل سیستم به طور کلی به عنوان یک کل در نظر گرفته می شود و در مورد وضعیت فرآیندهای داخلی بحث نمی کند ، اما اغلب کارآیی بین فرآیندهای داخلی را دقیقاً مانند ساخت.[مدل CRS](https://github.com/wurmen/DEA/blob/master/CRS_Model/CRS%20model.md)مثال پیشنهادی مانند است ، و استاد گائو کیانگ ساخت**مدل DEA شبکه مرتبط**. با معرفی فرآیندهای مجازی (فرآیندهای ساختگی) ، سیستم شبکه اصلی به یک سیستم سری تبدیل می شود و هر مرحله از این سری یک ساختار موازی برای دستیابی به هدف تجزیه کارآیی است. از طریق تجزیه کارایی ، فرایندهایی را که باعث می شود سیستم به طور ناکارآمد برای پیشرفت های آینده عمل کند ، پیدا کنید.**بنابراین ، در این مقاله ، ما عمدتاً از نمونه ها در مقاله و مدل ریاضی پیشنهادی برای نشان دادن و استفاده از پایتون-ژوروبی برای مدل سازی استفاده می کنیم**

## (ب) مثال

#### ※ این برای توضیح مثالهای ارائه شده در بخش 3 مقاله استفاده می شود

### § معماری سیستم نمونه

-   شکل زیر سیستمی است که توسط سه فرآیند تشکیل شده است. سیستم در ابتدا دارای دو ورودی و در نهایت سه خروجی است. شرایط ورودی و خروجی هر فرآیند در سیستم در شکل زیر نشان داده شده است:<br>

1.  دو سرمایه گذاری اولیه در سیستم برای پردازش 1 ، پردازش 2 و پردازش 3 به عنوان سرمایه گذاری مربوطه به سه بخش تقسیم می شود.<br>
2.  خروجی فرآیند 1 و فرآیند 2 به دو بخش تقسیم می شود ، یک قسمت خروجی سیستم نهایی است و بخش دیگر به عنوان بخشی از ورودی فرآیند 3 در نظر گرفته می شود.

<div align=center>
<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/network%20system.PNG" width="550" height="350">
</div>
<br>

-   به منظور دستیابی به تجزیه کارآیی و امکان اندازه گیری کارآیی هر فرآیند ، این مطالعه از طریق انجام شده است**به فرآیند مجازی بپیوندید**برای تبدیل سیستم فوق به یک سیستم با دو مرحله ، و هر مرحله یک ساختار موازی است ، همانطور که در شکل زیر نشان داده شده است:<br>

※ هر نمای نماد در شکل در مدل ریاضی زیر به تفصیل توضیح داده شده است

<div align=center>
<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/network%20system1.png" width="750" height="350">
</div>

##### ※ قبل از بخش 3 ، دو استدلال در این مطالعه مطرح شد (فرایند استنباط را می توان با جزئیات خواند[اصلی](https://www.sciencedirect.com/science/article/pii/S0377221707010077))

###### 1. در سیستمی که توسط یک فرآیند ساختار سری تشکیل شده است ، محصول راندمان هر فرآیند برابر با مقدار کارایی کلی است

###### 2. در سیستمی که توسط فرآیندهای ساختاری موازی تشکیل شده است ، جمع ناکارآمدی هر فرآیند برابر است با ضخامت های ناکارآمدی کارآیی کلی

###### بنابراین ، در این سیستم ، مقدار کل بازده سیستم محصول کارآیی هر مرحله از ساختار سری است ، یعنی محصول کارآیی مرحله 1 و مرحله 2 و آرامش کمترین بهره وری در هر مرحله ، مجموع آرامش با راندمان پایین است ، یعنی ، آرامش با راندمان پایین ، مجموع فرایند 1 و فرآیند آرامش بخش 2 است.

<br>

### § داده در مورد موارد مختلف خروجی و ورودی واحد تصمیم گیری

-   پنج واحد تصمیم گیری برای مقایسه وجود دارد و موقعیت های خروجی و ورودی سیستم ها و فرآیندهای آنها در جدول زیر نشان داده شده است:
    <div align=center>
    <img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/example-data.PNG" width="800" height="370">
    </div>

## (iii) مدل ریاضی

سیستم فوق می تواند یک مدل ریاضی را همانطور که در شکل زیر نشان داده شده است تشکیل دهد

### § شرح نماد

-   وت<sub>k</sup></sub>: ارزش کارایی واحد تصمیم k
-   N: تعداد واحدهای تصمیم گیری (DMU) (در این مثال n = 5)<br>
-   ε: مقدار مثبت بسیار کوچک آن را ثابت غیر Archimedean نامیده می شود ، که معمولاً روی 10 تنظیم می شود<sup>-4</sup></sub>یا 10<sup>-6</sup></sub>(هدف برای جلوگیری از نادیده گرفتن هرگونه ورودی یا خروجی)

### param توضیحات پارامتر

-   x<sub>IJ</sup></sub>: در سیستم کلی واحد تصمیم J (j = 1 ، ... ، n) ، موارد ورودی اولیه I (i = 1 ، ... ، m) (در این مثال m = 2)

-   x<sup>(T)</sup></sub><sub>IJ</sup></sub>: واحد تصمیم J (j = 1 ، ... ، n) در مورد ورودی i-th از فرآیند t است (در این مثال t = 1،2،3 ، i = 1،2)

-   وت<sup>()</sup></sub><sub>1J</sup></sub>وت<sup>(من)</sup></sub><sub>1J</sup></sub>: مورد خروجی واحد تصمیم J (j = 1 ، ... ، n) فرآیند 1 ، y<sup>()</sup></sub><sub>1J</sup></sub>برای خروجی سیستم نهایی ، y<sup>(من)</sup></sub><sub>1J</sup></sub>بخشی از سرمایه گذاری در فرآیند 3 خواهد شد

-   وت<sup>()</sup></sub><sub>ام الو</sup></sub>وت<sup>(من)</sup></sub><sub>ام الو</sup></sub>: مورد خروجی واحد تصمیم J (j = 1 ، ... ، n) فرآیند 1 ، y<sup>()</sup></sub><sub>ام الو</sup></sub>برای خروجی سیستم نهایی ، y<sup>(من)</sup></sub><sub>ام الو</sup></sub>بخشی از سرمایه گذاری در فرآیند 3 خواهد شد

-   وت<sub>IJ</sup></sub>: کل خروجی واحد تصمیم گیری J (J = 1 ، ... ، N) در فرآیند I

### § متغیرهای تصمیم گیری

-   در<sub>حرف</sup></sub>: وزن مورد خروجی R-Th (در این مثال r = 1،2،3)
-   در<sub>من</sup></sub>: وزن مورد سرمایه گذاری I-Th (در این مثال I = 1،2)

### § هدفمند و محدود شده است

این مدل ریاضی مدل DEA شبکه انجمن است که توسط استاد گائو پیشنهاد شده است<br>

※ این مدل بر اساس مدل CRS تمدید می شود (برای جزئیات بیشتر ، لطفاً به آن مراجعه کنید[اصلی](https://www.sciencedirect.com/science/article/pii/S0377221707010077))

<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/model1.png" width="550" height="250">

### § بهره وری هر فرآیند

پس از اتمام راه حل ، مقادیر کارایی فردی هر فرآیند را می توان از طریق فرمولهای ریاضی زیر محاسبه کرد.

<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/model2.png" width="450" height="120">

### § بهره وری در هر مرحله

پس از اتمام راه حل ، می توان از فرمول ریاضی زیر برای محاسبه مقادیر کارایی هر مرحله استفاده کرد.

<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/model3.png" width="470" height="105">

## (iii) پایتون-گروبی

در اینجا ما نحوه استفاده از Python-Gurobi برای ساخت مدل DEA از شبکه مرتبط را توضیح می دهیم

##### ※ می توان روی کد برنامه کامل کلیک کرد[در اینجا](https://github.com/wurmen/DEA/blob/master/Network_DEA/network_dea_code.py)

### وارد کردن گورویوپو

```python
from gurobipy import*
```

### پارامترها اضافه کنید

-   راندمان هر واحد تصمیم را از طریق حلقه برای محاسبه کنید

```python
DMU=['A', 'B','C','D','E']
E={}
val_p1,val_p2,val_p3,val_s1,val_s2={},{},{},{},{}
slack_p1,slack_p2,slack_p3={},{},{}
for k in DMU:

    I=2 # 兩項投入
    O=3 # 三項產出
```

-   TOTX1 و TOTX2 دو داده ورودی اولیه سیستم کلی هر واحد تصمیم گیری هستند.

```python
    DMU,Totx1,Totx2=multidict({("A"):[11,14],("B"):[7,7],("C"):[11,14],("D"):[14,14],("E"):[14,15]})
```

-   داده های خروجی و ورودی هر فرآیند را ضبط کنید و فرآیند 1 را به عنوان نمونه انجام دهید:<br>Proc1x1: ضبط اولین داده های ورودی فرآیند 1<br>Proc1x2: ضبط داده های ورودی دوم فرآیند 1<br>Proc1Totyo: کل داده های خروجی برای فرآیند ضبط 1 (Proc1Totyo = Proc1yo+Proc1yi)<br>Proc1yo: داده های حاصل از کل خروجی فرآیند ضبط 1 خروجی سیستم نهایی است<br>Proc1yi: داده هایی که مورد ورودی فرآیند 3 در کل خروجی فرآیند 1 خواهد بود<br>

```python
    DMU,proc1x1,proc1x2,proc1TotyO,proc1yO,proc1yI=multidict({("A"):[3,5,4,2,2],("B"):[2,3,2,1,1],("C"):[3,4,2,1,1],("D"):[4,6,3,2,1],("E"):[5,6,4,3,1]})
    DMU,proc2x1,proc2x2,proc2TotyO,proc2yO,proc2yI=multidict({("A"):[4,3,3,2,1],("B"):[2,1,2,1,1],("C"):[5,3,2,1,1],("D"):[5,5,4,3,1],("E"):[5,4,4,2,2]})
    DMU,proc3x1,proc3x2,proc3TotyO=multidict({("A"):[4,6,1],("B"):[3,3,1],("C"):[3,7,2],("D"):[5,3,1],("E"):[4,5,3]})
```

### مدل

```python
    m=Model("network_DEA")
```

### متغیرهای تصمیم گیری را اضافه کنید

-   وزن ورودی و خروجی متغیرهای تصمیم را تعیین کنید<sub>من</sup></sub>、 تو<sub>حرف</sup></sub>

```python
    P1,P2,P3={},{},{}
    v,u={},{}
   
    for i in range(I):
        v[i]=m.addVar(vtype=GRB.CONTINUOUS,name="v_%d"%i)
    
    for r in range(O):
        u[r]=m.addVar(vtype=GRB.CONTINUOUS,name="u_%d"%i)
```

### بروزرسانی

```python
    
    m.update()
```

### هدف را اضافه کنید

```python
    m.setObjective(u[0]*proc1yO[k]+u[1]*proc2yO[k]+u[2]*proc3TotyO[k],GRB.MAXIMIZE)
```

### محدودیت ها را اضافه کنید

```python
    m.addConstr(v[0]*Totx1[k]+v[1]*Totx2[k]==1)
    for j in DMU:
        P1[j]=m.addConstr(u[0]*proc1TotyO[j]-(v[0]*proc1x1[j]+v[1]*proc1x2[j])<=0)
        P2[j]=m.addConstr(u[1]*proc2TotyO[j]-(v[0]*proc2x1[j]+v[1]*proc2x2[j])<=0)
        P3[j]=m.addConstr(u[2]*proc3TotyO[j]-(v[0]*proc3x1[j]+v[1]*proc3x2[j]+u[0]*proc1yI[j]+u[1]*proc2yI[j])<=0)
```

### نتیجه چاپی

```python
    m.optimize()
    E[k]="The efficiency of DMU %s:%4.4g"%(k,m.objVal) #取得決策單位的整體效率值
```

-   راه حل V را دریافت کنید<sub>من</sup></sub>、 تو<sub>حرف</sup></sub>ارزش

```python
    u_sol = m.getAttr('x', u)
    v_sol = m.getAttr('x',v)
```

-   مقادیر کارایی هر فرآیند را محاسبه کنید

```python
    
    E1=u_sol[0]*proc1TotyO[k]/(v_sol[0]*proc1x1[k]+v_sol[1]*proc1x2[k]) 
    E2=u_sol[1]*proc2TotyO[k]/(v_sol[0]*proc2x1[k]+v_sol[1]*proc2x2[k])
    E3=u_sol[2]*proc3TotyO[k]/(v_sol[0]*proc3x1[k]+v_sol[1]*proc3x2[k]+u_sol[0]*proc1yI[k]+u_sol[1]*proc2yI[k])
```

-   مقادیر کارایی هر مرحله را محاسبه کنید

```python
    
    stage1=(u_sol[0]*proc1TotyO[k]+u_sol[1]*proc2TotyO[k]+v_sol[0]*proc3x1[k]+v_sol[1]*proc3x2[k])/(v_sol[0]*Totx1[k]+v_sol[1]*Totx2[k])
    stage2=(u_sol[0]*proc1yO[k]+u_sol[1]*proc2yO[k]+u_sol[2]*proc3TotyO[k])/(u_sol[0]*proc1TotyO[k]+u_sol[1]*proc2TotyO[k]+v_sol[0]*proc3x1[k]+v_sol[1]*proc3x2[k])
```

-   مقادیر کارایی هر فرآیند و مرحله هر واحد تصمیم گیری را ثبت کنید

```python
    val_p1[k]='The efficiency of process 1 of DMU %s:%4.4g'%(k,E1)
    val_p2[k]='The efficiency of process 2 of DMU %s:%4.4g'%(k,E2)
    val_p3[k]='The efficiency of process 3 of DMU %s:%4.4g'%(k,E3)
    val_s1[k]='The efficiency of stage 1 of DMU %s:%4.4g'%(k,stage1)
    val_s2[k]='The efficiency of stage 2 of DMU %s:%4.4g'%(k,stage2)
```

-   برای به دست آوردن مقدار ناکارآمدی هر فرآیند از پارامترهای Slack در گوروبی استفاده کنید

```python

    process1_slack=m.getAttr('slack',P1)
    slack_p1[k]='The inefficiency of process 1 of DMU %s:%4.4g'%(k,process1_slack[k])
    process2_slack=m.getAttr('slack',P2)
    slack_p2[k]='The inefficiency of process 2 of DMU %s:%4.4g'%(k,process2_slack[k])
    process3_slack=m.getAttr('slack',P3)
    slack_p3[k]='The inefficiency of process 3 of DMU %s:%4.4g'%(k,process3_slack[k])
```

-   نتایج را نشان می دهد

```python
for k in DMU:
    
    print (E[k])
    print (val_p1[k])
    print (val_p2[k])
    print (val_p3[k])
    print (val_s1[k])
    print (val_s2[k])
    print (slack_p1[k])
    print (slack_p2[k])
    print (slack_p3[k])

```

**سرانجام ، نتایج نشان داده شده در زیر می توان بدست آورد**<br>

    The efficiency of DMU A:0.5227
    The efficiency of process 1 of DMU A:   1
    The efficiency of process 2 of DMU A:0.75
    The efficiency of process 3 of DMU A:0.3462
    The efficiency of stage 1 of DMU A:0.9091
    The efficiency of stage 2 of DMU A:0.575
    The inefficiency of process 1 of DMU A:   0
    The inefficiency of process 2 of DMU A:0.09091
    The inefficiency of process 3 of DMU A:0.3864

    The efficiency of DMU B:0.5952
    The efficiency of process 1 of DMU B:0.8333
    The efficiency of process 2 of DMU B:   1
    The efficiency of process 3 of DMU B:0.5088
    The efficiency of stage 1 of DMU B:0.9286
    The efficiency of stage 2 of DMU B:0.641
    The inefficiency of process 1 of DMU B:0.07143
    The inefficiency of process 2 of DMU B:   0
    The inefficiency of process 3 of DMU B:0.3333

    The efficiency of DMU C:0.5682
    The efficiency of process 1 of DMU C: 0.5
    The efficiency of process 2 of DMU C: 0.4
    The efficiency of process 3 of DMU C:0.9474
    The efficiency of stage 1 of DMU C:0.5909
    The efficiency of stage 2 of DMU C:0.9615
    The inefficiency of process 1 of DMU C:0.1364
    The inefficiency of process 2 of DMU C:0.2727
    The inefficiency of process 3 of DMU C:0.02273

    The efficiency of DMU D:0.4821
    The efficiency of process 1 of DMU D:0.5625
    The efficiency of process 2 of DMU D: 0.8
    The efficiency of process 3 of DMU D:0.3333
    The efficiency of stage 1 of DMU D:0.8036
    The efficiency of stage 2 of DMU D: 0.6
    The inefficiency of process 1 of DMU D:0.125
    The inefficiency of process 2 of DMU D:0.07143
    The inefficiency of process 3 of DMU D:0.3214

    The efficiency of DMU E: 0.8
    The efficiency of process 1 of DMU E:0.8333
    The efficiency of process 2 of DMU E: 0.5
    The efficiency of process 3 of DMU E:   1
    The efficiency of stage 1 of DMU E: 0.8
    The efficiency of stage 2 of DMU E:   1
    The inefficiency of process 1 of DMU E:0.06667
    The inefficiency of process 2 of DMU E:0.1333
    The inefficiency of process 3 of DMU E:   0
