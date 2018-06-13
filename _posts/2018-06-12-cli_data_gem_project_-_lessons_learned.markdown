---
layout: post
title:      "CLI Data Gem Project - Lessons Learned"
date:       2018-06-13 02:06:02 +0000
permalink:  cli_data_gem_project_-_lessons_learned
---


Prior to writing any code for this lab I watched Avi’s lab walkthrough a couple of times. My first thought was that this info is great to outline how to get a ruby gem started, however I need to take a step back. This was the first time I had to start coding from scratch with files and folders that did not originate from forking a Learn Lesson. This frightened me. How do I start a project from the IDE? How does the IDE connect to github? What is github? Do I have to save the file locally on my computer?

I definitely needed to refresh my memory on some past lessons that I did not fully master or comprehend, and that started with a couple of study groups like Github Advanced and Debugging with Pry. Other topics this project consisted of were creating a gem, the benefits of outlining your CLI prior to writing any code, using object oriented ruby vs arrays and hashes, and refactoring. I also refreshed my memory on some ruby methods, cli interface, and regular expressions. My notes and learnings are outlined below.

**Git/Github –**  git is a version control system that tracks changes to your git project on your local machine. Github is webservice that lets you host and track git repositories. 

Commands used in this lab: `git init`, `git remote -v`, `git status`, `git add .`, `git commit –m “add message here"`, `git push`

**Debugging with Binding.pry/.inspect/puts –** There are a few different ways to test to see if a section of code is executing properly. Prior to this project I was mainly debugging my code by running sections of it in http://repl.it. For this project I needed to use nokogiri, open-uri and classes that interacted with each other, so I needed an approach that could be used within the Learn IDE. 

* To exit binding.pry on the command line type: `exit`, `exit!`, `!!!`, or `ctrl-c`
* `raise obj.inspect        #=> “#<obj:0x0300c868>” `  --- this is good to use in a loop instead of `binding.pry` as it will only iterate once. However, this does not prompt the user with an ‘irb’ type interface. 
* Puts can be used as a flag. It is a good way to make sure an if statement is functioning properly.

**Generating a Gem -**

RubyGems: https://guides.rubygems.org/make-your-own-gem/

**Nokogiri, Open-uri, Webscraping, and Regex –** Setting up nokogiri and open-uri is fairly straightforward. My issue with this part of the project was (1) understanding what I needed to be scraping from the HTML and (2) selecting the right information through regular expressions (regex). Lots of trial and error. And this website was a huge help: http://www.rubular.com/

**General Outline of Creating the Project –** The outline below was given in the CLI Project Walkthrough. This direction was extremely helpful to have. Stubbing out the interface of the CLI helped define the classes I needed to create, and interestingly enough, they did not change much during the project.

1.	Plan your gem, imagine your interface
2.	Start with the project structure - google
3.	Start with the entry point - the file run
4.	Force that to build the CLI interface
5.	stub out the interface
6.	Start making things real
7.	discover objects
8.	program

**Object Oriented Ruby –** This project further convinced me on the benefits of object oriented ruby. The metaphor that it creates makes extracting properties of an object functional as opposed to searching through indexes of arrays and hashes.

**Refactoring -** I definitely need to work on this moving forward. 

