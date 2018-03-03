# Github-Contributions-API

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
  =>> nohup python3 ./contributions.py &.
  
  It would be running with started as background and daemon-like
  
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
     check out -> [Yunbin-Chang.JSON](https://github.com/Yunbin-Chang/Github-Contributions-API/blob/master/Yunbin-Chang.JSON)
     
  * /contributions/weekly/<uname>
    * this provides a json data contains how many contributed during last year and is counted by day of week
    * JSON Example
  
    ```json
      { "Sunday" : "50", "Monday" : "25", "Tuesday" : "57", "Wednesday" : "33", "Thursday" : "14", "Friday" : "15", "Saturday" : "18" }
    ```
    
    If you want to find out more, check out -> [Yunbin-Chang-Weekly.JSON](https://github.com/Yunbin-Chang/Github-Contributions-API/blob/master/Yunbin-Chang-Weekly.JSON)
  
  * /contributions/monthly/<uname>
    * this provides a json data contains how many contributed during last year and is counted by month of year
    * JSON Example
  
    ```json
    { "January" : "4", "Febuary" : "6", "March" : "0", "April" : "0", "May" : "0", "June" : "0", "July" : "0","August" : "0", "September" : "0","October" : "1", "November" : "0", "December" : "0" }
    ```
    
    If you want to find out more, check out -> [Yunbin-Chang-Monthly.JSON](https://github.com/Yunbin-Chang/Github-Contributions-API/blob/master/Yunbin-Chang-Monthly.JSON)