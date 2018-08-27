#题目
合并区间
## 问题： 
给出一个区间的集合，请合并所有重叠的区间。
## 编程实现：
class Solution(object):

    def merge(self, intervals):
        """
        :type intervals: List[Interval]
        :rtype: List[Interval]
        """
        if len(intervals) <= 1:
            return intervals
        res = []
        intervals = sorted(intervals,key = lambda start: start.start)
        l = intervals[0].start
        h = intervals[0].end
        for i in range(1,len(intervals)):
            if intervals[i].start <= h:
                h = max(h,intervals[i].end)
            else:
                res.append([l,h])
                l = intervals[i].start
                h = intervals[i].end
        res.append([l,h])
        return res
##总结
将intervals按每一个元素的start进行升序排列。 此时后一个值的start一定在前一个值的start，这个时候只要判断后一个的start是否比前一个的end大。如果 intervals[i].start <= intervals[i-1].end, 那么l保持不变，h为max(intervals[i].end, intervals[i-1].end)。否则，往列表res添加[l,h]，更新l和h的值。接下来继续循环判断，循环结束再往res添加[l,h]。