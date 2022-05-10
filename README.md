# Tutor Finder
A tool for finding out *which* tutors are available and *when* to help with various classes at a given institution.

This particular repository focuses on tutors available at CSU Channel Islands.

## Background
This is an academic capstone project made in pursuit of a Bachelors in Computer Science at CSU Channel Islands.  With Human-Centered Design as the guiding principle of this capstone project, the focus was initially to find an actual problem that a group of people had, and to then use the skills learned in the degree program to find a software-based solution to that problem.  The problem found in need of a solution was the sluggish and confounding mess of spreadsheets required to find a tutor supporting a particular course at CSUCI.

Tutors - as well as those looking for help - were required to cross-reference two or more spreadsheets in order to figure out what tutors support a particular course and what time those tutors are available.  This wastes a couple minutes even for those familiar with the spreadsheets and is even more confusing for students that have never used the spreadsheets before.  Realizing first-hand that this was a problem, it became the main issue to solve.

A few different solutions were considered before deciding on a web application.  The Learning Resource Center already has certain software available to organize tutors and this was the initial focus.  However, there was no reliable way of making an add-on for this software, and so a different approach was found.  Without changing the system of spreadsheets the staff use for convenience, I designed a simple static website that can be hosted nearly anywhere that can parse the spreadsheets and display the results simply and easily.

## How Does It Work?
This web application uses basic HTML5, CSS, and JavaScript, with a little Bootstrap 5 for visual appeal.  The main components include a series of dropdown HTML select objects for users to enter their desired course, and a custom HTML table for displaying which times a tutor is available for that selected course.

The application relies on JavaScript to gather data about the tutors from a series of Google Sheets and to then update the HTML to reflect what courses have tutors supporting them and when.  There are two kinds of spreadsheets involved, one for [tutor availability](https://docs.google.com/spreadsheets/d/1IndeWlRySoNuQXwMFqSZFY0KAJNr2aHSHR77cRfI16I) and one for [tutor specialties](https://docs.google.com/spreadsheets/d/1vje4JcWWgUsCAJA7DhEeRfPdI0AJjHP9ECToWULqClI); see the links for examples.  Internally, each spreadsheet is converted into an object designed to make searching for tutors and times easier.

## Requirements and Testing
If you wish to run, test, edit, or develop this website, there are a few things you will need:
  - A web server that can host static files (e.g. AWS Buckets, [HelioHost](https://heliohost.org/), [CloudFlare Workers](https://workers.dev/), etc.)
    - Some websites use code to generate HTML/CSS/JS on request (dynamically generated), which has special 
      server requirements (sometimes costs more). Most hosting services allow "static" HTML/CSS/JS, where you only need to copy and paste the files you see here into a directory, and then request those files by a URL unique to your website (e.g. `https://yourdomain.com/citutors.html`)
  - A browser is of course required to test the website.  Chrome, Firefox, Brave, Edge, and many others
    have development tools available to make the process of testing and editing static HTML, CSS, and JavaScript easier.

If you wish to use this for your own academic institution, you will need to format a few spreadsheets in the same manner as the examples.  Color and styling is ignored by the website, but the formatting of names is not optional and must follow what you see in the examples.  You will need to make these sheets public and then copy the spreadsheet ids from the URL into the appropriate variables in the `citutors.html` file:
```js
    const specialtiesSheetID = ...;
    const timesheetIDs = [...];
```
Consult the [wiki](https://github.com/HydroPlume/capstone-tutorfinder/wiki) for specifics.

## Contributing and Licensing
This code falls under the MIT license which means you can do just about anything with the code as long as you provide notice of the original license of this project.  I'd rather you keep additions open-source and attribute this project where possible, but these are not required.

If you'd like to contribute code to *this* repository in particular, please make a fork, commit code to that fork, and send a pull request.  It's also recommended that you create an issue to describe why the pull request is useful in the first place.