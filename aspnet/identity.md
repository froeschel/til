# Identity for ASP.NET Core

To setup a project for identity add following nuget packages:

- ``Microsoft.AspNetCore.Identity.EntityFrameworkCore``
- ``Microsoft.AspNetCore.Identity.UI``
- ``Microsoft.VisualStudio.Web.CodeGeneration.Design``

After that change we the ``DataContext`` class to inherit from ``IdentityDbContext``. Then add authentication and authorization middleware to the project by adding ``app.UseAuthentication()`` and ``app.UseAuthorization()`` to ``Program.cs`` class. When this is done build the project and add a migration to make the database ready for identity. 