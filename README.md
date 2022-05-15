## ****WIP****
# C# Live Project
After completing the C# and .NET course, I participated in a two-week sprint working with a small dev team. We were tasked to build an interactive website for managing the content and productions for a local theater company. The application was built using ASP.NET MVC and Entity Framework. Below is a breakdown of the individual features that I was tasked to design and implement.

## Table of Contents
- [Create Entity Model and CRUD pages](#Create-Entity-Model-and-CRUD-pages)
- [Styling the Create and Edit Pages](#Styling-the-Create-and-Edit-Pages)
- [Photo Storage and Retrieval](#Photo-Storage-and-Retrieval)
- [Styling the Index Page](#Styling-the-Index-Page)
- [Styling the Details and Delete Pages](#Styling-the-Details-and-Delete-Pages)
- [Index Page Search Feature](#Index-Page-Search-Feature)


## Create Entity Model and CRUD pages
My first assigned story from the client was to create a model for their rental items and then scaffold the CRUD pages in order for them to easily manage their data. Utilzing ASP.NET MVC and Entity Framework, I was able to create an entity model using Code First so that the client can save data to the database. I then was able to scaffold the model to create the CRUD pages. This task was easily done thanks to the Entity Framework.

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

```
### Create
For the Create page, the client wanted an overall clean design, hover and on-click effects for the form inputs, and unique buttons. I used bootstrap to easily seperate the form into two colums which I believe created a cleaner and more unique design.

```cs

```

[image of create page]

### Edit
It was requested that the edit page was styled almost identical to the create page. The one difference was that it displayed a photo if one was added.

```cs

```

[image of edit page]

## Photo Storage and Retrieval
The next task, was to add photo storage and retrieval functionality to the RentalItem model. This allows users to upload photo files from their file system; then in the controller, the uploaded image is converted into a byte array (byte[]) and stored in the database. The byte[] representing the photo is able to be retrieved from the database, and the converted back into an image where it can be displayed in the view.

First, I created a method in the RentalItem Controller that takes in the uploaded photo and converts that photo into a byte[].

```cs

```

Next, I added file input fields to the Create and Edit views, so the image can be uploaded.

[add image example]

Within the Create and Edit Controller methods, I created a method that converts the uploaded image to a byte[] and assigns the byte[] to the database.

```cs

```

Additionally, I had to create two methods within the controller that enable the user to retrieve the stored byte[] from the database using RentalItemId. The second method then returns the file of the converted photo to be displayed.

```cs

```

Finally, I used the DisplayImage method to display the photos on the index and CRUD pages. Here are some examples of the method being applied to the Create and Edit views.

```cs

```

## Styling the Index Page
The next task was a total design overhall of the index page. I added Bootstrap cards to the index view that display each individual rental item in a bootstrap grid. The client requested adding and designing a large create button that directs the user to the create page. They also wanted an overlay effect on the item cards where edit and delete buttons appear on hover. I was able to add extra on-hover features like opacity and image scaling. Finally, they wanted each card to be clickable and direct the user to the rental items details view.

[Show gif of overlay and button effects and index design]

```cs

```

## Styling the Details and Delete Pages
Finally, the last pages (details and delete) in the app needed to be styled. I was given an overall layout request that I had to follow. They wanted these two pages to be exactly the same except for the addition of a delete button on the delete page.

### Details
[image of details page]

### Delete
[image of delete page]

## Index Page Search Feature
As a final feature, the client wanted to add a search bar to the index page that allows the user to search rental items by name or a matching word/phrase in the item description. The items that don't match the search are hidden from view and if there are no items that match the search, the section itself is hidden. After turning this in, they had a new idea to add an additional button that resets the form/page.

This was done with a simple line of code added to the index method in the controller followed by adding an input and buttons to the index page.

```cs

```

```cs

```

[GIF of index search feature demo]

## Conclusion
The C# live project provided me a chance to apply all the knowledge I have accumulated during my time in the software development boot camp. I utilized AGILE/SCRUM project methodologies and gained real-world experience with version control. I participated in daily standup meetings to discuss progress and roadblocks, as well as a retrospective meeting upon completion of the app. One of the biggest things I learned from this experience is the importance of keeping my branch up to date with the master to minimize merge conflicts. I found myself very comfortable using C# and ASP.NET and I was able to get through every step effeciently, and with minimal issues. I look forward to developing these skills further and applying them!

