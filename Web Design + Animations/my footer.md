-   my footer
    
    ```html
    <!DOCTYPE html>
    <html>
      <head>
        <title>Home | BYTE
        </title>
        <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
        <style>
          /*for the Navigation Bar*/
          a {
            text-decoration: none;
            padding: 10px;
          }
          .header a:hover {
            background-color: #cac6a5;
            padding: 10px;
          }
          .headFont {
            color: #4b493e;
            text-shadow: 5px 2px 4px #A1A1A5;
            display: block;
            font-family: "Lucida Console", Helvetica, Arial, sans-serif;
            font-style:normal;
            font-size: 35px;
            line-height: 29.75px;
            margin-block-end: 16px;
            margin-block-start: 14px;
            margin-inline-end: 0px;
            margin-inline-start: 0px;
            text-align: left;
            text-rendering: optimizeLegibility;
          }
          .wideOnly {
            color: rgb(55, 61, 66);
            display: block;
            font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
            font-size: 28px;
            line-height: 29.75px;
            margin-block-end: 17px;
            margin-block-start: 17px;
            margin-inline-end: 0px;
            margin-inline-start: 0px;
            text-align: left;
            text-rendering: optimizeLegibility;
          }
          #mainHeader {
            background-color: #F9F6F1;
            width: 96%;
            margin: 0 auto;
            margin-bottom: 18px;
            display: grid;
            grid-gap: 10px;
            grid-template-columns: 56px 200px auto auto auto auto 20px auto 20px auto auto auto 1fr;
            color: #444;
            align-items: center;
            padding: 15px;
            position: fixed;
            opacity: 0.98;
            border:5px solid #86836D;
            border-radius: 5px;
            /*border-bottom: 2px solid var(--structureBorder);*/
          }
          #mainHeader .headerLink {
            font-weight: 700;
            justify-self: center;
            margin-left: 0;
            margin-right: 0;
            color: var(--darkText);
            padding: 12px;
            border-radius: 5px;
          }
          /*main body of page*/
          body {
            background-color:#F5F6F4;
            transition: all 1s ease-in;
          }
          .navBar {
            background-color: #F9F6F1;
            color: rgb(55, 61, 66);
            text-align: center;
            display: inline-block;
            padding: 10px;
            border-radius: 5px;
            text-decoration: none;
          }
          .link a:hover {
            background-color: rgb(55, 61, 66);
            color: #F9F6F1;
            border-radius: 5px;
            text-decoration: none;
          }
          ::selection {
            background: #696773;
            color: #EFF1F3;
          }
          #myDiv p {
            padding-left: 7px;
            margin-bottom: 15px;
            transition: all .2s ease-in-out;
            transform: translate3d(0px, 30px, 0);
            opacity: 0;
          }
          #myDiv p.active {
            transform: translate3d(0px, 0, 0);
            opacity: 1;
          }
          #footer {
            background-color: rgb(55, 61, 66);
            color: #F9F6F1;
            text-align: center;
            opacity: 0.95;
            font-family: "Lucida Console", Helvetica, Arial, sans-serif;
            height: 500px;
            width: 98.7%;
            padding: 20px;
            z-index: 5;
            transform:translate(-8px, 1500px);
            position: relative;
          }
        </style>
      </head>
      <div id="footer">
        <p style="font-size: 80px;">gO0dby3.
        </p>
        <p style="font-size: 50px;">- キミ
        </p>
        <p style="font-size: 20px;">
          <small>i said byee</small>
        </p>
        <nav class="navBar link">
          <a class="navBar link" href="#" target="_self">1919</a>
          <a class="navBar link" href="#" target="_self">Chicago</a>
          <a class="navBar link" href="#" target="_self">Race Riot</a>
        </nav>
      </div>
    ```