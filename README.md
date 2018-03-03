# Github-Contributions-API

## Status

[![Travis](https://img.shields.io/jenkins/s/https/jenkins.qa.ubuntu.com/view/Precise/view/All%20Precise/job/precise-desktop-amd64_default.svg)]() [![apm](https://img.shields.io/apm/l/vim-mode.svg)]()


## What you need befor running

  * Flask
  * BeautifulSoup4
  * Python3
  * Nginx (not yet)
  * Gunicorn (not yet)
  
  
  
## How to run

  1. clone the repository into your API server.
  2. make a python vertual environment.
  3. get into the vertualenv
  4. type python ./contributions.py for starting server
  
  
## Running like a Daemon

  If you want to run the server like daemon. which would not be stopped although you closed the terminal,
  running as background service.
  
  * It works in only linux environment.
  
  ```
   nohup python3 ./contributions.py &.
  ```
  
  It would be running with started as background and daemon-like.
  
## Route for API

  * /contributions/daily/<uname>

    * this provides a json data contains how many contributed in a day with a contributing date.
      ignoring a no contributing date.
    * JSON Example
  
     ```json
      [
        {
            "date" : "2017-02-27",
            "count" : "2"
        },
        {
            "date" : "2017-02-28",
            "count" : "10"
        }
      ]
     ```
     above json data ignored many contributing-date beacause the json is too big to write here.  
     check out -> [Yunbin-Chang.JSON](https://github.com/Yunbin-Chang/Github-Contributions-API/blob/master/sample-json/Yunbin-Chang.JSON)
     
  * /contributions/weekly/<uname>

    * this provides a json data contains how many contributed during last year and is counted by day of week
    * JSON Example
  
    ```json
      { "Sunday" : "50", "Monday" : "25", "Tuesday" : "57", "Wednesday" : "33", "Thursday" : "14", "Friday" : "15", "Saturday" : "18" }
    ```
    
    If you want to find out more, check out -> [Yunbin-Chang-Weekly.JSON](https://github.com/Yunbin-Chang/Github-Contributions-API/blob/master/sample-json/Yunbin-Chang-Weekly.JSON)
  
  * /contributions/monthly/<uname>

    * this provides a json data contains how many contributed during last year and is counted by month of year
    * JSON Example
  
    ```json
    { "January" : "58", "Febuary" : "102", "March" : "16", "April" : "0", "May" : "0", "June" : "0", "July" : "2","August" : "6","September" : "0","October" : "8","November" : "17","December" : "10" }
    ```
    
    If you want to find out more, check out -> [Yunbin-Chang-Monthly.JSON](https://github.com/Yunbin-Chang/Github-Contributions-API/blob/master/sample-json/Yunbin-Chang-Monthly.JSON)

## How does it works

  This API parse a contributions data from https://github.com/<some-user-name>

  Especially from below parts of the page.

![img/contribution-rect]()

  the code for above color-filled rectangles is formatted as

  ```html
    <rect class="day" width="10" height="10" x="?" y="?" fill="#ebedf0" data-count="<counting>" data-date="yyy-mm-dd"/>
  ```

  so the API parses from these parts and arrange and decorate with json and respond to request.