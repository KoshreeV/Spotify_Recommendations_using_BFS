BFS-Based Song Recommendation System 🎵
Overview
This project implements a Breadth-First Search (BFS) algorithm to generate song recommendations based on user interactions. The dataset consists of users and the songs they have listened to, forming a bipartite graph where users are connected to songs and vice versa. The BFS algorithm explores this graph to suggest new songs based on a user's listening history.

Graph Representation
The dataset is transformed into an undirected bipartite graph, where:

Users are connected to the songs they have listened to.
Songs are connected to the users who have listened to them.
This ensures that BFS alternates between users and songs at each level of traversal.
BFS Traversal for Song Recommendations
The BFS algorithm starts from a given user and expands outward level by level:

Hop 0: The starting user.
Hop 1: Songs directly listened to by the user.
Hop 2: Other users who have listened to those songs.
Hop 3: New songs that those users have listened to.
The final output groups recommended songs based on their hop distance from the starting user.

Why Are Some Hops Missing?
During BFS traversal, the output sometimes contains only hops = 1 and 3, skipping hop = 2. This occurs due to the bipartite nature of the graph:

Hop 2 represents users, but BFS only records songs as recommendations.
Since BFS alternates between users and songs, it skips users when collecting results, moving directly from songs at hop 1 to new songs at hop 3.
If no new songs are discovered at hop 2, BFS naturally progresses to hop 3.
Why Use a Double-Ended Queue (deque)?
BFS requires an efficient queue to process nodes in order. The deque (double-ended queue) is used because:

O(1) time complexity for adding/removing elements from both ends.
Efficient memory management compared to a standard list.
Time Complexity Analysis
The BFS traversal runs in O(V + E) time, where:

V is the number of users and songs (graph nodes).
E is the number of interactions (edges connecting users to songs).
This ensures an efficient recommendation system, as each user, song, and connection is processed only once.
Output File (comprise.csv)
The recommendations are saved in a CSV file with columns:

User Name: The user for whom recommendations are generated.
Hops: The number of hops from the user.
Recommended Songs: Songs suggested based on BFS traversal.
Conclusion
This BFS-based recommendation system efficiently provides personalized song suggestions while maintaining scalability. The absence of hops = 2 in some cases is expected due to the nature of the bipartite graph.
