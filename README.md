# leetcoding

题目一：
公有云中某 3 个数据中心 11 月份产生的告警类型（整数）分别记录在3个数组： array1，array2 和 array3 中，并且严格递增排列。
请你找出 3 个数据中心产生的共性告警（即：在 3 个数组中都存在的告警类型），并按照升序排列返回。
 
示例：
输入:array1 = [1,2,3,4,5],array2 = [1,2,5,7,9],array3 = [1,3,4,5,8]
输出:[1,5]
解释:只有 1 和 5 同时在这三个数组中出现。
 
提示：
1 <= array1.length, array2.length, array3.length <= 1000
1 <= array1[i], array2[i], array3[i] <= 2000


题目二：

/*
* Definition for a binary tree node.
* struct TreeNode {
*     int val;
*     TreeNode *left;
*     TreeNode *right;
*     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
* };
*/
 
测试工程师正在测试某款新型扫地机器人。工程师设计了一个形如二叉树（根节点记为 root）的测试路径，扫地机器人自路径对应的根节点出发，
一直行进至路径尽头（即二叉树叶节点）。如果这个路口的左右子节点都非空，机器人选择左转或右转的概率相等；如果这个路口的左右子节点仅一侧非空，则机器人选择非空侧走。

工程师给每个路口标记了数字，并且仅在标记数字 target 的所有路口设置了监控摄像机。请问扫地机器人被监控至少拍到一次的概率是多少？
 
输入：root = [1,2,3,2,5,6,2], target = 2
输出：0.75
 
   1
 /  \
2    3
/\    /\
2  5  6  2
 
 
解释：数组按二叉树层次遍历的顺序记录了标记数字。从 1 出发，从左侧走到 2 的概率为 0.5（被拍到）, 从右侧走到 3 的概率为 0.5, 从 3 继续出发，走到 2 的概率为 0.5（被拍到），所以结果为 0.5 + 0.5 * 0.5 = 0.75
即：左侧分支被拍到的概率为 0.5（红色圈的 2 是 0.5，继续走到 2 或 5，不会增加被拍概率，也不会降低被拍概率），右侧分支被拍到的概率为 0.25（红色圈的 2），合计为 0.75
 
示例 2:
输入：root = [1,null,3,2,2], target = 2
输出：1.0
限制：1 <= 树的节点数 <= 10000

题目三：
根据输入字符串，按规则进行 TLV 编码。规则如下：
 
所有字符均为数字，则类型(T)为 1，进行5421压缩编码(下有解释），长度(L)和内容(V)用来描述编码后的二进制码流。
其他所有输入均按字符串处理，类型(T)为2，长度(L)和内容(V)用来描述该字符串，L和V中均不包括结束符。
输出为 TLV 字节码流，要求如下：
 
前 2 字节为类型（T），接下来 4 字节为长度（L），后续为内容（V）
字节序使用网络序（大端）

5421压缩编码：
 
指用 4 bit 来描述单个十进制数字，每个bit的权重分别为5/4/2/1
编码后每个字节可以描述两个十进制数字；奇数位数字，高位补 0 后参与编码
 
举例：
45 -> 0x48
456 -> 0x04 0x89
 
输入：
 
输入为单行字符串，不包含换行符。
 
用例保证输入字符串长度范围 [0,255]。
 
输出：
 
输出为码流字符串：
 
码流中每个字节由十六进制两位数表示，字母a-f小写
码流字节间，由单个空格分隔。行末无空格。
 
样例 1：
输入："456"
输出："00 01 00 00 00 02 04 89"
 
样例 2：
输入："abc"
输出："00 02 00 00 00 03 61 62 63"

题目四：
某实习生在我司实习期间，有 3 件关键事情要做：
1.	参加一个在线连载算法课程的学习：实习生通常在有课程未学习完成时就要学习，并规划每天学习 k 个章节。其更新情况以 [更新日,更新章节数] 的形式存在二维数组 update 中。若当天剩余可学章节不满 k 个，当天任务仅为学习剩余章节，不刷题。
2.	有时实习生需要回学校写论文：写论文期间无法继续学习在线课程。其返校的起止时间以 [返校起始时间,返校结束时间] 的形式记录在二维数组 out 中，用例数据保证out数组中无区间重合。
3.	刷题练习：实习生既不需要在校改论文，也无新的章节可学之时，就会在家自己刷题练习；刷题练习无需等到课程更新后开始。
该实习生想估算下，在算法课程最后一次更新之前，自己可以进行刷题练习的日期有哪些。请以列表形式按日期大小升序返回。
 
示例 1：
输入：k = 3, update = [[3,6],[0,5],[9,1]], out = [[3,5]]
输出：[2,8]
解释：实习生每天学习 3 节，
第 0 天，更新 5 节，学习 3 节， 剩余 2 节
第 1 天，无更新，学习 2 节， 剩余 0 节
第 2 天，无更新，学习 0 节， 剩余 0 节，在家刷题
第 3 天，更新 6 节，观看 0 节，剩余 6 节，在校改论文
第 4 天，更新 0 节，观看 0 节，剩余 6 节，在校改论文
第 5 天，更新 0 节，观看 0 节，剩余 6 节，在校改论文
第 6 天，更新 0 节，观看 3 节，剩余 3 节
第 7 天，更新 0 节，观看 3 节，剩余 0 节
第 8 天，更新 0 节，观看 0 节，剩余 0 节，在家刷题
第 9 天，更新 1 节，观看 1 节，剩余 0 节，最后一次更新
示例 2：
输入：k = 7, update = [[4,4],[2,4]], out = []
输出：[0,1,3]
 
提示：
•	1 <= update.length <= 10000
•	0 <= out.length <= 10000

某运营商客户要在一小镇新建一批基站，经过专家勘测得到一批适合建设基站的地点列表 positions，考虑到经济原因，需要从中找出距离小镇最近的 num 个点建立基站。
 *
 * 地点的坐标为平面坐标，小镇的坐标为原点 (0,0)。
 *
 * 输出：请返回符合要求的 num 个站点坐标的列表。
 *
 * 列表中的坐标可以按照任何顺序排列；
 * 用例会保证解是唯一的，不存在多个解。
 *
 *
 * 示例 1:
 *
 * 输入：positions = [[1,3],[-2,2]], num = 1
 * 输出：[[-2,2]]
 * 解释：
 * (1, 3) 和原点之间的距离为 sqrt(10)，10 = 1^2 + 3^2
 * (-2, 2) 和原点之间的距离为 sqrt(8)，8 = (-2)^2 + 2^2
 * (-2, 2) 比 (1, 3) 站点离原点的距离更近。
 * 我们只需要距离原点最近的 num = 1 个点，所以答案就是 [[-2,2]]。
 * 示例 2：
 *
 * 输入：positions = [[3,3],[5,-1],[-2,4]], num = 2
 * 输出：[[3,3],[-2,4]]
 * （答案 [[-2,4],[3,3]] 也会被接受。）
 *
 *
 * 提示：
 *
 * 1 <= num <= positions.length <= 10000
 * -10000 < positions[i][0] < 10000
 * -10000 < positions[i][1] < 10000
 *
 * @since 2019-12-20
 */
public class First {

    public int[][] numClosestPositions(int[][] positions, int num) {
    }
}

/**
 * 工作级第2题（40分）
 *
 * 某企业行业客户是高铁公司，其要在一条高铁线路的沿途安装一些摄像头，假设共有 n 个点需要安装，每个摄像头安装点的位置记录在 sites 数组中。在此线路的沿途设置了一些供给点（放置如工具或配件的小仓库），每个供给点的位置记录在 stores 数组中，用于放置一些这次安装摄像头所需的零配件。
 * 假设所有安装点（sites）和供给点（stores）都在一条数轴（原点为 0）上，为了方便安装工人走最近的距离拿到所需的工具或配件，请计算出距离每个安装点最近的供给点位置（如果找到多个符合要求的供给点，则返回距离数轴原点最近的那个即可），并返回这些供给点位置的列表。
 *
 * * 示例 1：
 *
 * 输入：stores = [1, 5, 20, 11, 16], sites = [5, 10, 18]
 * 输出：[5,11,16]
 * 解释：距离 5 最近的是 5
 * 距离 10 最近的是11
 * 距离 18 最近的是 16 和 20，取较小的 16。
 * 示例 2：
 *
 * 输入：stores = [1, 5], sites = [5, 10, 18]
 * 输出：[5,5,5]
 *
 *
 * 限制：
 *
 * 1<= m, n <= 50000
 *
 * 1 <= stores[i] <= 1e9
 *
 * 1 <= sites[i] <= 1e9
 
public class Second {
    public int[] closest(int[] stores, int[] sites) {
    }
}


* 公司 IT 防攻击小组在做一次专项分析，由于受到干扰，本应接收到的一组 ip 地址（IPv4）信息被合并成一条长信息且缺失了部分内容。为了判断缺失情况，请你帮忙解析出字符串 str 形式的长信息中所有合法 ip 地址的个数，解析出的相同地址需要进行去重。
 *
 * 假设 IPv4 合法地址的规则如下：
 *
 * 采用 "." 分隔成四个字段，每个字段采用十进制记录。
 * 每个字段的值范围为：[0,255]
 * 每个字段的值除了 0 外，其他情况首位不可为 0。如：0.0.0.0 合法，0.01.0.1 不合法。
 *
 *
 * 示例 1：
 *
 * 输入：str = "1.1.1111.16..172.16.254.1.1"
 * 输出：5
 * 解释：字符串 str 可能被分为："172.16.254.1", "72.16.254.1", "2.16.254.1", "16.254.1.1", "6.254.1.1"
 *
 *
 * 示例 2：
 *
 * 输入：str = "1.2.3.04"
 * 输出：1
 * 解释：字符串 str 只可能被分为 "1.2.3.0"
 *
 *
 * 限制：
 *
 * 字符串长度 <= 100000
 *
 * 字符串由数字（’0’ - ‘9’）以及 ‘.’ 组成
 *
 * @since 2019-12-20
 */
public class Third {

    public int validNum(String str) {
    }

