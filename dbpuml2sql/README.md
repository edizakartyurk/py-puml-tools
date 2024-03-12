# PlantUML to SQL
 
Takes a tweaked PlantUML class diagram, that serves as a database diagram, and
spit out the SQL commands needed to create the tables.

## To do
 * Support more constraints (only PRIMARY KEY and FOREIGN KEY at this time)
 
## Running

Run the program with the PlantUML file as argument.

    $ ./dbpuml2sql.py db.puml 
    
    CREATE TABLE AirportCustomer (
  id INT PRIMARY KEY,
  homeaddress VARCHAR(255)
);

CREATE TABLE Luggage (
  id INT PRIMARY KEY,
  volume FLOAT,
  weight FLOAT,
  note VARCHAR(255),
  customer_id INT,
  FOREIGN KEY (customer_id) REFERENCES AirportCustomer(id)
);

CREATE TABLE Ticket (
  id INT PRIMARY KEY,
  flightid VARCHAR(50),
  customer_id INT,
  FOREIGN KEY (customer_id) REFERENCES AirportCustomer(id)
);
**Input diagram**

![Input database diagram](db.png)
