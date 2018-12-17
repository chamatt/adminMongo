# adminMongo on Dokku

A repository to help you setup [adminMongo](https://github.com/mrvautin/adminMongo) on a Dokku server with basic authentication, to help you manage your dokku mongoDB databases from anywhere.

(Although it's not safe to expose it to the world, use a strong password, and use at your own risk, i take no responsability)
 
# Installation

### Clone the repo on your local machine:

```git clone https://github.com/chamatt/dokku-adminMongo.git```

### Setup you authentication info on auth.json file (defaults to admin:admin):

```
{
  "username": "admin",
  "password": "admin"
}
```

### Create an app on your dokku server, with whatever name you want (example: adminmongo):

```dokku apps:create adminmongo```

### On your local machine, add your dokku server as a remote repository and push to it (change mydomain.tld to your domain):
```
git add .
git commit -m "Changed auth information"
git remote add dokku dokku@mydomain.tld:adminmongo
git push dokku master
```

Now it's ready to be used!

# Usage

If you want to access a mongodb database hosted in your dokku server, you need to link this database to adminmongo, like this (run this from your dokku server):

```dokku mongo:link yourdbname adminmongo```

Then get the connection string to this db by running:

```dokku mongo:info yourdbname```

Its gonna look like this: mongodb://<db_user>:<db_password>@<db_host>:27017/<db_name>

Copy this string, go to: adminmongo.yourdomain.tld, login with your authentication info, and paste it on "Connection String", and add a new connection.




