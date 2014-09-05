---
layout: post
title: Microsoft Interview Set 20
date: 2014-09-05 15:53:00
categories: microsoft
published: true
---

>This is the solution to the Interview question set for [Microsoft Interview Set](http://www.geeksforgeeks.org/microsoft-interview-set-20-campus-internship/ "External Link to geeksforgeeks.org") 

## Round 2

**Question:**
Given a word and a text, return the count of the occurences of anagrams of the word in the text.
For eg. word is “for” and the text is “forxxorfxdofr”, anagrams of “for” will be “ofr”, “orf”,”fro”, etc. So the answer would be 3 for this particular example.

**Solution**
**_Method 1:_** By comparing the sorted forms of the word.

Steps:
-Sort the original word.
-Sort every substrings of the text, and check if it matches with the the original 'sorted' word.

**_Method 2:_** By finding all the anagrams of the word

In this method, the first thing required to know is to find all the possible anagrams of a given word. Then we'll traverse over the word and check if the substring is an anagram of the given word.

The code is as follows:
 {% highlight java %}

	public class CountOfOccurrencesOfAnagrams {
		private HashMap<String, Integer> anagrams = new HashMap<>();
		
		private void permutations(String prefix, String str){
			int n = str.length();
			if(n==0){
				anagrams.put(prefix, 0);
				return;
			}
			
			for(int i = 0; i<n ; i++){
				permutations(prefix + str.charAt(i), str.substring(0, i) + str.substring(i+1));
			}
		}
		
		public void countAna(String word, String text){
			permutations("", word);
			int count = 0;
			for(int i = 0; i<=text.length()-word.length(); i++){
				if(anagrams.get(text.substring(i, i+ word.length())) != null){
					count++;
					System.out.println(text.substring(i, i+ word.length()));
				}
			}
			System.out.println(count);
		}
		
		public static void main(String[] args){
			CountOfOccurrencesOfAnagrams ob = new CountOfOccurrencesOfAnagrams();
			ob.countAna("for", "forxxorfxdofr");
		}
	}
	
 {% endhighlight %}


**Question:**
Given a binary tree with parent pointers, find the right sibling of a given node(pointer to the node will be given), if it doesn’t exist return null. Do it in O(1) space and O(n) time.

**Solution:**
This is very straight forward. The pseudocode is as follows:

    IF ( NODE->PARENT AND NODE = NODE->PARENT->LEFT )
    	PRINT NODE->PARENT->RIGHT
    ELSE
    	PRINT NULL


## Round 3

**Question:**
Given a BST, one of the nodes violates the BST property( left-child < parent < right child ), return the pointer to that node.

**Solution:**
For every node in the BST this condition has to be satisfied: `NODE->LEFT->INFO < NODE->INFO`< NODE->RIGHT->INFO`

*Pseudo-code:*

    VIOLATE(NODE) 
    	IF (NODE != NIL)
    		VIOLATE( NODE->LEFT )
    		IF((NODE->LEFT != NIL) AND (NODE->RIGHT != NIL) AND  !( NODE->LEFT->INFO < NODE->INFO < NODE->RIGHT->INFO ))
    			PRINT NODE // this node violates the BST
    		VIOLATE(NODE->RIGHT)


**Question:**
Two no.s having equal no. of digits were given in the form of singly linklist. (For eg.- 102 will be given as 1 -> 0 -> 2 ). Add these no.s and return the answer in the form of a singly linkllist. Do it in O(n) time, given n digit numbers

**Solution:**
With the constraints given the closest solution I was able to get was `O(2n + (n+1))` ie. `O(3n+1)`

Steps:
-Traverse the first list and form the first number; `O(n)`
-Similarly traverse the second list and form the second number; `O(n)`
-Add the two numbers; `O(1)`
-Form a new linked list from the sum of the number; `O(n+1)`

## Round 5

**Question:**
Maximum sub-array problem in one pass

**Solution:**
This is done by [Kadane's Algorithm](http://en.wikipedia.org/wiki/Maximum_subarray_problem "Wikipedia Article- maximum sub array problem"):


{% highlight java %}

	public class MaximumSubArray {
		
		public static void get_max_subaray(int[] a){
			int max_now, max_so_far;
			
			// variables to keep a track of the max_subarray indices
			int max_so_far_start_index = 0, max_so_far_end_index = 0;;
			int max_now_start_index = 0;
			
			// initialize
			max_so_far = max_now = a[0];	
			
			for(int i = 1; i<a.length; i++){
				
				if(a[i] > max_now + a[i]){
					max_now_start_index = i;
					max_now = a[i];
				} else if(max_now + a[i] > a[i]){
					max_now = max_now + a[i];				
				}
				
				if(max_now > max_so_far){
					max_so_far = max_now;
					max_so_far_end_index = i;
					max_so_far_start_index = max_now_start_index;
				}
			}
			
			System.out.println(max_so_far + "\t" + max_so_far_start_index + "\t" + max_so_far_end_index);
		}

		public static void main(String[] args) {
			int[] a = {4,-1,2,1,-5,4};
			MaximumSubArray.get_max_subaray(a);
		}

	}


{% endhighlight %}





