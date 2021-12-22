1、swift中，常用到对NSArray的操作：

###
	class Employee {
    var id: Int
    var firstName: String
    var lastName: String
    var dateOfBirth: NSDate?

    init(id: Int, 
	  firstName: String, 
	  lastName: String) {
        self.id = id
        self.firstName = firstName
        self.lastName = lastName
    }
}

	let em0 = Employee.init(id: 0, firstName: "first0", lastName: "last0")
	let em1 = Employee.init(id: 1, firstName: "first1", lastName: "last1")
	let em2 = Employee.init(id: 2, firstName: "first2", lastName: "last2")
	let tempArr:[Employee] = [em0, em1, em2]

###


1、map与compactMap遍历 对数组里的对像进行一次操作

	let results = tempArr.compactMap { em in
   		return em.id == 4
	}
	print(results) 
**打印结果：[false, false, false]**



2、filter过滤出自己想要的， 返回的是[]

	let result = tempArr.filter{$0.id == 1}
	print(result) 
**打印结果：[Employee]**


3、filter过滤出自己想要的， 返回的是对像

	let result = tempArr.first{$0.id == 1}
	print(result.name) 
**打印结果：first1**

4、for针对array过滤循环

	for item in tempArr where item.id == 1 {
   	   print(item.firstName)
	}

	for item in tempArr {
   	   print(item.firstName)
	}

5、tempArr是否包含某个对像

	let flag = tempArr.contains(where: {$0.id == 1})
	print(flag) 

6、tempArr过滤出某个对像

	let result = tempArr.filter { em in
  	 	return em.firstName.contains("first1")
	}
	print(result)

7、reduce：初始化了一个initialResult为0，对元素做相加，每次相加后的结果作为下次闭包的参数，y就是数组的每个

	let result = tempArr.reduce(0, { partialResult, y in
    	partialResult + y.id
	})
	print(result) 
**打印结果：2**

