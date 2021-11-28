-   event propagation
    
    there are 2 ways of event propagation in the HTML DOM: **bubbling** and **capturing**.
    
    Event propagation allows for the definition of the element order when an event occurs. If have a \<p> element inside a \<div> element, and the user clicks on the \<p> element, which element's "click" event should be handled first?
    
    In **bubbling**, the innermost element's event is handled first and then the outer element's event is handled. The \<p> element's click event is handled first, followed by the \<div> element's click event.
    
    In **capturing**, the outermost element's event is handled first and then the inner. The \<div> element's click event is handled first, followed by the \<p> element's click event.
    
    note that Capturing goes **down** the DOM, and Bubbling goes **up** the DOM.