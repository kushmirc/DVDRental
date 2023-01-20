# DVD Rental

### <em>Video Walkthrough: </em>https://youtu.be/jQ7rpQ4HABs
<a href="https://youtu.be/jQ7rpQ4HABs">
<img src="https://user-images.githubusercontent.com/107213928/213590644-30eb6bda-fa01-433a-9c49-9b395832176e.png" alt="video walkthrough"></a>


## Introduction:
This project uses the DVD Rental sample database included in PostgreSQL.  The scenario is that of the DVD Rental Company inventory manager who wants to determine how many copies of each DVD should be stocked on the shelves.  To make this decision, the manager needs to know which DVDs are rented most frequently, and how many days they are rented for.  This information needs to be store-specific because each store has their own stock of DVDs on the shelves.  

The data used for the report includes rental information about the DVDs, such as the dates rented and returned. It also includes information identifying which store the DVDs are from, and what films they are.  

There are two source tables needed to provide the data necessary for the detailed and summary sections of the report.  These tables are the rental table and the inventory table.  The two new tables created are the rental_detail, and rental_summary tables.

The fields that are included in the detailed and summary reports from the source data rental table are the rental _id, rental_date, and return_date fields.  The fields included from the source data inventory table are the the store_id field, the film_id field.  

A data transformation included is the days_rented_out field in the detailed report which calculates the difference, in days and time, between the rental_date, and the return_date fields from the rental table. The days_rented_out field allows the inventory manager to quickly identify DVDs which were kept for an especially long period of time, and which were therefore unavailable for rental during that time.  

The detail table provides a record of every rental record in the report.  This will be useful because it will indicate how many total rentals have taken place.  It will also show the number of days that a DVD was rented out for each rental.  The summary table shows the total number of times rented for each DVD (film_id) at each store.  

The report should be refreshed bi-weekly.  The inventory manager needs to decide how often to evaluate the relative popularity of DVD titles to adjust and optimize the stock levels accordingly.  If he does it too often though, weekly for example, it will take too much time away from other duties while providing relatively little benefit.  However, monthly wouldn’t be frequent enough because the popularity of movie titles is likely to fluctuate significantly over a one-month span.  


## Project execution screenshots:
Create rental_detail and rental_summary tables:
![B](https://user-images.githubusercontent.com/107213928/213591156-95d64512-38b3-4223-ad83-4221bf05e69f.png)


Extract data and insert into rental_detail table:
![C](https://user-images.githubusercontent.com/107213928/213591228-b1968918-252f-48dd-afdb-2a5d1f6d86da.png)


Data transformation.  Add column days_rented_out, and set the timestamp interval:
![D1](https://user-images.githubusercontent.com/107213928/213591353-65edd439-0f91-438c-a77d-2591499f9430.png)
![D2](https://user-images.githubusercontent.com/107213928/213591366-f6335110-c834-4c1e-846f-a633123ca27d.png)



