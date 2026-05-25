```javascript
use company
```

```javascript
db.createCollection("emp");
```

```javascript
db.emp.insert({
    "emp_id":1,
    "e_name":"Radha",
    "Age":25,
    "email":"radha@gmail.com"
});
```

```javascript
db.emp.insert({
    "emp_id":2,
    "e_name":"ramesh",
    "Age":28,
    "email":"ramesh@gmail.com"
});
```

```javascript
db.emp.insert({
    "emp_id":3,
    "e_name":"john",
    "Age":28,
    "email":"john@gmail.com"
});
```

```javascript
db.emp.insert({
    "emp_id":4,
    "e_name":"joe",
    "Age":25,
    "email":"joe@gmail.com"
});
```

```javascript
db.emp.find();
```

```javascript
db.emp.find({Age:{"$gt":25}});
```

```javascript
db.emp.updateOne(
    {"emp_id":1},
    {$set:{"age":31}}
);
```

```javascript
db.emp.find();
```

```javascript
db.emp.deleteOne({e_name:"Radha"});
```

```javascript
db.emp.count();
```
