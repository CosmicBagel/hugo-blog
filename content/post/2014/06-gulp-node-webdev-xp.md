---
date: 2014-11-14T13:51:00-07:00
description: "Man, I am lovin’ gulp. It was a shaky relationship at first, but I think we’ve come a long way.

I’ve been working on a new website for myself to show off work I’ve done, I thought I’d give Node a try and try to embrace the node realm of tools as much as possible."
title: "Gulp & node, best web dev experience ever"
draft: false
topics:
- how-to
type: post
---

Man, I am lovin’ gulp. It was a shaky relationship at first, but I think we’ve come a long way.

I’ve been working on a new website for myself to show off work I’ve done, I thought I’d give Node a try and try to embrace the node realm of tools as much as possible. The one major hitch I ran into is not being able to use Jekyll since it has some OSX specific requirements (I’m working on a windows machine). This was part of me trying to get all of Bootstrap’s grunt workers running. Long story short I gave up on bootstrap and decided to just have a section in my LESS main file dedicated to Bootstrap modifications. Really I was only using Bootstrap for its grid css.

I just mentioned LESS, I had stopped using it for a while since previously I only had used it where it is compiled server side and wasn’t interested in setting up the tools to compile it locally. Well the time to set that up has come. My time exploring the node way of life led me to a number of discoveries, one of which being that tasks runners are a big deal.

Task runners in node take care of a lot of the annoying work and extra steps. One such step being refreshing your browser. BrowserSync watches files and refreshes your browser when one of those files change. Another one might be compiling and minifying your LESS files, you can use the command line version easily enough, but you could also have it compile and minify every time you save. Once that’s done browser sync will see that your minified css file has changed and refresh your browser. (MAGICAL!)

Setting up a task runner isn’t hard, there’s plenty of documentation as I’ve discovered. In my case I decided to go for gulp over grunt. It appeared to be getting a lot of fan fare, fixing a number of issues grunt had by taking files and streaming them from task to task rather than having to write everything to the hard drive at the end of each task. A good case for this would be compiling your LESS files, then minifying them into a single CSS file. You actually have three steps in there, compile to separate files, combine into one, then minify. Gulp’s syntax was also much cleaner I discovered since you could pleasantly chain steps in a task using `.pipe()` at the end of each one.

Here’s what my `LESS` task looks like in my `gulpfile.js`

    gulp.task('less', function () {
        gulp.src('public/css/main.less')
            .pipe(plumber({
                errorHandler: notify.onError({
                    message: "<%= error.message %>",
                    title: "Style error"
                })}))
            .pipe(watch('public/css/*.less'))
            .pipe(less())
            .pipe(autoprefixer())
            .pipe(cssMinify())
            .pipe(concat('cb-style.min.css'))
            .pipe(gulp.dest('public/css'));
    });

You tell gulp about the task by giving it a name and passing in a function. Get the files with `gulp.src`, and then you’re off. I’m using Plumber to keep gulp from crashing anytime I make a mistake in my less files. And the `watch` function is what keeps the task runner actively watching the files.

I don’t run the node server with gulp, instead I use `nodemon` alone by itself. The benefits of this are that if one or the other crashes, they don’t both die needlessly, requiring a longer wait time for them to spin back up. Nodemon is quite capable all by itself and doesn’t need gulp to wrap it, nodemon’s job is to watch the server js files are restart it if changes are made to the code. Additionally it will try to restart the server if it crashes.

I think that’s enough ranting for now.
