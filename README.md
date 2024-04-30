# Sanity

## Content Management System

A Content Storage Platform. A Content backend that can be used with any front end

Sanity delivers content anywhere (just like a headless CMS). Beyond that, it gives you total composability. A fully decoupled, real-time content back end. Entirely customizable content workspaces.

To install Sanity, run

```bash
npm create sanity@latest
```

Then navigate to the directory of your project

```bash
cd Your-Project
```

To run the Sanity Studio run

```bash
npm run dev
```

Then open the localhost port in the browser

## Sanity Studio

In this project, I'm using the Blog Schema Temmplate.

- Content
- Post
- Author
- Category

All our content lives in the cloud. We call this, the "Content Lake"

## Studio Plugins

### Vision Plugin

To install run

```bash
npm i @sanity/vision/latest
```

Then add this code to the import section in "sanity.config.ts" file

```typescript
import { visionTool } from "@sanity/vision";
```

Vision Plugin is a Studio Playground for qerying our content
After installing the Vision Plugin you'll use Groq / GraphQL to fetch data. In this case, we'll use Groq

## Query Language GROQ(Graph-Relational Object Queries)

See Groq documentation here [Groq Documentation](https://www.sanity.io/docs/groq)

Running ` *` fetches everything

Running ` *[_type == "post"]` fetches posts. Note: If a post was in draft mode it will count it and show it as a draft

We will end up having a GROQ query like this

```groq
*[_type == "post"]{
  title,
    author->{
      name,
      nickname
    }
}
```

And we can filter it more to get what we want.

Once we get have the exact query that we want, we can copy the whole GROQ code and put it into the fetch/Sanity Client to integrate it with our front end project.

The Content is sent to the content-lake and then being fetched from the content-lake via GROQ

The next thing is to **deploy** and we'll use Sanity CLI to deploy

```bash
npm install -g sanity@latest
```

If it doesn't work on your computer, try

```bash
npx sanity@latest
```

The next thing is to run

```bash
sanity deploy
```

You'll be prmpted to enter some details:

- hostname should be unique

Then we have our Studio running locally. The studio url is what you share to the team
So we have the local version and the deployed version. Any change that I make to the local version is implemented on the deployed version.

Successfully deployed my Application at [Wil Sanity](https://wilsanity.sanity.studio/)
