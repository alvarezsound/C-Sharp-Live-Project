# C# Live Project
After completing the C# and .NET course, I participated in a two-week sprint working with a small dev team. We were tasked to build an interactive website for managing the content and productions for a local theater company. The application was built using ASP.NET MVC and Entity Framework. Below is a breakdown of the individual features that I was tasked to design and implement.

## Table of Contents
- [Create Entity Model and CRUD pages](#Create-Entity-Model-and-CRUD-pages)
- [Styling the Create and Edit Pages](#Styling-the-Create-and-Edit-Pages)
- [Photo Storage and Retrieval](#Photo-Storage-and-Retrieval)
- [Styling the Index Page](#Styling-the-Index-Page)
- [Styling the Details and Delete Pages](#Styling-the-Details-and-Delete-Pages)
- [Index Page Search Feature](#Index-Page-Search-Feature)
- [Create Admin Role and Restrict Access](#Create-Admin-Role-and-Restrict-Access)
- [Conclusion](#Conclusion)


## Create Entity Model and CRUD pages
My first assigned story from the client was to create a model for their rental items and then scaffold the CRUD pages in order for them to easily manage their data. Utilzing ASP.NET MVC and Entity Framework, I was able to create an entity model using Code First so that the client can save data to the database. I utilized DataType.Date property to get the date component from DateTime. I then was able to scaffold the model to create the CRUD pages. This task was easily done thanks to the Entity Framework.

The Model
```cs
public class RentalItem
    {
        public int RentalItemId { get; set; }
        public string Item { get; set; }
        public string ItemDescription { get; set; }

        [DataType(DataType.Date)]
        [DisplayFormat(DataFormatString = "{0:yyyy-MM-dd}", ApplyFormatInEditMode = true)]
        public DateTime PickupDate { get; set; }

        [DataType(DataType.Date)]
        [DisplayFormat(DataFormatString = "{0:yyyy-MM-dd}", ApplyFormatInEditMode = true)]
        public DateTime? ReturnDate { get; set; }

        public Byte[] ItemPhoto { get; set; }
    }
```

## Styling the Create and Edit Pages
The next task I was given was to style the Create and Edit Pages. The client had a strict color scheme as well as rough page layouts to use as a guide, but, ultimately it was up to me to iron out the details of the design. Below is a code snippit of all the custom CSS that I used for my portion of the application.

Rent.css
```cs
.Rent-RentalItem--CreateEditInput:focus {
    border-color: var(--main-color) !important;
    box-shadow: 0 0 0 0.2rem rgba(219, 26, 17, 0.25) !important;
}

.Rent-RentalItem--btnOne {
    background-color: var(--main-color--light);
    color: var(--dark-color);
    padding: 5px 20px;
    text-align: center;
    font-size: 18px;
    font-weight: 600;
    border-radius: 8px;
}

.Rent-RentalItem--btnOne:hover {
    background-color: var(--main-color--light);
    color: var(--light-color);
    border: 2px solid var(--light-color);
    transition-duration: 0.2s;
}

.Rent-RentalItem--btnTwo {
    background-color: var(--dark-color);
    color: var(--light-color);
    padding: 5px 20px;
    text-align: center;
    font-size: 18px;
    font-weight: 600;
    border-radius: 8px;
    transition-duration: 0.2s;
}

.Rent-RentalItem--btnTwo:hover {
    opacity: 1;
    background-color: var(--dark-color);
    border: 2px solid var(--main-color--light);
    color: var(--main-color--light);
}

.Rent-RentalItem--btnThree {
    background-color: var(--secondary-color);
    color: var(--dark-color);
    padding: 5px 20px;
    text-align: center;
    font-size: 18px;
    font-weight: 600;
    border-radius: 8px;
}

.Rent-RentalItem--btnThree:hover {
    background-color: var(--secondary-color--dark);
    border: 2px solid var(--light-color);
    color: var(--light-color);
}

.Rent-RentalItem--btnFour {
    background-color: var(--dark-color);
    color: var(--light-color);
    padding: 5px 20px;
    text-align: center;
    font-size: 18px;
    font-weight: 600;
    border-radius: 8px;
    transition-duration: 0.2s;
    border: 2px solid var(--light-color);
}

.Rent-RentalItem--btnFour:hover {
    opacity: 1;
    background-color: var(--dark-color);
    border: 2px solid var(--main-color--light);
    color: var(--main-color--light);
}

.Rent-RentalItem--IndexContainer {
    background-color: var(--secondary-color);
    padding: 0;
    overflow: hidden;
    margin: 5px;
    border: 3px solid var(--main-color);
    box-shadow: 0 0 0 1px var(--main-color--light);
    height: 250px;
    width: 250px;
    align-items: center;
    justify-content: center;
    display: flex;
}

.Rent-RentalItem--IndexContainer article {
    padding: 5%;
    position: absolute;
    bottom: 0;
    z-index: 1;
    -webkit-transition: all 0.4s ease;
    -moz-transition: all 0.4s ease;
    -o-transition: all 0.4s ease;
    -ms-transition: all 0.4s ease;
    transition: all 0.4s ease;
}

.Rent-RentalItem--IndexContainer h2 {
    color: var(--dark-color);
    font-weight: 800;
    font-size: 25px;
    text-shadow: 1px 1px var(--main-color--light);
    opacity: 0.9;
}

.Rent-RentalItem--IndexContainer img {
    width: 100%;
    opacity: 0.9;
    -webkit-transition: all 0.5s ease;
    -moz-transition: all 0.5s ease;
    -o-transition: all 0.5s ease;
    -ms-transition: all 0.5s ease;
    transition: all 0.5s ease;
}

.Rent-RentalItem--ImgHover {
    position: absolute;
    width: 100%;
    height: 60px;
    bottom: 0;
    z-index: 1;
    opacity: 0;
    transform: translate(0px, 60px);
    transition: all 0.2s ease-in-out;
    -webkit-transform: translate(0px, 60px);
    -moz-transform: translate(0px, 60px);
    -o-transform: translate(0px, 60px);
    -ms-transform: translate(0px, 60px);
    -webkit-transition: all 0.2s ease-in-out;
    -moz-transition: all 0.2s ease-in-out;
    -o-transition: all 0.2s ease-in-out;
    -ms-transition: all 0.2s ease-in-out;
}

.Rent-RentalItem--ImgHover span {
    font-size: 40px;
    color: var(--dark-color);
    position: relative;
    margin: 0 auto;
    width: 100%;
    top: 13px;
}

.Rent-RentalItem--IndexContainer:hover {
    cursor: pointer;
}

.Rent-RentalItem--IndexContainer:hover img {
    opacity: 0.6;
    transform: scale(1.1);
    transition: all 0.5s ease-in-out;
}

.Rent-RentalItem--IndexContainer:hover article {
    transform: translate(2px, -50px);
    -webkit-transform: translate(2px, -50px);
    -moz-transform: translate(2px, -50px);
    -o-transform: translate(2px, -50px);
    -ms-transform: translate(2px, -50px);
}

.Rent-RentalItem--IndexContainer:hover .Rent-RentalItem--ImgHover {
    transform: translate(0px, 0px);
    -webkit-transform: translate(0px, 0px);
    -moz-transform: translate(0px, 0px);
    -o-transform: translate(0px, 0px);
    -ms-transform: translate(0px, 0px);
    opacity: 1;
}

.Rent-RentalItem--Index {
    padding: 10px;
    border-radius: .5rem;
}

.Rent-RentalItem--Photo {
    border: 2px solid var(--dark-color);
    border-radius: .5rem;
    width: 380px;
    height: 380px;
}
```
### Create
For the Create page, the client wanted an overall clean design, hover and on-click effects for the form inputs, and unique buttons. I used bootstrap to easily seperate the form into two colums which I believe created a cleaner and more unique design.

[image of create page]

### Edit
It was requested that the edit page was styled almost identical to the create page. The one difference was that it displayed a photo if one was added.

[image of edit page]

## Photo Storage and Retrieval
The next assigned story, was to add photo storage and retrieval functionality to the RentalItem model. This allows users to upload photo files from their file system; then in the controller, the uploaded image is converted into a byte array (byte[]) and stored in the database. The byte[] representing the photo is able to be retrieved from the database, and the converted back into an image where it can be displayed in the view.

First, I created a method in the RentalItem controller that takes in the uploaded photo and converts that photo into a byte[].

```cs
public byte[] ImageToByte(HttpPostedFileBase imageFile)
        {
            byte[] bytes;
            using (BinaryReader br = new BinaryReader(imageFile.InputStream))
            {
                bytes = br.ReadBytes(imageFile.ContentLength);
            }
            return bytes;
        }
```

Next, I added file input fields to the Create and Edit views, so the image can be uploaded.

[Image of edit page photo area]

Within the Create and Edit Controller methods, I created a method that converts the uploaded image to a byte[] and assigns the byte[] to the database.

```cs
public ActionResult Create([Bind(Include = "RentalItemId,Item,ItemDescription,PickupDate,ReturnDate,ItemPhoto")] RentalItem rentalItem, HttpPostedFileBase imageFile)
        {
            if (ModelState.IsValid)
            {
                if (imageFile != null)
                {
                    rentalItem.ItemPhoto = ImageToByte(imageFile);
                    db.RentalItems.Add(rentalItem);
                }
                else
                {
                    db.RentalItems.Add(rentalItem);
                }
                db.SaveChanges();
                return RedirectToAction("Index");
            }

            return View(rentalItem);
        }
```
```cs
public ActionResult Edit([Bind(Include = "RentalItemId,Item,ItemDescription,PickupDate,ReturnDate,ItemPhoto")] RentalItem rentalItem, HttpPostedFileBase imageFile)
        {
            if (ModelState.IsValid)
            {
                if (imageFile != null)
                {
                    db.Entry(rentalItem).State = EntityState.Modified;
                    rentalItem.ItemPhoto = ImageToByte(imageFile);
                }
                db.SaveChanges();
                return RedirectToAction("Index");
            }
            return View(rentalItem);
        }
```

Additionally, I had to create two methods within the controller that enable the user to retrieve the stored byte[] from the database using RentalItemId. The second method then returns the file of the converted photo to be displayed.

```cs
public byte[] GetImageFromDB(int id)
{
    RentalItem item = db.RentalItems.Find(id);
    byte[] itemPhoto = item.ItemPhoto;
    return itemPhoto;
}
```
```cs
public ActionResult DisplayImage(RentalItem id)
        {
            RentalItem item = db.RentalItems.Find(id.RentalItemId);
            byte[] image = GetImageFromDB(item.RentalItemId);
            if (image != null)
            {
                return File(image, "image/png");
            }
            else
            {
                return null;
            }
        }
```

Finally, I used the DisplayImage method to display the photos on the index and CRUD pages. Here are is an example of the method being applied to the index page view.
```cs
<img src="@Url.Action("DisplayImage", "RentalItems", new { item.RentalItemId })" alt="Rental Item Photo">
```

## Styling the Index Page
The next story was a total design overhall of the index page. I added Bootstrap cards to the index view that display each individual rental item in a bootstrap grid. The client requested adding and designing a large create button that directs the user to the create page. They also wanted an overlay effect on the item cards where edit and delete buttons appear on hover. I was able to add extra on-hover features like opacity and image scaling. Finally, they wanted each card to be clickable and direct the user to the rental items details view.

[Show gif of overlay and button effects and index design]

## Styling the Details and Delete Pages
Finally, the last pages (details and delete) in the app needed to be styled. I was given an overall layout request that I had to follow. They wanted these two pages to be exactly the same except for the addition of a delete button on the delete page. Later on in the sprint, I suggested a design update to these pages.

### Details
[image of details page]

### Delete
[image of delete page]

## Index Page Search Feature
The client wanted to add a search bar to the index page that allows the user to search rental items by name or a matching word/phrase in the item description. The items that don't match the search are hidden from view and if there are no items that match the search, the section itself is hidden. After turning this in, they decided they wanted to add an additional button that resets the form/page.

This feature was done with a simple line of code inside the index method in the controller. Then I added an input and buttons to the index page.

```cs
public ActionResult Index(string searchString)
        {
            return View(db.RentalItems.Where(x => x.Item.Contains(searchString) || x.ItemDescription.Contains(searchString) || searchString == null).ToList());
        }
```

```cs
<div class="mt-5">
    <div class="row justify-content-between">
        <h2 class="col-3">Rental Items</h2>
        <div class="col-5 py-1 pl-4">
            @using (Html.BeginForm("Index", "RentalItems", FormMethod.Get))
            {
                @Html.TextBox("searchString", null, new { @style = "padding: 3px; font-size: 14px; width: 262px;", placeholder = "Search an item..." })
                <input class="Rent-RentalItem--btnOne" style="font-size: 14px !important;" type="submit" value="Search" />
                <a href="/Rent/RentalItems/Index">
                    <input class="Rent-RentalItem--btnThree" style="font-size: 14px !important;" type="button" value="Reset" />
                </a>
            }
        </div>
    </div>
    <div class="mx-auto">
        <div class="w-100" style="height: 12px; background-color: var(--secondary-color)"</div>
    </div>
</div>
```

[GIF of index search feature demo]

## Create Admin Role and Restrict Access
As a final feature, the client wanted to restrict access to certain views for non admin users. This was accomplished by adding the below code to the RentalItem controller. 

```cs
[Authorize(Roles = "Admin")]
```

To allow non-admin access to certain views, I added the below code to the top of each method that non-admin users should see.
```cs
[AllowAnonymous]
```

In order to hide certain html elements on the pages depending if the user is an admin, I placed those elements within an if statement using Razor syntax. Here is an example:
```cs
@if (ViewContext.HttpContext.User.IsInRole("Admin"))
{
    <div class="d-flex justify-content-center mt-4">
        <input type="submit" value="Create New" class="Rent-RentalItem--btnThree w-50" onclick="location.href='@Url.Action("Create")'" />
    </div>
}
```

Finally, to create the admin role and a admin super user for testing, I added this block of code to the Startup.cs:
```cs
private void CreateRoleAndUser ()
        {
            ApplicationDbContext db = new ApplicationDbContext();
            var roleManager = new RoleManager<IdentityRole>(new RoleStore<IdentityRole>(db));
            var UserManager = new UserManager<ApplicationUser>(new UserStore<ApplicationUser>(db));

            if (!roleManager.RoleExists("Admin"))
            {
                // creates admin role
                var role = new IdentityRole();
                role.Name = "Admin";
                roleManager.Create(role);

                // creates admin super user
                var user = new ApplicationUser()
                {
                    UserName = "admin",
                    Email = "admin@gmail.com"
                };
                string password = "Password1!";

                var checkUser = UserManager.Create(user, password);

                if (checkUser.Succeeded)
                {
                    var result = UserManager.AddToRole(user.Id, "Admin");
                }
            
            }
        }
```

Here are screenshots of the index page as a admin and non-admin to compare.
[Insert images of index pages to compare]


## Conclusion
The C# live project provided me a chance to apply all the knowledge I have accumulated during my time in the software development boot camp. I utilized AGILE/SCRUM project methodologies and gained real-world experience with version control. I participated in daily standup meetings to discuss progress and roadblocks, as well as a retrospective meeting upon completion of the app. One of the biggest things I learned from this experience is the importance of keeping my branch up to date with the master to minimize merge conflicts. I found myself very comfortable using C# and ASP.NET and I was able to get through every step effeciently, and with minimal issues. I look forward to developing these skills further and applying them!

Back to [Top](#C#-Live-Project)

