## Creating a Blazor App (.NET 8) with MudBlazor and Interactive Server Rendering

### Step 1: Create a New Blazor App

To start, you need to create a new Blazor application.

1. **Open a terminal or command prompt.**
2. **Run the following command to create a new Blazor app:**
   ```bash
   dotnet new blazorserver -o BlazorAppWithMudBlazor
   ```
   This creates a new Blazor Server project in a folder named `BlazorAppWithMudBlazor`.

3. **Navigate to the project folder:**
   ```bash
   cd BlazorAppWithMudBlazor
   ```

4. **Open the project in your favorite IDE** (e.g., Visual Studio, Visual Studio Code, or JetBrains Rider).

### Step 2: Enable Interactive Server Rendering Globally

By default, Blazor in .NET 8 uses **Static Server Rendering (SSR)**. To enable **Interactive Server Rendering** globally:

1. **Open the `Program.cs` file.**
2. **Locate the `AddRazorComponents()` method** and update it to include `AddInteractiveServerComponents()`:
   ```csharp
   builder.Services.AddRazorComponents()
       .AddInteractiveServerComponents();
   ```

3. **Locate the `app.MapRazorComponents()` line** and update it to include `AddInteractiveServerRenderMode()`:
   ```csharp
   app.MapRazorComponents()
       .AddInteractiveServerRenderMode();
   ```

4. **Save the file.**

Now, your entire application will use **Interactive Server Rendering**.

### Step 3: Install MudBlazor

MudBlazor is a popular component library for Blazor that provides a rich set of UI components. Let’s install it.

1. **Open a terminal in the project folder.**
2. **Run the following command to install the MudBlazor NuGet package:**
   ```bash
   dotnet add package MudBlazor
   ```

3. **Install the MudBlazor fonts and icons** by adding the following lines to the `_Layout.cshtml` file (for Blazor Server):
   ```html
    <link href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap" rel="stylesheet" />
    <link href="_content/MudBlazor/MudBlazor.min.css" rel="stylesheet" />
   ```

4. **Add the MudBlazor script** at the end of the file:
   ```html
   <script src="_content/MudBlazor/MudBlazor.min.js"></script>
   ```

### Step 4: Configure MudBlazor in the Application

Now that MudBlazor is installed, let’s configure it in the app.

1. **Open the `Program.cs` file.**
2. **Add the MudBlazor service** to the dependency injection container:
   ```csharp
   builder.Services.AddMudServices();
   ```

3. **Add the necessary using directive** at the top of your Razor components where you plan to use MudBlazor components:
   ```csharp
   @using MudBlazor
   ```

### Step 5: Test MudBlazor Components

To ensure MudBlazor is working correctly, let’s add a simple component to one of your pages.

1. **Open a Razor page** (e.g., `Index.razor`).
2. **Add a MudBlazor component** like a button:
   ```html
   Click Me
   ```

3. **Add an event handler** in the code section:
   ```csharp
   @code {
       void HandleClick()
       {
           Console.WriteLine("Button clicked!");
       }
   }
   ```

4. **Run the application** using `dotnet run` and verify that the MudBlazor components are displayed and functional.