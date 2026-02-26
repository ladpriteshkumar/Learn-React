https://react.dev/learn/creating-a-react-app

# [Create React App](https://create-react-app.dev/docs/getting-started) #



### Create React App  build tool is deprecated  [See Reference](https://react.dev/blog/2025/02/14/sunsetting-create-react-app) 
### USE(https://vite.dev) Vite, Parcel, or RSBuild build tools to Create new React App

### `nodeJS` is required to use build tools like Vite, Parcel, or RSBuild.

# Install nodeJS

1. Install node.js Latest version from Node.js official site.

You can check the node version installed in your machine by running the following command that displays the node version as follows:

```
node -v
```

To unistall node.Js, use "winget" command in command prompt as below
```
winget uninstall nodejs
```

Learn mode about "winget"  [click here](https://learn.microsoft.com/en-us/windows/package-manager/winget/)

Install create-react-app by running the following command:
```
npm install -g create-react-app
```

If you do not want to install create-react-app then you can use the below command to create a React application
```
npx create-react-app my-app
```
npx is a tool to run node packages without  installing binaries

The above command creates a project my-app with the below folder structure:

<p align="center">
  <img src="/react_folder_structure.PNG" alt="react folder structure"/>
</p>

