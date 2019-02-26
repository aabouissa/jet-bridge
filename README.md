Jet Bridge
==========

**Universal admin panel for Django**

![Preview](https://raw.githubusercontent.com/jet-admin/jet-bridge/master/static/overview.gif)

Description
===========

* Jet Admin: https://jetadmin.io
* **Live Demo**: https://app.jetadmin.io/demo
* Documentation: https://docs.jetadmin.io/
* Support: support@jetadmin.io

**Jet** is a SaaS service that automatically generates back office for your Django Application through REST API of **Jet Bridge** package installed to your project.

– **Visual**. Admin interface can be easily changed without need of development with the help of Visual Editor.

– **Secure**. Jet does not access your data: its transferred directly from browser to your application.

– **Customizable**. Flex functions allow you to solve your specific business tasks when standard functionality is not enough.

This is a complete remake of popular [Django Jet](https://github.com/geex-arts/django-jet) admin interface.

- **Visual editor:**

  Customize the admin area to make it easy for any manager to use. Allow managers to modify the interface, configure features, and set up analytics widgets without using any developers — just like WIX, Squarespace….

- **Secure:**

  Your data is safe. We do not have access to your information. We simply plug your information in to an easy-to-use interface for you to interact with it better.
  
  - **Works with any technology:**

  The interface is generated automatically based on an analysis of the data and data structure of your applications.

- **Quick installation:**

  It takes only a few hours to integrate with your project.

- **Available 24/7:**

  Use it around the clock and don’t worry about updates — we take care of that.

Features
========

- **CRUD (create, read, update, delete):**

  All common operations to view, create, update or delete data. 

- **Search and Filter:**

  Filter data easily by any field with most common lookups and search them by text occurrence. For some specific cases you can create SQL Segment to filter with.
  
- **Segments:**

  Segments allow you to save applied set of filters as a Segment or create it from SQL query for quick use in future. 
  
- **Export:**

  You can export all collection data or part of it into the most common formats like CSV or Excel.

- **Dashboards:**

  Create different types of charts, tables and other widgets to visualize your KPIs or monitor data without programming – inside your visual interface. Complex data queries can be created with SQL.

- **Teams and Permissions:**

  Invite users to collaborate on a project and assign access rights based on their team.

- **Responsive Layout:**

  The interface is optimized for any device from phones to tablets to desktops.
  
- **WYSIWYG Interface Customization**

  You can customize almost every part of interface visually – navigation menu, collection list views, record create/update forms.

- **Custom Views**
  
  For very specific pages you can create your own custom FlexView based on React, Angular or any other framework and integrate it in Jet Admin interface. Writing your own custom JS/CSS/HTML has no limits in implementing any page you need.

- **Custom Actions**

  If need to run some operations on records or any other business logic inside your Backend you can create FlexActions and run them directly from Jet Admin interface. Passing some additional parameters to your Backend is supported.

- **Custom Fields**

  Sometimes using existing fields is not enough and you need to create custom which can be a combination of multiple fields, use fields from related collections and be result of some calculation. In this case you can use FlexField and write your custom JavaScript function which can format fields data any way you want.

How It Works
============

Integrating Jet Admin with your project requires installing only one component - Jet Bridge.

![Jet Admin architecture](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LQ08RFAKZvFADEiXKFy%2F-LWGeA3oSBVFoNy8gVVi%2F-LWGozY2Zrbc4W3JmrIg%2Fimage.png?alt=media&token=d09de1b5-b56f-4d0e-aece-8c578752bac8)

**Your app**

Any of your applications which works with database. Jet Admin does not interact with it.

**Database**

Your database Jet has no access to.

**Jet Bridge**

An open source application installed on your server's side and connected to your database. Used for automatically API generation based on your data structure. It is needed for Jet Admin to operate with your data. 

**Jet Interface**

Web application accessible from any browser. Maintaining and updating this web application is on Jet Admin team side. Your data is transmitted directly from Jet Bridge to Jet Interface which works in your browser and remain invisible for the Jet service.

Requirements
============

- **Python** 2.7 or 3.4+
- Any of the following **SQL Databases**:

  - PostgreSQL
  - MySQL
  - SQLite
  - Oracle
  - Microsoft SQL Server
  - Firebird
  - Sybase

Installation
============

1. Install **jet\_bridge** package using pip or update if you did it before

```bash
pip install jet_bridge -U
```

2. Install appropriate database adapter

```bash
# for PostgreSQL
pip install psycopg2
# for MySQL
pip install mysqlclient
```

3. Run **Jet Bridge** for your configuration.
You can read about all possible settings at [Configuration](configuration.md) page.

```bash
DATABASE_ENGINE=postgresql \
    DATABASE_HOST=host.docker.internal \
    DATABASE_PORT=5432 \
    DATABASE_NAME=database \
    DATABASE_USER=postgres \
    DATABASE_PASSWORD=password \
    jet_bridge
```

![Result of running Jet Bridge](https://github.com/jet-admin/docs/raw/master/.gitbook/assets/image%20%2828%29.png)

4. Register your project by opening in your browser:
**http://localhost:8888/** where **localhost** is your **Jet Bridge** HOST and **8888** is its PORT.
If you want to run Jet Bridge on different host/port you can configure it \(read more at [Configuration](configuration.md) page\).

> If you don't have **Jet** account yet you will be asked to create one and sign in with the existing account.

> After registering your project you will be redirected to your project and can start working with **Jet**

After registering your project you will be redirected to your project and can start working with **Jet**

### Method 2. Using Jet Bridge inside Docker

**Jet Bridge** has **Docker** image available on [Docker Hub](https://cloud.docker.com/u/jetadmin/repository/docker/jetadmin/jetbridge).
In order start it inside **Docker** for your configuration run the following command.
You can read about all possible settings at [Configuration](configuration.md) page.

1. Install **Docker** if you don't have it [https://docs.docker.com/install/](https://docs.docker.com/install/)
2. Make sure **Docker** is running
3. Update **Jet Bridge** image if downloaded it before

```text
docker pull jetadmin/jetbridge
```

4. Run **Docker** container. This will run Jet Bridge on **http://localhost:8888/.**

> If you want to run on different port change it here:
> ****`... -p 9000:8888 ...` – this will run on **9000**

```bash
docker run -p 8888:8888 \
    -e DATABASE_ENGINE=postgresql \
    -e DATABASE_HOST=host.docker.internal \
    -e DATABASE_PORT=5432 \
    -e DATABASE_NAME=database \
    -e DATABASE_USER=postgres \
    -e DATABASE_PASSWORD=password \
    jetadmin/jetbridge
```

> If you are using **Docker before 18.03** you can't use `host.docker.internal` for DATABASE\_HOST
> **Docker 17.12 – 18.02** use `docker.for.mac.host.internal`
> **Docker 17.06 – 17.11** use `docker.for.mac.localhost`
> **Docker 17.05 and below** your `local host IP address` \(can be found using `ifconfig` command\)

5. Register your project by opening in your browser:
**http://localhost:8888/** where **localhost** is your **Jet Bridge** HOST and **8888** is its PORT.
If you want to run Jet Bridge on different host/port you can configure it by changing **Docker** container port in this command.

> If you don't have **Jet** account yet you will be asked to create one and sign in with the existing account.

> After registering your project you will be redirected to your project and can start working with **Jet**

Support
=======

Feel free to Email us – support@jetadmin.io

License
=======

This project is **MIT** licensed - see the LICENCE file for details.