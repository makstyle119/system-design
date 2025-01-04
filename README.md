#  System Design

**note:** **over engineering** always sucks, either it will kill your app, your job or you. in short it's a bad thing and try to avoid it. maybe you asked how, well it's try to explain but sometime i stuck with it too. in simple word if I can say don't make things over complicated in other words don't use a gun to kill a mouse

**Q1- what is Design Pattern ?** <br />
**A1-** **Design Pattern** prefer to how you organize the code. it will focus on how organize the code

**Q2- what is MVC ?** <br />
**A2-** **MVC (Module View Controller)** - As per name **MVC** this system will have a module (to communicate with the database), a controller (to handle user request), and a view to render (to render a response)
- here are few key point in a **MVC**
    - it will be single repo
    - deploy on a single server
- **MVC** is a **design pattern**.

**Q3- what is Software Architecture ?** <br />
**A3-** **Software Architecture** is the structure of the code. **software architecture** follow how different system connect/communicate

**Q4- what is 3-tier Architecture ?** <br />
**A4-** in **3-tier Architecture** we will break all there component from **MVC** and separate them into different server. so your **model** (database)  will be host in different server, as well as your **view** (frontend) and your **controller** (backend). <br />
**example:** let's say you are using mongoDB as database so your model is on mongodb's server (aws/azure/ or what cluster you select), and you host your frontend which is on reactJS is host on vercel and for database you maybe use any cloud providing service - here you can see our system is divided on code level as well on hosting level as well.
- **3-tier** is an Architecture.
- the beauty of **3-tier** is if you want to boots your frontend or backend you can host more server to the specific end, and yes same for database

**Q5- what is System Design ?** <br />
**A5-** **System Design** is the process of solving a specific problem.

**Q6- what is a Monolith ?** <br />
**A6-** if a single serve is doing everything and project is wrap in one source control then it's a **monolith** application <br />
**example:** you write a app in js and deploy it in a server and maybe it have a database as well and the database is also in the same server and this single server is managing your app completely then it's a **monolith** application

**Q7- what is Micro Service ?** <br />
**A7-** **Micro Service** is when you break your system into smaller chunks (at architecture level). <br />
**example:** having different application (different codebase/server/repo) for user module, payment module and other stuff
- the beautify of **micro service** is as we see in the **3-tier** we can add frontend server or backend but the problem is - let's say your application is a e-commerce store and a lot of people spend more time on searching as compare to payment page so maybe you can host 2 server for searching and 1 for payment service because searching service get more traffic while in **3-tier** you have to upgrade the server for complete application
