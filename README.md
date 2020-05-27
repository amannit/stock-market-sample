In a separate terminal window start the application:

    mvn clean spring-boot:run

Get users:

    curl -X GET "http://localhost:8080/users"

Create user:

    curl -X POST -H "Content-Type: application/json" -d '{"username": "petyr","budget": "1000"}' "http://localhost:8080/users"

Get shares:

    curl -X GET "http://localhost:8080/shares"

Create share:

    curl -X POST -H "Content-Type: application/json" -d '{"symbol": "rht","amount": 500,"price": 80}' "http://localhost:8080/shares"

Buy share:

    curl -X PUT "http://localhost:8080/portfolio/petyr/rht?amount=1"

If shares were bought successfully, you should see a similar outcome to the following in a log:

    ----> Updated 'petyr' budget to 920
    ----> Updated 'rht' amount to 499
    ----> 'petyr' just bought 1 shares of 'rht' for the amount of 80

Sell share:

    curl -X DELETE "http://localhost:8080/portfolio/petyr/rht?amount=1"

If shares were sold successfully, you should see a similar outcome to the following in a log:

    ----> Updated 'petyr' budget to 1000
    ----> Updated 'rht' amount to 500
    ----> 'petyr' just sold 1 shares of 'rht' for the amount of 80