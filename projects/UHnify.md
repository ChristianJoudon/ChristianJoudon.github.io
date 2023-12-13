---
layout: project
type: project
image: img/UmifyLOGO.png
title: "UHnify"
date: 2022-12-13  # Adjust the date as necessary
published: true
labels:
  - Meteor
  - Web Application
  - HTML/CSS
  - JavaScript
summary: "UHnify is designed to be a discovery platform; it's a hub for fostering engagement and community spirit. With its modern interface and advanced functionalities, UHnify invites students to immerse themselves in the UH Manoa club ecosystem actively."
---

# UHnify: The Ultimate Student Club Experience for UH Manoa

## Overview

UHnify aims to bring the UH Manoa student body together by:
- Enhancing the interaction between students and clubs at UH Manoa through a unified and interactive platform.
- Provide a comprehensive suite of tools for managing club activities and fostering community involvement.
- Allow students to both create their own clubs and join existing ones.
- Create an intuitive and personalized user experience that adapts to the evolving needs of the student body.

## System Architecture

UHnify's robust system architecture is composed of:
- **Backend**: MongoDB for flexible data storage paired with the Meteor framework for real-time data synchronization.
- **Frontend**: A combination of JavaScript, HTML, and CSS ensures a responsive and engaging user interface.


## Features

UHnify introduces features that make the university experience more connected and vibrant:
- **Club Discovery and Management**: Users can browse existing clubs to find that suits their interests. They can also create their own clubs.
- **Event Info**: Users can view info about upcoming events associated with clubs they are a member of.
- **My Clubs**: Users can browse the clubs they have membership with and leave clubs they are no longer interested in.

## User Guide

Each page on UHnify is designed to cater to specific user needs:
- **Sign In Page**: ![Sign In Page Screenshot](SignIn.png) Here users sign in to their account.
- - **Browse Clubs**: ![Browse Clubs Page Screenshot](FinalBrowseClubsPage.png) Here users can view existing clubs. They can filter through the clubs by category, as well as search for specific clubs. Users are able to join clubs that interest them.
- **My Clubs Page**: ![My Clubs Page Screenshot](FinalMyClubsPage.png) Here users can view clubs they are a member of.
- **Add Clubs**: ![Add Clubs Screenshot](StartClubForm.png) Here users can fill out a simple form to create their own club.
- **Browse Events Page**: ![Browse Events Page Screenshot](FinalEventsPage.png) Here users can view upcoming events.
- **My Events Page**: ![My Events Screenshot](FinalMyEventsPage.png) Here users can view the events they signed up for.
- **Add Events**: ![Add Clubs Screenshot](StartEventsForm.png) Users can fill out a form to organize their own events.
- **Edit Profile Page**: ![Add Clubs Screenshot](EditProfilePage.png) Here users can edit their own profile.
- **Profile Page**: ![Add Clubs Screenshot](FinalProfilePage.png) Here users can view their edited profile.
-  **Event Calendar**: ![Calendar Events Screenshot](FinalCalendarPage.png) Located at the bottom of all the event pages, this calendar offers a good reference for users to plan out their week.

## Community Feedback

Here are some recommendations and feedback from our users:
- **Adding clubs issues**: Adding clubs was not working. An error about needing a clubID was given whenever submit was pressed.
- **Landing page event card**: The card that linked to events on the landing page would not work if user was not signed in. It was suggested to make events visible to all users, even when not signed in.
- **Navbar Profile Image**: It was suggested to only have a profile image appear for logged in users. When not signed in, the dropdown menu should just say "Sign In."
- **Alerts & User Interaction**: There should be a notification when users join clubs to ensure them the command worked.

## Dev Guide

For those who want to iterate on the UHnify base:
- **Cloning the repo**: ![Clone Repo](CloneRepo.png) Head to the uhnify repository and make a copy of the repo. We recommend using Github Desktop for this.
- **Installations**: ![Commands](Installcommands.png) ![More Commands](CalendarInstalls.png) Using the terminal, run these commands in the app directory of the repo.
- **Start Editing**: Once the installations finish, invoke `meteor npm run start` in the terminal to pull up a local version of the app to make sure everything runs fine. Then, happy editing!

## Deployment

UHnify is deployed on Digital Ocean, providing a stable and scalable environment for our users. Access the application [here](https://uhnify.online).