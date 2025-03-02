# README

## About
This is a simple **Task Planner** application.

It is implemented to respond to RESTful request and serve JSON responses.

Made with Ruby on Rails 7.

## Deployment

### Requirements / Tech Stack

- **Ruby** 3+
- **Ruby on Rails** 7+
- **SQLite** 3+

### Prerequirements
On an Ubuntu- or Debian-eske system, prerequired packages can be installed via:
```
sudo apt install ruby-full build-essential zlib1g-dev libsqlite3-dev libyaml-dev sqlite3 ruby-sqlite3
```

### Installation
```
git clone https://github.com/sor/tasks_restful
cd tasks_restful
bundle install
rails db:migrate
```

### Run
```
# Run in development mode
rails server

# Run in production (though it is not recommended to use SQLite in production)
rails server -e production
```

## Commands to test the functionality

### List
`curl http://localhost:3000/tasks`

### Create
```
curl -X POST http://localhost:3000/tasks \
	-H "Content-Type: application/json" \
	-d '{"task": {"title": "Tierarzt Besuch", "description": "Katze zur Impfung bringen - 12. Juni 2025 um 11 Uhr", "completed": false}}'
```

```
curl -X POST http://localhost:3000/tasks \
	-H "Content-Type: application/json" \
	-d '{"task": {"title": "My Task", "description": "Do something", "completed": false}}'
```

### Individual Details
`curl http://localhost:3000/tasks/1`

`curl http://localhost:3000/tasks/2`

### Update
Single property
```
curl -X PUT http://localhost:3000/tasks/1 \
	-H "Content-Type: application/json" \
	-d '{"task": {"completed": true}}'
```

Multiple properties
```
curl -X PUT http://localhost:3000/tasks/1 \
	-H "Content-Type: application/json" \
 	-d '{"task": {"title": "Updated Title", "description": "Updated description", "completed": true}}'
```

### Delete
`curl -X DELETE http://localhost:3000/tasks/2`


## What was done
- Setup *WSL* (On Windows 10, WSL Version 2)
- Install *Ubuntu 22.04*
- `sudo apt update && sudo apt upgrade`
- `sudo apt install ruby-full build-essential zlib1g-dev libsqlite3-dev libyaml-dev sqlite3 ruby-sqlite3`
- `rails new tasks_restful --api -d sqlite3 --skip-bundle`
- `cd tasks_restful`
- edit *Gemfile*, change
	- from: `gem "sqlite3", ">= 1.4"`
	- to:   `gem "sqlite3", "~> 1.4"`
- `bundle install`
- `rails generate scaffold Task title:string description:text completed:boolean`
- `rails db:migrate`
- `rails server`

