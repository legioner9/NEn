foreign
are you tired of slow apis making your
applications luggish you're in the right
place in today's video we're going to
explore seven optimization techniques
that can help your apis perform at their
best
we've all been there you've built an
amazing API but it's just not as fast as
you like it to be but don't worry we are
here to help
before we start it's important to note
that optimization should not be the
first step in your process
optimization is powerful but it can lead
to unnecessary complexity you've done
prematurely the first step should always
be to identify the actual bottlenecks
through load testing and profiling
requests only begin optimization once
you've confirmed that an API endpoint
has performance issues
with that said let's get into the tips
first up caching this technique is one
of the most effective ways to speed up
your apis by caching restore the result
of an expensive computation so that we
can use it again later without needing
to redo the computation
if you have an endpoint that is
frequently accessed with the same
request parameters you can avoid
repeated database hits by caching the
response in redis or memcachd
most caching libraries make this easy to
add with just a few lines of code even a
brief period of caching can make a
significant difference in speed
next connection polling this
optimization technique involves
maintaining a pool of open connections
rather than opening a new database
connection for each API call
creating a new connection each time
involves a lot of handshake protocols
and setup which can slow down your API
this will use of connection can greatly
improve throughput
if you're using a serverless
architecture connection management can
be a bit more challenging
this is because each serverless function
instance typically opens its own
database connection and because
serverless can scale rapidly this could
potentially lead to a large number of
open connections that can overwhelm the
database
Solutions like AWS RDS proxy and azure's
SQL database serverless are designed to
handle this situation and manage
connection polling for you
closely related to database performance
our third tip is to avoid M plus one
query problems for example let's say you
are building an API endpoint to fetch
blog posts and their comments an M plus
one problem will occur if you first made
a query to fetch the post and enter for
each post you may another query to fetch
his comments now if you have M posts
this will result in one query for the
posts plus n queries for the comments
hence the term and plus one problem
to avoid this it's more efficient to
fetch the data in a single query or in
some cases two queries one to fetch the
posts and one to fetch all the comments
for those posts there's a voice making a
separate query for each post comments
and can significantly reduce the number
of round trips to the database this
improves performance
moving on to our fourth tip consider
using pagination
if your API response returns a large
amount of data you can slow things down
instead break the response into smaller
more manageable Pages using limit and
offset parameters this can speed up data
transfer and reduce low on the client
side
our fifth technique is about using
lightweight Json serializers
when returning Json responses from your
API the speed of your serialization
process can make a noticeable difference
in response times
consider using a fast serialization
library to minimize your time spent
converting your data into Json format
for our sixth Technique we have
compression
by enabling compression on large API
response payloads you can reduce the
amount of data transfer over the network
the client then decompresses the data
nowadays they're even more efficient
algorithms like broccoli that provide
better compression ratios also many
content delivery networks like
cloudflare can handle compression for
you offloading this tasks from your
server
finally we have asynchronous logging in
many applications the time it takes to
write logs is negligible however in high
throughput systems where every
millisecond counts the time taken to
write logs can add up in such cases
asynchronous login can help this
involves the main application thread
quickly placing the log entry into an
in-memory buffer while a separate
logging thread writes the logs to the
file or send them to the logging service
just keep in mind that with asynchronous
logging there's a small chance you might
lose some logs if your application
crashes before the logs have been
written
and there you have it seven tips to help
make your API faster and more efficient
if you have any other techniques that
you found useful let us know in the
comments
if you like our videos you may like our
system design newsletter as well it
covers topics and Trends in large-scale
system design trusted by 450 000 readers
subscribe that blog Dot bygo.com