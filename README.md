# Eat & Split

Eat & Split is a small React application for splitting a meal bill between friends.

The project was built to practice and demonstrate the fundamentals that make up a typical React application: component composition, local state, controlled forms, event handling, derived values, and communication between components.

The UI is intentionally simple. The focus is on keeping the state predictable and the data flow easy to follow.

## Live Demo

Coming soon

## What it does

* Add friends to the list
* Select a friend to split a bill with
* Enter the total bill and each person's share
* Calculate the remaining amount automatically
* Update the selected friend's balance
* Keep the UI synchronized with the current application state

## Implementation

The application is built around a small set of focused React components. The main application component owns the state that needs to be shared, while child components receive the data and actions they need through props.

The general flow is:

```text
User action
    ↓
Event handler
    ↓
State update
    ↓
React re-render
    ↓
Updated UI
```

This keeps the data flow unidirectional and makes it relatively straightforward to understand where a particular change originates.

### State

The application uses React's `useState` for managing friends, the currently selected friend, and the bill-splitting workflow.

Rather than storing values that can be calculated from existing state, the application derives them when rendering or handling an action. This keeps the state model small and avoids unnecessary sources of truth.

### Component communication

Shared state lives at the appropriate parent level and is passed down through props.

Child components communicate user actions back to the parent through callback functions. This keeps components relatively focused while following React's one-way data flow model.

### Forms

The bill-splitting form uses controlled inputs. Form values are represented by React state, allowing the application to validate the input and calculate the resulting balances before updating the UI.

### Immutable updates

Friend data is updated without directly mutating the existing state. New arrays and objects are created when state changes, allowing React to reliably detect updates and re-render the affected UI.

### Derived values

The amount owed by each person is derived from the bill and the individual contributions rather than being maintained as separate state.

This is a small detail, but it keeps the application state easier to reason about and reduces the possibility of inconsistent values.

## Project Structure

The project follows a simple component-based structure:

```text
src/
├── components/
│   ├── Friend.js
│   ├── FriendList.js
│   ├── FormAddFriend.js
│   └── FormSplitBill.js
│
├── App.js
├── index.js
└── index.css
```

Each component has a relatively narrow responsibility, while `App` coordinates the state shared across the application.

## Tech Stack

* React
* JavaScript (ES6+)
* CSS
* Create React App
* Git / GitHub

No external state-management library is used. For an application of this size, React's local state and component composition are sufficient.

## Running Locally

Clone the repository:

```bash
git clone https://github.com/imssc/eat-splitz.git
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm start
```

The application will be available at `http://localhost:3000`.

## Why I Built This

This project is intentionally small.

The goal wasn't to build another large application with a long list of dependencies. It was to get comfortable with the mechanics of React and understand how state, events, forms, and component communication work together in a real interactive UI.

It also serves as a foundation for the more advanced React projects that follow it, where the same concepts can be applied with TypeScript, more complex state management, form libraries, validation, testing, and API-driven data.

