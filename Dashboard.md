<h1>Dashboard</h1>



The Dashboard shows a broad range of information about a particular course. Information in the Dashboard includes the course outline, assets, settings, and student statistics. You must be the course author or have similar privileges (for example, teacher’s assistant) to access the Dashboard.


<img src='http://wiki.course-builder.googlecode.com/git/images/dashboard-teacher.png' />

Access the Dashboard from the menu bar. At the very top of every Dashboard page, there are breadcrumbs to aid your navigation. Breadcrumbs are navigational aids that help orient where you are on a site. It shows your current location (at the far right) and a “trail” or path that illustrates the pages you clicked through to arrive where you are now.

## Outline ##
This is your default landing page when you enter the Dashboard.  This page shows:

  * **Pages.** Links to your course announcement page and the preview page.
    * _Import_. Import settings and data from another course on the same Google App Engine instance. For example, you can import the example Power Searching course into your newly made course. This button is only available if your course is completely empty.
    * _Add Assessment_. Create new assessments directly online through the assessment editor. See [Writing Assessments](CreateAssessments#Writing_assessments.md) for more information on creating and editing courses.
    * _Add Link_. Add a URL into your course. The URL can be relative to your course URL or in can be an absolute URL.
    * _Add Unit_. Create new units. The newly created units show in the **Course Outline** section.
    * _Add Lesson_. Create new lessons and activities. The newly created lessons show in the **Course Outline** section. The newly created activities show up in the corresponding lesson pages.
    * _Organize__. Change the order of your course. You can change the order in which your students are presented with units, lessons, and assessments. You can change the order of your assessments, units, and the lessons within each unit through the up and down buttons. However, you cannot move lessons from one unit into another unit. For example, lesson 2.1 cannot "jump into" unit 1.
  * **Course Outline.** Outline of the course. It is ordered and structured exactly the way students see it. Each hyperlink goes to the corresponding course page.
  * **Data Files.** Shows the file and pathname of the data file(s) that contains lesson information for the course. If you created courses through the browser, these data files are in the Google App Engine datastore. You can use the [downloading](ExportCourseData.md) feature to download them to localhost._

## Assets ##
This page shows all the elements that are used to construct your course.

  * **Questions.** Create questions and question groups that you can use both in activities and assessments.
  * **Labels.** Use labels to allow your students to take particular tracks or paths through your course as opposed to taking the entire course.
  * **Images & Documents.** Links to the images and documents that you added to the course. To add images and documents, click the **Upload** button. This saves the file in Google App Engine datastore, which may be more expensive to host compared to statically hosting elsewhere.
  * **CSS.** Pathname to the inherited CSS. You can make changes here, by clicking **Override**, and they will propagate to all your courses.
  * **JavaScript.** Pathname to the inherited JavaScript libraries. You can make changes here, by clicking **Override**, and they will propagate to all your courses.
  * **Templates.** Pathname to the inherited HTML templates. You can make changes here, by clicking **Edit**, and they will propagate to all your courses.
  * **HTML.** Pathname to any inherited HTML files.
  * **Extensions.** List of any custom extensions you added.

## Settings ##
Settings shows how your course is customized in the `course.yaml` file described in [Customize Course Settings](CourseSettings.md). Sub-navigation tabs divide the Settings into logical groups.

  * **Course.** Settings that affect your entire course including making it public or private. You can also set whether to generate certificates for your students by setting percentage correct for any number of assessments you choose. Percentage correct can either by any positive number, for example 90% or 89.9%.
  * **Homepage.** Control details that affect your course homepage.
  * **Registration.** Control registration and student invitations.
  * **Units and Lessons.** Control unit, lesson, and assessment presentation.
  * **I18N.** Control internationalization settings like the base locale and whether students can change the locale if there is more than one.
  * **Advanced.** See and edit the contents of the `course.yaml` file directly. Caution: be careful editing this section. We suggest you use the other Setting pages instead. YAML uses whitespace and line delimiters. Introducing errant spaces can make your entire course unreachable.
  * **Preferences.** Set whether you want to see hook edit buttons or the Jinja context.  Hooks edits are custom text, links, or graphics you can add to the HTML itself, in defined parts of the page, through the browser. This elminates the need to edit the HTML directly while manually making sure those changes are carried forward on Course Builder upgrades.

## Roles ##
Create, manage, and view different roles for your course. You can associate created roles with particular emails and permissions. Currently, the role is limited to a translator role.

## Analytics ##
This page shows statistics regarding the students and the course, including individual questions, assessments, gradebook, notifications, and peer review.  Each section has its own sub-navigation item.

  * **Students.** Shows information about students in aggregate including progress and enrollment.
  * **Questions.** How students in aggregate interacted with each question in the course.
  * **Assessments.** How students in aggregate performed on the assessments.
  * **Gradebook.** How students in aggregate performed on the assessments. The Gradebook only works for questions authored on Course Builder version 1.3.0 or later.  Therefore, it will not work if you import and modify the example Power Searching with Google course, since that course was authored in version 1.0.
  * **Certificates Earned.** How many students earned certificates. You must specify the certificate requirements in **Dashboard > Course > Certificate criteria**.
  * **Data Pump.** Create custom analysis that are not natively supported in Course Builder by sending data to [Google BigQuery](https://cloud.google.com/bigquery/). See [Data Pump Configuration](https://www.youtube.com/watch?v=2ticBJcZGZ8) to see how to setup Course Buiilder and your instance to interface with BigQuery. Next see [Running Data Pump](https://www.youtube.com/watch?v=cz80K9DPtxg) to understand how to send data to BigQuery.
  * **Notifications.** Number of people who have been notified via email by a currently registered student.
  * **Peer Review.** See bar charts showing the number of assignments with a particular number of reviews.  You can also reassign reviews and delete reviewed assignments.

Remember that if you want to see progress on activities, you must turn on the activity recording setting in **Admin > Settings** by selecting the following items to `True`:
  * gcb\_can\_persist\_activity\_events
  * gcb\_can\_persist\_page\_events
  * gcb\_can\_persist\_tag\_events

<img src='http://wiki.course-builder.googlecode.com/git/images/dashboard-analytics.png' />

The **Update Statistics** button will refresh all statistics on the page. Note that the time it takes to update depends on the number of students you have.

## Search ##
Before you can retrieve results from a search through the Search box, you must index your course. Choose the appropriate option to index your course. When you first index a new course, it does not matter which indexing method you select.

Search will not cover results that are in sections marked "Private". It will also search over user created captions but not over automatically created captions.

<img src='http://wiki.course-builder.googlecode.com/git/images/dashboard-search-indexed.png' />

## Peer Review ##
Peer review is a way for students to grade each other's finished work. You would normally go into this section to see the contents of the peer review assignment and when students have issues about their peer review work. See [Peer Review](PeerReview.md) for detailed information.

  * **Select Assignment.** Here you pick a particular peer review assignment and a particular student. The student is identified by exact email. That is, the email address is case sensitive. If a peer review assignment was submitted by the student and particular peer review assignment you selected, information in the **Assignment** area show.
  * **Assignment.** This section will show the actual contents of the peer review assignment that was submitted by the selected student and any review that was done by a peer. As a course author, you can delete a particluar review with the "Remove This Review" button. You can also assign a specific person to be the reviewer of a particular stuent's work through the "Add New Reviewer" button. For example, you might want to add a Teacher's Assistant or yourself to review the work.

<img src='http://wiki.course-builder.googlecode.com/git/images/dashboard-peer-review.png' />

## Admin ##
The Administrator Page contains information regarding Google App Engine deployment and all your courses. See [Admin Page](AdminPage.md) for more information on this page.

## Help ##
This tab is a link that takes you to the relevant documentation for the current section.

## Support ##
This tab is a link to the forum where you can get and contribute information to and from the community.