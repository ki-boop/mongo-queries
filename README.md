# Last query - All languages 
```
db.collection.aggregate([
  {
    $project: {
      _id: 1,
      languages: {
        $objectToArray: "$languages",
      },
    },
  },
  {
    $unwind: "$languages",
  },
  {
    $group: {
      _id: null,
      languages: {
        $addToSet: "$languages.v",
      },
    },
  },
  {
    $sort: {
      languages: -1,
    },
  },
])
```
# Result
<img width="540" alt="image" src="https://user-images.githubusercontent.com/77934402/236606951-af418db4-b71a-47bb-ad9f-6f0175a24c8a.png">
