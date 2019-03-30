# Week_1 

## Algorithm

1. 两数之和
思路：
第一时间能想到的是暴力循环，时间复杂度O(n^2) 空间复杂度O(1)

```
 
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length - 1; i++)
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[] { i, j };
                }
            }
        return null;
    }
}

```
学习了别人使用哈希表后，1.利用哈希表查找，2.空间换时间，时间复杂度为O(n) 空间复杂度O(n)

```
class Solution {
    public int[] twoSum(int[] nums, int target)
    {
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        for(int i=0; i<nums.length; i++)
        {
            if(map.containsKey(target - nums[i]) && map.get(target - nums[i]) != i)
            {
                return new int[] {map.get(target - nums[i]), i};
            }
            map.put(nums[i], i);
        }
        return null;
    }
}
```
    
## Review 
[Music Genre Classification with Python](https://towardsdatascience.com/music-genre-classification-with-python-c714d032f0d8)


几乎每天都要听虾米，QQ音乐，也经常使用里面的智能推荐功能。这篇文章就是讲机器学习音乐分析上的运用。选这篇阅读就是为了满足自己的好奇心。

## Tip 
z.lua
经常在终端下工作的同学应该都体会过，当需要来回在不同目录切换的时候，不停cd是多么让人崩溃的一件事。最近发现的这个“神器”终于可以解放那些需要不断cd的同学了。
z.lua追踪你在在shell下访问过的路径，通过一套Frecent的机制，匹配到Frecent值最高的那条路径上去。
基本使用： 
cd到一个包含到 foo 的目录： z foo
cd到一个以foo结尾的目录：z foo$
交互选择多个匹配结果： z -i foo
快速返回父目录：z -b (项目标志，关键字，替换当前）..退1层 ...退2层 ....退3层 ..n退n层
最近常去的目录：z -- z - z -n

awk & sed 
因为耗子哥最近更新的文章，决定重新学习下awk和sed两个linux下的神器
具体的内容这里就不贴出来了

## Share 
重新认识linux下的容器

1.容器，其实是一种特殊的进程而已
在宿主机上和其他的进程并没有什么本质的不同，都是由宿主机的操作系统统一管理。
只是拥有额外设置的Namespace参数

2.容器的隔离，使用Namespace技术，修改应用进程看整个计算机的“视图”应用进程的“视线”被操作系统限制，只能“看到”特定的资源。为这个容器，装了天花板。
常见的Namespace， PID  Mount UTS Network User

3.容器的限制，使用Cgroups限制进程可以使用的资源上限（CPU、内存、磁盘、网络带宽），为这个容器修改了围墙
一个子系统目录就是一组资源限制文件的组合

4.容器的文件系统——容器镜像，rootfs只是一个操作系统包含的文件，配置和目录，不包括操作系统的内核。
分层镜像，利用分层Layer技术,在制作镜像的时候，每一步操作，都会生成一个层。因为共享层的存在，一方面在拉取和推送时内容小，另一方面，每个镜像的总空间也小。
再利用联合文件系统（不同位置的目录挂载到同一个目录下）组成一个完整的镜像
rootfs的三部分
第一部分，只读层，操作系统文件， readonly+whiteout
第二部分，可读写层，容器操作产生的内容 rw
第三部分，Init层，本来属于操作系统，但是用户需要修改，如/etc/hosts，但是有需要提交


## Saying

这么多年第一次写点东西。相信好的开始就是成功的一半，而另一半就是坚持。  
