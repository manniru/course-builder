<h1>Create New Courses</h1>



You can create new courses directly in the Administrator Page. Such newly created courses will exist in the Google App Engine datastore, as opposed to the filesystem on your local computer. You can create as many courses as you like and they will persist on a single Google App Engine instance.

To create a new course:

  1. Create new courses by clicking the **Add Course** button in the **Courses** tab on the Administrator page.
> > ![http://wiki.course-builder.googlecode.com/git/images/create-new-course.png](http://wiki.course-builder.googlecode.com/git/images/create-new-course.png)
  1. On the **New Course Entry**  page,
    1. Add a Unique name. This name represents this course's URL as well as its unique name in the datastore namespace. Course Builder automatically adds a `ns_` prefix to your name for its namespace representation. For example, if you choose the name `alpha`, then the URL would be `/alpha` and the automatically generated namespace will be `ns_alpha`. This namespace name can never be changed once it is generated.
    1. Add a Course Title. You can change this title later if you wish.
    1. Add the email address for the course administrator.
  1. Click **Add New Course**.
  1. Click **Close**. Access and see a list of all courses on the **Admin > Courses** page.

## Import Data into an Empty Course ##
All newly created courses are completely empty. You can however, import data from an existing course that exists on the same Google App Engine instance.

  1. Go to the **Dashboard > Outline** page of your empty course.
  1. Click **Import**.
  1. Choose a course that has the data you want from the **Available Courses** dropdown menu.
  1. Click **Import**.
  1. Click **Close**.

This does not import all the information in the `course.yaml` file. You must manually populate the `course.yaml` file in your new course. If you would like to use another course's `course.yaml` settings as a template, for example the one that comes with Power Searching with Google, do the following:

  1. Copy all the contents of the original `course.yaml`
  1. Go to **Dashboard > Settings** of your new course.
  1. Click **Edit** in the **Contents of course.yaml file** section.
  1. Delete all the contents.
  1. Paste all the contents of the original `course.yaml`
  1. Click **Save**.
  1. Click **Close**.

## Make Courses Viewable ##
When you create a new course, it is by default private, which means students cannot view it. To make your course public, go to **[Dashboard](Dashboard#Settings.md) > Settings** and change the `now_available:` assignment to `True` in the `course.yaml` section.  That is, the line should look like:

`now_available: True`

When you create a new course through the Admin Page, this setting is automatically populated in your `course.yaml` file. This setting is not in the default `course.yaml` file that is packaged with the default Power Searching with Google course. Therefore, you must manually add this entry. This setting is listed under `course:` in `course.yaml` (note the indentation):

```
course:
  now_available: True
```

## Create New Courses with gcb\_courses\_config ##
You can also add a new course through the **gcb\_courses\_config** setting in **Admin > Settings**. However, the suggested method is through the **Add Course** button because it is much easier. If you add a new course through the **gcb\_courses\_config** setting, you must specify the root course "`/`" as the last entry. For more information on mapping URLs, see [URL Mapping](URLMap.md).