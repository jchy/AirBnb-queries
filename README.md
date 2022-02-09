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
  db.data.find( {$or : [ {$and : [ {"address.country_code" : "US"} ,{ "review_scores.review_scores_rating" : {$eq : 95}}] }, {$and : [ {"address.country_code" : "CA"} ,{ "review_scores.review_scores_rating" : {$eq : 99}}] }] } ).count()
```

5. write a query of using querying arrays
    a. check all listings which have amenities of size 5, 6, 7, 8, 9, 10
    ```js 
      db.data.find({ $or: [{ amenities: { $size: 5 } },{ amenities: { $size: 6 } }, { amenities: { $size: 7 } },{ amenities: { $size: 8 } },{ amenities: { $size: 9 } },{ amenities: { $size: 10 } }  ] }).count()
    ```
    b. check all listings of where aminities contain 4 or 5 different listings 
    ```js
      db.data.find({$or : [{ amenities : {$size : 4}}, {amenities : {$size : 5 }}]} ).count()
    ```
    c. check all listings of reviews where it matches a particular user id and name 
    d. check all listings of reviews where it matches a particular user id and name, list only reviews that match the particular user id and name
