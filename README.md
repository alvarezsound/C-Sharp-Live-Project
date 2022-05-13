****WIP
# C# Live Project
After completing the C# and .NET course, I participated in a two-week sprint working with a small dev team. We were tasked to build an interactive website for managing the content and productions for a local theater company. The application was built using ASP.NET MVC and Entity Framework. Below is a breakdown of the individual features that I was tasked with designing and implementing.

## Table of Contents
- [Create Entity Model and CRUD pages](#Create-Entity-Model-and-CRUD-pages)
- [Styling the Create and Edit Pages](#Styling-the-Create-and-Edit-Pages)
- [Photo Storage and Retrieval](#Photo-Storage-and-Retrieval)
- [Styling the Index page](#Stylin-the-Index-page)
- [Index Page Search Feature](#Index-Page-Search-Feature)


## Create Entity Model and CRUD pages
My first assigned story from the client was to create a model for their rental items and then scaffold the CRUD pages in order for them to easily manage their data Utilzing ASP.NET MVC and Entity Framework, I was able to create an entity model using Code First so that the client can save data to the database. I then was able to scaffold the model to create the CRUD pages. This task was easily done thanks to the Entity Framework.

The Model
```cs
public class RentalItem
    {
        public int RentalItemId { get; set; }
        public string Item { get; set; }
        public string ItemDescription { get; set; }
        [DataType(DataType.Date)]
        public DateTime PickupDate { get; set; }
        [DataType(DataType.Date)]
        public DateTime? ReturnDate { get; set; }
        public Byte[] ItemPhoto { get; set; }
    }
```

## Styling the Create and Edit Pages
The next task I was given was to style the Create and Edit Pages. The client had a strict color scheme to stick to as well as a rough page layout as a guide, but,ultimately it was up to me to iron out the details. Below is a code snippit of all the custom CSS that I used for my portion of the application.

Rent.css
```cs

```
### Create

### Edit

## Photo Storage and Retrieval

## Styling the Index page

## Sytling the Details and Delete Pages

### Details

### Delete

## Index Page Search Feature

## Conclusion

