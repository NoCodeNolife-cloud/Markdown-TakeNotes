[toc]

# 向量



## ADT接口

![image-20210711142209164](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711142209164.png)

## Vector模板类

![image-20210711142248652](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711142248652.png)

![image-20210711142304166](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711142304166.png)

## 构造与析构

向量中秩为r的元素,对应于内部数组中的$\_elem[r]$,其物理地址为$\_elem+r$

### 默认构造方法

其中默认的构造方法是,首先根据创建者指是的初始容量,向系统申请空间,以创建内部私有数组$\_elem[]$;若容量未明确指定,则使用默认值$DEFAULT\_CAPACITY$,接下来,鉴于初生的向量尚不包含任何元素,故将指示规模的变量$\_size$初始化为$0$

整个过程顺序进行,没有任何迭代,故若忽略用于分配数组空间的时间,共需常数时间

### 基于复制的构造方法

![image-20210711143256891](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711143256891.png)

![image-20210711165051324](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711165051324.png)

#### 析构方法

与所有对象一样,不再需要的向量,应借助析构函数(destructor)及时清理(cleanup),以释放其占用的系统资源.与构造函数不同,同一对象只能有一个析构函数,不得重载.向量对象的析构过程,$\sim Vector()$:只需释放用于存放元素的内部数组$elem[]$,将其占用的空间交还操作系统.$\_capacity$和$\_size$之类的内部变量无需做任何处理,它们将作为向量对象自身的一部分被系统回收,此后既无需也无法被引用.若不计系统用于空间回收的时间,整个析构过程只需0(1)时间.同样地,向量中的元素可能不是程序语言直接支持的基本类型,在向量析构之前应该提前释放对应的空间

出于简化的考虑,这里约定并遵照"谁申请谁释放"的原则.究竟应释放掉向量各元素所指的对象,还是需要保留这些对象以便通过其它指针继续引用它们,应由上层调用者负责确定

## 动态空间管理

### 静态空间管理

内部数组所占物理空间的容量,若在向量的生命期内不允许调整,则称作==静态空间管理策略==.很遗憾,该策略的空间效率难以保证.一方面,既然容量固定,总有可能在此后的某一时刻,无法加入更多的新元素-即导致所谓的上溢(overflow) 

注意,造成此类溢出的原因,并非系统不能提供更多的空间.另一方面反过来,即便愿意为降低这种风险而预留出部分空间,也很难在程序执行之前,明确界定一个合理的预留量

向量实际规模与其内部数组容量的比值(即$\frac{\_size}{\_capacity}$) ,亦称作==装填因子==(load factor) ,它是衡量空间利用率的重要指标

### 可扩充向量

经过一段时间的生长,每当身体无法继续为其外壳所容纳,蝉就会蜕去外壳,同时换上一身更大的外壳.扩充向量(extendable vector)的原理,与之相仿.若内部数组仍有空余,则操作可照常执行.每经一次插入(删除) ,可用空间都会减少(增加)一个单元.一旦可用空间耗尽(图(b)) ,就动态地扩大内部数组的容量

![image-20210711192052153](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711192052153.png)

### 扩容

![image-20210711192534293](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711192534293.png)

实际上,在调用insert()接口插入新元素之前,都要先调用该算法,检查内部数组的可用容量.一旦当前数据区已满($\_size ==\_capacity$) ,则将原数组替换为一个更大的数组

新数组的地址由操作系统分配,与原数据区没有直接的关系.这种情况下,若直接引用数组,往往会导致共同指向原数组的其它指针失效,成为野指针(wild pointer) ;而经封装为向量之后,即可继续准确地引用各元素,从而有效地避免野指针的风险

### 分摊分析

#### 时间代价

与常规数组实现相比,可扩充向量更加灵活:只要系统尚有可用空间,其规模将不再受限于初始容量.不过,这并非没有代价—每次扩容,元素的搬迁都需要花费额外的时间.准确地,每一次由n到2n的扩容,都需要花费$\sigma(2n) =\sigma(n)$时间—这也是最坏情况下,单次插入操作所需的时间.表面看来,这一扩容策略似乎效率很低,但这不过是一种错觉.请注意,按照此处的约定,每花费$\sigma(n)$时间实施一次扩容,数组的容量都会加倍.这就意味着,至少要再经过n次插入操作,才会因为可能溢出而再次扩容.也就是说,随着向量规模的不断扩大,在执行插入操作之前需要进行扩容的概率,也将迅速降低.故就某种平均意义而言,用于扩容的时间成本不至很高

#### 分摊复杂度

这里,不妨考查对可扩充向量的足够多次连续操作,并将其间所消耗的时间,分摊至所有的操作.如此分摊平均至单次操作的时间成本,称作==分摊运行时间(amortized running time)==.请注意,这一指标与==平均运行时间(average running time)==有着本质的区别.后者是按照某种假定的概率分布,对各种情况下所需执行时间的加权平均,故亦称作期望运行时间(expected running time) .而前者则要求,参与分摊的操作必须构成和来自一个真实可行的操作序列,而且该序列还必须足够地长.相对而言,分摊复杂度可以针对计算成本和效率,做出更为客观而准确的估计

#### 其它扩容策略

以上分析确凿地说明,基于加倍策略的动态扩充数组不仅可行,而且就分摊复杂度而言效率也足以令人满意.当然,并非任何扩容策略都能保证如此高的效率.比如,早期可扩充向量多采用另一策略:一旦有必要,则追加固定数目的单元.实际上,无论采用的固定常数多大,在最坏情况下,此类数组单次操作的分摊时间复杂度都将高达$\Omega(n)$

### 缩容

导致低效率的另一情况是,向量的实际规模可能远远小于内部数组的容量.比如在连续的一系列操作过程中,若删除操作远多于插入操作,则装填因子极有可能远远小于100%,甚至非常接近于0.当装填因子低于某一阈值时,我们称数组发生了下溢(underflow) .尽管下溢不属于必须解决的问题,但在格外关注空间利用率的场合,发生下溢时也有必要适当缩减内部数组容量

![image-20210711201444098](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711201444098.png)

可见,每次删除操作之后,一旦空间利用率已降至某一阈值以下,该算法随即申请一个容量减半的新数组,将原数组中的元素逐一搬迁至其中,最后将原数组所占空间交还操作系统.这里以25%作为装填因子的下限,但在实际应用中,为避免出现频繁交替扩容和缩容的情况,可以选用更低的阈值,甚至取作0(相当于禁止缩容)

与expand()操作类似,尽管单次shrink()操作需要线性量级的时间,但其分摊复杂度亦为$\sigma(1)$.实际上shrink()过程等效于expand()的逆过程,这两个算法相互配合,在不致实质地增加接口操作复杂度的前提下,保证了向量内部空间的高效利用.当然,就单次扩容或缩容操作而言,所需时间的确会高达$\Omega(n)$,因此在对单次操作的执行速度极其敏感的应用场合以上策略并不适用,其中缩容操作甚至可以完全不予考虑

## 常规向量

### 直接引用元素

与数组直接通过下标访问元素的方式(形如"A[i]" )相比,向量ADT所设置的get()和put()接口都显得不甚自然.毕竟,前一访问方式不仅更为我们所熟悉,同时也更加直观和便捷.那么,在经过封装之后,对向量元素的访问可否沿用数组的方式呢?答案是肯定的

![image-20210711203326264](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711203326264.png)

### 置乱器

#### 置乱算法

可见,经重载后操作符"[]"返回的是对数组元素的引用,这就意味着它既可以取代get()操作(通常作为赋值表达式的右值),也可以取代set()操作(通常作为左值)

![image-20210711204411492](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711204411492.png)

该算法从待置乱区间的末元素开始,逆序地向前逐一处理各元素.对每一个当前元素V[i-1],先通过调用rand()函数在[0, i)之间等概率地随机选取一个元素,再令二者互换位置.注意,这里的交换操作swap(),隐含了三次基于重载操作符"[]"的赋值

![image-20210711204725680](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711204725680.png)

在软件测试、仿真模拟等应用中,随机向量的生成都是一项至关重要的基本操作,直接影响到测试的覆盖面或仿真的真实性.从理论上说,使用这里的算法permute(),不仅可以枚举出同一向量所有可能的排列,而且能够保证生成各种排列的概率均等

#### 区间置乱接口

![image-20210711205611431](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711205611431.png)

通过该接口,可以均匀地置乱任一向量区间[lo, hi)内的元素,故通用性有所提高.可见只要将该区间等效地视作另一向量V,即可从形式上完整地套用以上permute()算法的流程

### 判等器与比较器

从算法的角度来看, "判断两个对象是否相等"与"判断两个对象的相对大小"都是至关重要的操作,它们直接控制着算法执行的分支方向,因此也是算法的"灵魂"所在.当然,这两种操作之间既有联系也有区别,不能相互替代.比如,有些对象只能比对但不能比较;反之,支持比较的对象未必支持比对.

算法实现的简洁性与通用性,在很大程度上体现于:针对整数等特定数据类型的某种实现,可否推广至可比较或可比对的任何数据类型,而不必关心如何定义以及判定其大小或相等关系.若能如此,我们就可以将比对和比较操作的具体实现剥离出来,直接讨论算法流程本身

为此,通常可以采用两种方法.其一,将比对操作和比较操作分别封装成通用的判等器和比较器.其二,在定义对应的数据类型时,通过重载"<"和"=="之类的操作符,给出大小和相等关系的具体定义及其判别方法

![image-20210711210245435](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711210245435.png)

### 无序查找

#### 判等器

Vector: : find(e)接口,功能语义为"查找与数据对象e相等的元素".这同时也暗示着,向量元素可通过相互比对判等—比如,元素类型T或为基本类型,或已重载操作符"=="或"!=".这类仅支持比对,但未必支持比较的向量,称作无序向量(unsorted vector)

#### 顺序查找

![image-20210711211311938](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711211311938.png)

在无序向量中查找任意指定元素e时,因为没有更多的信息可以借助,故在最坏情况下比如向量中并不包含e时—只有在访遍所有元素之后,才能得出查找结论

#### 实现

针对向量的整体或区间,分别定义了一个顺序查找操作的入口,其中前者作为特例,可直接通过调用后者而实现

![image-20210711211546974](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711211546974.png)

#### 复杂度

最坏情况下,查找终止于首元素$\_elem[10]$,运行时间为$\sigma(hi-lo)=\sigma(n)$.最好情况下,查找命中于末元素$\_elem[hi-1]$,仅需$\sigma(1)$时间.对于规模相同、内部组成不同的输入,渐进运行时间却有本质区别,故此类算法也称作==输入敏感的(input sensitive)算法==

### 插入

![image-20210711225551165](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711225551165.png)

插入之前必须首先调用expand()算法,核对是否即将溢出;若有必要,则加倍扩容

![image-20210711225615926](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711225615926.png)

为保证数组元素物理地址连续的特性,随后需要将后缀$\_elem[r, _size)$ (如果非空)整体后移一个单元.这些后继元素自后向前的搬迁次序不能颠倒,否则会因元素被覆盖而造成数据丢失

在单元_elem[r]腾出之后,方可将待插入对象e置入其中

#### 复杂度

时间主要消耗于后继元素的后移,线性正比于后缀的长度,故总体为$\sigma(\_size-r+ 1)$

可见,新插入元素越靠后(前)所需时间越短(长) .特别地, r取最大值_size时为最好情况,只需$\sigma(1)$时间;r取最小值0时为最坏情况,需要$\sigma(\_size)$时间.一般地,若插入位置等概率分布,则平均运行时间为$\sigma(\_size)=\sigma(n)$,线性正比于向量的实际规模

### 删除

删除操作重载有两个接口, remove(lo, hi)用以删除区间[lo, hi)内的元素,而remove(r)用以删除秩为r的单个元素

应将单元素删除视作区间删除的特例,并基于后者来实现前者

#### 区间删除

![image-20210711231801673](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210711231801673.png)

![image-20210712091528459](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712091528459.png)

#### 单元素删除remove(r)

![image-20210712091626127](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712091626127.png)

##### 复杂度

remove(lo, hi)的计算成本,主要消耗于后续元素的前移,线性正比于后缀的长度,总体不过$\sigma(m+1) =\sigma(_size-hi+1)$

这与此前的预期完全吻合:区间删除操作所需的时间,应该仅取决于后继元素的数目,而与被删除区间本身的宽度无关

### 唯一化

很多应用中,在进一步处理之前都要求数据元素互异.以网络搜索引擎为例,多个计算节点各自获得的局部搜索结果,需首先剔除其中重复的项目,方可合并为一份完整的报告.类似地,所谓向量的唯一化处理,就是剔除其中的重复元素

![image-20210712094446572](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712094446572.png)

#### 正确性

算法的正确性由以下不变性保证

<center>在while循环中,在当前元素的前缀_elem[0, i)内,所有元素彼此互异</center>

![image-20210712094557593](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712094557593.png)

#### 复杂度

该算法过程所具有的单调性

<center>随着循环的不断进行,当前元素的后继持续地严格减少</center>

### 遍历

#### 功能

在很多算法中,往往需要将向量作为一个整体,对其中所有元素实施某种统一的操作,比如,输出向量中的所有元素,或者按照某种运算流程统一修改所有元素的数值.针对此类操作,可为向量专门设置一个遍历接口traverse()

![image-20210712095351872](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712095351872.png)

可见, traverse ()遍历的过程,实质上就是自前向后地逐一对各元素实施同一基本操作.而具体采用何种操作,可通过两种方式指定.前一种方式借助函数指针*visit()指定某一函数,该函数只有一个参数,其类型为对向量元素的引用,故通过该函数即可直接访问或修改向量元素另外,也可以函数对象的形式,指定具体的遍历操作.这类对象的操作符"()"经重载之后,在形式上等效于一个函数接口,故此得名

## 有序向量

若向量S[0, n)中的所有元素不仅按线性次序存放,而且其数值大小也按此次序单调分布,则称作有序向量(sorted vector)

与通常的向量一样,有序向量依然不要求元素互异,故通常约定其中的元素自前(左)向后(右)构成一个非降序列,即对任意$0\leq si < j<n$都有$S[i] \leq S[j]$

### 有序性甄别

作为无序向量的特例,有序向量自然可以沿用无序向量的查找算法.然而,得益于元素之间的有序性,有序向量的查找、唯一化等操作都可更快地完成.因此在实施此类操作之前,都有必要先判断当前向量是否已经有序,以便确定是否可采用更为高效的接口

![image-20210712100443592](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712100443592.png)

### 唯一化

#### 低效版

![image-20210712102512361](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712102512361.png)

其正确性基于如下事实:

<center>有序向量中的重复元素必然前后紧邻</center>

于是,可以自前向后地逐一检查各对相邻元素:若二者雷同则调用remove( )接口删除靠后者,否则转向下一对相邻元素.如此,扫描结束后向量中将不再含有重复元素

#### 高效版

![image-20210712102816671](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712102816671.png)

### 查找

有序向量S中的元素不再随机分布,秩r是S[r]在S中按大小的相对位次,位于S[r]前(后)方的元素均不致于更大(小).当所有元素互异时, r即是S中小于S[r]的元素数目.一般地,若小于、等于S[r]的元素各有i、k个,则该元素及其雷同元素应集中分布于$S[i, i + k)$利用上述性质,有序向量的查找操作可以更加高效地完成

尽管在最坏情况下,无序向量的查找操作需要线性时间,但我们很快就会看到,有序向量的这一效率可以提升至$\sigma(\log n)$.为区别于无序向量的查找接口find(),有序向量的查找接口将统一命名为search()

![image-20210712132017879](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712132017879.png)

### 二分查找(版本A)

![image-20210712132049762](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712132049762.png)

![image-20210712132101550](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712132101550.png)

#### 复杂度

以上算法采取的策略可概括为,以"当前区间内居中的元素"作为目标元素的试探对象.从应对最坏情况的保守角度来看,这一策略是最优的.每一步迭代之后无论沿着哪个方向深入,新问题的规模都将缩小一半.因此,这一策略亦称作==二分查找==(binary search)也就是说,随着迭代的不断深入,有效的查找区间宽度将按1/2的比例以几何级数的速度递减.于是,经过至多1og2 (hi- 1o)步迭代后,算法必然终止.鉴于每步迭代仅需常数时间,故总体时间复杂度不超过:
$$
\sigma(\log_2(hi-l))=\sigma(\log n)
$$

#### 查找长度

以上迭代过程所涉及的计算,主要分为两类:元素的大小比较、秩的算术运算及其赋值.虽然二者均属于$\sigma(1)$复杂度的基本操作,但元素的秩无非是(无符号)整数,而向量元素的类型则通常更为复杂,甚至复杂到未必能够保证在常数时间内完成.因此就时间复杂度的常系数而言,前一类计算的权重远远高于后者,而查找算法的整体效率也更主要地取决于其中所执行的元素大小比较操作的次数,即所谓查找长度(search length) .通常,可针对查找成功或失败等情况,从最好、最坏和平均情况等角度,分别测算查找长度,并凭此对查找算法的总体性能做一评估

#### 成功查找长度

![image-20210712132828337](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712132828337.png)
$$
\sigma(1.5k)=\sigma(1.5\cdot\log_2n)
$$

#### 失败查找长度

仿照以上对平均成功查找长度的递推分析方法,不难证明,一般情况下的平均失败查找长度亦为$\sigma(1.5\cdot\log_2n)$

### Fibonacci查找

#### 递推方程

递推方程法既是复杂度分析的重要方法,也是我们优化算法时确定突破口的有力武器

实际上,最终求解所得到的平均复杂度,在很大程度上取决于这一等式.更准确地讲,主要取决于$(2^{k-1}-1)$和$2 \times (2^{k-1}-1)$两项,其中的$(2^{k-1}-1)$为子向量的宽度,而系数1和2则是算法为深入前、后子向量,所需做的比较操作次数.以此前的二分查找算法版本A为例,之所以存在均衡性方面的缺陷,根源正在于这两项的大小不相匹配

基于这一理解,不难找到解决问题的思路,具体地不外乎两种

* 其一,调整前、后区域的宽度,适当地加长(缩短)前(后)子向量其二
* 统一沿两个方向深入所需要执行的比较次数,比如都统一为一次

#### 黄金分割

实际上,减治策略本身并不要求子向量切分点mi必须居中,故按上述改进思路,不妨按黄金分割比来确定mi.为简化起见,不妨设向量长度$n=fib(k) -1$

![image-20210712135622570](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712135622570.png)

#### 实现

![image-20210712135753368](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712135753368.png)

![image-20210712135801159](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712135801159.png)

### 二分查找(版本B)

#### 从三分支到两分支

二分查找算法版本A的不均衡性体现为复杂度递推式中$(2^{k-1}-1)$和$2\times(2^{k-1}-1)$两项的不均衡.为此, Fibonacci查找算法已通过采用黄金分割点,在一定程度上"降低了时间复杂度的常系数.实际上还有另一更为直接的方法,即令以上两项的常系数同时等于1,也就是说,无论朝哪个方向深入,都只需做1次元素的大小比较.相应地,算法在每步迭代中(或递归层次上)都只有两个分支方向,而不再是三个

![image-20210712140011312](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712140011312.png)

#### 实现

![image-20210712140040890](%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712140040890.png)

#### 性能

尽管版本B中的后端子向量需要加入A[mi],但得益于mi总是位于中央位置,整个算法$\sigma(\log n)$的渐进复杂度不受任何影响

在这一版本中,只有在向量有效区间宽度缩短至1个单元时算法才会终止,而不能如版本A那样,一旦命中就能及时返回.因此,最好情况下的效率有所倒退.当然,作为补偿,最坏情况下的效率相应地有所提高.实际上无论是成功查找或失败查找,版本B各分支的查找长度更加接近,故整体性能更趋稳定

### 二分查找(版本C)

#### 实现

![image-20210712155110992](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712155110992.png)

#### 正确性

版本C与版本B的差异,主要有三点.首先,只有当有效区间的宽度缩短至0(而不是1)时,查找方告终止.另外,在每次转入后端分支时,子向量的左边界取作mi +1而不是mi

表面上看,后一调整存在风险—此时只能确定切分点$A[mi] \leq e$"贸然"地将A[mi]排除在进一步的查找范围之外,似乎可能因遗漏这些元素,而导致本应成功的查找以失败告终

然而这种担心大可不必.通过数学归纳可以证明,版本C中的循环体,具有如下不变性:

<center>A[0, lo)中的元素皆不大于e;A[hi, n)中的元素皆大于e</center>

首次迭代时, lo=0且hi=n, A[0,lo)和A[hi, n)均空,不变性自然成立

![image-20210712155723419](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712155723419.png)

## 排序与下界

### 有序性

从数据处理的角度看,有序性在很多场合都能够极大地提高计算的效率

### 排序及其分类

有序向量的诸如查找等操作,效率远高于一般向量.因此在解决许多应用问题时我们普遍采用的一种策略就是,首先将向量转换为有序向量,再调用有序向量支持的各种高效算法.这一过程的本质就是向量的排序

排序算法是个庞大的家族,可从多个角度对其中的成员进行分类.比如,根据其处理数据的规模与存储的特点不同,可分为内部排序算法和外部排序算法:前者处理的数据规模相对不大,内存足以容纳;后者处理的数据规模很大,必须将借助外部甚至分布式存储器,在排序计算过程的任一时刻,内存中只能容纳其中一小部分数据.又如,根据输入形式的不同,排序算法也可分为离线算法(offline algorithm)和在线算法(online algorithm) .前一情况下,待排序的数据以批处理的形式整体给出;而在网络计算之类的环境中,待排序的数据通常需要实时生成,在排序算法启动后数据才陆续到达.再如,针对所依赖的体系结构不同,又可分为串行和并行两大类排序算法.另外,根据排序算法是否采用随机策略,还有确定式和随机式之分

### 复杂度下界

尽管很多算法都可以优化,但有一个简单的事实却往往为人所忽略:=对任一特定的应用问题,随着算法的不断改进,其效率的提高必然存在某一极限.毕竟,我们不能奢望不劳而获.这一极限不仅必然存在,而且其具体的数值,应取决于应用问题本身以及所采用的计算模型.一般地,任一问题在最坏情况下的最低计算成本,即为该问题的复杂度下界(lower bound).一旦某一算法的性能达到这一下界,即意味着它已是最坏情况下最优的(worst-case optimal)可见,尽早确定一个问题的复杂度下界,对相关算法的优化无疑会有巨大的裨益.比如上例所提出的问题,就是从最坏情况的角度,质疑"2次比对操作"是否为解决这一问题的最低复杂度.以下结合比较树模型,介绍界定问题复杂度下界的一种重要方法

### 比较树

#### 基于比较的分支

![image-20210712163749752](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712163749752.png)

这一转化方法也可以推广并应用于其它算法.一般地,树根节点对应于算法入口处的起始状态(如此处三个苹果已做好标记) ;内部节点(即非末端节点,图中以白色大圈示意)对应于过程中的某步计算,通常属于基本操作;叶节点(即末端节点,图中以黑色小圈示意)则对应于经一系列计算后某次运行的终止状态.如此借助这一树形结构,可以涵盖对应算法所有可能的执行流程

#### 比较树

算法所有可能的执行过程,都可涵盖于这一树形结构中.具体地,该树具有以下性质:

* 每一内部节点各对应于一次比对(称量)操作
* 内部节点的左、右分支,分别对应于在两种比对结果(是否等重)下的执行方向
* 叶节点(或等效地,根到叶节点的路径)对应于算法某次执行的完整过程及输出
* 反过来,算法的每一运行过程都对应于从根到某一叶节点的路径.

按上述规则与算法相对应的树,称作==比较树==(comparison tree)

### 估计下界

#### 最小树高

考查任一CBA式算法A,设CT(A)为与之对应的一棵比较树

==根据比较树的性质,算法A每一次运行所需的时间,将取决于其对应叶节点到根节点的距离(称作叶节点的深度);而算法A在最坏情况下的运行时间,将取决于比较树中所有叶节点的最大深度(称作该树的高度,记作h(CT(A)))==.因此就渐进的意义而言,算法A的时间复杂度应不低于$\Omega(h(CT(A)))$

对于存在CBA式算法的计算问题,既然其任一CBA式算法均对应于某棵比较树,该问题的复杂度下界就应等于这些比较树的最小高度.

估计这些比较树的最小高度,只需考查树中所含叶节点(可能的输出结果)的数目.具体地,在一棵高度为h的二叉树中,叶节点的数目不可能多于$2^h$.因此反过来,若某一问题的输出结果不少于$N$种,则比较树中叶节点也不可能少于N个,树高h不可能低于$\log_2N$

#### 苹果签别

就该问题而言,可能的输出结果共计N =3种(不同的苹果分别为A, B或C) ,故解决该问题的任一CBA式算法所对应比较树的高度为
$$
h \geq \lceil \log_23\rceil=2
$$
因此,只要是采用CBA式算法来求解该问题,则无论如何优化,在最坏情况下都至少需要2次称量—尽管最好情况下的确仍可能仅需1次.这也意味着,算法虽平淡无奇,却已是解决苹果鉴别问题的最佳CBA式算法

## 排序器

### 统一入口

![image-20210712170451894](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712170451894.png)

### 起泡排序

依次比较各对相邻元素,每当发现逆序即令二者彼此交换;一旦经过某趟扫描之后未发现任何逆序的相邻元素,即意味着排序任务已经完成,则通过返回标志"sorted" ,以便主算法及时终止

#### 起泡排序

![image-20210712173726561](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712173726561.png)

#### 扫描交换

![image-20210712173744151](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712173744151.png)

# 列表

## 从向量到列表

不同数据结构内部的存储与组织方式各异,其操作接口的使用方式及时空性能也不尽相同.在设计或选用数据结构时,应从实际应用的需求出发,先确定功能规范及性能指标

## 从静态到动态

数据结构支持的操作,通常无非静态和动态两类:前者仅从中获取信息,后者则会修改数据结构的局部甚至整体.基于数组实现的向量结构,其size()和get()等静态操作均可在常数时间内完成,而insert()和remove()等动态操作却都可能需要线性时间.究其原因,在于"各元素物理地址连续"的约定-此即所谓的"静态存储"策略.得益于这种策略,可在$\sigma(1)$时间内由秩确定向量元素的物理地址;但反过来,在添加(删除)元素之前(之后) ,又不得不移动$\sigma(n)$个后继元素.可见,尽管如此可使静态操作的效率达到极致,但就动态操作而言,局部的修改可能引起大范围甚至整个数据结构的调整

==列表(list)结构尽管也要求各元素在逻辑上具有线性次序,但对其物理地址却未作任何限制-此即所谓"动态存储"策略.==具体地,在其生命期内,此类数据结构将随着内部数据的需要,相应地分配或回收局部的数据空间.如此,元素之间的逻辑关系得以延续,却不必与其物理次序相关.作为补偿,此类结构将通过指针或引用等机制,来确定各元素的实际物理地址.例如,链表(linked list)就是一种典型的动态存储结构.其中的数据,分散为一系列称作节点(node)的单位,节点之间通过指针相互索引和访问.为了引入新节点或删除原有节点,只需在局部,调整少量相关节点之间的指针.这就意味着,采用动态存储策略,至少可以大大降低动态操作的成本

### 由秩到位置

改用以上动态存储策略之后,在提高动态操作效率的同时,却又不得不舍弃原静态存储策略中循秩访问的方式,从而造成静态操作性能的下降.以采用动态存储策略的线性结构(比如链表)为例.尽管按照逻辑次序,每个数据元素依然具有秩这一指标,但为了访问秩为r的元素,我们只能顺着相邻元素之间的指针,从某一端出发逐个扫描各元素,经过r步迭代后才能确定该元素的物理存储位置.这意味着,原先只需$\sigma(1)$时间的静态操作,此时的复杂度也将线性正比于被访问元素的秩,在最坏情况下等于元素总数n;即便在各元素被访问概率相等的情况下,平均而言也需要$\sigma(n)$时间

对数据结构的访问方式,应与其存储策略相一致.此时,既然继续延用循秩访问的方式已非上策,就应更多地习惯于通过位置,来指代并访问动态存储结构中的数据元素.与向量中秩的地位与功能类似,列表中的位置也是指代各数据元素的一个标识性指标,借助它可以便捷地(比如在常数时间内)得到元素的物理存储地址.各元素的位置,通常可表示和实现为联接于元素之间的指针或引用.因此,基于此类结构设计算法时,应更多地借助逻辑上相邻元素之间的位置索引,以实现对目标元素的快速定位和访问,并进而提高算法的整体效率

### 列表

与向量一样,列表也是由具有线性逻辑次序的一组元素构成的集合:
$$
L = \{a_0, a_1,\dots, a_{n-1}\}
$$
列表是链表结构的一般化推广,其中的元素称作节点(node) ,分别由特定的位置或链接指代.与向量一样,在元素之间,也可定义前驱、直接前驱,以及后继、直接后继等关系;相对于任意元素,也有定义对应的前缀、后缀等子集

## 接口

### 列表节点

![image-20210713110203076](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210713110203076.png)

### ListNode模板类

![image-20210713110231881](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210713110231881.png)

### ADT按口

![image-20210713110258556](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210713110258556.png)

![image-20210713110307249](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210713110307249.png)

### List模板类

![image-20210713110747905](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210713110747905.png)

![image-20210713110835627](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210713110835627.png)

## 列表

### 头、尾节点

![image-20210713125337021](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210713125337021.png)

### 默认构造方法

![image-20210715123942546](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715123942546.png)

![image-20210715123955330](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715123955330.png)

### 由秩到位置的转换

![image-20210715124126005](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715124126005-1626324087523.png)

### 查找

![image-20210715124224653](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715124224653.png)

复杂度$\sigma(n)$

### 插入

#### 接口

![image-20210715124336632](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715124336632.png)

![image-20210715124345316](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715124345316.png)

#### 前插入

![image-20210715124450915](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715124450915.png)

![image-20210715124548377](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715124548377.png)

#### 后插入

![image-20210715124754613](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715124754613.png)

### 基于复制的构造

#### copyNodes()

![image-20210715151753335](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715151753335.png)

#### 基于复制的构造

![image-20210715152130266](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715152130266.png)

### 删除

![image-20210715152150551](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715152150551.png)

![image-20210715152400434](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715152400434.png)

### 析构

#### 释放资源及清除节点

![image-20210715152538711](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715152538711.png)

![image-20210715152547763](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715152547763.png)

### 唯一化

![image-20210715152747364](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715152747364.png)

### 遍历

![image-20210715152820520](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715152820520.png)

### 唯一化

![image-20210715153135769](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715153135769.png)

### 查找

![image-20210715153217138](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715153217138.png)

## 排序器

### 统一入口

![image-20210715153252238](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715153252238.png)

### 插入排序

<center>在任何时刻,相对于当前节点e = S[r],前缀S[0, r)总是业已有序</center>

![image-20210715153447815](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715153447815.png)

![image-20210715153536707](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715153536707.png)

### 选择排序

<center>在任何时刻,后缀S[r, n)已经有序,且不小于前缀S[0, r)</center>

![image-20210715153725283](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715153725283.png)

![image-20210715153806834](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715153806834.png)

![image-20210715153919501](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715153919501.png)

### 归并排序

![image-20210715153937567](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715153937567.png)

![image-20210715153947460](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210715153947460.png)

# 栈与队列

## 栈

### 入栈与出栈

![image-20210718181447224](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210718181447224.png)

特质：后进先出

### stack模板类

![image-20210718182800278](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210718182800278.png)

## 栈与递归

### 函数调用栈

![image-20210718182927317](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210718182927317.png)

在windows等大部分操作系统中,每个运行中的二进制程序都配有一个调用栈(call stack)或执行栈(execution stack) .借助调用栈可以跟踪属于同一程序的所有函数,记录它们之间的相互调用关系,并保证在每一调用实例执行完毕之后,可以准确地返回

### 函数调用

调用栈的基本单位是帧(frame).每次函数调用时,都会相应地创建一帧,记录该函数实例在二进制程序中的返回地址(return address) ,以及局部变量、传入参数等,并将该帧压入调用栈.若在该函数返回之前又发生新的调用,则同样地要将与新函数对应的一帧压入栈中,成为新的栈顶.函数一旦运行完毕,对应的帧随即弹出,运行控制权将被交还给该函数的上层调用函数,并按照该帧中记录的返回地址确定在二进制程序中继续执行的位置

在任一时刻,调用栈中的各帧,依次对应于那些尚未返回的调用实例,亦即当时的活跃函数实例(active function instance).特别地,位于栈底的那帧必然对应于入口主函数main(),若它从调用栈中弹出,则意味着整个程序的运行结束,此后控制权将交还给操作系统

仿照递归跟踪法,程序执行过程出现过的函数实例及其调用关系,也可构成一棵树,称作该程序的运行树.任一时刻的所有活跃函数实例,在调用栈中自底到顶,对应于运行树中从根节点到最新活跃函数实例的一条调用路径.此外,调用栈中各帧还需存放其它内容.比如,因各帧规模不一,它们还需记录前一帧的起始地址,以保证其出栈之后前一帧能正确地恢复

### 避免递归

包括C++在内的各种高级程序设计语言几乎都允许函数直接或间接地自我调用,通过递归来提高代码的简洁度和可读性.而Cobol和Fortran等早期的程序语言虽然一开始并未采用栈来实现过程调用,但在其最新的版本中也陆续引入了栈结构来支持过程调用.尽管如此,==系统在后台隐式地维护调用栈的过程中,难以区分哪些参数和变量是对计算过程有实质作用的,更无法以通用的方式对它们进行优化,因此不得不将描述调用现场的所有参数和变量悉数入栈==.再加上每一帧都必须保存的执行返回地址以及前一帧起始位置,往往导致程序的空间效率不高甚至极低;同时,隐式的入栈和出栈操作也会令实际的运行时间增加不少.==因此在追求更高效率的场合,应尽可能地避免递归,尤其是过度的递归.==实际上,我们此前已经介绍过相应的方法和技巧

既然递归本身就是操作系统隐式地维护一个调用栈而实现的,我们自然也可以通过显式地模拟调用栈的运转过程,实现等效的算法功能.采用这一方式,程序员可以精细地裁剪栈中各帧的内容,从而尽可能降低空间复杂度的常系数.尽管算法原递归版本的高度概括性和简洁性将大打折扣,但毕竟在空间效率方面可以获得足够的补偿

## 匹配括号算法

#### 递归实现

![image-20210718220547022](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210718220547022.png)

### 迭代实现

![image-20210718205039561](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210718205039561.png)

## 队列

### 概述

先进先出

由以上的约定和限制不难看出,与栈结构恰好相反,队列中各对象的操作次序遵循所谓先进先出(first-in-first-out, FIFO)的规律:更早(晚)出队的元素应为更早(晚)入队者,反之,更早(晚)入队者应更早(晚)出队

### ADT接口

![image-20210722180644092](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210722180644092.png)

### Queue模板类

![image-20210722180853655](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210722180853655.png)

#  二叉树

根据其实现方式,这些数据结构大致可以分为两种类型:==基于数组的实现与基于链表的实现==.正如我们已经看到的,就其效率而言,二者各有长短

具体来说,前一实现方式允许我们通过下标或秩,在常数的时间内找到目标对象;然而,一旦需要对这类结构进行修改,那么无论是插入还是删除,都需要耗费线性的时间.反过来,后一实现方式允许我们借助引用或位置对象,在常数的时间内插入或删除元素;但是为了找出居于特定次序的元素,我们却不得不花费线性的时间,对整个结构进行遍历查找

能否将这两类结构的优点结合起来,并回避其不足呢?本章所讨论的树结构,将正面回答这一问题.在此前介绍的这些结构中,元素之间都存在一个自然的线性次序,故它们都属于所谓的线性结构( linear structure) .树则不然,其中的元素之间并不存在天然的直接后继或直接前驱关系.不过,正如我们马上就要看到的,只要附加某种约束(比如遍历) ,也可以在树中的元素之间确定某种线性次序,因此==树属于半线性结构==(semi-linear structure)无论如何,随着从线性结构转入树结构,我们的思维方式也将有个飞跃;相应地,算法设计的策略与模式也会因此有所变化,许多基本的算法也将得以更加高效地实现

树是一种分层结构,而层次化这一特征几乎蕴含于所有事物及其联系当中,成为其本质属性之一.从文件系统、互联网域名系统和数据库系统,一直到地球生态系统乃至人类社会系统,层次化特征以及层次结构均无所不在.有趣的是,作为树的特例,二叉树实际上并不失其一般性

## 二叉树及其表示

### 有根树

==从图论的角度看,树等价于连通无环图==.因此与一般的图相同,树也由一组顶点(vertex)以及联接与其间的若干条边(edge)组成.在计算机科学中,往往还会在此基础上,再指定某一特定顶点,并称之为根(root) .在指定根节点之后,我们也称之为有根树(rooted tree) .此时,从程序实现的角度,我们也更多地将顶点称作节点(node)

### 深度与层次

由树的连通性,每一节点与根之间都有一条路径相联;而根据树的无环性,由根通往每个节点的路径必然唯一.沿每个节点v到根r的唯一通路所经过边的数目,称作v的深度(depth) ,记作$depth(v)$​.依据深度排序,可对所有节点做分层归类.特别地,约定根节点的深度depth(r) =0,故属于第0层

### 祖先、后代与子树

任一节点v在通往树根沿途所经过的每个节点都是其祖先(ancestor) , v是它们的后代(descendant) .特别地, ==v的祖先/后代包括其本身==,而v本身以外的祖先/后代称作真祖先(proper ancestor) /真后代(properdescendant)

节点v历代祖先的层次, 自下而上以1为单位逐层递减;在每一层次上, v的祖先至多一个.特别地,若节点u是v的祖先且恰好比v高出一层,则称u是v的父亲(parent),v是u的孩子(child)

v的孩子总数,称作其度数或度(degree) ,记作deg(v).无孩子的节点称作叶节点(leaf) ,包括根在内的其余节点皆为内部节点(internal node) 

v所有的后代及其之间的联边称作子树(subtree) ,记作subtree(v).在不致歧义时,我们往往不再严格区分节点(v)及以之为根的子树(subtree(v) )

### 高度

树T中所有节点深度的最大值称作该树的高度(height) ,记作height(T)不难理解,树的高度总是由其中某一叶节点的深度确定的.特别地,本书约定,仅含单个节点的树高度为0,空树高度为-1.推而广之,任一节点v所对应子树subtree (v)的高度,亦称作该节点的高度,记作height(v).特别地,全树的高度亦即其根节点r的高度, $height(T) = height(r)$

### 二叉树

![image-20210723183616856](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210723183616856.png)

因此在二叉树中,同一父节点的孩子都可以左、右相互区分—此时,亦称作有序二叉树(ordered binary tree) .本书所提到的二叉树,默认地都是有序的

### 多叉树

一般地,树中各节点的孩子数目并不确定.每个节点的孩子均不超过k个的有根树,称作k叉树(k-ary tree) 

#### 父节点

在多叉树中,根节点以外的任一节点有且仅有一个父节点

将各节点组织为向量或列表,其中每个元素除保存节点本身的信息(node)外,还需要保存父节点(parent)的秩或位置.可为树根指定一个虚构的父节点-1或NULL,以便统一判断

如此,所有向量或列表所占的空间总量为$\sigma (n)$​,线性正比于节点总数n.时间方面,仅需常数时间,即可确定任一节点的父节点;但反过来,孩子节点的查找却不得不花费$\sigma (n)$​时间访遍所有节点

#### 孩子节点

![image-20210723184918865](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210723184918865.png)

若注重孩子节点的快速定位,令各节点将其所有的孩子组织为一个向量或列表.如此,对于拥有r个孩子的节点,可在$\sigma(r + 1)$​时间内列举出其所有的孩子

#### 父节点+孩子节点

![image-20210723185139261](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210723185139261-16270375006321.png)

以上父节点表示法和孩子节点表示法各有所长,但也各有所短.为综合二者的优势,消除缺点,令各节点既记录父节点,同时也维护一个序列以保存所有孩子

尽管如此可以高效地兼顾对父节点和孩子的定位,但在节点插入与删除操作频繁的场合,为动态地维护和更新树的拓扑结构,不得不反复地遍历和调整一些节点所对应的孩子序列.然而,向量和列表等线性结构的此类操作都需耗费大量时间,势必影响到整体的效率

#### 有序多叉树=二叉树

解决上述难题的方法之一,就是采用支持高效动态调整的二叉树结构.为此,==必须首先建立起从多叉树到二叉树的某种转换关系,并使得在此转换的意义下,任一多叉树都等价于某棵二叉树==.当然,为了保证作为多叉树特例的二叉树有足够的能力表示任何一棵多叉树,我们只需给多叉树增加一项约束条件—同一节点的所有孩子之间必须具有某一线性次序

仿照有序二叉树的定义,凡符合这一条件的多叉树也称作==有序树==(ordered tree).幸运的是,这一附加条件在实际应用问题中往往自然满足.以互联网域名系统所对应的多叉树为例,其中同一域名下的分支通常即按照字典序排列

#### 长子 + 兄弟

![image-20210723185937873](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210723185937873.png)

有序多叉树中任一非叶节点都有唯一的"长子",而且从该"长子"出发,可按照预先约定或指定的次序遍历所有孩子节点.为每个节点设置两个指针,分别指向其"长子"和下一"兄弟"

尽管二叉树只是多叉树的一个子集,但其对应用问题的描述与刻画能力绝不低于后者.实际上以下我们还将进一步发现,即便是就计算效率而言,二叉树也并不逊色于一般意义上的树.反过来,得益于其定义的简洁性以及结构的规范性,二叉树所支撑的算法往往可以更好地得到描述,更加简捷地得到实现.二叉树的身影几乎出现在所有的应用领域当中,这也是一个重要的原因

## 编码树

通讯理论中的一个基本问题是,如何在尽可能低的成本下,以尽可能高的速度,尽可能忠实地实现信息在空间和时间上的复制与转移.在现代通讯技术中,无论采用电、磁、光或其它任何形式,在信道上传递的信息大多以二进制比特的形式表示和存在,而每一个具体的编码方案都对应于一棵二叉编码树

### 二进制编码

在加载到信道上之前,信息被转换为二进制形式的过程称作编码(encoding);反之,经信道抵达目标后再由二进制编码恢复原始信息的过程称作解码(decoding)

![image-20210723191551917](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210723191551917.png)

编码和解码的任务分别由发送方和接收方分别独立完成,故在开始通讯之前,双方应已经以某种形式,就编码规则达成过共同的约定或协议

### 生成编码表

原始信息的基本组成单位称作字符,它们都来自于某一特定的有限集合$\Sigma$​,也称作字符集 （alphabet）。而以二进制形式承载的信息,都可表示为来自编码表$Γ =\{0, 1\}$*的某一特定二进制串。从这个角度理解,每一编码表都是从字符集$\Sigma$​到编码表Γ的一个单射,编码就是对信息文本中各字符逐个实施这一映射的过程,而解码则是逆向映射的过程

编码表一旦制定,信息的发送方与接收方之间也就建立起了一个约定与默契,从而使得独立的编码与解码成为可能

# 冒泡算法	bubbleSort

```cpp
/// <summary>
/// sort vector from greater to less
/// </summary>
/// <typeparam name="T">typename</typeparam>
/// <param name="vec">vector parameter</param>
/// <returns>result vector</returns>
template<typename T>
vector<T>bubbleSort(vector<T>vec) {
	vector<T>res(vec);
	for (int i = 0; i < res.size(); i++) {
		for (int j = 0; j < res.size() - i - 1; j++) {
			if (res[j] < res[j + 1]) {
				swap(res[j], res[j + 1]);
			}
		}
	}
	return res;
}
```

### 提前冒泡算法

```cpp
void bubblesort1A(int A[], int n) {
    bool sorted = false;
    while (!sorted) {
        sorted = true;
        for (int i = 1; i < n; ++i) {
            if (A[i - 1] > A[i]) {
                swap(A[i - 1], A[i]);
                sorted = false;
            }
        }
        n--;
    }
}
```



## 选择排序	selectionSort

```cpp
/// <summary>
/// sort vector from greater to less
/// </summary>
/// <typeparam name="T">typename</typeparam>
/// <param name="vec">vector parameter</param>
/// <returns>result vector</returns>
template<typename T>
vector<T>selectionSort(vector<T>vec) {
	vector<T>res(vec);
	for (int i = 0; i < res.size(); i++) {
		size_t maxindex = i;
		for (int j = i + 1; j < res.size(); j++) {
			if (res[maxindex] < res[j]) {
				maxindex = j;
			}
		}
		swap(res[maxindex], res[i]);
	}
	return res;
}
```

## 插入排序	insertionSort

```cpp
/// <summary>
/// sort vector from greater to less
/// </summary>
/// <typeparam name="T">typename</typeparam>
/// <param name="vec">vector parameter</param>
/// <returns>result vector</returns>
template<typename T>
vector<T> insertionSort(vector<T> vec) {
	vector<T>res(vec);
	for (int i = 1; i < res.size(); i++) {
		T temp = res[i];
		int j;
		for (j = i - 1; j >= 0 and res[j] < temp; j--) {
			res[j + 1] = res[j];
		}
		res[j + 1] = temp;
	}
	return res;
}
```

## 快速排序	quickSort

```cpp
/// <summary>
/// sort vector from less to greater
/// </summary>
/// <typeparam name="T">typename</typeparam>
/// <param name="vec">vector parameter</param>
/// <returns>result vector</returns>
template<typename T>
vector<T>quickSort(vector<T> vec) {
	vector<T>res(vec);
	quickSort(res, 0, res.size() - 1);
	return res;
}
template<typename T>
void quickSort(vector<T>& vec, int left, int right) {
	int middle = vec[(left + right) / 2];
	int tleft = left, tright = right;
	while (tleft <= tright) {
		while (vec[tleft] < middle) {
			tleft++;
		}
		while (middle < vec[tright]) {
			tright--;
		}
		if (tleft <= tright) {
			swap(vec[tleft], vec[tright]);
			tleft++;
			tright--;
		}
	}
	if (tleft == tright) {
		tleft++;
	}
	if (left < tright) {
		quickSort(vec, left, tleft - 1);
	}
	if (tleft < right) {
		quickSort(vec, tright + 1, right);
	}
	return;
}
```

# 归并排序

## 有序向量的二路归并

与起泡排序通过反复调用单趟扫描交换类似,归并排序也可以理解为是通过反复调用所谓二路归并(2-way merge)算法而实现的.所谓二路归并,就是将两个有序序列合并成为一个有序序列.归并排序所需的时间,也主要决定于各趟二路归并所需时间的总和

二路归并属于迭代式算法.每步迭代中,只需比较两个待归并向量的首元素,将小者取出并追加到输出向量的末尾,该元素在原向量中的后继则成为新的首元素.如此往复,直到某一向量为空.最后,将另一非空的向量整体接至输出向量的末尾

![image-20210712194741462](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712194741462.png)

## 分治策略

![image-20210712195001135](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712195001135.png)

## 二路归并接口的实现

![image-20210712195418030](%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E8%AE%BE%E8%AE%A1C++.assets/image-20210712195418030.png)

# sort函数

```cpp
/// <summary>
/// greater to lower
/// </summary>
/// <typeparam name="T">typename</typeparam>
/// <param name="a"></param>
/// <param name="b"></param>
/// <returns>
/// true: don't swap
/// false: swap
/// </returns>
template<typename T>
bool cmp(T a, T b) {
	if (a > b) {
		return true;
	}
	else {
		return false;
	}
}
```

```cpp
/// <summary>
/// lower to greater
/// </summary>
/// <typeparam name="T">typename</typeparam>
/// <param name="a"></param>
/// <param name="b"></param>
/// <returns>
/// true: don't swap
/// false: swap
/// </returns>
template<typename T>
bool cmp(T a, T b) {
	if (a < b) {
		return true;
	}
	else {
		return false;
	}
}
```



# 查找

## 二分法

```cpp
/// <summary>
/// binary search
/// </summary>
/// <typeparam name="T">typename</typeparam>
/// <param name="vec">vector</param>
/// <param name="target">search value</param>
/// <returns>find or not</returns>
template<typename T>
bool binarySearch(vector<T>vec, int target) {
	int left = 0, right = vec.size() - 1;
	while (left <= right) {
		int middleindex = (left + right) / 2;
		T middleValue = vec[middleindex];
		if (middleValue < target) {
			left = middleindex + 1;
		}
		else if (middleValue > target) {
			right = middleindex - 1;
		}
		else {
			return true;
		}
	}
	return false;
}
```

## 查找是否有相同的值

```cpp
/// <summary>
/// find if vector has equal value item
/// </summary>
/// <typeparam name="T">typename</typeparam>
/// <param name="vec"></param>
/// <returns></returns>
bool findEqual(vector<T> vec) {
	map<T, bool>hash;
	for (int i = 0; i < vec.size(); i++) {
		if (hash.find(vec[i]) == hash.end()) {
			hash[vec[i]] = true;
		}
		else {
			return true;
		}
	}
	return false;
}

```

# 拆分字符串

## 生成单词

```cpp
/// <summary>
/// detached string
/// </summary>
/// <param name="str">object string</param>
/// <returns>vector of the string</returns>
vector<string> detachedString(string& str) {
	istringstream ss(str);
	vector<string>res;
	string temp;
	while (ss >> temp) {
		res.push_back(temp);
	}
	return res;
}
// another edition
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>

int main () {
	std::vector<std::string> coll;

	// read all words from the standard input
	std::copy ( std::istream_iterator<std::string> ( std::cin ) , std::istream_iterator<std::string> () , std::back_inserter ( coll ) );

	// sort elements
	sort ( coll.begin () , coll.end () );

	// print all elements without duplicates
	std::unique_copy ( coll.begin () , coll.end () , std::ostream_iterator<std::string> ( std::cout , "\n" ) );

	//exit
	std::exit ( EXIT_SUCCESS );
}
```

# 计数

## map

```cpp
/// <summary>
/// count for the value
/// </summary>
/// <typeparam name="T">typename</typeparam>
/// <param name="vec">vector</param>
/// <returns>return map</returns>
template<typename T>
map<T, int> count(vector<T>& vec) {
	map<T, int>res;
	for (int i = 0; i < vec.size(); i++) {
		if (res.find(vec[i]) == res.end()) {
			res[vec[i]] = 1;
		}
		else {
			res[vec[i]]++;
		}
	}
	return res;
}
```

## vector+pair

```cpp
/// <summary>
/// count number of the vector item value
/// </summary>
/// <typeparam name="T">typename</typeparam>
/// <param name="vec">vector</param>
/// <returns>return pair of the vector</returns>
template<typename T>
vector<pair<T, int>> count(vector<T>& vec) {
	vector<pair<T, int>>res;
	if (vec.size() == 0) {
		return res;
	}
	else {
		pair<T, int>temp;
		temp.first = vec[0];
		temp.second = 1;
		res.push_back(temp);
		for (int i = 1; i < vec.size(); i++) {
			bool find = false;
			for (int j = 0; j < res.size(); j++) {
				if (res[j].first == vec[i]) {
					res[j].second++;
					find = true;
					break;
				}
			}
			if (!find) {
				temp.first = vec[i];
				temp.second = 1;
				res.push_back(temp);
			}
		}
		return res;
	}
}
```

## vector(26,0)——只出现英文单词

```cpp
string str = "frtrhehgvaewhrqhfbvzvjkaheglaefsdarg";
vector<int>count(26, 0);
for (char x : str) {
	count[x - 'a']++;
}
for (int i = 0; i < count.size(); i++) {
	if (count[i] != 0) {
		cout << setw(4) << left << char(i + 'a') << count[i] << endl;
	}
}
```



# 质数

```cpp
/// <summary>
/// get primes
/// </summary>
/// <param name="n">range of the primes</param>
/// <returns>vector of the primes</returns>
vector<int> primes(int n) {
	vector<int>res;
	if (n <= 0) {
		return res;
	}
	bool* notPrime = new bool[n];
	for (int i = 0; i < n; i++) {
		notPrime[i] = false;
	}
	for (int i = 2; i < n; i++) {
		if (notPrime[i] == false) {
			res.push_back(i);
		}
		for (int j = 2; i * j < n; j++) {
			notPrime[i * j] = true;
		}
	}
	return res;
}
```

# 最小公约数

```cpp
//辗转相除法求最大公约数函数
int divisor(int a, int b) {
	int temp;

	//比较两个数的大小,值大的数为a,值小的数为b
	if (a < b) {
		temp = a;
		a = b;
		b = temp;
	}

	//求余
	while (b != 0) {
		temp = a % b;
		a = b;
		b = temp;
	}
	return a;
}

//求最小公倍数
int multiple(int a, int b) {
	int divisor(int a, int b);
	int temp;
	temp = divisor(a, b);
	return(a * b / temp);
}

//函数递归调用求最大公约数
int gcd(int a, int b) {
	if (a % b == 0) {
		return b;
	}
	else {
		return gcd(b, a % b);
	}
}

//穷举法求最大公约数
int divisor1(int a, int b) {
	int temp;
	temp = (a > b) ? b : a;   //求较小值
	while (temp > 0) {
		if (a % temp == 0 && b % temp == 0) {
			break;
		}
		else {
			temp--;
		}
	}
	return (temp);
}

//穷举法求最小公倍数
int multiple1(int a, int b) {
	int p, q, temp;
	p = (a > b) ? a : b;  //求两数中的最大值
	q = (a > b) ? b : a;  //求两数中的最小值
	temp = p;
	while (1) {
		if (p % q == 0) {
			break;
		}
		else {
			p += temp;
		}
	}
	return (p);
}

//更相减损法求最大公约数
int gcd1(int a, int b) {
	int i = 0, temp, x = 0;
	while (a % 2 == 0 && b % 2 == 0) {    //m,n有公约数2时
		a /= 2;
		b /= 2;
		i += 1;
	}
	//a,b的值互换
	if (a < b) {
		temp = a;
		a = b;
		b = temp;
	}
	while (x) {
		x = a - b;
		a = (b > x) ? b : x;   
		b = (b < x) ? b : x;
		if (b == (a - b)) {    //差和减数相等
			break;
		}
	}
	if (i == 0) {
		return b;
	}
	else {
		return (int)pow(2, i)*b;
	}
}
```

# 最大公倍数

```cpp
int lcm(int m, int n)
{
	int max;
	if (m < n)
	{
		max = n;
	}
	else
	{
		max = m;
	}
	
	while (true)
	{
		if (max % m == 0 && max % n == 0 )
		{
			return max;
		}
		
		max++;
	}
}
```

# 进制转换

## 十进制转二进制

```cpp
/// <summary>
/// get Binary
/// </summary>
/// <param name="x">Decimalism value</param>
/// <returns>vector of the Binary Code</returns>
vector<int> getBinary(int x){
    vector<int>res(32,0);
    if(x>=0){
        int i=0;
        while(x!=0){
            res[31-i]=x%2;
            x/=2;
            i++;
        }
    }
    else{
        x=abs(x);
        int i=0;
        while(x!=0){
            res[31-i]=x%2;
            x/=2;
            i++;
        }
        for(int i=0;i<32;i++){
            if(res[i]==0){
                res[i]=1;
            }
            else{
                res[i]=0;
            }
        }
        for(int i=31;i>=0;i--){
            if(res[i]==0){
                res[i]=1;
                break;
            }
            else{
                res[i]=0;
            }
        }
    }
    return res;
}
```

## 十进制转十六进制

```cpp
/// <summary>
/// get Hex
/// </summary>
/// <param name="x">Hex value</param>
/// <returns>vector of the Hex Code</returns>
string toHex(int num) {
    if(num==0){
        return "0";
    }
    int len=0;
    string ans="";
    while(num&&len<8){
        int bit=num&15;
        if(bit<10){
            ans=(char)('0'+bit)+ans;
        }
        else{
            ans=(char)('a'+bit-10)+ans;
        }
        num>>=4;
        len++;
    }
    return ans;
}
```

# 补数

```cpp
int findComplement(int num) {
    vector<int>res;
    while(num!=0){
        res.push_back(num%2);
        num/=2;
    }
    for(int &x:res){
        if(x==1){
            x=0;
        }
        else{
            x=1;
        }
    }
    int count=0;
    for(int i=0;i<res.size();i++){
        count+=pow(2,i)*res[i];
    }
    return count;
}
```

# 八皇后

![image-20210720181359786](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210720181359786.png)

![image-20210720181409874](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210720181409874.png)

![image-20210720181418302](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210720181418302.png)

## 实例

![image-20210720181438966](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210720181438966.png)

# 寻径

![image-20210720183144716](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210720183144716.png)

![image-20210720183210579](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210720183210579.png)

![image-20210720183228983](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210720183228983.png)

![image-20210720183238490](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210720183238490.png)

![image-20210720183311822](E:\programe\GitHub project warehouse manager\Markdown-TakeNotes\数据结构与算法设计C++.assets\image-20210720183311822.png)

# 判断是非为n的幂



```cpp
bool isPowerOfN(int num,int n) {
	if (num <= 0) {
		return false;
	}
	while (num != 0) {
		if (num % n != 0 and num != 1) {
			return false;
		}
		else {
			num /= n;
		}
	}
	return true;
}
```

# 获得不同的vector序列	unique

```cpp
/// <summary>
/// greater to lower
/// </summary>
/// <typeparam name="T">typename</typeparam>
/// <param name="a"></param>
/// <param name="b"></param>
/// <returns>
/// true: don't swap
/// false: swap
/// </returns>
template<typename T>
bool cmp(T a, T b) {
	if (a > b) {
		return true;
	}
	else {
		return false;
	}
}
/// <summary>
/// get difference vector
/// </summary>
/// <typeparam name="T">typename</typeparam>
/// <param name="vec">vector</param>
/// <returns>difference vector</returns>
template<typename T>
vector<T> getDifference(vector<T> vec) {
	vector<T>res = vec;
	sort(res.begin(), res.end(), cmp<T>);
	auto iter = unique(res.begin(), res.end());
	res.erase(iter, res.end());
	return res;
}
```

# DP动态规划

```cpp
int longestIncreasingSubsequence(vector<int>& nums) {
    if (nums.size() == 0) {
        return 0;
    }
    int res = 1;
    vector<int> LIS(nums.size(), 1);
    for (int i = 1; i < nums.size(); ++i) {
        for (int j = 0; j < i; ++j) {
            if (nums[i] > nums[j]) {
                LIS[i] = max(LIS[i], LIS[j] + 1);
            }
        }
        res = max(res, LIS[i]);
    }
    return res;
}
int jump(vector<int> &A) {
    int n=A.size();
    vector<int>dp(n);
    dp[0]=0;
    for(int i=1;i<n;i++){
        dp[i]=INT_MAX;
        for(int j=0;j<i;j++){
            if(A[j]+j>=i){
                dp[i]=min(dp[i],dp[j]+1);
            }
        }
    }
    return dp[n-1];
}
```

>    ### *重要三要素：*
>
>    ####      (1) 每个问题的阶段.
>
>    ####     (2) 每个阶段的状态.
>
>    ####     (3) 上一阶段状态转换到下一阶段状态之间的递推关系.
>
>    ####     递推关系必须是从次小的问题开始到较大的问题之间的转化, 从这个角度来说 , DP算法往往可以用递归程序来实现 ,  不过因为递推可以充分利用前面保存的子问题的解来减少重复计算 ,  所以对于大规模问题来说 ,  有递归不可比拟的优势 ,  这也是DP算法的核心之处.确定了动态规划的这三要素之后呢 ,  整个求解过程就可以用一个最优决策表来描述 ,  最优决策表是一个二维表 ,  其中行表示决策的阶段 ,  列表示问题状态,表格需要填写的数据一般对应此问题的在某个阶段某个状态下的最优值(如最短路径问题,  最长公共子序列问题 ,  最大价值问题等) ,  填表的过程就是根据递推关系 ,  从 1 行 1 列开始 ,  以行或者列优先的顺序 ,  依次填写表格,最后根据整个表格的数据通过简单的取舍或者运算求得问题的最优解：f(i, j) = max {f(i - 1, j), f(i - 1, j - dp[n]) + base(i, j)}.

---

# DFS

深度优先遍历图算法步骤：

1.   访问顶点v;
2.   依次从v的未被访问的邻接点出发,对图进行深度优先遍历;直至图中和v有路径相通的顶点都被访问;
3.   若此时图中尚有顶点未被访问,则从一个未被访问的顶点出发,重新进行深度优先遍历,直到图中所有顶点均被访问过为止.

# LeetCode

# 1. A + B 问题

给出两个整数 a*a* 和 b*b* , 求他们的和.

### 样例

**样例 1:**

```
输入:  a = 1, b = 2
输出: 3	
样例解释: 返回a+b的结果.
```

**样例 2:**

```
输入:  a = -1, b = 1
输出: 0	
样例解释: 返回a+b的结果.
```

### 挑战

显然你可以直接 return a + b,但是你是否可以挑战一下不这样做？(不使用++等算数运算符)

### 说明

a和b都是 `32位` 整数么？

-    是的

我可以使用位运算符么？

-    当然可以

### 注意事项

你不需要从输入流读入数据,只需要根据`aplusb`的两个参数a和b,计算他们的和并返回就行.

```cpp
class Solution {
public:
    /**
     * @param a: An integer
     * @param b: An integer
     * @return: The sum of a and b 
     */
    int aplusb(int a, int b) {
        return a+b;
    }
};
```

# 2. 尾部的零

设计一个算法,计算出n阶乘中尾部零的个数

### 样例

```
样例  1:
	输入: 11
	输出: 2
	
	样例解释: 
	11! = 39916800, 结尾的0有2个.

样例 2:
	输入:  5
	输出: 1
	
	样例解释: 
	5! = 120, 结尾的0有1个.
```

### 挑战

O(logN)的时间复杂度

```cpp
class Solution {
public:
    /*
     * @param n: A long integer
     * @return: An integer, denote the number of trailing zeros in n!
     */
    long long trailingZeros(long long n) {
        long long sum = 0;
		while (n != 0) {
			sum += n / 5;
			n /= 5;
		}
		return sum;
    }
};
```

# 3. 统计数字

计算数字 k 在 0 到 n 中的出现的次数,k 可能是 0~9 的一个值.

### 样例

**样例 1：**

```
输入：
k = 1, n = 1
输出：
1
解释：
在 [0, 1] 中,我们发现 1 出现了 1 次 (1).
```

**样例 2：**

```
输入：
k = 1, n = 12
输出：
5
解释：
在 [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12] 中,我们发现 1 出现了 5 次 (1, 10, 11, 12)(注意11中有两个1).
```

```cpp
class Solution {
public:
    /**
     * @param k: An integer
     * @param n: An integer
     * @return: An integer denote the count of digit k in 1..n
     */
    int digitCounts(int k, int n) {
        int count = 0;
		if (k == 0) {
			count = 1;
		}
		for (int i = 1; i <= n; i++) {
			int number = i;
			while (number > 0) {
				if (number % 10 == k) {
					count++;
				}
				number /= 10;
			}
		}
		return count;
    }
};
```

# 4. 丑数 II

设计一个算法,找出只含素因子`2`,`3`,`5` 的第 *n* 小的数.

符合条件的数如：`1, 2, 3, 4, 5, 6, 8, 9, 10, 12...`

### 样例

**样例 1：**

```
输入：9
输出：10
```

**样例 2：**

```
输入：1
输出：1
```

### 挑战

要求时间复杂度为 O(*n*log*n*) 或者 O(*n*).

### 注意事项

我们可以认为 `1` 也是一个丑数.

```cpp
class Solution {
public:
    /**
     * @param n: An integer
     * @return: return a  integer as description.
     */
    int nthUglyNumber(int n) {
		int* uglys = new int[n];
		uglys[0] = 1;
		int next = 1;
		int* p2 = uglys;
		int* p3 = uglys;
		int* p5 = uglys;
		while (next < n) {
			int m = min(min(*p2 * 2, *p3 * 3), *p5 * 5);
			uglys[next] = m;
			while (*p2 * 2 <= uglys[next]) {
				*p2++;
			}
			while (*p3 * 3 <= uglys[next]) {
				*p3++;
			}
			while (*p5 * 5 <= uglys[next]) {
				*p5++;
			}
			next++;
		}
		int uglyNum = uglys[n - 1];
		delete[]uglys;
		return uglyNum;
    }
};
```

# 5. 第k大元素

在数组中找到第 k 大的元素.

### 样例

**样例 1：**

```
输入：
n = 1, nums = [1,3,4,2]
输出：
4
```

**样例 2：**

```
输入：
n = 3, nums = [9,3,2,4,8]
输出：
4
```

### 挑战

要求时间复杂度为O(n),空间复杂度为O(1).

### 注意事项

你可以交换数组中的元素的位置

```cpp
class Solution {
public:
    /**
     * @param n: An integer
     * @param nums: An array
     * @return: the Kth largest element
     */
	int kthLargestElement(int k, vector<int>& nums) {
		int n = nums.size();
		k = n - k;
		return partition(nums, 0, n - 1, k);
	}
	int partition(vector<int>& nums, int start, int end, int k) {
		int left = start, right = end;
		int pivot = nums[left];
		while (left <= right) {
			while (left <= right and nums[left] < pivot) {
				left++;
			}
			while (left <= right and nums[right] > pivot) {
				right--;
			}
			if (left <= right) {
				swap(nums[left], nums[right]);
				left++;
				right--;
			}
		}
		if (k <= right) {
			return partition(nums, start, right, k);
		}
		if (k >= left) {
			return partition(nums, left, end, k);
		}
		return nums[k];
	}
};
```

# 6. 合并排序数组

合并两个有序升序的整数数组A和B变成一个新的数组.新数组也要有序.

### 样例

**样例 1:**

```
输入: A=[1], B=[1]
输出:[1,1]	
样例解释: 返回合并后的数组.
```

**样例 2:**

```
输入: A=[1,2,3,4], B=[2,4,5,6]
输出: [1,2,2,3,4,4,5,6]	
样例解释: 返回合并后的数组.
```

### 挑战

你能否优化你的算法,如果其中一个数组很大而另一个数组很小？

```cpp
class Solution {
public:
    /**
     * @param A: sorted integer array A
     * @param B: sorted integer array B
     * @return: A new sorted integer array
     */
    vector<int> mergeSortedArray(vector<int> &A, vector<int> &B) {
		if (A.size() > B.size()) {
			return insertSort(A, B);
		}
		else {
			return insertSort(B, A);
		}
	}

	vector<int> insertSort(vector<int>& C, vector<int>& D) {
		int length = C.size() + D.size(), size = C.size();
		int j = 0;
		C.insert(C.end(), D.begin(), D.end());
		for (int i = size; i < length; i++) {
			int temp = C[i];
			for (j = i - 1; j >= 0 && temp < C[j]; j--) {
				C[j + 1] = C[j];
			}
			C[j + 1] = temp;
		}
		for (int x : C) {
			cout << x << " ";
		}
		return C;
	}
};
```

# 8. 旋转字符串

给定一个字符串(以字符数组的形式给出)和一个偏移量,根据偏移量`原地`旋转字符串(从左向右旋转).

### 样例

**样例 1:**

```
输入:  str="abcdefg", offset = 3
输出:  str = "efgabcd"	
样例解释:  注意是原地旋转,即str旋转后为"efgabcd"
```

**样例 2:**

```
输入: str="abcdefg", offset = 0
输出: str = "abcdefg"	
样例解释: 注意是原地旋转,即str旋转后为"abcdefg"
```

**样例 3:**

```
输入: str="abcdefg", offset = 1
输出: str = "gabcdef"	
样例解释: 注意是原地旋转,即str旋转后为"gabcdef"
```

**样例 4:**

```
输入: str="abcdefg", offset =2
输出: str = "fgabcde"	
样例解释: 注意是原地旋转,即str旋转后为"fgabcde"
```

**样例 5:**

```
输入: str="abcdefg", offset = 10
输出: str = "efgabcd"	
样例解释: 注意是原地旋转,即str旋转后为"efgabcd"
```

### 挑战

在数组上原地旋转,使用O(1)的额外空间

### 说明

`原地旋转`意味着你要在s本身进行修改.你不需要返回任何东西.

### 注意事项

offset >= 0
str的长度 >= 0

```cpp
class Solution {
public:
    /**
     * @param str: An array of char
     * @param offset: An integer
     * @return: nothing
     */
    void rotateString(string &str, int offset) {
		if (str.size() == 0) {
			return;
		}
		offset %= str.size();
		string tempA = str.substr(0, str.size() - offset);
		string tempB = str.substr(str.size() - offset, str.size());
		str = tempB + tempA;
	}
};
```

# 9. Fizz Buzz 问题

给你一个整数*n*. 从 *1* 到 *n* 按照下面的规则打印每个数：

-    如果这个数被3整除,打印`fizz`.
-    如果这个数被5整除,打印`buzz`.
-    如果这个数能同时被`3`和`5`整除,打印`fizz buzz`.
-    如果这个数既不能被 `3` 整除也不能被 `5` 整除,打印数字`本身.`

### 样例

比如 *n* = `15`, 返回一个字符串数组：

```
[
  "1", "2", "fizz",
  "4", "buzz", "fizz",
  "7", "8", "fizz",
  "buzz", "11", "fizz",
  "13", "14", "fizz buzz"
]
```

### 挑战

你是否可以只用一个 `if` 来实现

```cpp
class Solution {
public:
    /**
     * @param n: An integer
     * @return: A list of strings.
     */
    vector<string> fizzBuzz(int n) {
		vector<string> result(n);
		for (int i = 1; i <= n; i++) {
			if (i % 15 == 0) {
				result[i - 1] = "fizz buzz";
			}
			else if (i % 3 == 0) {
				result[i - 1] = "fizz";
			}
			else if (i % 5 == 0) {
				result[i - 1] = "buzz";
			}
			else {
				result[i - 1] = to_string(i);
			}
		}
		return result;
	}
};
```

# 12. 带最小值操作的栈

实现一个栈, 支持以下操作:

-    `push(val)` 将 val 压入栈
-    `pop()` 将栈顶元素弹出, 并返回这个弹出的元素
-    `min()` 返回栈中元素的最小值

要求 O(1) 开销.

### 样例

**样例 2:**

```
输入: 
  push(1)
  min()
  push(2)
  min()
  push(3)
  min()
输出: 
  1
  1
  1
```

### 注意事项

保证栈中没有数字时不会调用 `min()`

```cpp
class MinStack {
public:
    stack<int> s1;
    stack<int> s2;
    MinStack() {
        // do intialization if necessary
    }

    /*
     * @param number: An integer
     * @return: nothing
     */
    void push(int number) {
        // write your code here
        s1.push(number);
        if(!s2.empty()){
            int temp=s2.top();
            if(number<temp){
                s2.push(number);
            }else{
                s2.push(temp);
            }
        }
        else{
            s2.push(number);
        }
    }

    /*
     * @return: An integer
     */
    int pop() {
        // write your code here
        int temp=s1.top();
        s1.pop();
        s2.pop();
        return temp;
    }

    /*
     * @return: An integer
     */
    int min() {
        // write your code here
        return s2.top();
    }
};
```

# 13. 字符串查找

对于一个给定的 source 字符串和一个 target 字符串,你应该在 source 字符串中找出 target 字符串出现的第一个位置(从0开始).如果不存在,则返回 `-1`.

### 样例

**样例 1:**

```
输入: source = "source" , target = "target"
输出:-1	
样例解释: 如果source里没有包含target的内容,返回-1
```

**样例 2:**

```
输入: source = "abcdabcdefg" ,target = "bcd"
输出: 1	
样例解释: 如果source里包含target的内容,返回target在source里第一次出现的位置
```

### 挑战

O(n2)的算法是可以接受的.如果你能用O(n)的算法做出来那更加好.(提示：KMP)

### 说明

在面试中我是否需要实现KMP算法？

-    不需要,当这种问题出现在面试中时,面试官很可能只是想要测试一下你的基础应用能力.当然你需要先跟面试官确认清楚要怎么实现这个题.

```cpp
class Solution {
public:
    /**
     * @param source: 
     * @param target: 
     * @return: return the index
     */
    int strStr(string &source, string &target) {
		return source.find(target);
    }
};
```

# 14. 二分查找

给定一个排序的整数数组(升序)和一个要查找的整数`target`,用`O(logn)`的时间查找到target第一次出现的下标(从0开始),如果target不存在于数组中,返回`-1`.

### 样例

```
样例  1:
	输入:[1,4,4,5,7,7,8,9,9,10],1
	输出: 0
	
	样例解释: 
	第一次出现在第0个位置.

样例 2:
	输入: [1, 2, 3, 3, 4, 5, 10],3
	输出: 2
	
	样例解释: 
	第一次出现在第2个位置
	
样例 3:
	输入: [1, 2, 3, 3, 4, 5, 10],6
	输出: -1
	
	样例解释: 
	没有出现过6, 返回-1
```

### 挑战

如果数组中的整数个数超过了2^32,你的算法是否会出错？

```cpp
class Solution {
public:
    /**
     * @param nums: The integer array.
     * @param target: Target to find.
     * @return: The first position of target. Position starts from 0.
     */
    int binarySearch(vector<int> &nums, int target) {
		int tempa = 0, tempb = nums.size();
		while (tempb >= tempa) {
			int medium = (tempa + tempb) / 2;
			if (nums[medium] > target) {
				tempb = medium-1;
			}
			else if (nums[medium] == target) {
				while (nums[medium] == nums[medium - 1]) {
					medium--;
				}
				return medium;
			}
			else {
				tempa = medium+1;
			}
		}
		return -1;
	}
};
```

# 15. 全排列

给定一个数字列表,返回其所有可能的排列.

### 样例

**样例 1：**

```
输入：[1]
输出：
[
  [1]
]
```

**样例 2：**

```
输入：[1,2,3]
输出：
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

### 挑战

使用递归和非递归分别解决.

### 注意事项

你可以假设没有重复数字.

```cpp
class Solution {
public:
	/*
	 * @param nums: A list of integers.
	 * @return: A list of permutations.
	 */
	vector<vector<int>> permute(vector<int>& nums) {
		vector<vector<int>>results;
		if (nums.size() == 0) {
			results.push_back(vector<int>());
			return results;
		}
		vector<bool>used(nums.size(), 0);
		vector<int>current;
		dfs(nums, used, current, results);
		return results;
	}
	void dfs(vector<int>nums, vector<bool>& used, vector<int>& current, vector<vector<int>>& results) {
		if (current.size() == nums.size()) {
			results.push_back(current);
			return;
		}
		for (int i = 0; i < nums.size(); i++) {
			if (used[i]) {
				continue;
			}
			current.push_back(nums[i]);
			used[i] = true;
			dfs(nums, used, current, results);
			used[i] = false;
			current.pop_back();
		}
		return;
	}
};
```

# 16. 带重复元素的排列

给出一个具有重复数字的列表,找出列表所有**不同**的排列.

### 样例

**样例 1：**

```
输入：[1,1]
输出：
[
  [1,1]
]
```

**样例 2：**

```
输入：[1,2,2]
输出：
[
  [1,2,2],
  [2,1,2],
  [2,2,1]
]
```

### 挑战

使用递归和非递归分别完成该题.

```cpp
class Solution {
private:
	void helper(vector<vector<int>>& results, vector<int>& permutation, vector<int>& nums, bool used[]) {
		if (nums.size() == permutation.size()) {
			results.push_back(permutation);
			return;
		}
		for (int i = 0; i < nums.size(); i++) {
			if (used[i]) {
				continue;
			}
			if (i > 0 && used[i - 1] == false && nums[i] == nums[i - 1]) {
				continue;
			}
			used[i] = true;
			permutation.push_back(nums[i]);
			helper(results, permutation, nums, used);
			permutation.pop_back();
			used[i] = false;
		}
	}
public:
	/*
	 * @param nums: A list of integers.
	 * @return: A list of permutations.
	 */
	vector<vector<int>> permuteUnique(vector<int>& nums) {
		vector<vector<int>>results;
		vector<int>permutation;
		bool* used = new bool[nums.size()];
		for (int i = 0; i < nums.size(); i++) {
			used[i] = false;
		}
		sort(nums.begin(), nums.end());
		helper(results, permutation, nums, used);
		return results;
	}
};
```

# 17. 子集

给定一个含不同整数的集合,返回其所有的子集.

### 样例

**样例 1：**

```
输入：[0]
输出：
[
  [],
  [0]
]
```

**样例 2：**

```
输入：[1,2,3]
输出：
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```

### 挑战

你可以同时用递归与非递归的方式解决么？

### 注意事项

子集中的元素排列必须是非降序的,解集必须不包含重复的子集.

```cpp
class Solution {
public:
	/**
	 * @param nums: A set of numbers
	 * @return: A list of lists
	 */
	vector<vector<int>> subsets(vector<int>& nums) {
		vector<vector<int>>results;
		vector<int> subset;
		sort(nums.begin(), nums.end());
		helper(results, subset, nums, 0);
		return results;
	}
private:
	void helper(vector<vector<int>>& results, vector<int>& subset, vector<int>& nums, int start) {
		results.push_back(subset);
		for (int i = start; i < nums.size(); i++) {
			subset.push_back(nums[i]);
			helper(results, subset, nums, i + 1);
			subset.pop_back();
		}
	}
};
```

# 20. 骰子求和

扔 *n* 个骰子,向上面的数字之和为 *S*.给定 *n*,请列出所有可能的 *S* 值及其相应的概率.

### 样例

**样例 1：**

```
输入：n = 1
输出：[[1, 0.17], [2, 0.17], [3, 0.17], [4, 0.17], [5, 0.17], [6, 0.17]]
解释：掷一次骰子,向上的数字和可能为1,2,3,4,5,6,出现的概率均为 0.17.
```

**样例 2：**

```
输入：n = 2
输出：[[2,0.03],[3,0.06],[4,0.08],[5,0.11],[6,0.14],[7,0.17],[8,0.14],[9,0.11],[10,0.08],[11,0.06],[12,0.03]]
解释：掷两次骰子,向上的数字和可能在[2,12],出现的概率是不同的.
```

### 注意事项

你不需要关心结果的准确性,我们会帮你输出结果.

```cpp
class Solution {
public:
    /**
     * @param n an integer
     * @return a list of pair<sum, probability>
     */
    vector<pair<int, double>> dicesSum(int n) {
		vector<map<int, double>>dp(n + 1);
		dp[1] = { {1,1 / 6.0},{2,1 / 6.0},{3,1 / 6.0},{4,1 / 6.0},{5,1 / 6.0},{6,1 / 6.0} };
		for (int i = 2; i <= n; i++) {
			for (auto a1 : dp[i - 1]) {
				for (auto a2 : dp[1]) {
					dp[i][a1.first + a2.first] += a1.second * a2.second;
				}
			}
		}
		vector<pair<int, double>>res;
		for (auto a : dp[n]) {
			res.push_back({ a.first,a.second });
		}
		return res;
    }
};
```

# 21. 移动的圆

题目将给出两个圆A和B的圆心坐标(x,y)和半径r,现给你一个点P,使圆A圆心沿直线运动至点P.
请问圆A在运动过程中是否会与圆B相交？(运动过程包括起点和终点)
若会相交返回1,否则返回-1.

### 样例

**样例 1**

```
输入：[0,0,2.5,3,2,0.5,0,2]
输出：1
样例解释：圆A的圆心(0,0),半径为2.5,圆B的圆心(3,2),半径为0.5,点P(0,2)
```

**样例 2**

```
输入：[0,0,2,5,0,1,0,2]
输出：-1
样例解释：圆A的圆心(0,0),半径为2,圆B的圆心(5,0),半径为1,点P(0,2)
```

### 注意事项

两个圆的半径均不超过10000.
横纵坐标值的绝对值均不超过10000.
输入数组的意义为[X_A*X*​*A*​​,Y_A*Y*​*A*​​,R_A*R*​*A*​​,X_B*X*​*B*​​,Y_B*Y*​*B*​​,R_B*R*​*B*​​,X_P*X*​*P*​​,Y_P*Y*​*P*​​].

```cpp
class Solution {
public:
	/**
	 * @param position: the position of circle A,B and point P.
	 * @return: if two circle intersect return 1, otherwise -1.
	 */
	typedef struct point {
		double x, y;
	}point;
	double xmult(point B, point C, point A) {
		return (B.x - A.x) * (C.y - A.y) - (C.x - A.x) * (B.y - A.y);
	}
	double distance(point A, point B) {
		return sqrt((A.x - B.x) * (A.x - B.x) + (A.y - B.y) * (A.y - B.y));
	}
	double dis_ptoline(point A, point B, point C) {
		return fabs(xmult(A, B, C)) / distance(B, C);
	}
	int IfIntersect(vector<double>& position) {
		point A, B, P, M;
		double ra, rb;
		double dmin, dmax;
		A.x = position[0];//initialize
		A.y = position[1];
		ra = position[2];
		B.x = position[3];
		B.y = position[4];
		rb = position[5];
		P.x = position[6];
		P.y = position[7];
		M.x = B.x - (P.y - A.y), M.y = B.y + (P.x - A.x);
		if (xmult(A, B, M) * xmult(B, P, M) >= 0) {
			if (A.x == P.x && A.y == P.y) {
				dmin = distance(B, A);
			}
			else {
				dmin = dis_ptoline(B, A, P);
			}
		}
		else {
			dmin = min(distance(A, B), distance(P, B));
		}
		dmax = max(distance(A, B), distance(P, B));
		if (dmin > ra + rb || dmax < fabs(ra - rb)) {
			return -1;
		}
		return 1;
	}
};
```

# 22. 列表扁平化

给定一个列表,该列表中的每个元素要么是个列表,要么是整数.将其变成一个只包含整数的简单列表.

### 样例

```
样例  1:
	输入: [[1,1],2,[1,1]]
	输出:[1,1,2,1,1] 
	
	样例解释:
	将其变成一个只包含整数的简单列表.


样例 2:
	输入: [1,2,[1,2]]
	输出:[1,2,1,2]
	
	样例解释: 
	将其变成一个只包含整数的简单列表.
	
样例 3:
	输入:[4,[3,[2,[1]]]]
	输出:[4,3,2,1]
	
	样例解释: 
	将其变成一个只包含整数的简单列表.
	
```

### 挑战

请用非递归方法尝试解答这道题.

### 注意事项

如果给定的列表中的要素本身也是一个列表,那么它也可以包含列表.

```cpp
/**
 * // This is the interface that allows for creating nested lists.
 * // You should not implement it, or speculate about its implementation
 * class NestedInteger {
 *   public:
 *     // Return true if this NestedInteger holds a single integer,
 *     // rather than a nested list.
 *     bool isInteger() const;
 *
 *     // Return the single integer that this NestedInteger holds,
 *     // if it holds a single integer
 *     // The result is undefined if this NestedInteger holds a nested list
 *     int getInteger() const;
 *
 *     // Return the nested list that this NestedInteger holds,
 *     // if it holds a nested list
 *     // The result is undefined if this NestedInteger holds a single integer
 *     const vector<NestedInteger> &getList() const;
 * };
 */
class Solution {
public:
    // @param nestedList a list of NestedInteger
    // @return a list of integer
    vector<int> flatten(vector<NestedInteger> &nestedList) {
        vector<int>res;
        flatten(nestedList,res);
        return res;
    }
    void flatten(const vector<NestedInteger> &nestedList,vector<int>&result){
        for(auto ni:nestedList){
            if(ni.isInteger()){
                result.push_back(ni.getInteger());
            }else{
                flatten(ni.getList(),result);
            }
        }
    }
};
```

# 23. 判断数字与字母字符

给出一个字符`c`,你需要判断它是不是一个数字字符或者字母字符.
如果是,返回`true`,如果不是返回`false`.

### 样例

**样例 1:**

```plain
输入：'1'
输出：true
```

### 注意事项

如果您使用的是Python语言,那么输入将是一个长度为1的字符串.

```cpp
class Solution {
public:
    /**
     * @param c: A character.
     * @return: The character is alphanumeric or not.
     */
	bool isAlphanumeric(char c) {
		if (isalpha(c) || isdigit(c)) {
			return true;
		}
		else {
			return false;
		}
	}
};
```

# 25. 打印X

输入一个正整数N, 你需要按如下方式返回一个字符串列表.

### 样例

**样例 1:**

```
输入：1
输出：
[
"X"
]
```

**样例 2:**

```
输入：2
输出：
[
"XX",
"XX"
]
```

**样例 3:**

```
输入：3
输出：
[
"X X",
" X ",
"X X"
]
```

**样例 4:**

```
输入：4
输出：
[
"X  X",
" XX ",
" XX ",
"X  X"
]
```

**样例 5:**

```
输入：5
输出：
[
"X   X",
" X X ",
"  X  ",
" X X ",
"X   X"
]
```

输入测试数据(每行一个参数)如何理解测试数据？

```cpp
class Solution {
public:
    /**
     * @param n: An integer.
     * @return: A string list.
     */
	vector<string> printX(int n) {
		vector<string>result;
		for (int i = 0; i < n; i++) {
			string temp(n, ' ');
			temp[i] = 'X';
			temp[n - i - 1] = 'X';
			result.push_back(temp);
		}
		return result;
	}
};
```

# 28. 搜索二维矩阵

写出一个高效的算法来搜索 *m* × *n*矩阵中的值.

这个矩阵具有以下特性：

-    每行中的整数从左到右是排序的.
-    每行的第一个数大于上一行的最后一个整数.

### 样例

```
样例  1:
	输入: [[5]],2
	输出: false
	
	样例解释: 
  没有包含,返回false.

样例 2:
	输入:  
[
  [1, 3, 5, 7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
],3
	输出: true
	
	样例解释: 
	包含则返回true.
```

### 挑战

O(log(n) + log(m)) 时间复杂度

```cpp
class Solution {
public:
    /**
     * @param matrix: matrix, a list of lists of integers
     * @param target: An integer
     * @return: a boolean, indicate whether matrix contains target
     */
    bool searchMatrix(vector<vector<int>> &matrix, int target) {
		int n = matrix.size();
		if (n == 0) {
			return false;
		}
		int m = matrix[0].size();
		if (m == 0) {
			return false;
		}
		int start = 0, end = n * m - 1;
		while (start + 1 < end) {
			int mid = start + (end - start) / 2;
			int row = mid / m;
			int col = mid % m;
			if (matrix[row][col] < target) {
				start = mid;
			}
			else {
				end = mid;
			}
		}
		if (matrix[start / m][start % m] == target) {
			return true;
		}
		if (matrix[end / m][end % m] == target) {
			return true;
		}
		return false;
    }
};
```

# 35. 翻转链表

翻转一个链表

### 样例

**样例 1:**

```
输入: 1->2->3->null
输出: 3->2->1->null
```

**样例 2:**

```
输入: 1->2->3->4->null
输出: 4->3->2->1->null
```

### 挑战

在原地一次翻转完成.

```cpp
/**
 * Definition of singly-linked-list:
 * class ListNode {
 * public:
 *     int val;
 *     ListNode *next;
 *     ListNode(int val) {
 *        this->val = val;
 *        this->next = NULL;
 *     }
 * }
 */

class Solution {
public:
    /**
     * @param head: n
     * @return: The new head of reversed linked list.
     */
    ListNode * reverse(ListNode * head) {
		ListNode* result = nullptr;
		while (head != nullptr) {
			ListNode* temp = head->next;
			head->next = result;
			result = head;
			head = temp;
		}
		return result;
    }
};
```

# 37. 反转一个3位整数

反转一个只有3位数的整数.

### 样例

**样例 1:**

```
输入: number = 123
输出: 321
```

**样例 2:**

```
输入: number = 900
输出: 9
```

### 注意事项

你可以假设输入一定是一个只有三位数的整数,这个整数大于等于100,小于1000.

```cpp
class Solution {
public:
    /**
     * @param number: A 3-digit number.
     * @return: Reversed number.
     */
    int reverseInteger(int number) {
		return number / 100 + ((number / 10) % 10) * 10 + (number % 10) * 100;
    }
};
```

# 39. 恢复旋转排序数组

给定一个**旋转**排序数组,在原地恢复其排序.(升序)

### 样例

**样例1:**
`[4, 5, 1, 2, 3]` -> `[1, 2, 3, 4, 5]`
**样例2:**
`[6,8,9,1,2]` -> `[1,2,6,8,9]`

### 挑战

使用O(1)的额外空间和O(*n*)时间复杂度

### 说明

什么是旋转数组？

-    比如,原始数组为[1,2,3,4], 则其旋转数组可以是[1,2,3,4], [2,3,4,1], [3,4,1,2], [4,1,2,3]

```cpp
class Solution {
public:
    /**
     * @param nums: An integer array
     * @return: nothing
     */
    void recoverRotatedSortedArray(vector<int> &nums) {
		int maxindex = -1;
		int size = nums.size();
		for (int i = 0; i < size - 1; i++) {
			if (nums[i] > nums[i + 1]) {
				maxindex = i;
				break;
			}
		}
		if (maxindex == -1) {
			return;
		}
		vector<int>temp;
		for (int i = maxindex + 1; i < size; i++) {
			temp.push_back(nums[i]);
		}
		for (int i = 0; i <= maxindex; i++) {
			temp.push_back(nums[i]);
		}
		nums = temp;
		return;
    }
};
```

# 40. 用栈实现队列

正如标题所述,你需要使用两个栈来实现队列的一些操作.

队列应支持push(element),pop() 和 top(),其中pop是弹出队列中的第一个(最前面的)元素.

pop和top方法都应该返回第一个元素的值.

### 样例

**例1:**

```
输入:
    push(1)
    pop()    
    push(2)
    push(3)
    top()    
    pop()     
输出:
    1
    2
    2
```

**例2:**

```
输入:
    push(1)
    push(2)
    push(2)
    push(3)
    push(4)
    push(5)
    push(6)
    push(7)
    push(1)
输出:
[]
```

### 挑战

仅使用两个栈来实现它,不使用任何其他数据结构,push,pop 和 top的复杂度都应该是均摊O(1)的

### 注意事项

假设调用pop()函数的时候,队列非空

```cpp
class MyQueue {
public:
    stack<int> stk;
    MyQueue() {
        // do intialization if necessary
    }

    /*
     * @param element: An integer
     * @return: nothing
     */
    void push(int element) {
        stk.push(element);
    }

    /*
     * @return: An integer
     */
    int pop() {
        stack<int> temp;
        int size=stk.size();
        for(int i=0;i<size;i++){
            temp.push(stk.top());
            stk.pop();
        }
        int res=temp.top();
        temp.pop();
        size=temp.size();
        for(int i=0;i<size;i++){
            stk.push(temp.top());
            temp.pop();
        }
        return res;
    }

    /*
     * @return: An integer
     */
    int top() {
        stack<int> temp;
        int size=stk.size();
        for(int i=0;i<size;i++){
            temp.push(stk.top());
            stk.pop();
        }
        int res=temp.top();
        size=temp.size();
        for(int i=0;i<size;i++){
            stk.push(temp.top());
            temp.pop();
        }
        return res;
    }
};
```

### 41. 最大子数组

给定一个整数数组,找到一个具有最大和的子数组,返回其最大和.

### 样例

**样例1:**

```
输入：[−2,2,−3,4,−1,2,1,−5,3]
输出：6
解释：符合要求的子数组为[4,−1,2,1],其最大和为 6.
```

**样例2:**

```
输入：[1,2,3,4]
输出：10
解释：符合要求的子数组为[1,2,3,4],其最大和为 10.
```

### 挑战

要求时间复杂度为O(n)

### 注意事项

子数组最少包含一个数

```cpp
class Solution {
public:
    /**
     * @param nums: A list of integers
     * @return: A integer indicate the sum of max subarray
     */
    int maxSubArray(vector<int> &nums) {
        int sum = 0, maxAns = INT_MIN;
        for (int i = 0; i < nums.size(); ++i) {
            sum += nums[i];
            maxAns = max(maxAns, sum);
            sum = max(sum, 0);
        }
        return maxAns;
    }
};
```

# 44. 最小子数组

给定一个整数数组,找到一个具有最小和的连续子数组.返回其最小和.

### 样例

**样例 1**

```
输入：[1, -1, -2, 1]
输出：-3
```

**样例 2**

```
输入：[1, -1, -2, 1, -4]
输出：-6
```

### 注意事项

子数组最少包含一个数字

```cpp
class Solution {
public:
    /*
     * @param nums: a list of integers
     * @return: A integer indicate the sum of minimum subarray
     */
	int minSubArray(vector<int>& nums) {
		int s = nums[0], minsum = s;
		for (int i = 1; i < nums.size(); i++) {
			s = min(0, s) + nums[i];
			minsum = min(minsum, s);
		}
		return minsum;
	}
};
```

# 46. 主元素

给定一个整型数组,找出主元素,它在数组中的出现次数严格大于数组元素个数的二分之一.



### 样例

**样例 1:**

```
输入: [1, 1, 1, 1, 2, 2, 2]
输出: 1
```

**样例 2:**

```
输入: [1, 1, 1, 2, 2, 2, 2]
输出: 2
```

### 挑战

要求时间复杂度为O(n),空间复杂度为O(1)

### 注意事项

你可以假设数组非空,且数组中总是存在主元素.

```cpp
class Solution {
public:
    /*
     * @param nums: a list of integers
     * @return: find a  majority number
     */
    int majorityNumber(vector<int> &nums) {
		vector<pair<int, int>>count;
		pair<int, int>temp(nums[0], 1);
		count.push_back(temp);
		for (int i = 1; i < nums.size(); i++) {
			int flags = 0;
			for (int j = 0; j < count.size(); j++) {
				if (nums[i] == count[j].first) {
					flags = 1;
					count[j].second++;
				}
			}
			if (flags == 0) {
				temp.first = nums[i];
				temp.second = 1;
				count.push_back(temp);
			}
		}
		double size = nums.size() / 2.0;
		for (int i = 0; i < count.size(); i++) {
			if (count[i].second > size) {
				return count[i].first;
			}
		}
    }
};
```

# 50. 数组剔除元素后的乘积

给定一个整数数组A.
定义`B[i] = A[0] * ... * A[i-1] * A[i+1] * ... * A[n-1]`, 计算B的时候请不要使用除法.请输出B.

### 样例

**样例 1**

```
输入: A = [1, 2, 3]
输出: [6, 3, 2]
解析：B[0] = A[1] * A[2] = 6; B[1] = A[0] * A[2] = 3; B[2] = A[0] * A[1] = 2
```

**样例 2**

```
输入: A = [2, 4, 6]
输出: [24, 12, 8]
```

```cpp
class Solution {
public:
    /*
     * @param nums: Given an integers array A
     * @return: A long long array B and B[i]= A[0] * ... * A[i-1] * A[i+1] * ... * A[n-1]
     */
    vector<long long> productExcludeItself(vector<int> &nums) {
		vector<long long>res;
		for (int i = 0; i < nums.size(); i++) {
			long long temp = 1;
			for (int j = 0; j < nums.size(); j++) {
				if (i != j) {
					temp *= nums[j];
				}
			}
			res.push_back(temp);
		}
		return res;
    }
};
```

# 52. 下一个排列

给定一个整数数组来表示排列,找出其之后的一个排列.

### 样例

例1:

```
输入:[1]
输出:[1]
```

例2:

```
输入:[1,3,2,3]
输出:[1,3,3,2]
```

例3:

```
输入:[4,3,2,1]
输出:[1,2,3,4]
```

### 注意事项

排列中可能包含重复的整数

```cpp
class Solution {
public:
    /**
     * @param nums: A list of integers
     * @return: A list of integers
     */
    vector<int> nextPermutation(vector<int> &nums) {
        if(nums.size()==1){
            return nums;
        }
        int i=nums.size()-2;
        while(i>=0 and nums[i]>=nums[i+1]){
            i--;
        }
        int j=nums.size()-1;
        if(i>=0){
            while(nums[j]<=nums[i]){
                j--;
            }
            swap(nums[i],nums[j]);
        }
        reverse(nums.begin()+i+1,nums.end());
        return nums;
    }
};
```



# 53. 翻转字符串中的单词

给定一个字符串,逐个翻转字符串中的每个单词.

### 样例

```
样例  1:
	输入:  "the sky is blue"
	输出:  "blue is sky the"
	
	样例解释: 
	返回逐字反转的字符串.

样例 2:
	输入:  "hello world"
	输出:  "world hello"
	
	样例解释: 
	返回逐字反转的字符串.
```

### 说明



-    单词的构成：无空格字母构成一个单词,有些单词末尾会带有标点符号
-    输入字符串是否包括前导或者尾随空格？可以包括,但是反转后的字符不能包括
-    如何处理两个单词间的多个空格？在反转字符串中间空格减少到只含一个

```cpp
class Solution {
public:
    /*
     * @param s: A string
     * @return: A string
     */
	string reverseWords(string& s) {
		if (s.find_first_not_of(' ') == string::npos) {
			return "";
		}
		string res;
		int i = s.length() - 1;
		do {
			vector<char>temp;
			for (; i >= 0 and s[i] != ' '; i--) {
				temp.push_back(s[i]);
			}
			i--;
			reverse(temp.begin(), temp.end());
			if (temp.size() > 0) {
				for (int j = 0; j < temp.size(); j++) {
					res += temp[j];
				}
				res += ' ';
			}
		} while (i >= 0);
		return res;
	}
};
```

# 55. 比较字符串

比较两个字符串A和B,确定A中是否包含B中所有的字符.字符串A和B中的字符都是 **大写字母**

### 样例

给出 A = `"ABCD"` B = `"ACD"`,返回 `true`

给出 A = `"ABCD"` B = `"AABC"`, 返回 `false`

### 注意事项

在 A 中出现的 B 字符串里的字符不需要连续或者有序.

```cpp
class Solution {
public:
    /**
     * @param A: A string
     * @param B: A string
     * @return: if string A contains all of the characters in B return true else return false
     */
	bool compareStrings(string& A, string& B) {
		for (int i = 0; i < B.size(); i++) {
			bool find = false;
			for (int j = 0; j < A.size(); j++) {
				if (A[j] == B[i]) {
					A.erase(A.begin() + j);
					find = true;
					break;
				}
			}
			if (!find) {
				return false;
			}
		}
		return true;
	}
};
```

# 56. 两数之和

给一个整数数组,找到两个数使得他们的和等于一个给定的数 *target*.

你需要实现的函数`twoSum`需要返回这两个数的下标, 并且第一个下标小于第二个下标.注意这里下标的范围是 0 到 *n-1*.

### 样例

```
样例1:
给出 numbers = [2, 7, 11, 15], target = 9, 返回 [0, 1].
样例2:
给出 numbers = [15, 2, 7, 11], target = 9, 返回 [1, 2].
```

### 挑战

给自己加点挑战

-    O(n)*O*(*n*) 空间复杂度,O(nlogn)*O*(*n**l**o**g**n*) 时间复杂度,
-    O(n)*O*(*n*) 空间复杂度,O(n)*O*(*n*) 时间复杂度,

### 注意事项

你可以假设只有一组答案.

```cpp
class Solution {
public:
    /**
     * @param numbers: An array of Integer
     * @param target: target = numbers[index1] + numbers[index2]
     * @return: [index1 + 1, index2 + 1] (index1 < index2)
     */
    vector<int> twoSum(vector<int> &numbers, int target) {
		vector<int>res;
		size_t size = numbers.size();
		for (int i = 0; i < size; ++i) {
			for (int j = i + 1; j < size; ++j) {
				if (target == numbers[i] + numbers[j]) {
					res.push_back(i);
					res.push_back(j);
					return res;
				}
			}
		}
    }
};
```

# 60. 搜索插入位置

给定一个排序数组和一个目标值,如果在数组中找到目标值则返回索引.如果没有,返回到它将会被按顺序插入的位置.

你可以假设在数组中无重复元素.

### 样例

**[1,3,5,6]**,5 → 2

**[1,3,5,6]**,2 → 1

**[1,3,5,6]**, 7 → 4

**[1,3,5,6]**,0 → 0

### 挑战

时间复杂度为O(log(n))

```cpp
class Solution {
public:
    /**
     * @param A: an integer sorted array
     * @param target: an integer to be inserted
     * @return: An integer
     */
    int searchInsert(vector<int> &A, int target) {
        if(A.size()==0){
            return 0;
        }
        for(int i=0;i<A.size();i++){
            if(A[i]>=target){
                return i;
            }
        }
        return A.size();
    }
};
```

# 64. 合并排序数组(简单版)

合并两个排序的整数数组A和B变成一个新的数组.

### 样例

**样例 1:**

```
输入：[1, 2, 3]  3  [4,5]  2
输出：[1,2,3,4,5]
解释:
经过合并新的数组为[1,2,3,4,5]
```

**样例 2:**

```
输入：[1,2,5] 3 [3,4] 2
输出：[1,2,3,4,5]
解释：
经过合并新的数组为[1,2,3,4,5]
```

### 注意事项

你可以假设A具有足够的空间(A数组的大小大于或等于m+n)去添加B中的元素.

```cpp
class Solution {
public:
    /*
     * @param A: sorted integer array A which has m elements, but size of A is m+n
     * @param m: An integer
     * @param B: sorted integer array B which has n elements
     * @param n: An integer
     * @return: nothing
     */
    void mergeSortedArray(int A[], int m, int B[], int n) {
        for(int i=0;i<n;i++){
            A[m+i]=B[i];
        }
        sort(A,A+m+n,less<int>());
        return;
    }
};
```

# 66.  二叉树的前序遍历

描述

给出一棵二叉树,返回其节点值的前序遍历.

首个数据为根节点,后面接着是其左儿子和右儿子节点值,"#"表示不存在该子节点.节点数量不超过20

样例

**样例 1:**

```
输入：{1,2,3}
输出：[1,2,3]
解释：
   1
  / \
 2   3
它将被序列化为{1,2,3}
前序遍历
```

**样例 2:**

```
输入：{1,#,2,3}
输出：[1,2,3]
解释：
1
 \
  2
 /
3
它将被序列化为{1,#,2,3}
前序遍历
```

挑战

你能使用非递归实现么？

```cpp
/**
 * Definition of TreeNode:
 * class TreeNode {
 * public:
 *     int val;
 *     TreeNode *left, *right;
 *     TreeNode(int val) {
 *         this->val = val;
 *         this->left = this->right = NULL;
 *     }
 * }
 */

class Solution {
public:
    /**
     * @param root: A Tree
     * @return: Preorder in ArrayList which contains node values.
     */
    vector<int>preorder;
    void traverse(TreeNode*root){
        if(root==NULL){
            return;
        }
        preorder.push_back(root->val);
        traverse(root->left);
        traverse(root->right);
    }
    vector<int> preorderTraversal(TreeNode * root) {
        preorder.clear();
        traverse(root);
        return preorder;
    }
};
```

# 67.  二叉树的中序遍历

描述

给出一棵二叉树,返回其中序遍历

样例

**样例 1:**

```
输入：{1,2,3}
输出：[2,1,3]
解释：
   1
  / \
 2   3
它将被序列化为{1,2,3}
中序遍历
```

**样例 2:**

```
输入：{1,#,2,3}
输出：[1,3,2]
解释：
1
 \
  2
 /
3
它将被序列化为{1,#,2,3}
中序遍历
```

```cpp
/**
 * Definition of TreeNode:
 * class TreeNode {
 * public:
 *     int val;
 *     TreeNode *left, *right;
 *     TreeNode(int val) {
 *         this->val = val;
 *         this->left = this->right = NULL;
 *     }
 * }
 */

class Solution {
public:
    /**
     * @param root: A Tree
     * @return: Inorder in ArrayList which contains node values.
     */
    vector<int>res;
    void traversal(TreeNode* root){
        while(root==NULL){
            return;
        }
        traversal(root->left);
        res.push_back(root->val);
        traversal(root->right);
    }
    vector<int> inorderTraversal(TreeNode * root) {
        res.clear();
        traversal(root);
        return res;
    }
};
```



# 68. 二叉树的后序遍历

描述

给出一棵二叉树,返回其节点值的前序遍历.

首个数据为根节点,后面接着是其左儿子和右儿子节点值,"#"表示不存在该子节点.节点数量不超过20

样例

**样例 1:**

```
输入：{1,2,3}
输出：[1,2,3]
解释：
   1
  / \
 2   3
它将被序列化为{1,2,3}
前序遍历
```

**样例 2:**

```
输入：{1,#,2,3}
输出：[1,2,3]
解释：
1
 \
  2
 /
3
它将被序列化为{1,#,2,3}
前序遍历
```

挑战

你能使用非递归实现么？

```cpp
/**
 * Definition of TreeNode:
 * class TreeNode {
 * public:
 *     int val;
 *     TreeNode *left, *right;
 *     TreeNode(int val) {
 *         this->val = val;
 *         this->left = this->right = NULL;
 *     }
 * }
 */

class Solution {
public:
    /**
     * @param root: A Tree
     * @return: Preorder in ArrayList which contains node values.
     */
    vector<int>preorder;
    void traverse(TreeNode*root){
        if(root==NULL){
            return;
        }
        preorder.push_back(root->val);
        traverse(root->left);
        traverse(root->right);
    }
    vector<int> preorderTraversal(TreeNode * root) {
        preorder.clear();
        traverse(root);
        return preorder;
    }
};
```



# 75. 寻找峰值

你给出一个整数数组(size为n),其具有以下特点：

-    相邻位置的数字是不同的
-    A[0] < A[1] 并且 A[n - 2] > A[n - 1]

假定*P*是峰值的位置则满足`A[P] > A[P-1]`且`A[P] > A[P+1]`,返回数组中任意一个峰值的位置.

### 样例

```
样例 1:
	输入:  [1, 2, 1, 3, 4, 5, 7, 6]
	输出:  1 or 6
	
	解释:
	返回峰顶元素的下标


样例 2:
	输入: [1,2,3,4,1]
	输出:  3
```

### 挑战

时间复杂度O (logN)

### 注意事项

-    数组保证至少存在一个峰
-    如果数组存在多个峰,返回其中任意一个就行
-    数组至少包含 3 个数

```cpp
class Solution {
public:
    /**
     * @param A: An integers array.
     * @return: return any of peek positions.
     */
    int findPeak(vector<int> &A) {
        int l=1,r=A.size();
        while(l<=r){
            int mid=(l+r)/2;
            if(A[mid]>A[mid-1] and A[mid]>A[mid+1]){
                return mid;
            }
            if(A[mid]>A[mid-1]){
                l=mid+1;
            }
            else{
                r=mid-1;
            }
        }
        return -1;
    }
};
```

# 76. 最长上升子序列

给定一个整数序列,找到最长上升子序列(LIS),返回LIS的长度.

### 样例

```
样例 1:
	输入:  [5,4,1,2,3]
	输出:  3
	
	解释:
	LIS 是 [1,2,3]


样例 2:
	输入: [4,2,4,5,3,7]
	输出:  4
	
	解释: 
	LIS 是 [2,4,5,7]
```

### 挑战

要求时间复杂度为O(n^2) 或者 O(nlogn)

### 说明

最长上升子序列的定义：

最长上升子序列问题是在一个无序的给定序列中找到一个尽可能长的由低到高排列的子序列,这种子序列不一定是连续的或者唯一的.
https://en.wikipedia.org/wiki/Longest_increasing_subsequence

```cpp
class Solution {
public:
    int longestIncreasingSubsequence(vector<int> &nums) {
        if (nums.size() == 0) {
            return 0;
        }
        int res = 1;
        vector<int> LIS(nums.size(), 1);
        for (int i = 1; i < nums.size(); ++i) {
            for (int j = 0; j < i; ++j) {
                if (nums[i] > nums[j]) {
                    LIS[i] = max(LIS[i], LIS[j] + 1);
                }
            }
            res = max(res, LIS[i]);
        }
        return res;
    }
};
```

# 80. 中位数

给定一个未排序的整数数组,找到其中位数.

中位数是排序后数组的中间值,如果数组的个数是偶数个,则返回排序后数组的第N/2个数.

### 样例

**样例 1:**

```
输入：[4, 5, 1, 2, 3]
输出：3
解释：
经过排序,得到数组[1,2,3,4,5],中间数字为3
```

**样例 2:**

```
输入：[7, 9, 4, 5]
输出：5
解释：
经过排序,得到数组[4,5,7,9],第二个(4/2)数字为5
```

### 挑战

时间复杂度为O(n)

### 注意事项

数组大小不超过10000

```cpp
class Solution {
public:
    /**
     * @param nums: A list of integers
     * @return: An integer denotes the middle number of the array
     */
    int median(vector<int> &nums) {
		sort(nums.begin(), nums.end());
		if (nums.size() % 2 == 0) {
			return nums[(nums.size() / 2) - 1];
		}
		else {
			return nums[nums.size() / 2];
		}
    }
};
```

# 82. 落单的数

给出 `2 * n + 1`个数字,除其中一个数字之外其他每个数字均出现两次,找到这个数字.

### 样例

**样例 1:**

```
输入：[1,1,2,2,3,4,4]
输出：3
解释：
仅3出现一次
```

**样例 2:**

```
输入：[0,0,1]
输出：1
解释：
仅1出现一次
```

### 挑战

一次遍历,常数级的额外空间复杂度

### 注意事项

-    n≤100

```cpp
class Solution {
public:
    /**
     * @param A: An integer array
     * @return: An integer
     */
    int singleNumber(vector<int> &A) {
		vector<pair<int, int>>count;
		pair<int, int>temp;
		temp.first = A[0];
		temp.second = 1;
		count.push_back(temp);
		for (int i = 1; i < A.size(); i++) {
			bool flag = true;
			for (int j = 0; j < count.size(); j++) {
				if (count[j].first == A[i]) {
					count[j].second++;
					flag = false;
					break;
				}
			}
			if (flag) {
				temp.first = A[i];
				temp.second = 1;
				count.push_back(temp);
			}
		}
		for (int i = 0; i < count.size(); i++) {
			if (count[i].second == 1) {
				return count[i].first;
			}
		}
    }
};
```

# 93.  平衡二叉树

描述

给定一个二叉树,确定它是高度平衡的.对于这个问题,一棵高度平衡的二叉树的定义是：一棵二叉树中每个节点的两个子树的深度相差不会超过1. 

样例

```
样例  1:
	输入: tree = {1,2,3}
	输出: true
	
	样例解释:
	如下,是一个平衡的二叉树.
		  1  
		 / \                
		2  3

	
样例  2:
	输入: tree = {3,9,20,#,#,15,7}
	输出: true
	
	样例解释:
	如下,是一个平衡的二叉树.
		  3  
		 / \                
		9  20                
		  /  \                
		 15   7 

	
样例  2:
	输入: tree = {1,#,2,3,4}
	输出: false
	
	样例解释:
	如下,是一个不平衡的二叉树.1的左右子树高度差2
		  1  
		   \                
		   2                
		  /  \                
		 3   4
	
```

```cpp
/**
 * Definition of TreeNode:
 * class TreeNode {
 * public:
 *     int val;
 *     TreeNode *left, *right;
 *     TreeNode(int val) {
 *         this->val = val;
 *         this->left = this->right = NULL;
 *     }
 * }
 */

class Solution {
public:
    /**
     * @param root: The root of binary tree.
     * @return: True if this Binary tree is Balanced, or false.
     */
    bool isBalanced(TreeNode * root) {
        return dfs(root).first;
    }
    pair<bool,int>dfs(TreeNode*root){
        if(!root){
            return {true,0};
        }
        auto l=dfs(root->left);
        auto r=dfs(root->right);
        pair<bool,int>ans={true,max(l.second,r.second)+1};
        ans.first&=l.first&&r.first &&(abs(l.second-r.second)<=1);
        return ans;
    }
};
```



# 100. 删除排序数组中的重复数字

给定一个排序数组,在原数组中"删除"重复出现的数字,使得每个元素只出现一次,并且返回"新"数组的长度.

不要使用额外的数组空间,必须在不使用额外空间的条件下原地完成.

### 样例

**样例 1:**

```
输入:  []
输出: 0
```

**样例 2:**

```
输入:  [1,1,2]
输出: 2	
解释:  数字只出现一次的数组为: [1,2]
```

```
class Solution {
public:
    /*
     * @param nums: An ineger array
     * @return: An integer
     */
    int removeDuplicates(vector<int> &nums) {
        vector<int>::iterator iter=unique(nums.begin(),nums.end());
        nums.erase(iter,nums.end());
        return nums.size();
    }
};
```

# 101. 删除排序数组中的重复数字 II

给你一个排序数组,删除其中的重复元素,使得每个数字最多出现两次,返回新的数组的长度.
如果一个数字出现超过2次,则这个数字最后保留两个.

### 样例

```
样例 1:
	输入: []
	输出: 0


样例 2:
	输入:  [1,1,1,2,2,3]
	输出: 5
	
	样例解释: 
	长度为 5,  数组为：[1,1,2,2,3]
```

### 注意事项

需要在原数组中操作

```cpp
class Solution {
public:
    /**
     * @param A: a list of integers
     * @return : return an integer
     */
    int removeDuplicates(vector<int> &nums) {
        if(nums.size()==0){
            return 0;
        }
        bool equal=false;
        for(int i=1;i<nums.size();){
            if(nums[i]==nums[i-1] and equal==false){
                equal=true;
                ++i;
            }
            else if(nums[i]!=nums[i-1]){
                equal=false;
                ++i;
            }
            else{
                nums.erase(nums.begin()+i);
            }
        }
        return nums.size();
    }
};
```

# 110. 最小路径和

给定一个只含非负整数的m*n网格,找到一条从左上角到右下角的可以使数字和最小的路径.



### 样例

样例 1:

```
输入:  [[1,3,1],[1,5,1],[4,2,1]]
输出: 7	
样例解释：
路线为： 1 -> 3 -> 1 -> 1 -> 1.
```

样例 2:

```
输入:  [[1,3,2]]
输出:  6
解释:  
路线是： 1 -> 3 -> 2
```

### 注意事项

你在同一时间只能向下或者向右移动一步

```cpp
class Solution {
public:
    /**
     * @param grid: a list of lists of integers
     * @return: An integer, minimizes the sum of all numbers along its path
     */
    int minPathSum(vector<vector<int>> &grid) {
        int f[1000][1000];
        if(grid.size()==0 or grid[0].size()==0){
            return 0;
        }
        f[0][0]=grid[0][0];
        for(int i=0;i<grid.size();i++){
            f[i][0]=f[i-1][0]+grid[i][0];
        }
        for(int i=1;i<grid[0].size();i++){
            f[0][i]=f[0][i-1]+grid[0][i];
        }
        for(int i=1;i<grid.size();i++){
            for(int j=1;j<grid[0].size();j++){
                f[i][j]=min(f[i-1][j],f[i][j-1])+grid[i][j];
            }
        }
        return f[grid.size()-1][grid[0].size()-1];
    }
};
```

# 111. 爬楼梯

假设你正在爬楼梯,需要n步你才能到达顶部.但每次你只能爬一步或者两步,你能有多少种不同的方法爬到楼顶部？

### 样例

```
样例 1:
	输入:  n= 3
	输出: 3
	
	样例解释：
	1) 1, 1, 1
	2) 1, 2
	3) 2, 1
	共3种


样例 2:
	输入:  n = 1
	输出: 1
	
	解释:  
	只有一种方案
```

```cpp
class Solution {
public:
    /**
     * @param n: An integer
     * @return: An integer
     */
    int climbStairs(int n) {
        int a=min(n,1);
        for(auto i=1,b=a;i<n;++i,b=a-b){
            a+=b;
        }
        return a;
    }
};
```

# 112. 删除排序链表中的重复元素

给定一个排序链表,删除所有重复的元素每个元素只留下一个.

### 样例

```
样例 1:
	输入:  null
	输出: null


样例 2:
	输入: 1->1->2->null
	输出: 1->2->null

样例 3:
	输入: 1->1->2->3->3->null
	输出: 1->2->3->null
```

```cpp
/**
 * Definition of singly-linked-list:
 * class ListNode {
 * public:
 *     int val;
 *     ListNode *next;
 *     ListNode(int val) {
 *        this->val = val;
 *        this->next = NULL;
 *     }
 * }
 */

class Solution {
public:
    /**
     * @param head: head is the head of the linked list
     * @return: head of linked list
     */
    ListNode * deleteDuplicates(ListNode * head) {
        ListNode *res=head;
        if(head==nullptr){
            return head;
        }
        for(ListNode *reshead=nullptr;head->next!=NULL;){
            reshead=head->next;
            if(head->val==reshead->val){
                head->next=reshead->next;
            }else{
                head=head->next;
            }
        }
        return res;
    }
};
```

# 114. 不同的路径

有一个机器人的位于一个 *m* × *n* 个网格左上角.

机器人每一时刻只能向下或者向右移动一步.机器人试图达到网格的右下角.

问有多少条不同的路径？

### 样例

**样例 1:**

```
输入: n = 1, m = 3
输出: 1	
解释: 只有一条通往目标位置的路径.
```

**样例 2:**

```
输入:  n = 3, m = 3
输出: 6	
解释:
	D : Down
	R : Right
	1) DDRR
	2) DRDR
	3) DRRD
	4) RRDD
	5) RDRD
	6) RDDR
```

### 注意事项

n和m均不超过100
且答案保证在32位整数可表示范围内.

```cpp
class Solution {
public:
    /**
     * @param m: positive integer (1 <= m <= 100)
     * @param n: positive integer (1 <= n <= 100)
     * @return: An integer
     */
	int uniquePaths(int m, int n) {
		vector<vector<int>>count(m, vector<int>(n, 1));
		for (int i = m - 2; i >= 0; --i) {
			for (int j = n - 2; j >= 0; --j) {
				count[i][j] = count[i + 1][j] + count[i][j + 1];
			}
		}
		return count[0][0];
	}
};
```

# 117. 跳跃游戏 II

给出一个非负整数数组,你最初定位在数组的第一个位置.

数组中的每个元素代表你在那个位置可以跳跃的最大长度.　　　

你的目标是使用最少的跳跃次数到达数组的最后一个位置.

### 样例

***样例 1***

```
输入 : [2,3,1,1,4]
输出 : 2
解释 : 到达最后位置的最小跳跃次数是2(从下标0到1跳跃1个距离长度,然后跳跃3个距离长度到最后位置)
```

```cpp
class Solution {
public:
    /**
     * @param A: A list of integers
     * @return: An integer
     */
    int jump(vector<int> &A) {
        int n=A.size();
        vector<int>dp(n);
        dp[0]=0;
        for(int i=1;i<n;i++){
            dp[i]=INT_MAX;
            for(int j=0;j<i;j++){
                if(A[j]+j>=i){
                    dp[i]=min(dp[i],dp[j]+1);
                }
            }
        }
        return dp[n-1];
    }
};
```

# 125. 背包问题 II

有 `n` 个物品和一个大小为 `m` 的背包. 给定数组 `A` 表示每个物品的大小和数组 `V` 表示每个物品的价值.

问最多能装入背包的总价值是多大?

### 样例

**样例 1:**

```
输入: m = 10, A = [2, 3, 5, 7], V = [1, 5, 2, 4]
输出: 9
解释: 装入 A[1] 和 A[3] 可以得到最大价值, V[1] + V[3] = 9 
```

**样例 2:**

```
输入: m = 10, A = [2, 3, 8], V = [2, 5, 8]
输出: 10
解释: 装入 A[0] 和 A[2] 可以得到最大价值, V[0] + V[2] = 10
```

### 挑战

O(nm) 空间复杂度可以通过, 不过你可以尝试 O(m) 空间复杂度吗?

### 注意事项

1.   `A[i], V[i], n, m` 均为整数
2.   你不能将物品进行切分
3.   你所挑选的要装入背包的物品的总大小不能超过 `m`
4.   每个物品只能取一次

```cpp
class Solution {
public:
    /**
     * @param m: An integer m denotes the size of a backpack
     * @param A: Given n items with size A[i]
     * @param V: Given n items with value V[i]
     * @return: The maximum value
     */
    int backPackII(int m, vector<int> &A, vector<int> &V) {
        vector<int>f(m+1,0);
        for(int i=0;i<A.size();i++){
            for(int j=m;j>=A[i];j--){
                f[j]=max(f[j],f[j-A[i]]+V[i]);
            }
        }
        return f[m];
    }
};
```

# 128. 哈希函数

在数据结构中,哈希函数是用来将一个字符串(或任何其他类型)转化为小于哈希表大小且大于等于零的整数.一个好的哈希函数可以尽可能少地产生冲突.一种广泛使用的哈希函数算法是使用数值33,假设任何字符串都是基于33的一个大整数,比如：

hashcode("abcd") = (ascii(a) * 333 + ascii(b) * 332 + ascii(c) *33 + ascii(d)) % HASH_SIZE 

​               = (97* 333 + 98 * 332 + 99 * 33 +100) % HASH_SIZE

​               = 3595978 % HASH_SIZE

其中HASH_SIZE表示哈希表的大小(可以假设一个哈希表就是一个索引0 ~ HASH_SIZE-1的数组).

给出一个字符串作为key和一个哈希表的大小,返回这个字符串的哈希值.

### 样例

**样例 1:**

```
输入:  key = "abcd", size = 1000
输出: 978	
样例解释：(97 * 33^3 + 98*33^2 + 99*33 + 100*1)%1000 = 978
```

**样例 2:**

```
输入:  key = "abcd", size = 100
输出: 78	
样例解释：(97 * 33^3 + 98*33^2 + 99*33 + 100*1)%100 = 78
```

### 说明

对于这个问题,您没有必要设计自己的哈希算法或考虑任何冲突问题,您只需要按照描述实现算法.

```cpp
class Solution {
public:
    /**
     * @param key: A string you should hash
     * @param HASH_SIZE: An integer
     * @return: An integer
     */
    int hashCode(string &key, int HASH_SIZE) {
		vector<long long>hash;
		hash.push_back(1);
		for (int i = 1; i < key.size(); i++) {
			hash.push_back((hash[i - 1] * 33) % HASH_SIZE);
		}
		long long res = 0;
		for (int i = 0; i < key.size(); i++) {
			res += int(key[i]) * hash[key.size() - 1 - i];
			res %= HASH_SIZE;
		}
		return res;
    }
};
```

# 133. 最长单词

给一个词典,找出其中所有最长的单词.

### 样例

```
样例 1:
	输入:   {
		"dog",
		"google",
		"facebook",
		"internationalization",
		"blabla"
		}
	输出: ["internationalization"]



样例 2:
	输入: {
		"like",
		"love",
		"hate",
		"yes"		
		}
	输出: ["like", "love", "hate"]
```

### 挑战

遍历两次的办法很容易想到,如果只遍历一次你有没有什么好办法？

```cpp
class Solution {
public:
    /*
     * @param dictionary: an array of strings
     * @return: an arraylist of strings
     */
    vector<string> longestWords(vector<string> &dictionary) {
		vector<string>res;
		res.push_back(dictionary[0]);
		vector<string>::iterator iter;
		for (iter = dictionary.begin() + 1; iter != dictionary.end(); ++iter) {
			if (iter->size() > res[0].size()) {
				res.clear();
				res.push_back(*iter);
			}
			else if (iter->size() == res[0].size()) {
				res.push_back(*iter);
			}
		}
		return res;
    }
};
```

# 138. 子数组之和

给定一个整数数组,找到和为 0 的子数组.你的代码应该返回满足要求的子数组的起始位置和结束位置

### 样例

**样例 1:**

```
输入: [-3, 1, 2, -3, 4]
输出: [0,2] 或 [1,3]	
样例解释： 返回任意一段和为0的区间即可.
```

**样例 2:**

```
输入: [-3, 1, -4, 2, -3, 4]
输出: [1,5]
```

### 注意事项

至少有一个子数组的和为 0

```cpp
class Solution {
public:
    /**
     * @param nums: A list of integers
     * @return: A list of integers includes the index of the first number and the index of the last number
     */
    vector<int> subarraySum(vector<int> &nums) {
		vector<int>result;
		unordered_map<int, int>hash;
		hash[0] = -1;
		int sum = 0;
		for (int i = 0; i < nums.size(); i++) {
			//累加前缀和
			sum += nums[i];
			//前缀和曾经出现,即这个区间的和为0
			if (hash.find(sum) != hash.end()) {
				result.push_back(hash[sum] + 1);
				result.push_back(i);
				break;
			}
			//前缀和第一次出现,存入hash
			hash[sum] = i;
		}
		return result;
    }
};
```

# 141. 对x开根

实现 `int sqrt(int x)` 函数,计算并返回 *x* 的平方根.

### 样例

```
样例 1:
	输入:  0
	输出: 0


样例 2:
	输入: 3
	输出: 1
	
	样例解释：
	返回对x开根号后向下取整的结果.

样例 3:
	输入: 4
	输出: 2
```

### 挑战

```cpp
class Solution {
public:
    /**
     * @param x: An integer
     * @return: The sqrt of x
     */
    int sqrt(int x) {
        long long res=1+x/2,del=res;
        for(;abs(del=res*res-x)>=res*2;res-=del/2/res);
        return del>0?--res:res;
    }
};
```

# 142. O(1)时间检测2的幂次

用 O(*1*) 时间检测整数 *n* 是否是 *2* 的幂次.

### 样例

`n=4`,返回 `true`;

`n=5`,返回 `false`.

### 挑战

O(*1*) 时间复杂度

```cpp
class Solution {
public:
    /**
     * @param n: An integer
     * @return: True or false
     */
    bool checkPowerOf2(int n) {
        if(n==0){
            return false;
        }
        while(n%2==0){
            n/=2;
        }
        return n==1;
    }
};
```

# 145. 大小写转换

将一个字符由小写字母转换为大写字母

### 样例

**样例 1:**

```
输入: 'a'
输出: 'A'
```

**样例 2:**

```
输入: 'b'
输出: 'B'
```

### 注意事项

你可以假设输入一定在小写字母 a ~ z 之间

```cpp
class Solution {
public:
    /**
     * @param character: a character
     * @return: a character
     */
    char lowercaseToUppercase(char character) {
		character = toupper(character);
		return character;
    }
};
```

# 148. 颜色分类

给定一个包含红,白,蓝且长度为 n 的数组,将数组元素进行分类使相同颜色的元素相邻,并按照红、白、蓝的顺序进行排序.

我们可以使用整数 0,1 和 2 分别代表红,白,蓝.

### 样例

***样例 1***

```
输入 : [1, 0, 1, 2]
输出 : [0, 1, 1, 2]
解释 : 原地排序.
```

### 挑战

一个相当直接的解决方案是使用计数排序扫描2遍的算法.

首先,迭代数组计算 0,1,2 出现的次数,然后依次用 0,1,2 出现的次数去覆盖数组.

你否能想出一个仅使用常数级额外空间复杂度且只扫描遍历一遍数组的算法？

### 注意事项

不能使用代码库中的排序函数来解决这个问题.
排序需要在原数组中进行.

```cpp
bool cmp(int a,int b){
    if(a<b){
        return true;
    }
    else{
        return false;
    }
}
class Solution {
public:
    /**
     * @param nums: A list of integer which is 0, 1 or 2 
     * @return: nothing
     */
    void sortColors(vector<int> &nums) {
        sort(nums.begin(),nums.end(),cmp);
    }
};
```

# 156. 合并区间

给出若干闭合区间,合并所有重叠的部分.

### 样例

**样例1:**

```
输入: [(1,3)]
输出: [(1,3)]
```

**样例 2:**

```
输入:  [(1,3),(2,6),(8,10),(15,18)]
输出: [(1,6),(8,10),(15,18)]
```

### 挑战

O(*n* log *n*) 的时间和 O(1) 的额外空间.

```cpp
class Solution {
public:
	/**
	 * @param intervals: interval list.
	 * @return: A new interval list.
	 */
	vector<Interval> merge(vector<Interval>& intervals) {
		if (intervals.size() == 1 or intervals.size() == 0) {
			return intervals;
		}
		Sort(intervals);
		vector<Interval>res;
		int left = intervals[0].start, right = intervals[0].end;
		for (int i = 1; i < intervals.size(); i++) {
			if (intervals[i].start < right and intervals[i].end>right) {
				right = intervals[i].end;
			}
			else if (intervals[i].start > right) {
				Interval temp(left, right);
				res.push_back(temp);
				left = intervals[i].start;
				right = intervals[i].end;
			}
			else if (intervals[i].start == right and left<intervals[i].end) {
				right = intervals[i].end;
			}
			if (i == intervals.size() - 1) {
				Interval temp(left, right);
				res.push_back(temp);
			}
		}
		return res;
	}
	void Sort(vector<Interval>& intervals) {
		for (int i = 0; i < intervals.size(); i++) {
			for (int j = 0; j < intervals.size() - 1 - i; j++) {
				if (intervals[j].start > intervals[j + 1].start) {
					swap(intervals[j], intervals[j + 1]);
				}
			}
		}
	}
};
```

# 157. 判断字符串是否没有重复字符

实现一个算法确定字符串中的字符是否均唯一出现

### 样例

**样例 1:**

```
输入:  "abc_____"
输出:  false
```

**样例 2:**

```
输入:  "abc"
输出:  true	
```

### 挑战

如果不使用额外的存储空间,你的算法该如何改变？

输入测试数据(每行一个参数)如何理解测试数据？

```cpp
class Solution {
public:
    /*
     * @param str: A string
     * @return: a boolean
     */
    bool isUnique(string &str) {
		char ascii[128] = { 0 };
		for (int i = 0; i < str.size(); i++) {
			if (ascii[str[i]] == 0) {
				ascii[str[i]] = 1;
			}
			else {
				return false;
			}
		}
		return true;
    }
};
```

# 158. 两个字符串是变位词

写出一个函数 `anagram(s, t)` 判断两个字符串是否可以通过改变字母的顺序变成一样的字符串.

### 样例

**样例 1:**

```
输入: s = "ab", t = "ab"
输出: true
```

**样例 2:**

```
输入:  s = "abcd", t = "dcba"
输出: true
```

**样例 3:**

```
输入:  s = "ac", t = "ab"
输出: false
```

### 挑战

O(n) 的时间复杂度, O(1) 的额外空间

### 说明

什么是 **Anagram**?

-    在更改字符顺序后两个字符串可以相同

```cpp
class Solution {
public:
    /**
     * @param s: The first string
     * @param t: The second string
     * @return: true or false
     */
    bool anagram(string &s, string &t) {
        sort(s.begin(),s.end());
        sort(t.begin(),t.end());
        if(s==t){
            return true;
        }
        else{
            return false;
        }
    }
};
```

# 165. 合并两个排序链表

描述

将两个排序(升序)链表合并为一个新的升序排序链表

样例

```
样例 1:
	输入: list1 = null, list2 = 0->3->3->null
	输出: 0->3->3->null


样例2:
	输入:  list1 =  1->3->8->11->15->null, list2 = 2->null
	输出: 1->2->3->8->11->15->null
```

```cpp
/**
 * Definition of singly-linked-list:
 * class ListNode {
 * public:
 *     int val;
 *     ListNode *next;
 *     ListNode(int val) {
 *        this->val = val;
 *        this->next = NULL;
 *     }
 * }
 */

class Solution {
public:
    /**
     * @param l1: ListNode l1 is the head of the linked list
     * @param l2: ListNode l2 is the head of the linked list
     * @return: ListNode head of linked list
     */
    ListNode * mergeTwoLists(ListNode * l1, ListNode * l2) {
        if(l1==NULL){
            return l2;
        }
        if(l2==NULL){
            return l1;
        }
        if(l1->val<l2->val){
            return sort(l1,l2);
        }
        else{
            return sort(l2,l1);
        }
    }

    ListNode * sort(ListNode * l1, ListNode * l2){
        ListNode*res=l1;
        ListNode*run=l1;
        l1=l1->next;
        do{
            if(l1->val<l2->val){
                run->next=l1;
                run=run->next;
                if(l1->next!=NULL){
                    l1=l1->next;
                }
                else{
                    run->next=l2;
                    break;
                }
            }
            else{
                run->next=l2;
                run=run->next;
                if(l2->next!=NULL){
                    l2=l2->next;
                }
                else{
                    run->next=l1;
                    break;
                }
            }   
        }while(1);
        return res;
    }
};
```



# 167. 链表求和

你有两个用链表代表的整数,其中每个节点包含一个数字.数字存储按照在原来整数中`相反`的顺序,使得第一个数字位于链表的开头.写出一个函数将两个整数相加,用链表形式返回和.

### 样例

**样例 1:**

```
输入: 7->1->6->null, 5->9->2->null
输出: 2->1->9->null	
样例解释: 617 + 295 = 912, 912 转换成链表:  2->1->9->null
```

**样例 2:**

```
输入:  3->1->5->null, 5->9->2->null
输出: 8->0->8->null	
样例解释: 513 + 295 = 808, 808 转换成链表: 8->0->8->null
```

```cpp
/**
 * Definition of singly-linked-list:
 * class ListNode {
 * public:
 *     int val;
 *     ListNode *next;
 *     ListNode(int val) {
 *        this->val = val;
 *        this->next = NULL;
 *     }
 * }
 */

class Solution {
public:
    /**
     * @param l1: the first list
     * @param l2: the second list
     * @return: the sum list of l1 and l2 
     */
    ListNode * addLists(ListNode * l1, ListNode * l2) {
		ListNode* result = nullptr, ** prev = &result;
		for (int carry = 0; l1 || l2 || carry;) {
			if (l1) {
				carry += l1->val;
				l1 = l1->next;
			}
			if (l2) {
				carry += l2->val;
				l2 = l2->next;
			}
			*prev = new ListNode(carry % 10);
			prev = &((*prev)->next);
			carry /= 10;
		}
		return result;
    }
};
```

# 172. 删除元素

给定一个数组和一个值,在原地删除与值相同的数字,返回新数组的长度.

元素的顺序可以改变,并且对新的数组不会有影响.

### 样例

给出一个数组 **[0,4,4,0,0,2,4,4]**,和值 4

返回 4 并且4个元素的新数组为**[0,0,0,2]**

```cpp
class Solution {
public:
    /*
     * @param A: A list of integers
     * @param elem: An integer
     * @return: The new length after remove
     */
    int removeElement(vector<int> &A, int elem) {
		for (int i = 0; i < A.size();) {
			if (A[i] == elem) {
				A.erase(A.begin() + i);
			}
			else {
				i++;
			}
		}
		return A.size();
    }
};
```

# 181. 将整数A转换为B

如果要将整数n转换为m,需要改变多少个bit位？

### 样例

```
样例 1:
	输入: n = 31, m = 14
	输出:  2
	
	解释:
	(11111) -> (01110) 需要改变两个位.


样例 2:
	输入: n = 1, m = 7
	输出:  2
	
	解释:
	(001) -> (111) 需要更改两位
```

### 注意事项

*n*和*m*均为32位整数.

```cpp
class Solution {
public:
    /**
     * @param a: An integer
     * @param b: An integer
     * @return: An integer
     */
	int bitSwapRequired(int a, int b) {
		vector<int>binarya(32, 0), binaryb(32, 0);
		if (a >= 0) {
			int i = 0;
			while (a != 0) {
				binarya[i] = a % 2;
				i++;
				a /= 2;
			}
		}
		else {
			a = abs(a);
			int i = 0;
			while (a != 0) {
				binarya[i] = a % 2;
				i++;
				a /= 2;
			}
			for (int j = 0; j < binarya.size(); j++) {
				if (binarya[j] == 0) {
					binarya[j] = 1;
				}
				else {
					binarya[j] = 0;
				}
			}
			for (int k = 0; k < binarya.size(); ++k) {
				if (binarya[k] == 0) {
					binarya[k] = 1;
					break;
				}
				else {
					binarya[k] = 0;
				}
			}
		}
		if (b >= 0) {
			int i = 0;
			while (b != 0) {
				binaryb[i] = b % 2;
				i++;
				b /= 2;
			}
		}
		else {
			b = abs(b);
			int i = 0;
			while (b != 0) {
				binaryb[i] = b % 2;
				i++;
				b /= 2;
			}
			for (int j = 0; j < binaryb.size(); j++) {
				if (binaryb[j] == 0) {
					binaryb[j] = 1;
				}
				else {
					binaryb[j] = 0;
				}
			}
			for (int k = 0; k < binaryb.size(); ++k) {
				if (binaryb[k] == 0) {
					binaryb[k] = 1;
					break;
				}
				else {
					binaryb[k] = 0;
				}
			}
		}
		int res = 0;
		for (int i = 0; i < 32; i++) {
			if (binarya[i] != binaryb[i]) {
				++res;
			}
		}
		return res;
	}
};
```

# 185.  矩阵的之字型遍历

描述

给你一个包含 *m* x *n* 个元素的矩阵 (*m* 行, *n* 列), 求该矩阵的之字型遍历.

样例

```
样例 1:
	输入: [[1]]
	输出:  [1]

样例 2:
	输入:   
	[
    [1, 2,  3,  4],
    [5, 6,  7,  8],
    [9,10, 11, 12]
  ]

	输出:  [1, 2, 5, 9, 6, 3, 4, 7, 10, 11, 8, 12]
```

```cpp
class Solution {
public:
    /**
     * @param matrix: An array of integers
     * @return: An array of integers
     */
    vector<int> printZMatrix(vector<vector<int>> &matrix) {
        vector<int>ret;
        if(matrix.empty()||matrix[0].empty()){
            return ret;
        }
        int n=matrix.size(),m=matrix[0].size();
        int i,j;
        for(int s=0;s<=n+m-2;++s){
            if(s%2!=0){
                for(j=min(s,m-1),i=s-j;i<n and i>=0 and j<m and j>=0;++i,--j){
                    ret.push_back(matrix[i][j]);
                }
            }
            else{
                for(i=min(s,n-1),j=s-i;i>=0 and i<n and j>=0 and j<m;--i,++j){
                    ret.push_back(matrix[i][j]);
                }
            }
        }
        return ret;
    }
};
```



# 188. 插入五

给定一个数字,在数字的任意位置插入一个5,使得插入后的这个数字最大

### 样例

**样例 1:**

```
输入:  a = 234
输出: 5234	
```

### 注意事项

|a| \leq 10^6∣*a*∣≤10^6

```cpp
class Solution {
public:
    /**
     * @param a: A number
     * @return: Returns the maximum number after insertion
     */
	int InsertFive(int a) {
		if (a > 0) {
			vector<int>num;
			while (a != 0) {
				num.push_back(a % 10);
				a /= 10;
			}
			size_t numsize = num.size();
			bool add = false;
			for (int i = numsize - 1; i >= 0; --i) {
				if (num[i] < 5) {
					num.insert(num.begin() + i + 1, 5);
					add = true;
					break;
				}
			}
			if (!add) {
				num.push_back(5);
			}
			int sum = 0;
			numsize = num.size();
			for (int i = 0; i < numsize; ++i) {
				sum += num[i] * pow(10, i);
			}
			return sum;
		}
		else if(a<0){
			a = abs(a);
			vector<int>num;
			while (a != 0) {
				num.push_back(a % 10);
				a /= 10;
			}
			size_t numsize = num.size();
			bool add = false;
			for (int i = numsize - 1; i >= 0; --i) {
				if (num[i] > 5) {
					num.insert(num.begin() + i + 1, 5);
					add = true;
					break;
				}
			}
			if (!add) {
				num.push_back(5);
			}
			int sum = 0;
			numsize = num.size();
			for (int i = 0; i < numsize; ++i) {
				sum += num[i] * pow(10, i);
			}
			return -1 * sum;
		}
		else {
			return 50;
		}
	}
};
```

# 309.  交叉数组

描述

给定两个相同长度的数组,通过取第一个数组的第一个元素,第二个数组的第一个元素,第一个数组的第二个元素...依此类推来交叉它们.返回新的交错数组.
注意 ： 长度 ≤ 10000

样例

```
输入: 
[1,2]
[3,4]
输出: 
[1,3,2,4]
```

```cpp
class Solution {
public:
    /**
     * @param A: the array A
     * @param B: the array B
     * @return: returns an alternate array of arrays A and B.
     */
    vector<int> interleavedArray(vector<int> &A, vector<int> &B) {
        vector<int>res;
        if(A.size()==0){
            return res;
        }
        else{
            size_t size= A.size();
            for(int i=0;i<size;i++){
                res.push_back(A[i]);
                res.push_back(B[i]);
            }
        }
        return res;
    }
};
```

# 334. 队列检查

描述

班上的学生根据他们的年级照片的身高升序排列,确定当前未站在正确位置的学生人数

1<= len(heights) <=10^51<=*l**e**n*(*h**e**i**g**h**t**s*)<=1051<= heights[i] <= 10^91<=*h**e**i**g**h**t**s*[*i*]<=109

样例

```
	输入:  heights = [1,1,3,3,4,1]
	输出: 3
	解释:  经过排序后 heights变成了[1,1,1,3,3,4],有三个学生不在应在的位置上
```

```cpp
bool cmp(int x,int y){
    if(x<y){
        return true;
    }
    else{
        return false;
    }
}
class Solution {
public:
    /**
     * @param heights: Students height
     * @return: How many people are not where they should be
     */
    int orderCheck(vector<int> &heights) {
        int res=0;
        vector<int>count(heights);
        sort(count.begin(),count.end(),cmp);
        for(int i=0;i<count.size();i++){
            if(count[i]!=heights[i]){
                res++;
            }
        }
        return res;
    }
};
```

# 376. 二叉树的路径和

描述

给定一个二叉树,找出所有路径中各节点相加总和等于给定 `目标值` 的路径.

一个有效的路径,指的是从根节点到叶节点的路径.

样例

**样例1:**

```
输入:
{1,2,4,2,3}
5
输出: [[1, 2, 2],[1, 4]]
说明:
这棵树如下图所示：
	     1
	    / \
	   2   4
	  / \
	 2   3
对于目标总和为5,很显然1 + 2 + 2 = 1 + 4 = 5
```

**样例2:**

```
输入:
{1,2,4,2,3}
3
输出: []
说明:
这棵树如下图所示：
	     1
	    / \
	   2   4
	  / \
	 2   3
注意到题目要求我们寻找从根节点到叶子节点的路径.
1 + 2 + 2 = 5, 1 + 2 + 3 = 6, 1 + 4 = 5 
这里没有合法的路径满足和等于3.
```

```
/**
 * Definition of TreeNode:
 * class TreeNode {
 * public:
 *     int val;
 *     TreeNode *left, *right;
 *     TreeNode(int val) {
 *         this->val = val;
 *         this->left = this->right = NULL;
 *     }
 * }
 */


class Solution {
public:
    /*
     * @param root: the root of binary tree
     * @param target: An integer
     * @return: all valid paths
     */
    vector<vector<int>> binaryTreePathSum(TreeNode * root, int target) {
        vector<vector<int>> res;
        if (root == NULL){
            return res;
        }
        vector<int> path;
        dfs(root, target, path, res);
        return res;
    }

private:
    void dfs(TreeNode* root, int target, vector<int>& path, vector<vector<int>>& res){
        // 空节点
        if (root == NULL){
            return;
        }
        path.push_back(root -> val);
        // 叶节点
        if (root -> left == NULL && root -> right == NULL){
            if (target == root -> val){
                res.push_back(vector<int>(path)); // 新的内存
            }
            path.pop_back(); // 原内存
            return;
        }
        // 非叶节点
        dfs(root -> left, target - root -> val, path, res);
        dfs(root -> right, target - root -> val, path, res);
        path.pop_back();
    }
};
```



# 402. 连续子数组求和

给定一个整数数组,请找出一个连续子数组,使得该子数组的和最大.输出答案时,请分别返回第一个数字和最后一个数字的下标.(如果存在多个答案,请返回字典序最小的)

### 样例

**样例 1:**

```
输入: [-3, 1, 3, -3, 4]
输出: [1, 4]
```

**样例 2:**

```
输入: [0, 1, 0, 1]
输出: [0, 3]
解释: 字典序最小.
```

```cpp
class Solution {
public:
    /*
     * @param A: An integer array
     * @return: A list of integers includes the index of the first number and the index of the last number
     */
    vector<int> continuousSubarraySum(vector<int> &A) {
        vector<int>res(2,0);
        int n=A.size();
        int res_sum=A[0];
        int sum=0;
        int l=0;
        for(int r=0;r<n;r++){
            if(sum<0){
                l=r;
                sum=A[r];
            }
            else{
                sum+=A[r];
            }
            if(sum>res_sum){
                res_sum=sum;
                res[0]=l;
                res[1]=r;
            }
        }
        return res;
    }
};
```

# 408. 二进制求和

给定两个二进制字符串,返回他们的和(用二进制表示).

### 样例

**样例 1：**

```
输入：
a = "0", b = "0"
输出：
"0"
```

**样例 2：**

```
输入：
a = "11", b = "1"
输出：
"100"
```

```cpp
class Solution {
public:
    /**
     * @param a: a number
     * @param b: a number
     * @return: the result
     */
    string addBinary(string &a, string &b) {
		int size=max(a.size(),b.size());
		string res;
		reverse(a.begin(),a.end());
		reverse(b.begin(),b.end());
		int carry=0;
		for(int i=0;i<size;i++){
			int tempa,tempb;
			if(i<a.size()){
				tempa=a[i]-'0';
			}
			else{
				tempa=0;
			}
			if(i<b.size()){
				tempb=b[i]-'0';
			}
			else{
				tempb=0;
			}
			int sum=carry+tempa+tempb;
			carry=0;
			if(sum>=2){
				carry=1;
				sum-=2;
			}
			res.push_back(sum+'0');
		}
		if(carry==1){
			res.push_back('1');
		}
		reverse(res.begin(),res.end());
		return res;
    }
};
```

## 402. 删除链表中的元素

描述

删除链表中等于给定值 `val` 的所有节点.

样例

**样例 1：**

```
输入：head = 1->2->3->3->4->5->3->null, val = 3
输出：1->2->4->5->null
```

**样例 2：**

```
输入：head = 1->1->null, val = 1
输出：null
```

```cpp
/**
 * Definition of singly-linked-list:
 * class ListNode {
 * public:
 *     int val;
 *     ListNode *next;
 *     ListNode(int val) {
 *        this->val = val;
 *        this->next = NULL;
 *     }
 * }
 */

class Solution {
public:
    /**
     * @param head: a ListNode
     * @param val: An integer
     * @return: a ListNode
     */
    ListNode * removeElements(ListNode * head, int val) {
        if(head==NULL){
            return NULL;
        }
        ListNode*befor=NULL;
        ListNode*temp;
        for(temp=head;temp!=NULL;){
            if(temp->val==val){
                if(befor==NULL){
                    head=head->next;
                    if(head==NULL){
                        return NULL;
                    }
                    temp=temp->next;
                }
                else{
                    temp=temp->next;
                }
            }
            else{
                if(befor==NULL){
                    befor=head;
                }
                else{
                    befor->next=temp;
                    befor=temp;
                }
                temp=temp->next;
            }
        }
        befor->next=NULL;
        return head;
    }
};
```

# 551.  嵌套列表的加权和

描述

给一个嵌套的整数列表, 返回列表中所有整数由它们的深度加权后的总和. 每一个元素可能是一个整数或一个列表(其元素也可能是整数或列表)

样例

例1:

```
输入: the list [[1,1],2,[1,1]], 
输出: 10. 
解释:
four 1's at depth 2, one 2 at depth 1, 4 * 1 * 2 + 1 * 2 * 1 = 10
```

例2:

```
输入: the list [1,[4,[6]]], 
输出: 27. 
解释:
one 1 at depth 1, one 4 at depth 2, and one 6 at depth 3; 1 + 4 * 2 + 6 * 3 = 27
```

```cpp
/**
 * // This is the interface that allows for creating nested lists.
 * // You should not implement it, or speculate about its implementation
 * class NestedInteger {
 *   public:
 *     // Return true if this NestedInteger holds a single integer,
 *     // rather than a nested list.
 *     bool isInteger() const;
 *
 *     // Return the single integer that this NestedInteger holds,
 *     // if it holds a single integer
 *     // The result is undefined if this NestedInteger holds a nested list
 *     int getInteger() const;
 *
 *     // Return the nested list that this NestedInteger holds,
 *     // if it holds a nested list
 *     // The result is undefined if this NestedInteger holds a single integer
 *     const vector<NestedInteger> &getList() const;
 * };
 */
class Solution {
private:
    int sum=0,depth=1;
public:
    int depthSum(const vector<NestedInteger>& nestedList) {
        for(auto i:nestedList){
            if(i.isInteger()){
                sum+=i.getInteger()*depth;
            }
            else{
                depth++;
                depthSum(i.getList());
                depth--;
            }
        }
        return sum;
    }
};
```

# 987.  具有交替位的二进制数

描述

给一个正整数,检查它的二进制表示是否具有交替位.即,两个相邻的位总是具有不同的值.

样例

**样例 1:**

```
输入: 5
输出: True
解释:
5 的二进制表示为: 101
```

**样例 2:**

```
输入: 7
输出: False
解释:
7 的二进制表示为: 111.
```

**样例 3:**

```
输入: 11
输出: False
解释:
11 的二进制表示为: 1011.
```

**样例 4:**

```
输入: 10
输出: True
解释:
10 的二进制表示: 1010.
```

```cpp
class Solution {
public:
    /**
     * @param n: a postive Integer
     * @return: if two adjacent bits will always have different values
     */
    bool hasAlternatingBits(int n) {
        vector<int>count;
        while(n!=0){
            count.push_back(n%2);
            n/=2;
        }
        if(count[0]==0){
            for(int i=1;1;1){
                if(i<count.size()){
                    if(count[i]==1){
                        i++;
                    }
                    else{
                        return false;
                    }
                }
                else{
                    break;
                }
                if(i<count.size()){
                    if(count[i]==0){
                        i++;
                    }
                    else{
                        return false;
                    }
                }
                else{
                    break;
                }
            }
            return true;
        }
        else{
            for(int i=1;1;1){
                if(i<count.size()){
                    if(count[i]==0){
                        i++;
                    }
                    else{
                        return false;
                    }
                }
                else{
                    break;
                }
                if(i<count.size()){
                    if(count[i]==1){
                        i++;
                    }
                    else{
                        return false;
                    }
                }
                else{
                    break;
                }
            }
            return true;
        }
    }
};
class Solution2 {
public:
    /**
     * @param n: a postive Integer
     * @return: if two adjacent bits will always have different values
     */
    bool hasAlternatingBits(int n) {
        bool sign;
        if(n%2==0){
            sign=true;
            n/=2;
            while(n!=0){
                if(sign==true){
                    if(n%2!=0){
                        n/=2;
                        sign=false;
                    }
                    else{
                        return false;
                    }
                }
                else{
                    if(n%2==0){
                        n/=2;
                        sign=true;
                    }
                    else{
                        return false;
                    }
                }
            }
            return true;
        }
        else{
            sign=false;
            n/=2;
            while(n!=0){
                if(sign==false){
                    if(n%2==0){
                        n/=2;
                        sign=true;
                    }
                    else{
                        return false;
                    }
                }
                else{
                    if(n%2!=0){
                        n/=2;
                        sign=false;
                    }
                    else{
                        return false;
                    }
                }
            }
            return true;
        }
    }
};
```

# 988.  硬币摆放

描述

你有 n 枚硬币,想要摆放成阶梯形状,即第 k 行恰好有 k 枚硬币.

给出 n,找到可以形成的**完整**楼梯行数.

n 是一个非负整数,且在32位有符号整数范围内.

样例

**样例 1:**

```
输入：n = 5
输出：2
解释：
硬币可以形成以下行：
¤
¤ ¤
¤ ¤
因为第3行不完整,我们返回2.
```

**样例 2:**

```
输入：n = 8
输出：3
解释：
硬币可以形成以下行：
¤
¤ ¤
¤ ¤ ¤
¤ ¤
因为第4行不完整,我们返回3.
```

```cpp
class Solution {
public:
    /**
     * @param n: a non-negative integer
     * @return: the total number of full staircase rows that can be formed
     */
    int arrangeCoins(int n) {
        int res=1,sum=0;
        while(1){
            sum+=res;
            if(sum<=n){
                res++;
            }
            else{
                return res-1;
            }
        }
    }
};
```

# 1013. 独特的摩尔斯编码

描述

摩尔斯电码定义了一种标准编码,把每个字母映射到一系列点和短划线,例如：`a` -> `.-`,`b` -> `-...`,`c` ->`-.-.`.

给出26个字母的完整编码表格：

```
[".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
```

现在给定一个单词列表,每个单词中每个字母可以写成摩尔斯编码. 例如,`cab`可以写成`-.-.-....-`,(把`c`,`a`,`b`的莫尔斯编码串接起来). 我们称之为一个词的转换.

返回所有单词中不同变换的数量.

`words`的长度最多为`100`.每一个`words[i]`的长度范围为`[1, 12]`.`words[i]`仅仅包含小写字母.

样例

**样例1：**

```
输入: words = ["gin", "zen", "gig", "msg"]
输出: 2
解释: 
每一个单词的变换是:
"gin" -> "--...-."
"zen" -> "--...-."
"gig" -> "--...--."
"msg" -> "--...--."

这里有两种不同的变换结果： "--...-."和"--...--.".
```

**样例2：**

```
输入: words = ["a", "b"]
输出: 2
解释: 
每一个单词的变换是:
"a" -> ".-"
"b" -> "-..."
这里有两种不同的变换结果：".-" and "-...".
```

```cpp
class Solution {
public:
    /**
     * @param words: the given list of words
     * @return: the number of different transformations among all words we have
     */
    int uniqueMorseRepresentations(vector<string> &words) {
        string cnt[]={".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."};
        set<string> coll;
        for(string item:words){
            string tmp;
            for(int i=0;i<item.size();++i){
                tmp+=cnt[item[i]-'a'];
            }
            coll.insert(tmp);
        }
        return coll.size();
    }
};
```

# 1029. 寻找最便宜的航行旅途(最多经过k个中转站)

描述

有n个城市被一些航班所连接.每个航班 (u,v,w) 从城市u出发,到达城市v,价格为w.

给定城市数目 `n`,所有的航班`flights`.你的任务是找到从起点`src`到终点站`dst`的最便宜线路的价格,而旅途中最多只能中转`K`次.

如果没有找到合适的线路,返回 `-1`.

总城市数 `n` 在 1-100 之间,每个城市被标号为 0 到 n-1.航线的总数在 0 到 n * (n - 1) / 2 之间每条航线会被以 [出发站,终点站,价格] 的形式展现.每条航线的价格都在 1-10000之间.中转站的总数限制范围为 0 到 n-1 之间.不会有重复或者自环航线出现

样例

**样例 1:**

```
输入: 
  n = 3,
  flights = [[0,1,100],[1,2,100],[0,2,500]],
  src = 0, dst = 2, K = 0
输出: 500
```

**样例 2:**

```
输入: 
  n = 3,
  flights = [[0,1,100],[1,2,100],[0,2,500]],
  src = 0, dst = 2, K = 1
输出: 200
```

```cpp
class Solution {
public:
    /**
     * @param n: a integer
     * @param flights: a 2D array
     * @param src: a integer
     * @param dst: a integer
     * @param K: a integer
     * @return: return a integer
     */
    int findCheapestPrice(int n, vector<vector<int>> &flights, int src, int dst, int K) {
        
        unordered_map<int, vector<int>> outdegrees;
        
        for (int i = 0; i < flights.size(); ++i) {
            outdegrees[flights[i][0]].push_back(i);
        }
        
        queue<pair<int, int>> que; //flight and money

        int k = 0, ans = INT_MAX;
        
        for (int i = 0; i < outdegrees[src].size(); ++i) {
            que.push(make_pair(outdegrees[src][i], 0));
        }
        
        unordered_map<int, int> memo;
        
        while (!que.empty() && k <= K) {
            int size = que.size();
            for (int i = 0; i < size; ++i) {
                int curr_f = que.front().first;
                int start = flights[curr_f][0];
                int end = flights[curr_f][1];
                int curr_mon = que.front().second + flights[curr_f][2];
                que.pop();
                if (memo.find(end) == memo.end()) {
                    memo[end] = curr_mon;
                }
                else {
                    if (memo[end] <= curr_mon) {
                        continue;
                    }
                    memo[end] = curr_mon;
                }
                if (end == dst) {
                    ans = min(ans, curr_mon);
                }
                for (int j = 0; j < outdegrees[end].size(); ++j) {
                    que.push(make_pair(outdegrees[end][j], curr_mon));
                }
            }
            k++;
        }
        
        return ans == INT_MAX ? -1 : ans;
    }
};
```

# 1033. BST中的最小差值

描述

给定一个确定根的二叉搜索树,返回树中任意两个不同节点的值的最小差.

1.这棵二叉搜索树的大小在 2 到`100`之间.
2.这棵二叉搜索树是存在的,每个点的数值是一个整数,而且每个点的数值将会是不同的.

样例

**样例1:**

```
输入: root = {4,2,6,1,3,#,#}
输出: 1
解释:
请留意,root是一个树节点的结构,而非一个普通数组.

给定的树{4,2,6,1,3,#,#}的样子如下图：

          4
        /   \
      2      6
     / \    
    1   3  

在这棵树中,最小数值差距为 1, 它出现在node 1 与 node 2 之间, 也同时存在 node 3 与 node 2之间
```

**样例2:**

```
输入: root = {5,1,8}
输出: 3
解释:
请留意,root是一个树节点的结构,而非一个普通数组.

给定的树{5,1,8}的样子如下图：

     5
   /   \
 1      8
 
在这棵树中,最小数值差距为 3, 它出现在node 5与node 8之间.
```

```cpp
/**
 * Definition of TreeNode:
 * class TreeNode {
 * public:
 *     int val;
 *     TreeNode *left, *right;
 *     TreeNode(int val) {
 *         this->val = val;
 *         this->left = this->right = NULL;
 *     }
 * }
 */

class Solution {
public:
    vector<int> nums;
    
    /**
     * @param root: the root
     * @return: the minimum difference between the values of any two different nodes in the tree
     */
    int minDiffInBST(TreeNode *root) {
        // Write your code here
        traverse(root);
        int ret = INT_MAX;
        sort(nums.begin(), nums.end());
        for (int i = 1; i < nums.size(); i++) {
            ret = min(ret, nums[i] - nums[i - 1]);
        }
        return ret;
    }


    void traverse(TreeNode *root) {
        if (root != NULL) {
            nums.push_back(root->val);
            traverse(root->left);
            traverse(root->right);
        }
    }
};
```

# 1148. 最长和谐子序列

描述

我们将一个和谐数组定义为是其最大值和最小值之间的差值恰好为1的数组.

现在,给定一个整数数组,您需要在其所有可能的子序列中找到其最长的和谐子序列的长度.

输入数组的长度不会超过20,000.

样例

```
输入：[1,3,2,2,5,2,3,7]
输出：5
解释：最长的和谐子序列是[3,2,2,2,3].
```

```cpp
class Solution {
public:
    /**
     * @param nums: a list of integers
     * @return: return a integer
     */
    int findLHS(vector<int> &nums) {
        map<int,int>count;
        int ans=0;
        for(auto num:nums){
            count[num]++;
        }
        for(auto num:nums){
            if(count[num] and count[num-1]){
                ans=max(ans,count[num]+count[num-1]);
            }
        }
        return ans;
    }
};
```

# 1178. 学生出勤记录 I

描述

给定一个字符串表示学生出勤记录，记录仅由下列三个字符组成：

- **'A'** : 缺席（Absent）.
- **'L'** : 迟到（Late）.
- **'P'** : 到场（Present）.

如果学生的出勤情况不包含 **超过一个'A'(缺席)** 或者 **超过连续两个'L'(迟到)** ，那么他就应该受到奖励。

返回该学生是否会受到奖励。

样例

**样例 1:**

```
输入: "PPALLP"
输出: True
```

**样例 2:**

```
输入: "PPALLL"
输出: False
```

```cpp
class Solution {
public:
    /**
     * @param s: a string
     * @return: whether the student could be rewarded according to his attendance record
     */
    bool checkRecord(string &s) {
        int cntA = 0;
        int cntL = 0;
        for (char i : s) {
            if (i == 'A') {
                ++cntA;
                cntL = 0;
            } else if (i == 'L') {
                ++cntL;
                if (cntL > 2) {
                    return false;
                }
            } else {
                cntL = 0;
            }
        }
        if (cntA > 1) {
            return false;
        }
        return true;
    }
};
```

# 1587.  字符串切分

描述

现在有一个字符串,首字符代表一级分隔符,分隔不同的键值对key-value;第二个字符代表二级分隔符,分隔key和value;后面的字符串表示待处理的字符串.请给出所有的有效键值对.

有效键值对即key和value均不为空的键值对.
题目保证分隔符不为字母或数字,待处理的字符串中只包含两种分隔符：小写字母和数字,且两个一级分隔符中间最多只出现一个二级分隔符.
题目保证所给字符串长度不超过1000.

样例

#### 样例1

```
输入:"#:a:3#b:8#c:9"
输出:[["a","3"],["b","8"],["c","9"]]
```

#### 样例2

```
输入:"#:aa:3#b:853#:9"
输出:[["aa","3"],["b","853"]]
```

```cpp
class Solution {
public:
    /**
     * @param str: the string need to be processed
     * @return: all the valid key-value pairs.
     */
    vector<vector<string>> StringSeg(string &str) {
        vector<vector<string>> res;
        char split = str[0];
        char dive_split = str[1];
        str.erase(str.begin(), str.begin() + 2);
        while (str.size() != 0) {
            string temp_key_value;
            if (str.find(split) != string::npos) {
                temp_key_value = str.substr(0, str.find_first_of(split));
                str.erase(0, str.find_first_of(split) + 1);
            } else {
                temp_key_value = str;
                str = "";
            }
            string temp_key, temp_value;
            if (temp_key_value.find(dive_split) != string::npos) {
                temp_key = temp_key_value.substr(0, temp_key_value.find(dive_split));
                temp_value = temp_key_value.substr(temp_key_value.find(dive_split) + 1, string::npos);
                if (!temp_key.empty() and !temp_value.empty()) {
                    vector<string> temp_vec = {temp_key, temp_value};
                    res.push_back(temp_vec);
                }
            }
        }
        return res;
    }
};
```

# 1746. 二叉搜索树结点最小距离



给定一个二叉搜索树的根结点 root, 返回树中任意两节点的差的最小值.

### 样例

**样例 1:**

```
输入: root = {4,2,6,1,3}
输出: 1
解释:
注意,root是树结点对象(TreeNode object),而不是数组.

给定的树 [4,2,6,1,3,null,null] 可表示为下图:

          4
        /   \
      2      6
     / \    
    1   3  

最小的差值是 1, 它是节点1和节点2的差值, 也是节点3和节点2的差值.
```

**样例 2:**

```
输入: root = {2,1}
输出: 1
解释:
注意,root是树结点对象(TreeNode object),而不是数组.

给定的树 {2,1} 可表示为下图:

      2
     / 
    1 

最小的差值是 1, 它是节点1和节点2的差值.
```

### 注意事项

-    二叉树的大小范围在 2 到 100.
-    二叉树总是有效的,每个节点的值都是整数,且不重复.

```cpp
/**
 * Definition of TreeNode:
 * class TreeNode {
 * public:
 *     int val;
 *     TreeNode *left, *right;
 *     TreeNode(int val) {
 *         this->val = val;
 *         this->left = this->right = NULL;
 *     }
 * }
 */

class Solution {
public:
    int res=INT_MAX,pre=-1;
    /**
     * @param root:  a Binary Search Tree (BST) with the root node
     * @return: the minimum difference
     */
    int minDiffInBST(TreeNode * root) {
        if(root->left!=NULL){
            minDiffInBST(root->left);
        }
        if(pre>=0){
            res=min(res,root->val-pre);
        }
        pre=root->val;
        if(root->right!=NULL){
            minDiffInBST(root->right);
        }
        return res;
    }
};
```

