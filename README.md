#  System Design

**note:** **over engineering** always sucks, either it will kill your app, your job or you. in short it's a bad thing and try to avoid it. maybe you asked how, well it's try to explain but sometime i stuck with it too. in simple word if I can say don't make things over complicated in other words don't use a gun to kill a mouse

## Question & Answer

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

**Q8- what is distributed computing ?** <br />
**A8-** in short, if any system run in different computer, for example a server running in different ec2 instances of AWS.

**Q9- What is Availability ?** <br />
**A9-** let's say you have a system and it's run one a single machine, and it this system break (either code error or something wrong with system) your system will no longer available for the people on internet. so this system have 0 **availability**, let's say you host your system into 2 server so even if one server is down you can use second server for the people who want to access your system. and this is what we called **availability**

**Q10- What is High Availability ?** <br />
**A10-** As we discuss in last question that having a backup is **availability** but we all know that maybe backup system will go down as well, so we measure the **availability** and decide if the server is high available or not <br />
we measure **availability** in **9**, so 1-9 would be 90% which mean in one year this service could be down in 36.5 days, second we have 2-9  which is 99% which mean service will be down 3.65 days in one year (all this are worst case scenario) and so on as 3-9 to 4-9 <br />
the bench mark is 4-9 (99.99%) which mean less then one hour per year

**Q11- What is Reliability ?** <br />
**A11-** in simple words, does the app do what it's suppose to do.

**Q12- Availability vs Reliability ?** <br />
**A12-** **Availability** is if the service is available to access and **Reliability** is if service functional as it should be functional.

**Q13- What is Consistency ?** <br />
**A13-** **Consistency** is something that everyone see same thing, (this only something if you work with **distributive system**).
- in **monolith Architecture** you have one db and everyone seeing data from that database so it will have 100% **Consistency**
- in **micro service** all your services have their own database so their is a chance data might be inconsistency

**Q14- What is Strong Consistency ?** <br />
**A14-** If you change some data in one server and all server is showing same data as we update it's **strong consistency**.
- **How to apply it**
    - it's simple in your first server where you update the data, data will stay in pending state until it get conformation that all the server have same data then it will update the data in the first server.
    - prefer for banking, medical stuff, military
- `+ point:` everything is consistence
- `- point:` take a little time

**Q15- What is Eventual Consistency ?** <br />
**A15-** If you change some data in one server and other server get this data in some time it's **eventual consistency**.
- **How to apply it**
    - it's simple first you update the first server which get the data request and after that or maybe after x amount of time or every hour you update data in other servers as well.
    - prefer for social media, basic crud app
- `+ point:` current server update quickly
- `- point:` other server take time to update

**Q16- What is Scalability ?** <br />
**A16- Scalability** is if your app can handle workload and **consistency** from a spiky traffic. in simple word if you have more resource then your spiky traffic then yes your app is scalable. but there is some other way to manage **scalability** if your server go beyond the available resource. there are two ways to manage it
1. **Vertical Scaling:**
    - In vertical scaling you will increase the resources of the existing server. but still stay 1 server (also know as scaling up)
2. **Horizontal Scaling**
    - In horizontal Scaling you will add more number of server. you go from one to many (also know as scaling down)

**Q17- What is Elasticity ?** <br />
**A17-** In **Elasticity** we will only increase the workload when their is a increase if work. so if you get more user there will be more server and if number of user decline server will be delete as well. (available in cloud)

**Q18- What is Single Point Of Failure - (SPOF) ?** <br />
**A18- Single Point Of Failure - (SPOF)** is if your service failed because you're server down and you don't have any backup.

**Q19- What is Redundancy ?** <br />
**A19- Redundancy** is having a extra layer of backup if something go down. One important thing to remember **redundancy** is more cost because now you need to manage multiple servers

**Q20- What is Fault Tolerance ?** <br />
**A20-** We have **Fault Tolerance** by removing **Single Point Of Failure** - and how by adding **redundancy** - so basically adding **redundancy** and removing **single point of failure** is **Fault Tolerance**

**Q21- What is Database Replication ?** <br />
**A21- Database Replication** is adding **redundancy** in the database - in other words creating a replica of existing as backup

**Q22- What is Database Cluster ?** <br />
**A22- Database Cluster** is having multiple database replica - 

**Q23- What is Synchronous and Asynchronous Replication ?** <br />
**A23- Synchronous Replication** is **Strong Consistency** and **Asynchronous Replication** is **Eventual Consistency**.

**Q24- What is Latency ?** <br />
**A24-** Time while getting the response. it can be on database **consistency**, either loading a landing page or something other.

**Q25- What is ACID - (Atomicity, Consistency, isolation, durability) ?** <br />
**A25-** Well it can be a little tricky to define:
- **Atomicity:** either thing you do in your system will be success or failed
- **Consistency:** means you can't create change which will break existing rules - common example deleting something which have foreign key reference
- **Isolation:** transition should be isolated
- **Durability:** permanent - once the data save it stay even if server down

**Q26- What is Database Partitioning?** <br />
**A26-** Database Partitioning is dividing a table into 2, there are 2 ways to do this:
- **Vertical Partitioning:**
    - divide a table's by columns
- **Horizontal Partitioning:**
    - dividing a table's data by rows

## Key words
- *Stale is use for old(incorrect) data*
- *note is a compute/server in multi computer system*
- *Database **Partitioning** at note level is know as **sharding***