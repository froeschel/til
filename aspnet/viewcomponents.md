# View Components

View components can be compared to partial views, but they work a bit different. View components rely on the data that are bassed into them during initialization. It is also possible to use dependency injection. A good use case for View Components is when we need to render data based on more complex logic. That can be for dynamic navigation menus or small content containers where we need to display parts of our data to the end user. 

View components derive from ViewComponent class and they are invoked from a view with the following code: <br>
``` @await Component.InvokeAsync("MyComponent") ```