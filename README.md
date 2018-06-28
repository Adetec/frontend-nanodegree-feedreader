# Feed Reader Testing

## Table of Contents

* [Introduction](#introduction)
* [Why this Project?](#why-this-project)
* [How to run?](#how-to-run?)
* [Presente test suites in this project](#presente-test-suites-in-this-project)
* [Dependencies documentation](#dependencies-documentation)

## Introduction
In this project, a web-based application reads RSS feeds. The original developer of this application clearly saw the value in testing, they've already included [Jasmine](http://jasmine.github.io/) and even started writing their first test suite! Unfortunately, they decided to move on to start their own company and we're now left with an application with an incomplete test suite. That's where I come in :wink: .

## Why this Project?

Testing is an important part of the development process and many organizations practice a standard of development known as "test-driven development". This is when developers write tests first, before they ever start developing their application. All the tests initially fail and then they start writing application code to make these tests pass.


## How to run?
Download the project, open `ìndex.html`, or you can check it out [here](http://adellassagtestfeedreader.bitballoon.com/), once the page is loaded, Test results should be displayed at the end of the page


# Presente test suites in this project

Following the Feed Reader Testing [Project Rubric](https://review.udacity.com/#!/projects/3442558598/rubric) specifications from [JavaScript Testing course](https://www.udacity.com/course/ud549), I:
1. downloaded the [required project assets](http://github.com/udacity/frontend-nanodegree-feedreader).
2. Reviewed the functionality of the application within my browser.
3. Explored the application's HTML `index.html`, CSS `css/style.css` and JavaScript `js/app.js` to gain an understanding of how it works.
4. Explored the Jasmine spec file in `jasmine/spec/feedreader.js` and reviewed the [Jasmine documentation](http://jasmine.github.io).
5. Edited the `allFeeds` variable in `js/app.js` to make the provided test fail and see how Jasmine visualizes this failure in your application.
6. Returned the `allFeeds` variable to a passing state.
7. Wrote a test that loops through each feed in the `allFeeds` object and ensures it has an URL defined and that the URL is not empty.
```
it('Each feed object has url and not empty', () => {
    for (feed of allFeeds ){// Loop over all array objects
        expect(feed.url).toBeDefined();// Expect if url key exist in each object
        expect(feed.url).not.toBe('');// Expect if it isn't empty
    };
});
```
8. Wrote a test that loops through each feed in the `allFeeds` object and ensures it has a name defined and that the name is not empty.
```
it('Each feed object has name and not empty', () => {
    for (feed of allFeeds ){
        expect(feed.name).toBeDefined();// Expect if name key exist in each object
        expect(feed.name).not.toBe('');// Expect if it isn't empty
    };
});
```
10. Wrote a new test suite named `"The menu"`.
11. Wrote a test that ensures the menu element is hidden by default.
12. Wrote a test that ensures the menu changes visibility when the menu icon is clicked. This test should have two expectations: does the menu display when clicked and does it hide when clicked again.
```
/* TODO: Write a new test suite named "The menu" */
describe('The Menu', () => {
    /* TODO: Write a test that ensures the menu element is
     * hidden by default. You'll have to analyze the HTML and
     * the CSS to determine how we're performing the
     * hiding/showing of the menu element.
     */
    it('Menu element is hidden by default', ()=>{
        expect($('body').hasClass('menu-hidden')).toBe(true);// Expect if menu element is hidden by default
    });
     /* TODO: Write a test that ensures the menu changes
      * visibility when the menu icon is clicked. This test
      * should have two expectations: does the menu display when
      * clicked and does it hide when clicked again.
      */
    it('Menu changes visibilty when Icon is clicked', ()=> {
        $('a.menu-icon-link').trigger('click');// trigger menu click event
        expect($('body').hasClass('menu-hidden')).toBe(false);// Expect then if menu appears
     
        $('a.menu-icon-link').trigger('click');// trigger menu click event
        expect($('body').hasClass('menu-hidden')).toBe(true);// Expect then if menu hides
    });
});
```
12. Wrote a test suite named `"Initial Entries"`.
14. Wrote a test that ensures when the `loadFeed` function is called and completes its work, there is at least a single `.entry` element within the `.feed` container.
```
/* TODO: Write a new test suite named "Initial Entries" */
describe('Initial Entries', () => {
    /* TODO: Write a test that ensures when the loadFeed
     * function is called and completes its work, there is at least
     * a single .entry element within the .feed container.
     * Remember, loadFeed() is asynchronous so this test will require
     * the use of Jasmine's beforeEach and asynchronous done() function.
     */
    beforeEach(done => {
        loadFeed(0, done);
    });

    it('There is at least one entry', ()=> {
        expect($('.entry').length).not.toBe(0);//Expect if There is one or more entries
    });
});
```
15. Wrote a test suite named `"New Feed Selection"`.
16. Wrote a test that ensures when a new feed is loaded by the `loadFeed` function that the content actually changes.
```
/* TODO: Write a new test suite named "New Feed Selection" */
describe('New Feed Selection', () => {
    /* TODO: Write a test that ensures when a new feed is loaded
     * by the loadFeed function that the content actually changes.
     * Remember, loadFeed() is asynchronous.
     */
    let oldFeed;
    beforeEach(done => {
        // Get actual feed
        oldFeed = $('.feed').html();
        // Bring
        loadFeed(1, done);
    });
    it('New feed is selected', () => {
        expect($('.feed').html()).not.toBe(oldFeed);// Expect if new feed is selected
    });
});
```
## Dependencies documentation
- [Jasmine](https://jasmine.github.io/)
- [Jquery](https://api.jquery.com/)