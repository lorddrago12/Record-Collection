# 🎵 Record Collection

A JavaScript utility for managing a music record collection. Supports adding, updating, and deleting album properties — including dynamic track list management.

---

## 📦 Data Structure

Each record is stored by a numeric ID and may contain the following fields:

| Field        | Type       | Description                        |
|--------------|------------|------------------------------------|
| `albumTitle` | `string`   | The title of the album             |
| `artist`     | `string`   | The name of the artist             |
| `tracks`     | `string[]` | An array of track names            |

```js
const recordCollection = {
  2548: {
    albumTitle: 'Slippery When Wet',
    artist: 'Bon Jovi',
    tracks: ['Let It Rock', 'You Give Love a Bad Name']
  },
  2468: {
    albumTitle: '1999',
    artist: 'Prince',
    tracks: ['1999', 'Little Red Corvette']
  },
  1245: {
    artist: 'Robert Palmer',
    tracks: []
  },
  5439: {
    albumTitle: 'ABBA Gold'
  }
};
```

---

## 🛠️ `updateRecords(records, id, prop, value)`

Updates a record in the collection based on the given rules.

### Parameters

| Parameter | Type     | Description                                      |
|-----------|----------|--------------------------------------------------|
| `records` | `object` | The full record collection object                |
| `id`      | `number` | The ID of the album to update                    |
| `prop`    | `string` | The property to update (`albumTitle`, `artist`, `tracks`) |
| `value`   | `string` | The new value to set (empty string to delete)    |

### Returns

The updated `records` object.

---

## ⚙️ Update Rules

| Condition                                      | Behavior                                              |
|------------------------------------------------|-------------------------------------------------------|
| `value === ""`                                 | Deletes the `prop` from the album                     |
| `prop !== "tracks"` and `value !== ""`         | Sets or updates `records[id][prop]` to `value`        |
| `prop === "tracks"` and album has no `tracks`  | Creates a `tracks` array and appends `value`          |
| `prop === "tracks"` and album has `tracks`     | Appends `value` to the existing `tracks` array        |

---

## 💡 Usage Examples

```js
// Update an album title
updateRecords(recordCollection, 5439, 'artist', 'ABBA');
// recordCollection[5439].artist === 'ABBA'

// Add a track to an existing list
updateRecords(recordCollection, 2548, 'tracks', 'Bad Medicine');
// recordCollection[2548].tracks === ['Let It Rock', 'You Give Love a Bad Name', 'Bad Medicine']

// Add a track to an album with no tracks property
updateRecords(recordCollection, 5439, 'tracks', 'Dancing Queen');
// recordCollection[5439].tracks === ['Dancing Queen']

// Delete a property
updateRecords(recordCollection, 2548, 'artist', '');
// recordCollection[2548].artist is now deleted
```

---

## 📁 Project Structure

```
record-collection/
├── recordCollection.js   # Collection data and updateRecords function
└── README.md             # Project documentation
```

---

## 🚀 Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/lorddrago12/Record-Collection.git
   ```

2. Open `recordCollection.js` in your editor or browser console.

3. Call `updateRecords()` with your desired parameters to manage the collection.

---
