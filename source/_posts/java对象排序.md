---
title: Java对象排序
date: 2017年8月23日18:33:22
tags: 
-  排序
categories:
- java
---

## Java对象排序
>  public class  TicketComparator implements Comparator{
	 public  int compare(Object  obj1, Object obj2 ){
	  PlatformActivitiesJoin join1 = (PlatformActivitiesJoin)obj1;
	  PlatformActivitiesJoin join2 = (PlatformActivitiesJoin)obj2;
	  if(join1.getVote()>join2.getVote()){
	      return -1;
	  }
	     return 1;  
	  }
	 
	 
	 public static void main(String[] args){		  
		 PlatformActivitiesJoin u1 =new PlatformActivitiesJoin();
		 u1.setVote(100);
		 PlatformActivitiesJoin u2 =new PlatformActivitiesJoin();
		 u2.setVote(200);
		 PlatformActivitiesJoin u3 =new PlatformActivitiesJoin();
		 u3.setVote(500);
		 PlatformActivitiesJoin u4 =new PlatformActivitiesJoin();
		 u4.setVote(300);  
		  ArrayList arrayList = new ArrayList();
		  arrayList.add(u1);
		  arrayList.add(u2);
		  arrayList.add(u3);
		  arrayList.add(u4);  
		  Object[] users =arrayList.toArray();
		  System.out.println ("排序前。。。。");
		  for (int i = 0; i<users.length; i++){
		   System.out.println (users[i]);
		  }
		  System.out.println ("*******************************");
		  System.out.println ("排序后。。。。。");
		  //把排序规则交给sort方法。该方法就回按照你自定义的规则进行排序
		  java.util.Arrays.sort(users,new TicketComparator());  
		   for (int i = 0; i<users.length; i++){
		     System.out.println (users[i]);
		  }
 
		}

##  result
>   排序前。。。。
   PlatformActivitiesJoin(id=null, platformActivitiesId=null, userId=null, addTime=null, state=0, email=null, nickname=null, avatar=null, topicTitle=null, inActivityDate=null, imgsrcs=null, albumcover=null, index=null, vote=200, imgsrclist=[])
   PlatformActivitiesJoin(id=null, platformActivitiesId=null, userId=null, addTime=null, state=0, email=null, nickname=null, avatar=null, topicTitle=null, inActivityDate=null, imgsrcs=null, albumcover=null, index=null, vote=500, imgsrclist=[])
   PlatformActivitiesJoin(id=null, platformActivitiesId=null, userId=null, addTime=null, state=0, email=null, nickname=null, avatar=null, topicTitle=null, inActivityDate=null, imgsrcs=null, albumcover=null, index=null, vote=300, imgsrclist=[])
*******************************
    排序后。。。。。
 PlatformActivitiesJoin(id=null, platformActivitiesId=null, userId=null, addTime=null, state=0, email=null, nickname=null, avatar=null, topicTitle=null, inActivityDate=null, imgsrcs=null, albumcover=null, index=null, vote=500, imgsrclist=[])
PlatformActivitiesJoin(id=null, platformActivitiesId=null, userId=null, addTime=null, state=0, email=null, nickname=null, avatar=null, topicTitle=null, inActivityDate=null, imgsrcs=null, albumcover=null, index=null, vote=300, imgsrclist=[])
PlatformActivitiesJoin(id=null, platformActivitiesId=null, userId=null, addTime=null, state=0, email=null, nickname=null, avatar=null, topicTitle=null, inActivityDate=null, imgsrcs=null, albumcover=null, index=null, vote=200, imgsrclist=[])
PlatformActivitiesJoin(id=null, platformActivitiesId=null, userId=null, addTime=null, state=0, email=null, nickname=null, avatar=null, topicTitle=null, inActivityDate=null, imgsrcs=null, albumcover=null, index=null, vote=100, imgsrclist=[])
