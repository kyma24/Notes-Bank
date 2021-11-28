-   form validation
    
    HTML5 adds some attributes that allow form validation. i.e. the **required** attribute can be added to an input field to make it mandatory to fill in.
    
    More complex form validation can be done using JS.
    
    The form element has an **onsubmit** event that can be handled to perform validation.
    
    i.e. create a form with two inputs and one button. The text in both fields should be the same and not blank to pass the validation.
    
    ```html
    <form onsubmit="return validate()" method="post">
    	Number: <input type="text" name="num1" id="num1" />
    	<br />
    	Repeat: <input type="text" name="num2" id="num2" />
    	<br />
    	<input type="submit" value="Submit" />
    </form>
    ```
    
    Now need to define the **validate**() function:
    
    ```jsx
    function validate() {
    	var n1 = document.getElementById("num1");
    	var n2 = document.getElementById("num2");
    	if(n1.value != "" && n2.value != "") {
    		if(n1.value == n2.value) {
    			return true;
    		}
    	}
    	alert("The values should be equal and not blank");
    	return false;
    }
    ```
    
    only return **true** when the values aren't blank and are equal.
    
    the form will not get submitted if its **onsubmit** event returns **false**.