## General
 
  
### Protocols
HTTP 80

HTTPS 443
Handshake -> 
Request:
```
GET /doc/ HTTP/1.1
Host: www.test.com

```
Response:
```
HTTP/1.1 200 OK
Content-Type: text/html; charset=utf-8
```
### SOLID

The SOLID design principle includes these five principles:
#### Single Responsibility Principle
In addition to keeping classes small and focused it also makes them easier to understand.
	
#### Open/Closed Principle
The Open/Closed Principle states that classes or methods should be open for extension, but closed for modification. This tells us we should strive for modular designs that make it possible for us to change the behavior of the system without making modifications to the classes themselves. This is generally achieved through the use of patterns such as the strategy pattern. Let’s look at an example of some code that is violating the Open/Closed Principle:
#### Liskov Substitution Principle
The principle says that objects of a superclass should be replaceable with objects of its subclasses without breaking the application. That requires the objects of your subclasses to behave in the same way as the objects of your superclass. 
An overridden method of a subclass needs to accept the same input parameter values as the method of the superclass. That means you can implement less restrictive validation rules, but you are not allowed to enforce stricter ones in your subclass. Otherwise, any code that calls this method on an object of the superclass might cause an exception, if it gets called with an object of the subclass.

Similar rules apply to the return value of the method. The return value of a method of the subclass needs to comply with the same rules as the return value of the method of the superclass. You can only decide to apply even stricter rules by returning a specific subclass of the defined return value, or by returning a subset of the valid return values of the superclass.

#### Interface Segregation Principle
**Clients should not be forced to depend upon interfaces that they do not use.**

#### Dependency Inversion Principle

### SLAP
Single Level of Abstraction Principle

### Parallelism and Concurrency
Threads
Threads are useful for IO bound applications: DB, API, File system
Wait for thread – thread.join	
GIL 

## Ruby
* Inheritance
* Composition
  * Include
  * Extends
  * Prepend
* Polymorphism
* Incapsulation
* Design pattern
  * Service objects
  * Form objects
  * Fat models
  * Skinny controllers
* N+1
  * Preload loads the association data in a separate query

## Rails

![image](https://user-images.githubusercontent.com/1765991/140758550-803f72d0-160a-494b-82e5-522b9dbd8b1f.png)

### Equality
`==` At the Object level, `==` returns true only if obj and other are the same object. Typically, this method is overridden in descendant classes to provide class-specific meaning.
`===` For class Object, effectively the same as calling `#==`, but typically overridden by descendants to provide meaningful semantics in case statements.
`eql?` — Hash e equal? — identity comparison
`equal?` Unlike ==, the equal? method should never be overridden by subclasses: it is used to determine object identity (that is, `a.equal?(b)` if `a` is the same object as `b`). quality

Algorithms

<details>
<summary>QuickSort</summary>
```ruby
   def   quicksort(arr, first, last)
	  if first < last
	    p_index = partition(arr, first, last)
	    quicksort(arr, first, p_index - 1)
	    quicksort(arr, p_index + 1, last)
	  end
	
	  arr
	end
	
	def partition(arr, first, last)
	  # first select one element from the list, can be any element. 
	  # rearrange the list so all elements less than pivot are left of it, elements greater than pivot are right of it.
	  pivot = arr[last]
	  p_index = first
	
	  i = first
	  while i < last
	    if arr[i] <= pivot
	      temp = arr[i]
	      arr[i] = arr[p_index]
	      arr[p_index] = temp
	      p_index += 1
	    end
	    i += 1
	  end
	  temp = arr[p_index]
	  arr[p_index] = pivot
	  arr[last] = temp
	  return p_index
	end
```
</details>

### Fault tolerance

*	CDN (Cloudflare, Fastly)
*	Nginx
*	Server optimization
*	Puma / Passenger / Unicorn
*	Caching
*	DB optimization
*	Proper database structure
*	Indexes
*	Views / materialized views
 

## DB
#### Postgres
* Locks
* Transactions
* Indexes (Hash, B-Tree, GiN, GisT)
* Replication (read, write)
* Sharding and partitioning are both about breaking up a large data set into smaller subsets. Sharding implies the data is spread across multiple computers while partitioning does not. Partitioning is about grouping subsets of data within a single database instance. In many cases, the terms sharding and partitioning are even used synonymously, especially when preceded by the terms “horizontal” and “vertical.” Thus, “horizontal sharding” and “horizontal partitioning” can mean the same thing.
	There are a several principle reasons to partition a table:
	1.	When a table grows so big that searching it becomes impractical even with the help of indexes (which will invariably become too big as well).
	2.	When data management is such that the target data is often the most recently added and/or older data is constantly being purged/archived, or even not being searched anymore (at least not as often).
	3.	If you are loading data from different sources and maintaining it as a data warehousing for reporting and analytics.
	4.	For a less expensive archiving or purging of massive data that avoids exclusive locks on the entire table.
	When should we resort to sharding?
	Here are a couple of classic cases:

	1.	To scale out (horizontally), when even after partitioning a table the amount of data is too great or too complex to be processed by a single server.
	2.	Use cases where the data in a big table can be divided into two or more segments that would benefit the majority of the search patterns. A common example used to describe a scenario like this is that of a company whose customers are evenly spread across the United States and searches to a target table involves the customer ZIP code. A shard then could be used to host entries of customers located on the East coast and another for customers on the West coast.
 
 
## Security
* XSS
* Cross-Site Request Forgery (CSRF) is an attack that allows a malicious user to spoof legitimate requests to your server, masquerading ...

 
## Blockchain
 
DAO

