# Coding Challenge

### Background and context
One component of our platform is administering standardized clinical assessments via our mobile app. In a nutshell, a standardized clinical assessment is a multiple-choice questionnaire that determines symptom severity for disorders such as depression, anxiety, etc. Here’s an [example](https://www.mdcalc.com/phq-9-patient-health-questionnaire-9) of a common assessment for depression called the PHQ-9.

Using our platform, clinicians are able to pick and choose which standardized clinical assessment(s) they want their patients to complete. A clinician only has to configure this once for each patient, and we’ll then take care of notifying the patient on the proper cadence, having them answer the necessary questions, scoring the assessment, documenting the results, and sharing the results back with the clinician.

### The challenge
You will build a portion of the patient-facing experience that allows an individual to complete any assessments that have been assigned to them. This experience should be dynamic, meaning different patients will be assigned different assessments. The code you write must be flexible enough so that patients are only prompted to complete assessments that they’re assigned.

To figure out which assessments a given user is assigned to complete, we’ve created mock endpoints. We have created two test cases for you (feel free to create more on your own), which are presented as two separate endpoints for simplicity:

- [Frank Smith](https://www.mocky.io/v2/5c86be20340000e21389c26b)
- [Jane Doe](https://www.mocky.io/v2/5c7164773500007000e9e82a)

*Note: In reality, this is a single endpoint which is passed a user_id, e.g. `GET /patients/assessments`…because there is no concept of a user_id in the mock endpoints, each endpoint represents a different user.*

The endpoints return an array of assessment objects that are assigned to a given patient. An **assessment** always contains:
- A unique id
- Metadata about the assessment (name, display name, total score, cadence)
- An array of questions
- An array of answers
- Mapping (used to score the answers)

Using the JSON response from the endpoint, the patient should be directed through each question of their assigned assessment(s). Here's an example of how the assessment experience should look for [Frank Smith](https://cl.ly/65964d254109). And here's an example of how it should look for [Jane Doe](https://cl.ly/110393a23cbe). Notice how Frank's flow shows two assessments (combined into one seamless experience) and Jane's flow only shows one. You’ll want to match this functionality.

As a patient answers each question, you will need to keep track of how they answered so the data can be sent to the backend and ultimately stored in a database. You should store the answer data in a specific format, an example of which can be found [here](https://gist.github.com/dannyfreed/002230ad612e397455732275212f8036)

### Requirements/Specs
- You can complete this challenge using any language or framework that you choose
- Patients should only be able to view/complete assessments that are assigned to them
- If a patient is assigned more than one assessment, they should be able to answer all questions back-to-back, as if it was a single combined assessment
- Questions should be displayed one at a time on a given page/screen
- Each page/screen should display:
  - The assessment `title`
  - The assessment `display_name`
  - The question `title`
  - All answer options for the given assessment, as buttons that just display the answer `title` as text
  - The question number out of the total number of questions in all assessments (e.g. `1 out of 16`)
- Tapping on an answer option should automatically advance the user to the next question
- Across all screens, display a progress bar that indidcates where the user is in the overall assessment experience that udpates with each completed question
- Upon answering the final question, simply log/print out the data as you would submit it to the backend POST endpoint (no need to actually make this POST request)
- When you’re done, host it somewhere (e.g. on Amazon EC2, Heroku, Google AppEngine, TestFlight, etc.)

### Deliverable
- Please send us a link to the hosted repository with your code (e.g. Github, Bitbucket)
- The repo should include a README that includes the following items:
  - Link to to the hosted application
  - Description of the problem and solution
  - Reasoning behind your technical choices
  - Trade-offs you might have made, anything you left out, or what you might do differently if you were to spend additional time on the project
  - Link to other code you're particularly proud of
  - Link to your resume or public profile

### How we review
**We value quality over feature-completeness.** It is fine to leave things aside provided you call them out in your project's README. The goal of this code challenge is to help us identify what you consider production-ready code. You should consider this code ready for final review with your colleague, i.e. this would be the last step before deploying to production.

The aspects of your code we will assess include:
- **Clarity**: does the README clearly and concisely explains the problem and solution? Are technical tradeoffs explained?
- **Correctness**: does the application do what was asked? If there is anything missing, does the README explain why it is missing?
- **Code quality**: is the code simple, easy to understand, and maintainable? Are there any code smells or other red flags? Does object-oriented code follows principles such as the single responsibility principle? Is the coding style consistent with the language's guidelines? Is it consistent throughout the codebase?
- **Security**: are there any obvious vulnerabilities?
- **UX**: is the web interface understandable and pleasing to use?
- **Technical choices**: do choices of libraries, frameworks, etc seem appropriate for the chosen application?
