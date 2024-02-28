Whenever something is written into the primary node, its also written to the secondary nodes as well. This process is known as replication and due to it even if the primary node is lost the data will still be available in the backup nodes.

While MongoDB uses the RAFT protocol for leadership decisions like picking the main database (primary node), it adds its own twist.

Traditionally, RAFT picks leaders randomly. But MongoDB considers each server's importance (priority), how up-to-date its data is, and how quickly it responds when picking the new leader. So, it's like an election where votes depend on experience and speed, not just luck.

Not all servers in MongoDB write at the same time. This delay depends on how far apart they are, their internet speed, and how busy they are. If one server falls behind, it uses a special log (oplog) to catch up to the others.

MongoDB keeps an eye on how far behind each server is and can even step in if the delay gets too big. This way, your data stays safe and consistent even if things slow down a bit.

For massive datasets spread across the globe, you can split your data into smaller, replicated chunks stored in different places (sharded cluster). 

> Each chunk is like a smaller, 3-copy database itself (replica sets within the cluster).

Think of it as distributing your belongings across safe deposit boxes in different cities for maximum security and accessibility.