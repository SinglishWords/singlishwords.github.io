---
layout: page
title: "Quality Assurance"
permalink: /front-end/quality-assurance/
---

# Quality Assurance

Remarks: To avoid any source of confusion, a distinction between the word “survey” and “study” is made. The word “survey” in this section refers to the “A Small World of Singlish Words” survey form, while the word “study” refers to the study of the Singapore mental lexicon using free associations. As such, end-users are referred to as survey participants as we are focusing on the interaction of the end-users with the survey form.
Top-Level Overview
The intention of the front-end form is for survey participants to take part in a word association study. For them to do so successfully, there are two important aspects of the form that have to be quality-assured. 
Firstly, survey participants need to see the instructions on the form to guide them towards survey completion. As such, they should be able to view the relevant instructions and interact with the various components (e.g texts, information dropdown buttons) on the page.
Secondly, survey participants should be able to perform various functionalities necessary for survey completion. 
To satisfy the first criteria, we will first perform a basic sanity check for the front-end form by using Graphical User Interface (GUI) testing. The goal of the testing is to ensure that all survey information that should be on the page can be seen on the page. Once we have ensured that the survey information on the page is accurate using GUI testing, we can proceed with testing the functionalities.
For the second criteria, we will adopt functionality testing to ensure that functionality end-goals are met. We will first define a set of user stories to understand the functionality end goals of the front-end form. User stories are short, simple descriptions of a feature told from the perspective of the person who desires the new capability, usually a user or customer of the system. From there, we will then define a set of test cases to ensure that these functionality end-goals are met.
As the front-end form for this project is a relatively simple piece of software, both GUI testing and functionality testing adopted will be manual. This is because the number of test cases is small, ranging from around 10 to 20 in total. Hence, test automation is not required.
