# Section 1: getting started

- How to install NEXT.js app-

```sh
npx create-next-app@latest
```

- template config: no in all

- How to run dev server

```sh
npm run dev
```

- clean-up process
  <br>
  In pages-folder, open index.js and perform "sanity check"
  opt: remove import head, image, inter, styles, const inter

<br>

# Section 3 Pages & files based routing

## Setup

- Download the attach Next.js template
- Install node module "npm install"
- In pages-folder create index.js-file
- In index.js create function based component (rfce)

```js
function HomePage() {
  return (
    <div>
      <h1>The Home Page</h1>
    </div>
  );
}

export default HomePage;
```

- run dev server

```sh
npm run dev
```

<br>

## About Page

- In pages-folder create about.js-file
- In about.js create function based component (rfce)

```js
function AboutPage() {
  return (
    <div>
      <h1>About Page</h1>
    </div>
  );
}

export default AboutPage;
```

- go to local host and manually type

```
localhost:3000/about
```

<br>

## Nested Paths & Routes

- In pages-folder create portfolio-subfolder and inside it create index.js-file
- In index.js-file create a functional component (rfce)

```js
function PortfolioPage() {
  return (
    <div>
      <h1>The Portfolio Page</h1>
    </div>
  );
}

export default PortfolioPage;
```

- go to local host and manually type

```
localhost:3000/portfolio
```

- In pages/portfolio-folder inside it create list.js-file
- In list.js-file create a functional component (rfce)

```js
function ListPage() {
  return (
    <div>
      <h1>The List Page</h1>
    </div>
  );
}

export default ListPage;
```

- go to local host and manually type

```
localhost:3000/portfolio/list
```

<br>

## Adding Dynamic Paths & Routes

- In pages/portfolio-subfolder create [projectid].js-file i.e dynamic file
- In [projectid].js-file create a functional component (rfce)

```js
function PortfolioProjectPage() {
  return (
    <div>
      <h1>The Portfolio Project Page</h1>
    </div>
  );
}

export default PortfolioProjectPage;
```

- go to local host and manually type

```
localhost:3000/portfolio/somethinxyz
```

<br>

## Extracting Dynamic Path Segment Data (Dynamic Routes)

- In [projectid].js-file modify component using useRouter hook

```js
import { useRouter } from "next/router";

function PortfolioProjectPage() {
  // return router-obj
  const router = useRouter();

  // what is the pathname
  console.log(router.pathname);
  // give key:value
  console.log(router.query);

  // send a request to some backend server
  // to fetch the piece of data with an id of router.query.projectid

  return (
    <div>
      <h1>The Portfolio Project Page</h1>
    </div>
  );
}

export default PortfolioProjectPage;
```

- go to local host and manually type

```
localhost:3000/portfolio/somethinxyz
```

- open dev tool console

<br>

## Building Nested Dynamic Routes & Paths

- In pages-folder create clients-subfolder, inside it create index.js-file
- In index.js-file create a functional component (rfce)

```js
import Link from "next/link";

function ClientsPage() {
  return (
    <div>
      <h1>The Clients Page</h1>
    </div>
  );
}

export default ClientsPage;
```

- In pages/clients-subfolder create [id]-subfolder i.e dynamic-folder name, inside it create index.js

- In index.js-file create a functional component (rfce)

```js
function ClientProjectsPage() {
  return (
    <div>
      <h1>The Projects of a Given Client</h1>
    </div>
  );
}

export default ClientProjectsPage;
```

- In pages/clients/[id]-subfolder, create [clientprojectid].js-file

- In [clientprojectid].js-file, create a functional component (rfce)

```js
function SelectedClientProjectPage() {
  return (
    <div>
      <h1>The Project Page for a Specific Project for a Selected Client</h1>
    </div>
  );
}

export default SelectedClientProjectPage;
```

- HOW TO REACH TO THE CLIENTS PAGE-default index:
  - go to local host and manually type

```
localhost:3000/clients
```

- HOW TO REACH TO THE [id] folder-default index: dynamic segement
  - go to local host and manually type

```
localhost:3000/clients/max
```

- HOW TO REACH TO THE [clientprojectid].js file: dynamic segment
  - go to local host and manually type

```
localhost:3000/clients/max/project1
```

- In [clientprojectid].js-file modify component using useRouter hook

```js
import { useRouter } from "next/router";

function SelectedClientProjectPage() {
  // return router-obj
  const router = useRouter();

  // what is the data {key/projectid: value/somethingxyz}
  console.log(router.query);

  return (
    <div>
      <h1>The Project Page for a Specific Project for a Selected Client</h1>
    </div>
  );
}

export default SelectedClientProjectPage;
```

- HOW TO REACH TO THE [clientprojectid].js file: dynamic segment
  - go to local host and manually type

```
localhost:3000/clients/max/project1
```

- open dev console to know key:value

<br>

## Adding Catch-All Routes using [...id] js spread feature

- In pages-folder create blog-subfolder and inside it create [...slug].js-file i.e dynamic segment
- In [...slug].js-file create functional component (rfce) and use useRouter hook

```js
import { useRouter } from "next/router";

function BlogPostsPage() {
  // return router-obj
  const router = useRouter();

  // what is the data {key/projectid: value/somethingxyz}
  console.log(router.query);

  return (
    <div>
      <h1>The Blog Posts</h1>
    </div>
  );
}

export default BlogPostsPage;
```

-HOW TO REACH TO THE [...slug].js file: dynamic segment

- go to local host and manually type

```
localhost:3000/blog/2020/12
```

- open dev console to know key:value

<br>

## Navigating with the "Link" Component-

- In pages/index.js-file modify

```js
import Link from "next/link";

function HomePage() {
  return (
    <div>
      <h1>The Home Page</h1>
      <ul>
        <li>
          <Link href="/portfolio">Portfolio</Link>
        </li>
        <li>
          <Link href="/clients">Clients</Link>
        </li>
      </ul>
    </div>
  );
}

export default HomePage;
```

- go to local host and manually type

```
localhost:3000
```

<br>

## Navigating To Dynamic Routes

- In pages/clients/index.js-file modify

```js
import Link from "next/link";

function ClientsPage() {
  return (
    <div>
      <h1>Sanity check -The Client Page</h1>

      <ul>
        <li>
          <Link href="/clients/kmax">maximilian</Link>
        </li>

        <li>
          <Link href="/clients/kmanu">Manuel</Link>
        </li>
      </ul>
    </div>
  );
}
export default ClientsPage;
```

- HOW TO REACH TO THE clients: default index.js page
- go to local host and manually type

```
localhost:3000/clients
```

<br>

## Generating dynamically injected clientid, page link from js-obj

- In pages/clients/index.js-file modify

```js
import Link from "next/link";

function ClientsPage() {
  const clients = [
    { id: "max", name: "Maximilian" },
    { id: "manu", name: "Manuel" },
  ];

  return (
    <div>
      <h1>The Clients Page</h1>

      <ul>
        {clients.map((client) => (
          <li key={client.id}>
            <Link href={`/clients/${client.id}`}>{client.name}</Link>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default ClientsPage;
```

- HOW TO REACH TO THE clients: default index.js page
  - go to local host and manually type

```
localhost:3000/clients
```

<br>

## A Different Way Of Setting Link Hrefs using object{key:value}

- In pages/clients/index.js-file modify

```js
import Link from "next/link";

function ClientsPage() {
  const clients = [
    { id: "max", name: "Maximilian" },
    { id: "manu", name: "Manuel" },
  ];

  return (
    <div>
      <h1>The Clients Page</h1>
      <ul>
        {clients.map((client) => (
          <li key={client.id}>
            <Link
              href={{
                pathname: "/clients/[id]",
                query: { id: client.id },
              }}
            >
              {client.name}
            </Link>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default ClientsPage;
```

- HOW TO REACH TO THE clients: default index.js page
  - go to local host and manually type

```
localhost:3000/clients
```

<br>

## Navigating Programmatically using button-

- In pages/clients/[id]/index.js-file, modify it

```js
import { useRouter } from "next/router";

function ClientProjectsPage() {
  const router = useRouter();

  console.log(router.query);

  {
    /*--- 2 button function event ---*/
  }
  function loadProjectHandler() {
    // load data...
    router.push({
      pathname: "/clients/[id]/[clientprojectid]",
      query: { id: "max", clientprojectid: "projecta" },
    });
  }

  return (
    <div>
      <h1>The Projects of a Given Client</h1>

      {/*--- 1 button setup ---*/}
      <button onClick={loadProjectHandler}>Load Project A</button>
    </div>
  );
}

export default ClientProjectsPage;
```

<br>

## Custom 404 page not found

- In pages-folder create 404.js
- In 404.js-file create a functional component (rfce)

```js
function NotFoundPage() {
  return (
    <div>
      <h1>Page not found!</h1>
    </div>
  );
}

export default NotFoundPage;
```

- go to local host and manually type

```
localhost:3000/nonexistingpage
```
