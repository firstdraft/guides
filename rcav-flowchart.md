# RCAV Flowchart

Our apps are nothing more than a collection of URLs that we decide to allow users to access:

 - `mydomain.com/products`
 - `mydomain.com/photos/193`
 - `mydomain.com/signin`

So remember: everything always starts with a **route** between a *URL* we want to support and a *Ruby method* that will be responsible for generating a response to the user's browser.

In order to support a URL in your app such as `http://localhost:3000/signin`, there are a lot of dots to connect!

![](/assets/rcav_flowchart.jpg)

 1. First we add a **route** for the **URL** we want to support (**green**).
 2. The route will specify the Ruby *class* and the *method* that will be responsible for rendering a response. We call the *class* a **controller** and the *method* an **action**.
 3. Whatever name you choose in the route for the **controller** determines the things in **red**:
    - the filename in the `app/controllers` folder (must be snake_case)
    - the class name in the file (must be CamelCase)
    - the folder name in the `app/views` folder
 4. Whatever name you choose in the route for the **action** determines the things in **blue**, and usually also the things in **pink**, since by convention we name them the same thing (but we don't have to):
    - the name of the method we define within the controller class
    - the name of the **view** template that we `render` in the action
    - the name of the `.html.erb` file within the `app/views/<CONTROLLER NAME>` folder

If something goes wrong, make sure everything matches perfectly:

 - Capitalization (all file, folder, method, variable, and symbol names should be `snake_case`; only class names are `CamelCase`).
 - Spelling/pluralization (by convention, controller names are usually plural, but don't have to be).
 - Location (controller files must be in `app/controllers/`, view templates must be in `views/<referring_controller_name>/`
 - **READ THE ERROR MESSAGE!** It usually tells you exactly what is going wrong, and where. It will at least give you a strong hint.