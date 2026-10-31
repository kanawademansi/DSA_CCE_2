# Music Playlist Manager (C++)

A menu-driven C++ console application that manages a music playlist using a **doubly linked list**. Songs can be added, deleted, displayed forwards and backwards, and navigated with next/previous controls.

> **Course:** DSA – CCE II (Unit IV)

---

## 1. Objectives

- Implement a doubly linked list with dynamic memory allocation in C++.
- Perform insertion at the end and deletion by title, handling all edge cases (first, middle, last, only node).
- Traverse the list in both directions using `next` and `prev` pointers.
- Build a user-friendly menu with input validation.
- Release all allocated memory before exiting.

## 2. Data Structure

Each song is stored in a node:

```cpp
struct Node {
    string songTitle;
    string artist;
    Node* prev;   // link to previous song
    Node* next;   // link to next song
};
```

| Pointer | Purpose |
|---|---|
| `head` | First song in the playlist |
| `current` | Song currently selected/playing |
| `p` | Helper for creating and deleting nodes |
| `q` | Helper for traversal |

A doubly linked list is used because the playlist needs to move both **forward** (next song) and **backward** (previous song) efficiently.

## 3. Features

| # | Option | Description |
|---|---|---|
| 1 | Add Song | Adds a song (title and artist) at the end |
| 2 | Delete Song | Deletes the first song matching a title |
| 3 | Display Playlist | Shows all songs from first to last |
| 4 | Display in Reverse | Shows all songs from last to first |
| 5 | Play Current Song | Plays the selected song |
| 6 | Play Next Song | Moves to and plays the next song |
| 7 | Play Previous Song | Moves to and plays the previous song |
| 8 | Play Complete Playlist | Plays every song in order |
| 9 | Repeat All | Plays the whole playlist twice |
| 10 | Show Current Song | Displays the selected song |
| 11 | Exit | Frees memory and quits |

## 4. Time Complexity

| Operation | Complexity |
|---|---|
| Add song (at end) | O(n) |
| Delete song by title | O(n) |
| Display forward / reverse | O(n) |
| Next / previous / current | O(1) |

## 5. Edge Cases Handled

- Deleting from an empty playlist
- Deleting the first, last, middle, or only song (the `current` pointer is moved safely)
- Empty song titles are rejected
- Invalid or non-numeric menu input
- No next song at the end, no previous song at the start
- All nodes are freed on exit (no memory leaks)

## 6. How to Compile and Run

**Requirements:** g++ (C++11 or later)

```bash
g++ your_file_name.cpp -o playlist
./playlist            # Linux / macOS
playlist.exe          # Windows
```

*(Replace `your_file_name.cpp` with the name of the source file in this repository.)*

## 7. Usage

1. Run the program and choose **1** to add songs (enter the title, then the artist).
2. Use **3** or **4** to view the playlist forwards or in reverse.
3. Use **5, 6, 7** to play the current, next or previous song.
4. Use **2** to delete a song by typing its exact title (case-sensitive).
5. Choose **11** to exit.

## 8. Sample Output

```
===== Music Playlist Manager =====
Enter your choice: 1
Enter song title: A
Enter artist name: A1
Added: "A" by A1

Enter your choice: 3
--- Playlist ---
1. A - A1

Enter your choice: 9
--- Repeat All: Pass 1 of 2 ---
Playing: A - A1
--- Repeat All: Pass 2 of 2 ---
Playing: A - A1
--- Repeat All finished ---

Enter your choice: 6
This is the last song. No next song.

Enter your choice: 2
Enter title of the song to delete: A
Deleted: "A" by A1

Enter your choice: 11
Playlist memory released. Goodbye!
```

## 9. Test Cases

| Test | Expected Result | Status |
|---|---|---|
| Delete / play on empty playlist | "Playlist is empty" message | Pass |
| Add one song, then display | Song listed as `1. A - A1` | Pass |
| Next song when on last song | "No next song" message | Pass |
| Delete a title that does not exist (`a`, `A1`) | "Song not found" message | Pass |
| Delete an existing title (`A`) | Song deleted, playlist becomes empty | Pass |
| Repeat All on empty playlist | "Nothing to repeat" message | Pass |
| Exit | Memory released, program ends | Pass |

## 10. Future Improvements

- Add a **stack** for "recently played" songs (undo/back history).
- Add a **queue** for "up next" songs.
- Insert a song at a chosen position and search by artist.
- Save and load the playlist from a file.

## 11. Author

**Mansi Kanawade** – Roll No. 6014  
GitHub: [kanawademansi](https://github.com/kanawademansi)
