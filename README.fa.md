# شبکه DEA

_POLab_<br>_2017/01/30_<br>[【بازگشت به صفحه اصلی】](https://github.com/wurmen/DEA)<br>

#### ※_مرجع_

_این مقاله عمدتا به[پروفسور گائو کیانگ](http://www.iim.ncku.edu.tw/files/11-1407-20368.php?Lang=zh-tw)مقاله منتشر شده در سال 2007:[تجزیه کارایی در تحلیل پوششی داده های شبکه: یک مدل رابطه ای](https://www.sciencedirect.com/science/article/pii/S0377221707010077)_

## (1) پیشگفتار

هنگامی که DEA معمولی کارایی را اندازه گیری می کند، به طور کلی با کل سیستم به عنوان یک کل برخورد می کند و وضعیت هر فرآیند داخلی را مورد بحث قرار نمی دهد، با این حال، اغلب کارایی بین فرآیندهای درون سیستم را نادیده می گیرد.[مدل CRS](https://github.com/wurmen/DEA/blob/master/CRS_Model/CRS%20model.md)مثال ارائه شده مشابه است و پروفسور گائو کیانگ یک را ساخت**مدل DEA شبکه انجمن**(Relational network DEA model)，藉由該模型來探討系統內部各製程間的相互關係，並同時衡量系統效率及各製程的效率，通過引入虛擬製程(Dummy processes)，將原始網絡系統轉換為串聯系統，並使串聯中的每個階段都是並行結構，以達到效率分解的目的，透過效率分解，找出導致系統低效運行的製程，以便將來進行改進；**بنابراین در این مقاله عمدتاً از مثال‌های موجود در مقاله و مدل ریاضی پیشنهادی برای توضیح و استفاده از Python-Gurobi برای مدل‌سازی استفاده می‌کنیم.**

## (2) شرح مثال

#### ※ در اینجا از مثال ارائه شده در بخش 3 مقاله برای توضیح استفاده می کنیم.

### § نمونه معماری سیستم

-   شکل زیر سیستمی است که توسط سه فرآیند تشکیل شده است. سیستم در ابتدا دارای دو ورودی است و در نهایت دارای سه خروجی خواهد بود.<br>

1.  دو ورودی اولیه سیستم به سه قسمت برای فرآیند 1، فرآیند 2 و فرآیند 3 به عنوان ورودی های مربوطه تقسیم می شوند.<br>
2.  خروجی فرآیند 1 و فرآیند 2 به دو قسمت تقسیم می شود که یک قسمت خروجی نهایی سیستم است و قسمت دیگر به عنوان بخشی از ورودی فرآیند 3 استفاده می شود.

<div align=center>
<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/network%20system.PNG" width="550" height="350">
</div>
<br>

-   به منظور دستیابی به تجزیه کارایی به طوری که بتوان کارایی هر فرآیند را اندازه گیری کرد، این مطالعه از**به فرآیند مجازی بپیوندید**برای تبدیل سیستم فوق به یک سیستم دارای دو مرحله، هر مرحله یک ساختار موازی است که در شکل زیر نشان داده شده است:<br>

※ هر نماد در شکل به طور کامل در مدل ریاضی زیر توضیح داده شده است.

<div align=center>
<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/network%20system1.png" width="750" height="350">
</div>

##### ※قبل از بخش سوم، این تحقیق دو استدلال ارائه کرده است (فرایند استنتاج را می توان با جزئیات خواند.[اصلی](https://www.sciencedirect.com/science/article/pii/S0377221707010077))

###### 1. در سیستمی که توسط فرآیندها در یک ساختار سری تشکیل شده است، محصول بازده هر فرآیند برابر با مقدار کارایی کلی است.

###### 2. در سیستمی که توسط فرآیندهای با ساختار موازی تشکیل شده است، مجموع سستی ناکارآمدی هر فرآیند برابر با افت ناکارآمدی بازده کلی است.

###### بنابراین، در این سیستم، مقدار بازده کلی سیستم، حاصل ضرب بازده هر مرحله در ساختار سری، یعنی حاصلضرب راندمان مرحله 1 و مرحله 2 است و ناکارآمدی هر مرحله به سطح کاهش می یابد. ناکارآمدی هر فرآیند در ساختار موازی آرامش کلی، یعنی آرامش ناکارآمد در مرحله 1، مجموع فرآیند 1 و فرآیند 2 است و آرامش ناکارآمد در مرحله 2 برابر با آرامش ناکارآمد در فرآیند 3 است.

<br>

### § داده های اقلام مختلف خروجی و اقلام ورودی واحدهای تصمیم گیری

-   پنج واحد تصمیم گیری برای مقایسه وجود دارد. خروجی و ورودی سیستم های آنها و هر فرآیند مطابق جدول زیر است
    <div align=center>
    <img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/example-data.PNG" width="800" height="370">
    </div>

## (3) مدل ریاضی

سیستم فوق می تواند یک مدل ریاضی مانند شکل زیر تشکیل دهد

### § شرح نماد

-   و<sub>ک</sup></sub>: ارزش کارایی واحد تصمیم گیری k
-   n: تعداد واحدهای تصمیم گیری (DMU) (n=5 در این مثال)<br>
-   ε: یک مقدار مثبت بسیار کوچک، ثابت غیر ارشمیدسی نامیده می شود که معمولاً روی 10 تنظیم می شود<sup>-4</sup></sub>یا 10<sup>-6</sup></sub>(هدف جلوگیری از نادیده گرفته شدن هر ورودی یا خروجی است)

### § شرح پارامتر

-   X<sub>ij</sup></sub>: در سیستم کلی واحد تصمیم گیری j (j=1,...,n)، آیتم ورودی اولیه i (i=1,...,m) (m=2 در این مثال)

-   X<sup>(t)</sup></sub><sub>ij</sup></sub>: i-امین مورد ورودی واحد تصمیم گیری j (j=1,...,n) در فرآیند t (در این مثال t=1,2,3, i=1,2)

-   و<sup>(The)</sup></sub><sub>1j</sup></sub>، و<sup>(من)</sup></sub><sub>1j</sup></sub>: آیتم خروجی فرآیند 1 واحد تصمیم گیری j (j=1,...,n), Y<sup>(The)</sup></sub><sub>1j</sup></sub>خروجی نهایی سیستم، Y است<sup>(من)</sup></sub><sub>1j</sup></sub>بخشی از موارد ورودی در فرآیند 3 خواهد شد

-   و<sup>(The)</sup></sub><sub>اوه</sup></sub>، و<sup>(من)</sup></sub><sub>اوه</sup></sub>: آیتم خروجی فرآیند 1 واحد تصمیم گیری j (j=1,...,n), Y<sup>(The)</sup></sub><sub>اوه</sup></sub>خروجی نهایی سیستم، Y است<sup>(من)</sup></sub><sub>اوه</sup></sub>بخشی از موارد ورودی در فرآیند 3 خواهد شد

-   و<sub>ij</sup></sub>: کل خروجی واحد تصمیم گیری j (j=1,...,n) در فرآیند i

### § متغیرهای تصمیم گیری

-   در<sub>r</sup></sub>: وزن r-امین آیتم خروجی (در این مثال r=1،2،3)
-   v<sub>من</sup></sub>: وزن i-امین آیتم ورودی (i=1,2 در این مثال)

### § هدف و محدودیت

این مدل ریاضی مدل DEA شبکه ارتباطی است که توسط پروفسور گائو پیشنهاد شده است<br>

※ این مدل بر اساس پسوند مدل CRS است (لطفاً مراجعه کنید[اصلی](https://www.sciencedirect.com/science/article/pii/S0377221707010077))

<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/model1.png" width="550" height="250">

### § کارایی هر فرآیند

پس از حل مسئله، مقادیر بازده فردی هر فرآیند را می توان از طریق فرمول های ریاضی زیر محاسبه کرد:

<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/model2.png" width="450" height="120">

### § کارایی هر مرحله

پس از حل مسئله می توان از فرمول های ریاضی زیر برای محاسبه مقدار بازده هر مرحله استفاده کرد.

<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/model3.png" width="470" height="105">

## (3) پایتون-گوروبی

در اینجا توضیحی در مورد نحوه استفاده از Python-Gurobi برای ساخت یک مدل شبکه ارتباطی DEA آورده شده است.

##### ※ کد برنامه کامل را می توان کلیک کرد[اینجا](https://github.com/wurmen/DEA/blob/master/Network_DEA/network_dea_code.py)

### واردات گوروبیپی

```python
from gurobipy import*
```

### پارامترها را اضافه کنید

-   کارایی هر واحد تصمیم گیری را از طریق حلقه for محاسبه کنید

```python
DMU=['A', 'B','C','D','E']
E={}
val_p1,val_p2,val_p3,val_s1,val_s2={},{},{},{},{}
slack_p1,slack_p2,slack_p3={},{},{}
for k in DMU:

    I=2 # 兩項投入
    O=3 # 三項產出
```

-   Totx1 و Totx2 دو داده ورودی اولیه سیستم کلی هر واحد تصمیم گیری هستند.

```python
    DMU,Totx1,Totx2=multidict({("A"):[11,14],("B"):[7,7],("C"):[11,14],("D"):[14,14],("E"):[14,15]})
```

-   داده های خروجی و ورودی هر فرآیند را با مثال از فرآیند 1 ثبت کنید:<br>proc1x1: اولین داده ورودی فرآیند 1 را ثبت می کند<br>proc1x2: دومین داده ورودی فرآیند 1 را ثبت می کند<br>proc1TotyO: کل داده های خروجی فرآیند 1 را ثبت کنید (proc1TotyO= proc1yO+Proc1yI)<br>proc1yO: داده های خروجی سیستم نهایی را در کل خروجی فرآیند 1 ثبت می کند<br>Proc1yI: ثبت داده های کل خروجی فرآیند 1 که به موارد ورودی فرآیند 3 تبدیل می شود.<br>

```python
    DMU,proc1x1,proc1x2,proc1TotyO,proc1yO,proc1yI=multidict({("A"):[3,5,4,2,2],("B"):[2,3,2,1,1],("C"):[3,4,2,1,1],("D"):[4,6,3,2,1],("E"):[5,6,4,3,1]})
    DMU,proc2x1,proc2x2,proc2TotyO,proc2yO,proc2yI=multidict({("A"):[4,3,3,2,1],("B"):[2,1,2,1,1],("C"):[5,3,2,1,1],("D"):[5,5,4,3,1],("E"):[5,4,4,2,2]})
    DMU,proc3x1,proc3x2,proc3TotyO=multidict({("A"):[4,6,1],("B"):[3,3,1],("C"):[3,7,2],("D"):[5,3,1],("E"):[4,5,3]})
```

### مدل

```python
    m=Model("network_DEA")
```

### متغیرهای تصمیم را اضافه کنید

-   تعیین وزن ورودی و خروجی متغیر تصمیم v<sub>من</sup></sub>تو<sub>r</sup></sub>

```python
    P1,P2,P3={},{},{}
    v,u={},{}
   
    for i in range(I):
        v[i]=m.addVar(vtype=GRB.CONTINUOUS,name="v_%d"%i)
    
    for r in range(O):
        u[r]=m.addVar(vtype=GRB.CONTINUOUS,name="u_%d"%i)
```

### به روز رسانی

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

### نتیجه چاپ

```python
    m.optimize()
    E[k]="The efficiency of DMU %s:%4.4g"%(k,m.objVal) #取得決策單位的整體效率值
```

-   دریافت راه حل v<sub>من</sup></sub>تو<sub>r</sup></sub>ارزش

```python
    u_sol = m.getAttr('x', u)
    v_sol = m.getAttr('x',v)
```

-   مقدار کارایی هر فرآیند را محاسبه کنید

```python
    
    E1=u_sol[0]*proc1TotyO[k]/(v_sol[0]*proc1x1[k]+v_sol[1]*proc1x2[k]) 
    E2=u_sol[1]*proc2TotyO[k]/(v_sol[0]*proc2x1[k]+v_sol[1]*proc2x2[k])
    E3=u_sol[2]*proc3TotyO[k]/(v_sol[0]*proc3x1[k]+v_sol[1]*proc3x2[k]+u_sol[0]*proc1yI[k]+u_sol[1]*proc2yI[k])
```

-   مقدار کارایی هر مرحله را محاسبه کنید

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

-   از پارامتر slack در gurobi برای بدست آوردن مقدار ناکارآمدی هر فرآیند استفاده کنید

```python

    process1_slack=m.getAttr('slack',P1)
    slack_p1[k]='The inefficiency of process 1 of DMU %s:%4.4g'%(k,process1_slack[k])
    process2_slack=m.getAttr('slack',P2)
    slack_p2[k]='The inefficiency of process 2 of DMU %s:%4.4g'%(k,process2_slack[k])
    process3_slack=m.getAttr('slack',P3)
    slack_p3[k]='The inefficiency of process 3 of DMU %s:%4.4g'%(k,process3_slack[k])
```

-   نمایش نتایج

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

**در نهایت می توانید نتیجه را مطابق شکل زیر بدست آورید**<br>

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
