Introduction
===

In previous versions of Zen Cart, pagination has been handled by the split_page_results class. 
This class has lots of problems. 

1. It has a poor API 
2. It's difficult to change the html output
3. It is bound to using sql results. 

For v160 we realised we needed to have a better class structure for doing pagination. 

