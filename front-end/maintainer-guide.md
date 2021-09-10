---
layout: page
title: "A Maintainer's Guide"
permalink: /front-end/maintainer-guide/
---

# A Maintainers’ Guide

## Installation Guide

1. Install [ReactJS](https://nodejs.org/en/download/). 
2. Clone the repository `singlish-words-frontend` from GitHub to a local folder on your computer. 
3. Open a terminal, navigate to the repository's root folder, and run `npm install` to install dependencies.
4. Run `npm start` to run the front-end software locally at [localhost:3000][localhost:3000].

## Deployment

To deploy the front-end, simply run the following commands in a terminal:
1. `npm run build` 
2. `cp -r build/* /var/lib/docker/volumes/deployment_frontend-static/_data/ # to copy the built front-end to docker`

## Switching between General Public and Student Survey Versions

1. Navigate to `src/components/Form.js`. 
2. To get the General Public version, comment out `EmailStudentVersion` and `IntroductionStudentVersion` from imports. Note that it is important to comment out the imports because CSS applied is global in nature. If the student versions are not commented out, the CSS applied on the form will persist on the general public form, causing CSS styling conflicts between the general public and student versions.

![switch-2](https://singlishwords.github.io/assets/img/switch-2.png)

3. After step 2, comment out `IntroductionStudentVersion` in case 1 of switch-case. Comment out `EmailStudentVersion` in the last case.

![switch-3-1](https://singlishwords.github.io/assets/img/switch-3-1.png)
![switch-3-2](https://singlishwords.github.io/assets/img/switch-3-2.png)

4. To get the Student version, repeat Steps 1 to 3. However, do the opposite for commenting/uncommenting. Comment out `Introduction` and `Email` in imports and switch-cases. Uncomment `IntroductionStudentVersion` and `EmailStudentVersion`.


## Changing Number of Words

1. Head to `formFields.js`.
2. Define new `{question, response, timeOnPage}` objects under data field. The number of `{question, response, timeOnPage}` objects should correspond to the number of words. For example, if the desired number of words is 20, there should be 20 `{question, response, timeOnPage}` objects declared in the data field.

![words-2](https://singlishwords.github.io/assets/img/words-2.png)

3. Head to `Form.js`.
4. The number of cases between the `<Instruction/>` component (exclusive) and `</Quiz>` component (inclusive) should be equivalent to the number of words. For example, if there are 20 words, then case 4 to case 23 are needed ($23 - 4 + 1 = 20$) to render 20 words.

![words-4](https://singlishwords.github.io/assets/img/words-4.png)

## Changing Survey Text

1. Simple Text Changes

	1. Simple text changes refer to plain description changes such as the addition or removal of text. Bold, italics, or any text design modifications are not required.
	2. Head to `formData.js`.
	3. Identify the page (introductionPage/informationAboutYouPage/ instructionsPage/quizPage/emailPageStudent) that you want to adjust the text of.
	4. Identify the text to be modified.
	5. Modify the string text to your desired text.

2. Text Changes with Design Changes

	1. If you wish to make text design modifications (e.g Bold, italics, URL additions) to a page in addition to text changes, head to the actual page. For example, assume that we want to bold the “Progress” text of the Quiz page.
	2. Head to Quiz.js and identify the text. Quiz.js is the code script for the Quiz page.

![text-2-2](https://singlishwords.github.io/assets/img/text-2-2.png)

	3. Add the bold tag <b></b>. (Depending on the modification needed, you can include other tags, e.g <i></i> for italics to make the text both bold and italic)

![text-2-3](https://singlishwords.github.io/assets/img/text-2-3.png)

	4. Make a text change in formData.js for formData.quizPage.progress.

![text-2-4](https://singlishwords.github.io/assets/img/text-2-4.png)

	5. Both text and text design are now modified.

*Remarks: Please note that text with special text design modifications has to be declared as a separate key-value pair from regular text.*

![how-it-works](https://singlishwords.github.io/assets/img/how-it-works.png)
![text-2e](https://singlishwords.github.io/assets/img/text-2e.png)

For example, notice that the phrase **“Enter the first word that comes to mind”** is in bold. If that happens, we need to break the description into multiple parts so that we can add a bold tag to the bolded words. In the code, the sentence “On top of the screen a Singapore English word will appear. **Enter the first word that comes to mind when reading this word.**” is broken down into `description1`, `description2`, and `description3`. This is so that we can apply `<b>instructionsPage.firstParagraphDescription.description2</b>` in `Instructions.js`.

Having such a HTML design implies that if there are drastic changes to the sentence structure (e.g Multiple text modifications that differs drastically from the original sentence structure), the maintainer has to go into the specific code page and make large changes to the tags defined, and also rewrite large parts of the existing key-value pairs.

However, by consolidating all text strings into formData.js, it will be very convenient to make minor text adjustments (refer to Simple Text Changes) or modify text with existing design modifications (refer to Text Changes with Design Changes). This is because the maintainer does not have to go into the specific code page and alter any HTML structures in the code. Thus, this design was chosen.

## Google reCAPTCHA Configuration
 
### Overview

To reduce the occurrences of botting, Google reCAPTCHA has been implemented on the survey form.

There are two reCAPTCHA validations - one compulsory validation on the Instructions Page, and a randomized validation on the Quiz/Word Page. The randomized validation has a 10% probability of appearing on each word page, and this randomized validation will occur at most once. In other words, it is also possible for a survey participant to go through the entire survey without having to perform the randomized validation.

As such, each survey participant will have to perform at least one reCAPTCHA validation and at most two reCAPTCHA validations.

### reCAPTCHA Configuration

If new site domains are introduced, these domain names have to be added to Google’s reCAPTCHA site so that reCAPTCHA can work on new site domains.

To add new site domains to Google reCAPTCHA, log in at 

URL
https://www.google.com/recaptcha/admin/create 

Add a new domain under “Add a domain, e.g. example.com”
