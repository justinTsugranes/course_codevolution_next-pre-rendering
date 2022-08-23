# Notes

Common examples of when you may want to use this type of pre-rendering are: displaying a list of articles on a blog homepage, displaying a list of products on a homepage, or displaying a list of topics on a documentation page.

All you have to do is define the async function _getStaticProps_ fetch your data within the function and return an object with the necessary props. The props will then be availabe for use in your component

---

## Setup

### First Steps

- delete API folder from Pages
- delete home.module.css from styles
- changed index.js file content into simple component that returns a plain h1 tag.

Using the users data from [JSONPlaceholder](https://jsonplaceholder.typicode.com/) for test APIs

---

- create a new file in Pages folder named "users.js"

  - within the file, defined and exported UserList compontent

- in Next, when you export a page component, you can also export an async function called "getStaticProps"

  - This function will run at build time in production. Inside the function, you can fetch external data and send it as "props" to the page.

- go to users.js and export the getStaticProps async function
- pass in the JSONPaceholder/users URL as an argument.
- once you have the reponse, you convert it into JSON and log it to the console
- then, you need to pass the data to the component above
- this is accomplished via a return object
- the object contains another object named 'props' that can contain any key value pairs, which will be automatically injected as props into the component.
  - in our case, we set one property named 'users' which is set to 'data'
  - when we return this, the userlist component will receive the props at build time
    - so, you pass in 'props' as an arugment. you could also destructure the users property.
- To render
  - wrap the UserList return in a React fragment
  - map over the list of user
    - for each user, we're returning a div tag where the key tag is set to user.id
    - then, we're rendering user.name and user.email
    - you could map more, but we're only using name and email in this example

---

### getStaticProps

1. getStaticProps runs only on the server side
   1. the fucntion will never fun client-side
   2. the code you write inside getStaticProp won't even be included in the JS bundle that is sent to the browser
2. You can write server-side code directly in getSaticProps
   1. Accessing the file system using the fs moduleor querying a database can be done inside getStaticProps
3. getStaticProps is allowed only in page and cannot be run from a regular component file
   1. It is used only for pre-rendering and not client-side data fetching
4. getStaticProps should return an object and object should contain a props key which is an object
5. getStaticProps will run at build time
   1. During development, getStaticProps runs on every request

---

## Original README info from create-next-app

This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.js`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.js`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.
