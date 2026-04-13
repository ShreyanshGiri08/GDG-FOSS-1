# Tech Deep Dive: FastAPI
**Written by:** Shreyansh Giri | LCS2025008


## The Hook: Why I Chose This Stack
As I dived deeper into the world of ML ,I learned about NumPy,Pandas,Scikit Learn , ML algorithms and various other libraries. But the problem in front of me was that I wanted to integrate them into my projects and serve my models to a web app.Because just by creating models with a high accuracy , I could not solve some real world issue, I actually needed to present it in a form where people could actually use it. Since I had already become comfortable with Python , FastAPI felt like the best option for integration of backend due to my comfort with the language.It is also the **fastest  python Web Framework**. 

With it , I could directly import my ML models and scikit learn pipelines into the same codebase. I also knew SpringBoot , but It was very unclear on how to use it for my models , Switching between JAVA and Python was also a problem for me. I was also captivated by /docs section of FastAPI which automatically wrote documentations for my API endpoints. It was really efficient for me , as it saved my manual work to write documentations. There was no need for Postman as well , as i could test every endpoint in the browser itself.  This was the biggest selling point for me. 

I integrated it for the first time in my Vector Visionary project and got outstanding outcomes with maximum efficiency and productivity . Since then , It has become my favourite TechStack. In a nutshell, I can say that it changed how I see ML , our models are not significant unless they can be served to people to solve their real world issues.

## Under the Hood: How it Works
-FastAPI is built on top of **Starlette** and **Pydantic**. Starlette is the actual web framework handling all the low level stuff like HTTP requests, routing, and middleware. FastAPI just adds a powerful layer on top of it

-Pydantic sits at the core of FastAPI — it is a data validation library that uses Python type hints to automatically check if incoming data is correct before it even reaches your logic.

-Every route is defined using decorators  such as  **@app.get()**, **@app.post()** — these tell FastAPI what HTTP method and URL path triggers which function.  Whatever the function returns , FastAPI itself converts it to JSON, so no manual conversion is needed .

-FastAPI uses **Python's async/await** which means it can handle multiple requests concurrently without blocking.

-**Uvicorn**  is the ASGI (Asynchronous Server Gateway Interface) server that runs FastAPI,ASGI is just the modern standard for  async Python web servers . Uvicorn actually listens for incoming HTTP requests.It is lightweight and fast.

-Swagger UI auto-generates at /docs directly from our code , so it saves our documentation work and increases efficiency of our tasks.

-**CORS middleware** ( Cross Origin Resource Sharing) is used which is  basically a security rule that tells the backend which frontend URLs are allowed to make requests to it.

- the ORM(Object Relational Mapper) generally used is **SQLAlchemy**  which converts Python Classes into database entities.However it is not built in.

-Response models in FastAPI ensure  our API always returns consistent, typed, predictable data.

## The Trade-offs: Pros and Cons

**Pros:**
  - It is the fastest Python web framework , it takes very less amount of time to setup.
  - AutoDocumentation feature saves our manual work and increases productivity.
  -Pydantic catches data errors before these reach our logic.
  -It has async support ,therefore it can handle multiple API calls simultaneously.
  -It is very easy to learn in comparison  to Django or SpringBoot
  -It is perfect for AI/ML projects, as the developers have to stay in Python ecosystem only.

**Cons:**
   -It is not opinionated which means we have to decide your own project structure.
   -There is no built-in ORM ,we have to separately integrate SQLAlchemy
   -It has smaller community than Express.js or Django.
   -It is not ideal for very large monolithic applications.
   -There is no built-in authentication ,we  have to implement JWT ourselves.

## From Theory to Practice: Overcoming Roadblocks
  When i first started using FastAPI , it was not as smooth as i had expected. The very first problem  i hit was CORS error , the moment i connected my React frontend to the backend , the browser threw a  Access-Control-Allow-Origin error and i was completely clueless , i spent hours debugging and it actually turned out to be literally 3 lines of middleware . Then came Pydantic ,i kept getting 422 Unprocessable Entity responses and had no idea why my data was being rejected , slowly i realized my request body simply did not match my model. The real nightmare however was during DevStakes submission, Groq API hit rate limits right in the middle of building , i panicked and had to urgently wire up Gemini as a fallback while running on . Deployment on Render was another difficult task —,my .env file was in .gitignore so all my API keys were missing on the server and the app crashed immediately , i had no idea what --host 0.0.0.0 --port $PORT even meant , i just copy pasted it and prayed. And to top it all , i had written all 9 endpoints in one main.py which became a 400 line  so i had to refactor everything into separate route files at 3am under deadline pressure. Every single one of these roadblocks taught me something that no tutorial ever could.

