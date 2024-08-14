# React & Rockets

**Description:** Challenge for Adjust Frontend Developer

**Owner:** [adjust](https://github.com/adjust)

**Contacts:** frontend-hiring@adjust.com

---

## Welcome to our little coding exercise! 👋

Here, you will have the opportunity to work with TypeScript and Rockets in the same project. We recommend setting aside 2-3 hours to complete it.

**Please make sure to read this page in its entirety before starting the challenge.** If you have any questions, feel free to [open an issue](#how-to-request-help) as described at the bottom of this page.

**Important:** We want to give all candidates taking this test an equal opportunity to solve the exercise in their own way. Therefore, **please do not fork or share this repo (or your solution) with anyone 🙏🏻**

<img align="center" src="https://i.imgur.com/ekyJNd9.jpg" width="600">

## Instructions

1. Push your solution to a **private repo** in your **personal GitHub account**.
2. When you're ready for us to review your work, please add [adjust-frontend-hiring][adjust-frontend-hiring] (GitHub user) as a collaborator.

## General notes

- The final solution must be a working React application.
  - It's up to you how to bootstrap a new React application.
- You can use any third-party library if you find it suitable.
- It's not necessary to heavily comment the code; please only leave comments where they are essential for code comprehension. However, we welcome notes and comments that reflect the higher-level decisions made during the challenge.
- Aspects to be assessed:
  - Code Style – meaningful naming conventions, consistent code formatting, and emphasis on code readability and future extensibility.
  - Quality Assurance – the solution you upload should work as expected, conforming to the specifications of the tasks. A solution that produces a different result than specified will not be considered.
  - Introducing best practices, such as tests and linting, is appreciated.

Good luck and happy coding! 🚀

---

## Exercise

### TASK #1 - TypeScript

Implement the `prepareData` higher-order function, which takes an object of filter parameters `{year, customerName}` and returns a function that processes a list of missions, showing only those launched in the specified `year` and carrying a payload belonging to `customerName`.

**Observations:**

- Missions should appear in inverse chronological order (sorted by the
  `launch_date_utc` field), except that those carrying more payloads should appear first.
- Payloads are carried in the second stage of a rocket, and they can belong to multiple customers.
- It doesn't matter to which `customerName` 'program' each payload belongs, as long as `customerName` is the customer.

**Example:**

Considering we have a response from the <a href="https://api.spacexdata.com/v3/launches/past" target="_blank">SpaceX API</a> and the following filter parameters:

```js
{
  year: 2018,
  customerName: "NASA"
}
```

The expected result should be:

```js
[
  {
    flight_number: 62,
    mission_name: "Iridium NEXT Mission 6",
    payloads_count: 2,
  },
  {
    flight_number: 72,
    mission_name: "CRS-16",
    payloads_count: 1,
  },
  {
    flight_number: 64,
    mission_name: "CRS-15",
    payloads_count: 1,
  },
  {
    flight_number: 60,
    mission_name: "TESS",
    payloads_count: 1,
  },
  {
    flight_number: 59,
    mission_name: "CRS-14",
    payloads_count: 1,
  },
];
```

---

### TASK #2 - React & Hooks

Implement the `<RocketsList>` component with the following specifications:

- The component receives a `filterParams` object (with the shape described in [task #1][task-1]) as a prop.
- The component obtains a list of 'missions' from a [custom hook][custom-hook], which fetches **the entire list of missions** from the [SpaceX API][spacex-api] and processes them using the `prepareData` function (from [task #1][task-1]) and the `filterParams` prop.
  - The mission data should only be fetched once.
  - As part of this challenge, you are not allowed to use any of the filter parameters provided by the [SpaceX API docs][spacex-api-docs].
- For each 'mission' obtained from the custom hook, the component renders a string using [template literals][template-literals] in the following format: "#`flight_number` `mission_name` (`payloads_count`)".
- While 'missions' are being fetched from the API, the component renders `"Loading..."` on the screen.
- If no 'missions' are obtained from the custom hook, the component renders `"No data"` on the screen.

**Expected outcome:**

Please set the `filterParams` to match the example below:

```js
<RocketsList
  filterParams={{
    year: 2018,
    customerName: "NASA",
  }}
/>
```

The expected render should match the following outcome:

<img align="center" src="img/expected_output.png" width="600">

We will be testing your solution with a small set of E2E tests. Please make sure your solution conforms to the specifications above. Our E2E tests rely on the following facts:

- Your React application starts a development server by running the `npm run start` command.
- The development server is hosted on `localhost:3000`.
- `filterParams` are specified as `{ year: 2018, customerName: "NASA" }`, as in the example above.
- The markup is represented as an unordered list, composed of `<ul>` and `<li>` HTML elements. Please refer to the example below:

```html
<ul>
  <li>#62 Iridium NEXT Mission 6 (2)</li>
  <li>#72 CRS-16 (1)</li>
  ...
</ul>
```

## How to request help

If you have any questions, you can reach out to us by [creating a GitHub issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/creating-an-issue#creating-an-issue-from-a-repository) in your private repo.

Describe your question(s) and [mention](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#mentioning-people-and-teams) [adjust-frontend-hiring][adjust-frontend-hiring] in your comments (don't forget to add the user as a collaborator). We will receive a notification and get back to you as soon as possible.

## Helpful links

- [SpaceX API Docs][spacex-api-docs]
- [Inviting collaborators to a personal repository][github-collaborators]

[spacex-api]: https://api.spacexdata.com/v3/launches/past
[spacex-api-docs]: https://docs.spacexdata.com/?version=latest#fce450d6-e064-499a-b88d-34cc22991bcc
[github-collaborators]: https://help.github.com/en/articles/inviting-collaborators-to-a-personal-repository
[task-1]: #task-1---typescript
[template-literals]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals
[custom-hook]: https://reactjs.org/docs/hooks-custom.html
[adjust-frontend-hiring]: https://github.com/adjust-frontend-hiring
