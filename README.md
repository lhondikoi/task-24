### Zen Class Schema

**NOTE: Please refer to <a href="./schema.md">`schema.md`</a> to view the schema used as a reference for these queries.**

### 1. Find all the topics and tasks which are taught in the month of October

```js
db.Topics.find({ $where: function() {
        return this.releaseDate.getMonth() === 9
    }
})
// getMonth() returns 0-11 for Jan-Dec.
```

### 2. Find all the company drives which occured between 15 oct-2020 and 31-oct-2020

```js
db.CompanyDrives.find({
    date: { $gte: new Date(2020,9,15), $lte: new Date(2020, 9, 31)}
})
```

### 3. Find all the company drives and students who are appeared for the placement.

```js
db.CompanyDrives.find()
```

### 4. Find the number of problems solved by the user in codekata.

```js
db.Users.aggregate([
    { $match: { name: "John Doe"} },
    { $count: "Solved problems"}
])
```

### 5. Find all the mentors with who has the mentee's count more than 15

```js
db.Mentors.find({ $where: function() {
    return this.mentees.length > 15
}})
```

### 6. Find the number of users who are absent and task is not submitted between 15 oct-2020 and 31-oct-2020

```js
db.Users.find(
    {"attendance.isPresent": false},
    {"attendance.date": {$gte: new Date(2020, 9, 15), $lte: new Date(2020, 9, 31)}},
    {"attendance.topicHasTask": true},
    {"attendance.taskSubmitted": false}
)
```