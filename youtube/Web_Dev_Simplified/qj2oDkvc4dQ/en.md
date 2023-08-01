in this video we're going to be setting
up our entire project by connecting it
to a database setting it up with NBC and
deploying to a server on Heroku so we
can view our application on the web
let's get started now
the first thing we need to do in order
to get our project started is to use NPM
to initialize our project if you don't
have n PM or node installed already make
sure to check out my how to install of
node video which will be linked in the
cards and the description so what we
need to do is run NPM and knit and we
can just patch - why - this function
which will default all the parameters -
yes and just give us all the default
values inside of our package that JSON
here next we'll change this from index J
s to server DJ s those are just personal
preference and we can close out of that
that's all we need to do next
we can actually install the dependencies
that we're going to need in order to get
a basic Express server up and running in
order to do that we need to run NPM I
which stands for NPM install and past it
the list of packages we want in our case
we'll use Express through our server
EGS for a templating language and then
we'll use Express ejs layouts which will
allow us to create a layout file for all
of our HTML we can just add an enter and
let that run that's going to download
all the packages for us and it's going
to add those to our package JSON as you
can see here in our dependency section
and it creates a lock file for us the
last thing that we want to do is install
a development dependency so we can run
NPM I and you put - - save - dev which
will save this as a development
dependency and we want node Mon which
will allow us to automatically refresh
and restart our server every time we
make a change now that that's done we
can go to our package JSON here we'll
see it's a dev dependency and we can
actually create the scripts we want for
running our server the first script
we're gonna want is to be able to start
our storage normally so we're just gonna
call this start and this is just going
to run node server das wrap that in
quotes since it's a string this is just
going to start our server on a
production environment without a node
mom our next is going to be called dev
start which is what we're going to be
using most of the time to start our
server and this was going to run node
Mon serve it ideas and this is just
essentially the same thing as node
server jeaious except for it'll
automatically refresh our server every
time we make a change so now we can save
that and we're completely done with our
package JSON and NPM the next thing that
we want to do is set up our actual
server so it'll create a server Don JS
file and it here is where we're going to
get expressed
our application and running first thing
we'll do is we're going to import
Express from the Express library that we
installed NPM and we also want to get
the app portion of that by calling this
function of Express next we'll get the
Express layouts package that we
installed as well we're just going to
require that package in and now we can
work on actually configuring our Express
application so the first thing we want
to do is set our view engine so we'll
just say app dot set tell it we want to
set the view engine and in our case
we're going to be using EJ us as our
view engine so we'll just pasion ejs
here also we want to set where our views
are going to be coming from
so we'll say app dot set views and in
our case we're going to put them inside
of a views directory so we want to get
our current directory name and just
append it here to views and now if we
create a views folder over here in our
project this is where all of the
different views of our files are going
to go for our server and lastly what we
want to do is hook up Express layouts so
we can say app dot set and we tell it we
want to set of what our layout file is
going to be and essentially the idea
behind a layout file is that every
single file is going to be put inside of
this layout file so we don't have to
duplicate all of the beginning HTML and
ending HTML of our projects such as the
header and the footer so we just say
that that is going to be inside of a
layouts folder instead of a file called
layout and we also need to tell our
Express application that we want to use
Express layouts so we'll just say after
use and we pass in that Express layouts
variable that we included from that
library we also want to tell Express
where our public files are going to be
these are there's going to be our files
such as our style sheets our JavaScript
all of our images so we're just going to
say that is going to be in place called
Express static public so again this is
just going to be a folder in our
application which is called public so if
we create that here now we have a folder
with all of our public views and abuse
folder which is going to be all of our
server rendered views and this naming of
public is just a very common name that's
used most of the time when referring to
these public files now we can just tell
our app that we want
listen on a certain Court so we can say
app dot listen and we're going to want
to set this up to be processed
environment dot port which is going to
pull from an environment variable for
when we deploy the server is going to
tell us what port it is listening to not
us but for development we're just going
to default this to port 3000 since the
server is not telling us anything for
our hosting platform so we're just going
to use port 3000 and now if we save that
this is all that we need to get our
server up and running and down here we
can run npm run dev start which is that
command that we created earlier and if
we hit enter you should see that it says
that it's starting up our node server
and if we open up our application here
localhost 3000 you can see that our
server is running and it says that it
can't get anything and that's because we
have no traps set up in our application
so that's what we're gonna work on next
now in many smaller applications you may
see that people put all of their routes
inside of this server dot JS file but
for a larger application such as this
application it becomes very hard to
manage so we're going to use MVC to
layout our application and we're going
to put all of our routes which could
also be called controllers inside of a
routes folder so we can just create here
a routes folder and all of our routes
are going to go inside this folder and
the reason we're using the word routes
instead of controllers is because in
node.js and Express land most people
refer to controllers as routes but you
can think of them as exactly the same
thing we already have our views folder
which is where all of yous from MVC are
going to go and lastly we just want to
create a folder here called models and
this is where all of our database models
are going to be going now that we have
our MVC structure set up let's create
our very first route which is going to
be our index route so essentially
everything for when we don't actually
have a resource or a model in our URL
so in our Rhapsody we can create a new
file just call it index J s and instead
of here we're going to set up all the
routes like I said for our index of our
application and for now we're just going
to set up a single route at our route so
we first need to import Express again
because we're using Express for our
entire application so we'll get that
Express variable and we want to get the
router portion of that Express variable
so we're just going to call the router
function here on Express set this equal
to it and now with that router variable
that we just created we can actually
create our routes so we can just say
router
this is going to be using the get action
in order to get a root here and this is
just going to be our very root of our
application this is just going to be
localhost 3000 just like this and in
here we just pass it a function and this
function is going to take two parameters
one is the actual request of the request
and the next one is the response which
we're sending back and we're just going
to for now send a basic default response
so we'll just say response dot send
we're just gonna send some text that
says hello world just so we know that
this is working and now as you see this
is automatically to refresh by a node
montt and if we refresh our application
you'll see that nothing actually happens
and that's because we haven't actually
hooked up our application yet to use
this router our server doesn't know that
this router exists so we want to import
this router into our server in order to
do that we just want to come down here
and require that file that we just
created so we'll just call it our index
router and it's going to be equal to
require and require here is going to
take a relative path so you start it
with dot slash which says relative to
where we are where's this route and it's
inside of our routes folder and it
should start index route inside that
routes folder so now we have the
reference to this index router right
here inside of this require and we can
tell our app to use that so down here if
we can just say app dot use tell it the
route path that this is coming from in
our case this is just the root of our
application so we can just pinned it and
slash right here which just says very
root of our application and we tell it
what router we want to handle that route
and we'll just say it's our index router
and now if we save this you'll see that
we get an issue here with our
application it's crashing because it
doesn't know how to get any information
from this index file because we're not
actually exporting any information from
this file what we want to do is we want
to export this router that we've created
and set up in this application so we
just go down to the bottom here and we
type in module exports we want to set
that equal to our router now whenever we
import this file inside of our
application such as here we're requiring
this this index router variable is going
to be set to this router variable here
and again after we save that you see
that we're still getting a crash so if
we look back in our trace log here you
can see that it says required is not
defined and it tells us the line here
where this is an error and as you can
see I excellent
typed-in required instead of required so
let's change that to require save that
and check and now it says it's all green
so our server is working and if we
refresh this you now see we get that
hello world text being sent to us from
our server and we can change this to say
anything else that we want and if we say
that refresh our page you'll see that
it's being sent to us from our server
now that we have our routes being hooked
up with our actual server we can work on
integrating our routes with our views as
we created it here in our server da
Janice we set up this layout file so
let's actually create that layout file
for our application we'll just create a
new file here inside the layouts folder
initial is going to be called layout ejs
in order to have syntax highlighting
inside of an ejs file make sure you
download the EGS language support
extension and visual studio code if you
are using visual studio code otherwise
you'll have no syntax highlighting
inside of this file and inside of this
file we're going to set up the
boilerplate HTML for every page in our
application in vs code you can use type
exclamation point and hit enter and
it'll set up some basic HTML for you we
can change the title here to my berry
which is the name of our application and
then inside of the body here we want to
put all of the code that goes inside of
our application before and after every
single page so for example we can just
type in some text here that says 'before
we'll just add a line break so we know
that there's a little bit of spacing
between it and we want to put something
after maybe so we'll do after with
another line break but in between here
we want to put the content of everything
inside of our application so in order to
do that we're just going to use this
syntax which is a less than sign a
percent sign and then a hyphen and in
here we just type the words body and
this is just going to include every
single other one of our pages right in
here in this body page so now we can
actually create a view for our index of
our application so create a new file
we'll call it index ejs and inside of
this view here we're just going to put
some code that's called middle and this
is going to be imported from this index
TGS into this layout ejs filed right
here where it says body and now all we
need to do is go into our route here and
instead of just sending some basic text
we actually want to render our view so
we can save render and pass in the name
of our view which is just this in
EGS file now if we save that we get
everything green down here and we can
refresh our page and you see that even
though our index TGS only has the text
middle in it we're getting before middle
and after as because this layout file
this body section is importing
everything from every single one of our
pages in our application and this is
going to make developing our application
much easier because if we need to change
anything in our layout we only have to
do it in one file instead of having to
do it in every single one of our files
in our application it also makes it so
we don't have to copy and paste all this
boilerplate HTML every single time we
create a new page the last thing that we
have to do before our application is
fully setup is working on getting our
models integrated and to do that we're
just going to connect our application to
a local MongoDB database if you don't
already have MongoDB installed on your
computer make sure to check out my how
to install MongoDB video which will also
be linked in the cards and the
description so now let's go to our
survey das file and actually integrate
MongoDB into our application the first
thing that we need to do is install the
library for MongoDB so we just use NPM I
in order to install this and it's called
the Mongoose this is allowing us to
integrate with MongoDB extremely easily
inside of our application there we go we
have Mongoose installed in our
application and then we can work on
setting up our database let's just do
that right here after our application
and we can import Mongoose so we'll
import that from the library we just
installed and now we can set up our
connection for our database the first
thing we want to say is Mongoose dot
connect and in here we're going to
actually put the URL for our connection
but since you never actually want to
hard-code your connection you want it to
be dependent upon your environment
because when you're developing you want
Mongoose to connect to your local
MongoDB server but when you have your
application deployed you want to connect
to a server that's on the web somewhere
so in here we're going to pass a string
for the URL which is going to come from
our environment variables so we'll say
process T and V dot database URL and
we're going to set this up in just a
little bit and then the next thing that
this is going to take is some options
for how we want to set up MongoDB inside
of our application
in our case because of the version of
MongoDB that we're using we're going to
want to set up a variable here that says
use new URL parser we're going to want
to set that to true and this is just
because the Mongoose Chen by default
uses an older way of accessing data in
MongoDB which is deprecated currently in
MongoDB depending on when you watch this
tutorial this may already be changed to
true by default so you may or may not
need this you can just play around with
it on your own to figure it out now the
last thing we want to do is actually
just log if we are or are not connected
to our database so we can access the
connection here which is create a
variable called DB and we can just get
this from Mongoose dot connection and
then we can just say DB on error so if
we run into an error when we're
connecting to our database we're just
going to want to print that error out so
instead of here we can just do console
dot error error and this will just allow
us to print out our error in giant red
text in our console and we can just do
this once again we can say dot once
which is only going to run one time this
is just when we open up our database for
the first time so essentially once we
connect for the very first time we just
want to console dot log here that we've
connected to mungus so we can say
connected to Mongoose and there we go
that's all the code that we need to run
for this but if we try to run our
application here we're going to get an
error immediately and that's because our
application doesn't actually have this
variable for our database URL so we need
to set that up now to do that we're
going to be using a library which is
called D&V which will allow us to load
in environment variables into our
application so we can just NPM I - -
save dev since we only want it to be
locally that we use this and we can type
in that env oops didn't actually spell
that right env now if we run that it'll
actually go in and install this for us
and we just can create a DNV file over
here and inside of this we put our
different variables in our case we want
to put database URL and we just want to
set this to our database URL this URL is
going to take the form of MongoDB since
we're using MongoDB colon double
backslash and then we're going to put in
here the localhost since this is going
to be local to our application
and since our application is called my
Brer II will call the database that
we're accessing library and if we say
that we now have our database URL and
all we need to do is tell our
application to load that into it
so at the very top of our application
here we can just do a simple check to
check if we are running in the
production environment or not so we can
set process env no DMV this will be set
by default by node and we want to check
if this is not equal to production
because we don't actually want to load
in this environment variable unless
we're in our development environment so
we can say if it's not production then
we want to run some code to actually
load up those different dependencies so
we're required inv and we're just going
to say dot load this is going to load
all the variables from our D&V file here
and it's going to import them into our
process env variable in our application
now if we save that and try to rerun our
application you'll see here that it
should work and as you can see
everything is green and we got the
message saying that we are connected to
Mongoose and if we refresh our page our
application is still up and running now
the very last thing to do is set up our
application with git so if we just close
out of this we can type in get in it and
it will initialize our repository here
if you don't already have git installed
or don't understand how to use git make
sure to check out my learn kit in 20
minutes video which will also be linked
in the cards and in the description down
below now that we have get initialized -
we want to create a git ignore file in
our project just call it dot git ignore
and in here we're going to put all the
files we don't want to include in our
git repository in our case we don't want
to include our env file because we never
want to include these environment
variables they could be sensitive
information we don't want to share with
the world and we also want to not
include these node modules because as
you can see this is a huge set of
dependencies this is where NPM installs
everything your application requires and
it becomes a very very large but this
package JSON and package lock JSON file
hold all that information in a much more
condensed way so that when someone pulls
down your project they can just run npm
install and it will install all these
dependencies in node modules for them so
when I get ignore you want to also
ignore those modules now if we save that
you see in Visual Studio code
these actually gray out to let you know
that they're ignored and these green
files of new files we added so we can
run get add with a period after to add
everything in our folder and below which
is perfect everything's been added and
we can run git commit and we just call
it whatever you want we can just say
initial setup this is going to add all
these different files to our project and
there we go
we now have everything set up and we can
push it to a remote git repository now
in order to get that code on github we
could just go to github click on the
create new repository button give a
repository a name in our case we're just
going to call this my berry since this
is the name of our application leave the
description off for now set it to public
so that everyone can view it and we
don't want to initialize it with a
readme or a daggit ignore since we
already have all of our information here
we can just click create repository and
now all we have to do is if we see here
we can say or push existing code all we
have to do is copy these commands into
our command line here paste them here
and we can just say git push and there
we go that'll push all of our code up to
master for us and there we go we are
done now if we refresh this page you'll
see that all the code that we just wrote
is up and github for us to use the last
thing I want to do is deploy this code
to an actual server so that we can view
this on an Internet and the easiest way
to do that is going to be through Heroku
since we've already set up our code with
github all we need to do is create an
account on Heroku and then click the
create new app button from here you just
give your app a name in our case we're
gonna call it my Barry and then we just
click create app give it a different
name system's already taken we'll call
it my very web dev create that and then
from here all we have to do is follow
these steps to deploy we can use the
Heroku get CLI and all we have to do is
install the Heroku CLI and once that CLI
gets installed we can just copy over
this Roku login command paste this in
here and follow the instructions it'll
default to your git email which is fine
in our case and we need to enter our
password and then it'll say that you're
logged in properly and now we can have
that Heroku remote to our project
soldiers copy over this Heroku remote
since we already have our project
initialize with git and that'll run and
now it says that our remote has been
added and now since we've already added
and committed our code
we need to do is push to Roku so we can
just copy this command to push to karoku
paste this in here and that will run and
as soon as that's done running you'll
see that it starts building our server
on Heroku which is perfect and this will
take a little bit to run but once it's
done run you can actually access your
site on Heroku by just clicking this
open app button so we'll click this here
you'll see that it says that there's
nothing deployed right now so I'll come
back as soon as this finishes and now
that it's done deploying all we have to
do is refresh our application here
I'm usually a spin for a little bit
since it's just starting up our
application since we're on a free
application and as soon as that loads up
you'll see that our entire application
that we created with our index page is
going to be loaded up right here you'll
see that it throws an error and that's
because we don't actually have this
environment variable for our database
URL in our Heroku application so if we
go to Heroku go to the settings we can
configure our environment variables here
and we could just put the key which is
going to be our database URL and now we
need to come up with the value for this
key and since we don't have a database
on our server to access we need to
create a database separately from our
server and we can do that using MongoDB
Atlas which is a free way we can create
a database for MongoDB once you create
an account all you need to do is click
the build a cluster button and from here
we can just choose the cluster that we
want to build in our example we can just
choose a free AWS cluster here in North
America whichever is closest to you for
this case it's going to be here for me
this should just be defaulted for you
selected and we just want to keep all
these essentially completely default and
as you can see this is going to be
completely free for us and if we hit
create cluster it's gonna load for a
little bit and you see it's creating our
cluster right here and once this is done
being crated we can actually pull the
URL from this cloud hosted cluster into
our Heroku app over here and everything
should work just fine now that our
connection has finished initializing all
we need to do is click connect add a
MongoDB user in our case we'll call them
user and I'm just going to auto generate
here a secure password and we're gonna
want to copy this since we're going to
need to know this password for later we
can click create the user and now we can
choose a connection method in our case
we want to connect to an application and
we're going to use this string here so
back in our application we want to paste
down that password so we don't lose it
copy over this connection string just
like that and if we paste that into here
what we need to do is we need to take
that password that we created and we
need to change this connection strings
password section to have that password
so just delete that paste in that
password and then all we need to do is
click Add and now our database URL is
added into our config and our server
will be restarting with that
configuration file and we can try
refreshing our page here now as you can
see with that loading we have our actual
server up and running and that's all it
takes to get the base work of our server
set up and running in the next video
we're going to create our first model
which will be the author model and we're
also going to create the routes for the
create index and new page of that author
if you're enjoying this content please
make sure to subscribe to the channel to
not miss any more of these videos and
also check out the next video which is
going to be linked over here when it
comes out thank you guys very much for
watching and have a good day
