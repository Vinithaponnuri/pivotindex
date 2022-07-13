1)    
class Solution:
    def pivotIndex(self,n):
        rightsum=sum(n)
        leftsum=0
        t=len(n)
        for i in range(t):
            rightsum=rightsum-n[i]
            if leftsum==rightsum:
                return i
            leftsum=leftsum+n[i]
        return -1
        
        
        OR
2)  
class Solution:
    def pivotIndex(self, nums: List[int]) -> int:
        n=len(nums)
        pf=[0]*n
        pf[0]=nums[0]
        for i in range(1,n):
            pf[i]=pf[i-1]+nums[i]
        for i in range(n):
            if i==0:
                lsum=0
            else:
                lsum=pf[i-1]
            rsum=pf[n-1]-pf[i]
            if lsum==rsum:
                return i
        return -1
