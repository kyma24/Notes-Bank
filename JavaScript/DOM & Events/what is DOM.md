-   what is DOM
    
    when opening any webpage in the browser, the HTML of the page is loaded and rendered visually on the screen.
    
    To accomplish that, the browser builds the **Document Object Model** of that page, which is an object oriented model of its logical structure.
    
    the DOM of an HTML document can be represented as a nested set of boxes:
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/989b6cf8-054e-48b5-ae99-fa28d04286e8/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T140010Z&X-Amz-Expires=86400&X-Amz-Signature=6d5832261a95f8b8f25e3f046fcbda3c76354010c646c69da79a6e4ed3cab8f5&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    JS can be used to manipulate the DOM of a page dynamically to add, delete, and modify elements.
    
    The DOM represents a document as a tree structure.
    
    HTML elements become interrelated **nodes** in the tree.
    
    All those nodes in the tree have some kind of relations among each other.
    
    Nodes can have **child** nodes. Nodes on the same tree level are called **siblings**.
    
    i.e. consider the above structure.
    
    \<html> has two children(\<head>, \<body>);
    
    \<head> has one child(\<title>) and one parent(\<html>)
    
    \<title> has one parent(\<head>) and no children;
    
    \<body> has two children(\<h1> and \<a>) and one parent(\<html>);
    
    it is important to understand the relationships between elements in an HTML document in order to be able to manipulate them with JS.