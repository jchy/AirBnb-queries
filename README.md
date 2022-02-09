# AirBnb-queries
Assignment : 5439, use the airbnb sample data and make the queries

1. write a query of using two OR operators, and check for listings from any two countries
- Ans 
```js
  db.data.find( {$or : [ {"address.country_code" : "US"} , {"address.country_code" : "AU"}]} ).count()
```
2. write a query of using two AND operators and check for one country and review ratings to be greater than a particular value
- Ans
```js
  db.data.find( {$and : [ { "review_scores.review_scores_rating" : {$gt : 95}},{ "address.country_code" : "US" }] } ) .count()
```

3. write a query of using AND and OR operator in conjuction
    a. it should belong to any two cities and
    b. it should have rating = 99
- Ans
```js
  db.data.find( {$and : [ { "review_scores.review_scores_rating" : {$eq : 99}},{ $or : [ {"address.country_code" : "US"} , {"address.country_code" : "AU"}] }] } ).count()
```
4. write a query of using AND and OR operator together
    a. it should belong to US and rating of 95 or
    b. it should belong to CA and rating of 99
- Ans
```js
  db.data.find( {$and : [ { "review_scores.review_scores_rating" : {$eq : 99}},{ $or : [ {"address.country_code" : "US"} , {"address.country_code" : "AU"}] }] } ).count()
```
