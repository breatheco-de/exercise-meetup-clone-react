<!--hide-->
# Meetup Clone with Context API
<!--endhide-->

Technologies: HTML, CSS, JS, React, React Hooks, React Router and React Context API.

![Meetup.com Clone](https://github.com/breatheco-de/exercise-meetup-clone-react/blob/master/preview.png?raw=true)

👆 This project is optimized for groups of 2 or max 3 students.

Hello! It is time to begin creating professional front-end applications. This time
we will be building a small Meetup.com clone that allows users to Browse and RSVP events, very similar to how Meetup.com works.

📹 [Here is a video on how the application must work](https://github.com/breatheco-de/exercise-meetup-clone-react/blob/master/preview.webm?raw=true)

- **Event**'s is the main Entity on this application, the main view (Home) will have a list of **Event**'s organized by date.
- Each **Event** is linked to _a single **Group**_.
- A **Group** can be linked to _one or more_ **Event**'s (one to many).

## This project is meant to be done in two phases

First, we want to focus on the visuals; make sure the viewable structures are working correctly. 
Secondly, we should implement dynamic data display.

### Phase 1: Create the views, then link them with React Router in your Layout Component.

Each group must create the following views:

- Home (List of Events)
- Event detail (View of a specific Event)
- Group detail (View for the Group with a list of upcoming events for the group)

```txt
🗒NOTE: You should draw wireframes first to gather your ideas. Also, make sure to use dummy content initially. PLEASE USE MEETUP.COM AS A DESIGN REFERENCE!
```

Each **Group** entity must have

```txt
- Title
- Description
- Members
```

Each **Event** Entity must have

```txt
- Title
- Description
- Date
- Time
- Group (This is an ID for the group)
```

After you finish your wireframes, get to coding. Please make sure to only use functional components and if you need to define state variables or do something during the component lifecycle, use the corresponding hooks. (`useState()` and `useEffect()`)

***Note:*** Think DRY (Don't repeat yourself) and declare only ***one*** component and use ```props``` to handle a similar structure but different content. Context should be used only when you need to share data between many views. Always use props when you can and context sparingly.

***REMEMBER:*** Anchor tags will cause a redirect, which you don't want in React. Be sure to import and use the ```Link``` component from React Router to implement the navigation between views.

```jsx

<Link to="/event">
    Title of event
</Link>
```

### Phase 2: Make the app dynamic by implementing React Context

React context is built into the flux boilerplate. If you are having trouble understanding how context works, please take a look at the demo component that comes with it. (In your views folder)

***Use the store to fill the dummy content*** within the views/components. The store is accessible using the ```Context.Consumer```

#### Reference: Using the Context

The `store` structure (```/store/store.js```):

Below, you will find an example of the date for the Meetup clone. This consists of 2 arrays (events and meetups) and an abject for the user session.

You can replace your current store object with this data and even expand it to add more events and groups. Remember that this is placeholder data for now. Later on, we will be using fetch to pull the data in from an API.

```javascript
store: {
    events:[
        {
            ID: 36,
            post_content: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nec libero consectetur risus vehicula interdum eu at elit. Proin a commodo erat, eu molestie ipsum. Aliquam tristique nunc a est tristique, et convallis risus ullamcorper. Fusce nec massa ac enim pellentesque ornare. Pellentesque non sapien varius, pellentesque tellus sit amet, facilisis justo. Duis rhoncus nunc id elementum dapibus. Sed dictum lacinia vestibulum.",
            post_title: "Lorem Event",
            meta_keys: {
                day: "20180428",
                time: "07:00:00",
                _groupId: 9,
                _rsvpNo: [
                    "robert",
                    "jjtime",
                    "username2"
                ],
                _rsvpYes: [
                    "cheeselover",
                    "neweradude",
                    "james1996"
                ]
            }
        }
    ],
    Groups:[
        {
            ID: 9,
            post_content: "The nicest Meetup ever",
            post_title: "Tech Enthusiasts",
            members: [
                "robert",
                "jjtime",
                "username2",
                "cheeselover",
                "neweradude",
                "james1996"
            ]
        }
    ],
    session:{
        ID: 2,
        username: "theUser",
        user_friendly_name:"Joey",
        token: "qwerty12345asdfgzxcv"
    }
};
```

In order to have access to the global data from your store in one of your components, you must import the Context. See the example below.

```jsx

import { Context } from '/path/to/store/appContext.jsx';

const MyView = () => {
    const { actions, store } = useContext(Context);
    //Then use the Consumer anywhere on the component
    return (<span> hello, {store.events[0].post_title} </span>);
}
```

All of your Fetch/AJAX calls should be in the `useEffect()` section of the `appContext.js` file. Due to the way the boilerplate is built, this area handles the calls that are done only at the initial load of your application.

<onlyfor saas="false" withBanner="false">
    
## 🌱  How to start this project

We recommend opening the `react flux boilerplate`, using a provisioning tool like [Codespaces](https://4geeks.com/lesson/what-is-github-codespaces) (recommended) or [Gitpod](https://4geeks.com/lesson/how-to-use-gitpod). Alternatively, you can [clone the GitHub repository](https://4geeks.com/how-to/github-clone-repository) on your local computer using the `git clone` command.

This is the repository you need to open or clone:

```sh
$ git clone https://github.com/4GeeksAcademy/react-hello-webapp
```

Do not clone this repository.

💡 Important: Remember to create a new repository, update the remote (`git remote set-url origin <your new url>`), and upload the code to your new repository using `add`, `commit` and `push`.

### Steps

1. Install the dependencies `$ npm install`.

2. Run the WebPack development `$ npm run start`.

3. That's it! Time to code.

> _"The scariest moment is always before you start"_
> _Stephen King_

</onlyfor>
