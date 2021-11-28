HTML5 brings many features and improvements to web form creation. There are new attributes and input types that were introduced to help create better experiences for web users.

Form creation is done in HTML5 the same way as it was in HTML4:

```html
<form>
	<label>Your name: </label>
	<input id="user" name="username" type="text" />
</form>
```

note: Use the novalidate attribute to avoid form validation on submissions.

-   new attributes
    
    HTML5 has introduced a new attribute called placeholder. On input and textarea elements, this attribute provides a hint to the user of what information can be entered into the field.
    
    ```html
    <form>
    	<label for="email">Your email address: </label>
    	<input type="text" name="email"
    	placeholder="email@example.com" />
    </form>
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e715db16-9966-4c29-a1ae-2ee94ca1bdf7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221925Z&X-Amz-Expires=86400&X-Amz-Signature=5cb9c54fbf240eec04d6ccd854123248aca6da2e3098bd38de55dd6a92f1c0e5&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    The autofocus attribute makes the desired input focus when the form loads:
    
    ```html
    <form>
    	<label for="email">Your email address: </label>
    	<input type="text" name="email" autofocus/>
    </form>
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cdcc351f-c1cf-4af1-a756-5aa2777748bf/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221940Z&X-Amz-Expires=86400&X-Amz-Signature=8908883a99b50151135e97bdbededbcdf6005d9a3e63d815fa7439b773308435&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    -   note: the required attribute tells the browser that the input is required.
-   forms w/ required fields
    
    The "required" attribute is used to make the input elements required.
    
    ```html
    <form autocomplete="off">
    	<label for="e-mail">Your email address: </label>
    	<input name="Email" type="text" required/>
    	<input type="submit" value="Submit" />
    </form>
    ```
    
    The form will not be submitted without filling in the required fields.
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/801363d9-7fb5-4a1f-bb54-03d419b42093/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T222047Z&X-Amz-Expires=86400&X-Amz-Signature=f6c760be44a5ef7ae68ca108352588985dc30d037b384e9b0cb3c146f7a044bd&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    -   note: The **autocomplete** attribute specifies whether a form or input field should have autocomplete turned on or off. When autocomplete is on, the browser automatically complete values based on values that the user has entered before.
    
    **HTML5 added several new input types:**
    
    -   color
    -   date
    -   datetime
    -   datetime-local
    -   email
    -   month
    -   number
    -   range
    -   search
    -   tel
    -   time
    -   url
    -   week
    
    **New input attributes in HTML5:**
    
    -   autofocus
        
    -   form
        
    -   formaction
        
    -   formenctype
        
    -   formmethod
        
    -   formnovalidate
        
    -   formtarget
        
    -   height and width
        
    -   list
        
    -   min and max
        
    -   multiple
        
    -   pattern (regexp)
        
    -   placeholder
        
    -   required
        
    -   step
        
        note: input types that are not supported by old web browsers, will behave as input type text.
        
-   creating search box
    
    The new search input type can be used to create a search box:
    
    ```html
    <input id="mysearch" name="searchitem" type="search" />
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/77a4acb3-deaa-4e99-ae4a-8b4f632110f6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T222114Z&X-Amz-Expires=86400&X-Amz-Signature=2ec5fad6933a09949a148d006439e187b9fa0d175cb3101d1250f01ccbf2cb2b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    -   note: You must remember to set a name for your input; otherwise, nothing will be submitted.
-   search options
    
    The datalist tag can be used to define a list of pre-defined options for the search field:
    
    ```html
    <input id="car" type="text" list="colors" />
    <datalist id="colors">
    	<option value="Red">
    	<option value="Green">
    	<option value="Blue">
    </datalist>
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/43284d3d-318b-46f8-b508-30e5dfdb12bc/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T222159Z&X-Amz-Expires=86400&X-Amz-Signature=020fd46105167c1fa1e27113ac0a7b3f195e3774028a6827568ce638f9ba22bb&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    the option tag defines the options in a drop-down list for the user to select.
    
    -   note: The ID of the datalist element must match with the list attribute of the input box.
-   creating more fields
    
    Some other new input types include email, url, and tel:
    
    ```html
    <input id="email" name="email" type="email" placeholder="example@example.com" />
    <br />
    <input id="url" name="url" type="url" placeholder="example.com" />
    <br />
    <input id="tel" name="tel" type="tel" placeholder="555.555.1211" />
    ```
    
    especially useful when opening page on modern mobile device; recognizes input types & opens corresponding keyboard matching field's type
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6233ff90-a70f-4c85-a6b2-5a5cfead7604/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T222222Z&X-Amz-Expires=86400&X-Amz-Signature=e8d09dfd76ad75f0a630bf128ae521a989bf8bc32a39eb6b8e29528465436ca6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    -   note: These new types make it easier to structure and validate HTML forms.