foreign
have you ever tried wrapping your mind
around oauth 2 but ended up lost in the
sea of jargons that's why we're here
today we're breaking down these complex
Concepts into digestible explanations
let's Dive Right In
imagine the early days of the internet
sharing info was straightforward just
hand over your username and password to
another service and they could access
anything they wanted
this practice is frowned upon these days
but we might still encounter this
practice in certain personal finance
software to scrape information from
crusty old Banks luckily we have
something much better these days enter
oauth 2.
oauth2 is like giving someone a special
key this key allows them to access
specific information in another
application we control who gets access
to our data without having to share a
password and yes we can revoke that key
at any time
now let's play this out with an example
consider a photo storage application
Snap Store we've been using it to store
our photos and now we want to print some
of them using a third-party printing
service print Magic
instead of manually uploading each photo
to pre-magic we asked pre-magic to do
the job
with a simple click we Grant pre-magic
permission to access our photos on
snapstore
using oauth2 pre-magic and then access
our Snap Store photos on our behalf
without ever knowing our Snap Store
login credentials
this is an example of the or flow it's
an elegant stance between us pre-magic
and snapstore all orchestrated by of2
now let's unpack this further
in this context we are the resource
owner because we own our photos on
snapstore snapstore is the resource
server that stores our photos
pre-magic is the client that wants to
access the photos the authorization
server could be a part of snapstore or
an external identity provider and is
responsible for handling the oauth2
process
let's follow the oauth2 flow in this
scenario it begins when we instruct
pre-magic to fetch photos from snapstore
pre-magic sends a client ID and scope
which represent the access level
requested to snap storage authorization
server
as a resource owner we authenticate
directly with snapstore and Grand Prix
magic the consent to access our photos
once consent is granted the
authorization server sends an
authorization code back to pre-magic
pre-magic then presents this
authorization code is client ID and
client secret to the authorization
server
the client secret is a private key
shared only between pre-magic and the
authorization server
if the authorization server verifies the
authorization code client ID and client
secret IT issues an access token to
pre-magic
finally pre-magic uses this access token
to request our photos from snapstor's
resource server
this oauth2 process ensures that our
Snap Store login credentials are never
exposed to pre-magic while allowing
pre-magic to access only the photos we
authorized it to see
it's also important to note that the
access token can be set to expire after
a certain time or can be revoked by us
at any point providing an additional
layer of security
oauth2 also support refresh tokens which
can be used to obtain a new access token
when the old one expires without
requiring our intervention
that's all of 2 in a nutshell is an
essential piece of the web security
infrastructure and the backbone of many
secure Seamless app interactions we use
daily
if you like our videos you might like
our system design newsletter as well it
covers topics and Trends in large-scale
system design trusted by 400 000 readers
subscribe that blog Dot bybico.com