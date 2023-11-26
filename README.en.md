# Network DEA

_POLab_<br>_2017/01/30_<br>[【back to the homepage】](https://github.com/wurmen/DEA)<br>

#### ※_Reference_

_This article mainly refers to[Professor Gao Qiang](http://www.iim.ncku.edu.tw/files/11-1407-20368.php?Lang=zh-tw)Paper published in 2007:[Efficiency decomposition in network data envelopment analysis: A relational model](https://www.sciencedirect.com/science/article/pii/S0377221707010077)_

## (I. Introduction

When common DEA measures efficiency, it generally treats the entire system as a whole and does not discuss the status of each internal process. However, it often ignores the efficiency between processes within the system, such as when building a system.[CRS Model](https://github.com/wurmen/DEA/blob/master/CRS_Model/CRS%20model.md)The example proposed is similar, and Professor Gao Qiang constructed a**Association network DEA model**(Relational network DEA model), using this model to explore the interrelationships between the various processes within the system, and simultaneously measure the system efficiency and the efficiency of each process, by introducing dummy processes (Dummy processes), the original network system is converted into a serial system And make each stage in the series a parallel structure to achieve the purpose of efficiency decomposition. Through efficiency decomposition, we can find out the processes that cause the system to run inefficiently for future improvements;**Therefore, in this article, we mainly use the examples in the paper and the mathematical model proposed to explain and use Python-Gurobi for modeling.**

## (2) Example description

#### ※Here we use the example proposed in Section 3 of the paper for explanation.

### § Sample system architecture

-   The figure below is a system formed by three processes. The system initially has two inputs and will eventually have three outputs. The input and output of each process within the system is as shown in the figure below:<br>

1.  The initial two inputs of the system will be divided into three parts for Process 1, Process 2 and Process 3 as their respective inputs.<br>
2.  The output of process 1 and process 2 will be divided into two parts, one part is the final system output, and the other part is used as part of the input of process 3

<div align=center>
<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/network%20system.PNG" width="550" height="350">
</div>
<br>

-   In order to achieve efficiency decomposition so that the efficiency of each process can be measured, this study uses**Join virtual process**To convert the above system into a system with two stages, each stage is a parallel structure, as shown in the following figure:<br>

※ Each symbol in the figure is explained in detail in the mathematical model below.

<div align=center>
<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/network%20system1.png" width="750" height="350">
</div>

##### ※Before the third section, this research has put forward two arguments (the inference process can be read in detail[original](https://www.sciencedirect.com/science/article/pii/S0377221707010077))

###### 1. In a system formed by processes in a series structure, the efficiency product of each process is equal to the overall efficiency value

###### 2. In a system formed by parallel-structured processes, the sum of the inefficiency slack of each process is equal to the inefficiency slack of the overall efficiency.

###### Therefore, in this system, the overall system efficiency value is the product of the efficiency of each stage in the series structure, that is, the product of the efficiency of stage 1 and stage 2, and the inefficiency of each stage is relaxed to the inefficiency of each process in the parallel structure The total relaxation, that is, the inefficient relaxation in stage 1 is the sum of process 1 and process 2, and the inefficient relaxation in stage 2 is equal to the inefficient relaxation in process 3.

<br>

### § Data on various output items and input items of decision-making units

-   There are five decision-making units to be compared. The output and input of their systems and each process are as shown in the following table:
    <div align=center>
    <img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/example-data.PNG" width="800" height="370">
    </div>

## (3) Mathematical model

The above system can form a mathematical model as shown below

### § Symbol Description

-   E<sub>k</sup></sub>: Efficiency value of decision-making unit k
-   n: Number of decision-making units (DMU) (n=5 in this example)<br>
-   ε: A very small positive value is called a non-Archimedean constant, usually set to 10<sup>-4</sup></sub>or 10<sup>-6</sup></sub>(The purpose is to prevent any input or output item from being ignored)

### § Parameter Description

-   X<sub>ij</sup></sub>: In the overall system of decision-making unit j (j=1,...,n), the initial i-th (i=1,...,m) input item (m=2 in this example)

-   X<sup>(t)</sup></sub><sub>ij</sup></sub>: The i-th input item of decision-making unit j (j=1,...,n) in process t (in this example t=1,2,3, i=1,2)

-   Y<sup>(O)</sup></sub><sub>1j</sup></sub>、Y<sup>(I)</sup></sub><sub>1j</sup></sub>: The output item of process 1 of decision-making unit j (j=1,...,n), Y<sup>(O)</sup></sub><sub>1j</sup></sub>is the final system output, Y<sup>(I)</sup></sub><sub>1j</sup></sub>Will become part of the input items in process 3

-   Y<sup>(O)</sup></sub><sub>Oh</sup></sub>、Y<sup>(I)</sup></sub><sub>Oh</sup></sub>: The output item of process 1 of decision-making unit j (j=1,...,n), Y<sup>(O)</sup></sub><sub>Oh</sup></sub>is the final system output, Y<sup>(I)</sup></sub><sub>Oh</sup></sub>Will become part of the input items in process 3

-   Y<sub>ij</sup></sub>: The total output of decision-making unit j (j=1,...,n) in process i

### § Decision variables

-   u<sub>r</sup></sub>: The weight of the r-th output item (r=1,2,3 in this example)
-   v<sub>i</sup></sub>: The weight of the i-th input item (i=1,2 in this example)

### § Goal and restriction

This mathematical model is the correlation network DEA model proposed by Professor Gao<br>

※This model is extended based on CRS Model (please refer to[original](https://www.sciencedirect.com/science/article/pii/S0377221707010077))

<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/model1.png" width="550" height="250">

### § Efficiency of each process

After solving the problem, the individual efficiency values ​​of each process can be calculated through the following mathematical formulas:

<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/model2.png" width="450" height="120">

### § Efficiency of each stage

After solving the problem, the following mathematical formulas can be used to calculate the efficiency value of each stage.

<img src="https://github.com/wurmen/DEA/blob/master/Network_DEA/pictures/model3.png" width="470" height="105">

## (3) Python-Gurobi

Here we explain how to use Python-Gurobi to construct an association network DEA model.

##### ※The complete program code can be clicked[here](https://github.com/wurmen/DEA/blob/master/Network_DEA/network_dea_code.py)

### Import gurobipy

```python
from gurobipy import*
```

### Add parameters

-   Calculate the efficiency of each decision-making unit through for loop

```python
DMU=['A', 'B','C','D','E']
E={}
val_p1,val_p2,val_p3,val_s1,val_s2={},{},{},{},{}
slack_p1,slack_p2,slack_p3={},{},{}
for k in DMU:

    I=2 # 兩項投入
    O=3 # 三項產出
```

-   Totx1 and Totx2 are the two initial input data of the overall system of each decision-making unit.

```python
    DMU,Totx1,Totx2=multidict({("A"):[11,14],("B"):[7,7],("C"):[11,14],("D"):[14,14],("E"):[14,15]})
```

-   Record the output and input data of each process, taking process 1 as an example:<br>proc1x1: records the first input data of process 1<br>proc1x2: records the second input data of process 1<br>proc1TotyO: Record the total output data of process 1 (proc1TotyO= proc1yO+Proc1yI)<br>proc1yO: records the data output by the final system in the total output of process 1<br>Proc1yI: Record the data of the total output of process 1 that will become the input items of process 3<br>

```python
    DMU,proc1x1,proc1x2,proc1TotyO,proc1yO,proc1yI=multidict({("A"):[3,5,4,2,2],("B"):[2,3,2,1,1],("C"):[3,4,2,1,1],("D"):[4,6,3,2,1],("E"):[5,6,4,3,1]})
    DMU,proc2x1,proc2x2,proc2TotyO,proc2yO,proc2yI=multidict({("A"):[4,3,3,2,1],("B"):[2,1,2,1,1],("C"):[5,3,2,1,1],("D"):[5,5,4,3,1],("E"):[5,4,4,2,2]})
    DMU,proc3x1,proc3x2,proc3TotyO=multidict({("A"):[4,6,1],("B"):[3,3,1],("C"):[3,7,2],("D"):[5,3,1],("E"):[4,5,3]})
```

### Model

```python
    m=Model("network_DEA")
```

### Add decision variables

-   Establish decision variable input and output weights v<sub>i</sup></sub>、 u<sub>r</sup></sub>

```python
    P1,P2,P3={},{},{}
    v,u={},{}
   
    for i in range(I):
        v[i]=m.addVar(vtype=GRB.CONTINUOUS,name="v_%d"%i)
    
    for r in range(O):
        u[r]=m.addVar(vtype=GRB.CONTINUOUS,name="u_%d"%i)
```

### Update

```python
    
    m.update()
```

### Add objective

```python
    m.setObjective(u[0]*proc1yO[k]+u[1]*proc2yO[k]+u[2]*proc3TotyO[k],GRB.MAXIMIZE)
```

### Add constraints

```python
    m.addConstr(v[0]*Totx1[k]+v[1]*Totx2[k]==1)
    for j in DMU:
        P1[j]=m.addConstr(u[0]*proc1TotyO[j]-(v[0]*proc1x1[j]+v[1]*proc1x2[j])<=0)
        P2[j]=m.addConstr(u[1]*proc2TotyO[j]-(v[0]*proc2x1[j]+v[1]*proc2x2[j])<=0)
        P3[j]=m.addConstr(u[2]*proc3TotyO[j]-(v[0]*proc3x1[j]+v[1]*proc3x2[j]+u[0]*proc1yI[j]+u[1]*proc2yI[j])<=0)
```

### Print result

```python
    m.optimize()
    E[k]="The efficiency of DMU %s:%4.4g"%(k,m.objVal) #取得決策單位的整體效率值
```

-   Get the solution v<sub>i</sup></sub>、 u<sub>r</sup></sub>value

```python
    u_sol = m.getAttr('x', u)
    v_sol = m.getAttr('x',v)
```

-   Calculate the efficiency value of each process

```python
    
    E1=u_sol[0]*proc1TotyO[k]/(v_sol[0]*proc1x1[k]+v_sol[1]*proc1x2[k]) 
    E2=u_sol[1]*proc2TotyO[k]/(v_sol[0]*proc2x1[k]+v_sol[1]*proc2x2[k])
    E3=u_sol[2]*proc3TotyO[k]/(v_sol[0]*proc3x1[k]+v_sol[1]*proc3x2[k]+u_sol[0]*proc1yI[k]+u_sol[1]*proc2yI[k])
```

-   Calculate the efficiency value of each stage

```python
    
    stage1=(u_sol[0]*proc1TotyO[k]+u_sol[1]*proc2TotyO[k]+v_sol[0]*proc3x1[k]+v_sol[1]*proc3x2[k])/(v_sol[0]*Totx1[k]+v_sol[1]*Totx2[k])
    stage2=(u_sol[0]*proc1yO[k]+u_sol[1]*proc2yO[k]+u_sol[2]*proc3TotyO[k])/(u_sol[0]*proc1TotyO[k]+u_sol[1]*proc2TotyO[k]+v_sol[0]*proc3x1[k]+v_sol[1]*proc3x2[k])
```

-   Record the efficiency values ​​of each process and stage of each decision-making unit

```python
    val_p1[k]='The efficiency of process 1 of DMU %s:%4.4g'%(k,E1)
    val_p2[k]='The efficiency of process 2 of DMU %s:%4.4g'%(k,E2)
    val_p3[k]='The efficiency of process 3 of DMU %s:%4.4g'%(k,E3)
    val_s1[k]='The efficiency of stage 1 of DMU %s:%4.4g'%(k,stage1)
    val_s2[k]='The efficiency of stage 2 of DMU %s:%4.4g'%(k,stage2)
```

-   Use the slack parameter in gurobi to obtain the inefficiency value of each process

```python

    process1_slack=m.getAttr('slack',P1)
    slack_p1[k]='The inefficiency of process 1 of DMU %s:%4.4g'%(k,process1_slack[k])
    process2_slack=m.getAttr('slack',P2)
    slack_p2[k]='The inefficiency of process 2 of DMU %s:%4.4g'%(k,process2_slack[k])
    process3_slack=m.getAttr('slack',P3)
    slack_p3[k]='The inefficiency of process 3 of DMU %s:%4.4g'%(k,process3_slack[k])
```

-   Show results

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

**Finally, you can get the result as shown below**<br>

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
