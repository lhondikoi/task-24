### Schemas:

```js
// Users
{
    _id: ObjectId,
    name: string,
    createdAt: datetime,
    mentor: ObjectId,
    batch: ObjectId,
    attendance: [
        {
            topicId: ObjectId,
            date: datetime,
            isPresent: boolean,
            topicHasTask: boolean,
            taskSubmitted: boolean,
            solutionURLs: [ string1, string2, ... ]
        },
    ],
    solvedCodekata: [
        {
            problemId: ObjectId,
            solveDate: datetime
        }
    ]
}
```

```js
// Mentors
{
    _id: ObjectId,
    name: string,
    created: datetime,
    mentees: [ ObjectId1, ObjectId2, ... ],
    batches: [ ObjectId1, ObjectId2, ... ]
}
```

```js
// Topics
{
    _id: ObjectId,
    name: string,
    description: string,
    release_date: datetime
    task: {
        taskId: ObjectId,
        description: string,
    }
}
```

```js
// Codekata
{
    _id: ObjectId,
    name: string,
    description: string,
    testCases: [{
        input: string,
        expectedOutput: string
    }]
}
```

```js
// CompanyDrives
{
    _id: ObjectId,
    date: datetime,
    companyName: string,
    students: [ ObjectId1, ObjectId2, ... ]
}
```