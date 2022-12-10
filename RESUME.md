## **FIND**
```JS
db.users.find();
db.users.findOne({username: "Alex"});

db.users.findOne({username: /a/i});

db.users.find({}, {username: 1, age: 1}); // los documentos solamente tendran las propiedades especificadas
db.users.find({}, {age: 0}); // elimina la propiedad
db.users.find({"address.street": "la industria"}); // busqueda dentro de un objeto

db.users.find().limit(5);
db.users.find().skip(3);
db.users.find().sort({username: 1}); // ascendente
db.users.find().sort({username: -1}); // descendente
```
[**Query Operators**](https://www.mongodb.com/docs/manual/reference/operator/query/)
```JS
{username: {$in: ["Alex", "Sally"]}}; 
{username: {$nin: ["Alex", "Sally"]}};
{username: {$exists: true}}; // existe la propiedad

{age: {$gt: 18}}; // mayor que
{age: {$lt: 18}}; // menor que
{age: {$not: {$gt: 20} } };

{$and:[{username:"Alex"}, {age: 21}]};
{$or:[{username:"Alex"}, {age: 21}]};
{$nor:[{username:"Alex"}, {age: 21}]};

{$expr:{$lt:["$debt", "$balance"]}}; // si la propiedad debt es mayor que la propiedad balance

// ------ otros
// array
$all
$elemMatch

```

## **INSERT**
```JS
const document = {username: "Alex", age: 19};
db.users.insertOne(document);
db.users.insertMany([document, document]);
```

## **UPDATE**
```JS
db.users.updateOne(
    { name: "Alex" }, // busqueda
    { $set: { age: 17 } } // dato a actualizar
);
db.users.updateMany(
    { age: { $exists: false } }, // busqueda
    { $set: { age: 17 } } // datos a actualizar
);
```
[**UPDATE OPERATORS**](https://www.mongodb.com/docs/manual/reference/operator/update/)
```JS
.updateOne({username:"Alex"}, {$inc: {age:3}}); // incrementar un numero
.updateOne({username:"Alex"}, {$rename: {email:"correo"}}); // renombrar una propiedad
.updateOne({username: "Alex"}, {$unset: {address:""}}); // elimina una propiedad

.updateOne({username: "Alex"}, {$push: {hobbies:"reader"}}); // agrega un dato en un array
.updateOne({username: "Alex"}, {$pull: {hobbies:"reader"}}); // elimina un dato en un array
```

## **DELETE**
```JS
db.users.deleteOne({username: "Alex"});
db.users.deleteMany({username: "Alex"});
```

<br>
<br>

# **RESOURCE**

- [Join docs](https://www.youtube.com/watch?v=cuLYt1ODSk4)
- [Indexes](https://www.youtube.com/watch?v=D14wWW9EEx8)
- [MongoDb Nodejs](https://mongodb.github.io/node-mongodb-native/4.10/index.html)
