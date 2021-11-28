-   ES6 rest parameters
    
    prior to ES6, if wanted to pass a variable number of arguments to a function, could use the **arguments** object, an array-like object, to access the parameters passed to the function.
    
    i.e. write a function that checks if an array contains all the arguments passed:
    
    ```jsx
    function containsAll(arr) {
    	for (let k = 1; k < arguments.length; k++) {
    		let num = arguments[k];
    		if (arr.indexOf(num) === -1) {
    			return false;
    		}
    	}
    	return true;
    }
    let x = [2, 4, 6, 7];
    console.log(containsAll(x, 2, 4, 7));
    console.log(containsAll(x, 6, 4, 9));
    ```
    
    can pass any number of arguments to the function and access it using the **arguments** object.
    
    while this does the job, ES6 provides a more readable syntax to achieve variable number of parameters by using a **rest parameter**:
    
    ```jsx
    function containsAll(arr, ...nums) {
    	for (let num of nums) {
    		if (arr.indexOf(num) === -1) {
    			return false;
    		}
    	}
    	return true;
    }
    ```
    
    the **...nums** parameter is called a **rest parameter**. It takes all the "extra" arguments passed to the function. The three dots (...) are called the **Spread operator**.
    
    note that only the last parameter of a function may be marked as a rest parameter. If there are no extra arguments, the rest parameter will simply be an empty array; the result parameter will never be **undefined**.
    
    ```jsx
    //i.e. this outputs 12(sum of all even numbers in the input of function magic()
    function magic(...nums) {
      let sum = 0;
      nums.filter(n => n % 2 == 0).map(el => sum+= el);
      return sum;
    }
    console.log(magic(1, 2, 3, 4, 5, 6));
    ```