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


## Introduction

At UH Manoa, the student body is bustling with clubs and organizations that foster community, learning, and networking. Despite the vibrant scene, there lacks a singular, cohesive platform to manage and engage with these groups. Enter "UHnify," the solution designed to centralize, streamline, and enhance the club experience for UH Manoa students.

## Overview

UHnify's key features include club discovery and management, event information, and a personalized user experience.

## System Architecture

Combines MongoDB and Meteor for the backend, with a frontend of JavaScript, HTML, and CSS.

## Features

- Club Discovery and Management
- Event Information
- My Clubs: View and manage club memberships

## User Guide

Each page on UHnify is designed to cater to specific user needs:
- **Sign In Page**: ![Sign In Page Screenshot](SignIn.png) Here users sign in to their account.
- **Browse Clubs**: ![Browse Clubs Page Screenshot](FinalBrowseClubsPage.png) Here users can view existing clubs. They can filter through the clubs by category, as well as search for specific clubs. Users are able to join clubs that interest them.
-  **Event Calendar**: ![Calendar Events Screenshot](FinalCalendarPage.png) Located at the bottom of all the event pages, this calendar offers a good reference for users to plan out their week.

## Community Feedback

Feedback includes suggestions for improving club addition, landing page event visibility, navbar user experience, and user notifications.

## Dev Guide

For those who want to iterate on the UHnify base:
- **Cloning the repo**: ![Clone Repo](CloneRepo.png) Head to the uhnify repository and make a copy of the repo. We recommend using Github Desktop for this.
- **Installations**: ![Commands](Installcommands.png) ![More Commands](CalendarInstalls.png) Using the terminal, run these commands in the app directory of the repo.
- **Start Editing**: Once the installations finish, invoke `meteor npm run start` in the terminal to pull up a local version of the app to make sure everything runs fine. Then, happy editing!

## Deployment

UHnify is deployed on Digital Ocean, providing a stable and scalable environment for our users. Access the application [here](https://uhnify.online).