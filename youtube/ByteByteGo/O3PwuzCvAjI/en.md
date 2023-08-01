In this video, we’re going to discuss not just a  database migration but a colossal task Discord  
engineers embarked on - moving trillions of  messages from one database to another.
If you’ve ever wondered what it takes to  migrate data of such unimaginable scale,  
you’re gonna love this. Let’s dive right in.
I’ve been eager to talk about this  topic ever since I joined Discord.
The engineering culture here  is dynamic and innovative,  
and this story is a perfect illustration  of that. Though this is all from public  
information, the insights  and takeaways are my own.
Discord recently peeled back the curtain  on how they migrated trillions of messages  
from Cassandra - the database that  houses your chats and conversations,  
to ScyllaDB - a faster  and more reliable alternative.
The process was first shared at  ScyllaDB Summit 2023 by Bo Ingram,  
followed by a detailed blog post.
A big shout-out to Bo for presenting  this complex process so clearly.
So, what did Bo share? I’ll summarize  and share my own takeaways. You can  
watch his video and read his blog post  if you want to learn more about it.
Let’s rewind back a few years.  Discord found themselves in a  
bit of a pickle with their database choice.
They were using Cassandra, but as the platform  
continued to grow, they faced  serious performance issues.
It took a lot of effort to maintain the  main Cassandra cluster that held messages.  
The latency was unpredictable, and the frequent  on-call incidents put huge strain on the team.
By 2022, the Cassandra cluster held  trillions of messages across 177 nodes.
They knew they needed something different,  
but this message cluster was critical to  Discord. If the message cluster is slow,  
Discord is going to be slow. If the message  cluster is down, Discord is going to be down.
Their solution? ScyllaDB, a  Cassandra-compatible database,  
but with a more powerful C++  based engine under the hood.
Instead of jumping in headfirst to  solve the riskiest and biggest problem,  
they started the migration with smaller databases.
And this is my first takeaway. At Discord, the  engineers move fast when mistakes are reversible,  
but if the solution is a one-way door, they  spend a lot more time and care to get it right.
They used these small migrations as an  opportunity to test the waters and iron  
out as many issues as possible before tackling  the big beast that held trillions of messages.
Let’s talk a bit about ScyllaDB. It was  written in C++ and promised better performance,  
faster repairs, and most importantly, it was  garbage collection-free. For a team that had  
so many issues with Cassandra's garbage  collector, this was a breath of fresh air.
The next key step was to create  an intermediate layer between the  
API monolith and the database clusters called  data services. The layer was written in Rust,  
which is a safe and highly performant  language. And it’s a joy to write in Rust.
The really cool idea about this layer  is something called request coalescing.  
If multiple users request the  same data, the database only  
needs to be queried once. This drastically  reduced the potential for hot partitions.  
Imagine all those unintended @everyone  messages in hugely popular discord servers.
With this layer in between, it is  no problem for the database at all.
Then, they came up with the concept  
of a Super-Disk. The database  clusters run on Google Cloud.
When faced with the challenges of disk latency,  they couldn't rely on the local NVMe SSDs on  
the virtual machines for their critical data  storage due to reliability and durability issues.
The alternative was Google Cloud’s Persistent  Disks. While it was reliable and flexible, it had  
the disadvantage of higher latency since they were  network-attached rather than directly attached.
So, what did Discord do? They went back to  the drawing board and focused on creating a  
solution tailored to their specific needs. They  chose to prioritize low-latency disk reads over  
all other disk metrics while maintaining  the existing database uptime guarantee.
What they came up with was a  super-disk combining the best  
of local SSDs and Persistent  Disks at the software level.
Their super-disk was a two-layered RAID solution.  They used RAID0 to combine multiple Local SSDs  
into one low-latency virtual disk, and then RAID1  to mirror this RAID0 array with a Persistent Disk.  
They then configured the linux kernel to direct  the write to the persistent disk, which had  
strong durability guarantee, and the read to the  local SSDs, which offered low latency. This setup  
ensured low-latency reads from the Local SSDs  and write durability from the Persistent Disks.
What's so great about this? It's an  excellent example of problem-solving  
from first principles. Discord was  dealing with a problem that had no  
ready-made solution. Instead of trying  to make do with what was available,  
they redefined the problem based on their  specific needs and then built a solution to match.
The super-disk worked. At peak load, the  databases no longer started queueing up  
disk operations, and they saw  no change in query latency.
Finally, with all this prep work done,  
it was time to migrate their largest  database - the 'cassandra-messages'  
cluster. With trillions of messages and  nearly 200 nodes, it was a daunting task.
But with a newly written data migrator  in Rust and some clever strategies,  
they managed to do it in just nine days! Yes,  
you heard that right - they migrated trillions of  messages with NO downtime in less than two weeks!
And the payoff? A significantly  quieter, more efficient system.  
They went from running 177 Cassandra  nodes to just 72 ScyllaDB nodes. It  
drastically improved latencies and the  quality of life for the on-call staff.
It was no ordinary task, but  with clever risk mitigation  
and innovative solutions, they pulled it off.
So there you have it. I’m incredibly proud  of what the team was able to pull off.  
Migrating a production database is no joke,  and doing it at this scale… well, it is hard.
If you like our videos, you may like  our system design newsletter as well.  
It covers topics and trends in large-scale  system design, trusted by 400k readers.
Subscribe at blog.bytebytego.com.
