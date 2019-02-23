# HelloJoy Code Challenge

### Background and context
A core component of the HelloJoy platform is administering standardized clinical assessments via our mobile app. In a nutshell, a standardized clinical assessment is a multiple-choice questionnaire that determines symptom severity for disorders such as depression, anxiety, etc. Here’s an example of a common assessment for depression called the PHQ-9: https://www.mdcalc.com/phq-9-patient-health-questionnaire-9.

Using our platform, clinicians are able to pick and choose which standardized clinical assessment(s) they want their patients to complete. A clinician only has to configure this once for each patient, and we’ll then take care of notifying the patient on the proper cadence, having them answer the necessary questions, scoring the assessment, documenting the results, and sharing the results back with the clinician.

### The challenge
You will build a portion of the patient-facing experience that allows an individual to complete any assessments that have been assigned to them. This experience should be dynamic, meaning different patients will be assigned different assessments. The code you write must be flexible enough so that patients are only prompted to complete assessments that they’re assigned.

To figure out which assessments a given user is assigned to complete, we’ve created mock endpoints. We have created two test cases for you (feel free to create more on your own), which are presented as two separate endpoints for simplicity:

- Frank Smith: https://www.mocky.io/v2/5c7164513500006000e9e829
- Jane Doe: https://www.mocky.io/v2/5c7164773500007000e9e82a

Note: In reality, this is a single endpoint which is passed a user_id, e.g. `GET /patients/assessments`…because there is no concept of a user_id in the mock endpoints, each endpoint represents a different user.

The endpoints return an array of assessment objects. An assessment always contains:

- A unique id
- Metadata about the assessment (name, display name, total score, cadence)
- An array of questions
- An array of answers
- Mapping (used to score the answers)

Using the JSON response from the endpoint, the patient should be directed through each question of their assigned assessment(s).

Here's an example of how the assessment experience should look for Frank Smith: https://cl.ly/65964d254109. And here's an example of how it should look for Jane Doe: https://cl.ly/110393a23cbe. Notice how Frank's flow shows two assessments (combined into one seamless experience) and Jane's flow only shows one. You’ll want to match this functionality.

As a patient answers each question, you will need to keep track of how they answered so the data can be sent to the backend and ultimately stored in a database. You should store the answer data in the following format:


    {
        "assessments": [{
            "id": <assessment_id>,
            "answers": [
                {
                    "key": <question.key>,
                    "value": <answer.value>
                },
                {
                    "key": <question.key>,
                    "value": <answer.value>
                },
                ...
            ]
        },
        {
            "id": <assessment_id>,
            "answers": [
                {
                    "key": <question.key>,
                    "value": <answer.value>
                },
                {
                    "key": <question.key>,
                    "value": <answer.value>
                },
                ...
            ]
        }
        ]
    }

And an example of the above format, using real data: https://gist.github.com/dannyfreed/002230ad612e397455732275212f8036


### Requirements
- You can complete this challenge using any languages, frameworks, or platforms you'd like, but it must be easily viewable/runnable on our local machines. We want to be able to click/tap through the experience like a user would as well as inspect the code.
- Patients should only be able to view/complete assessments that are assigned to them
- If a patient is assigned more than one assessment, they should be able to answer all questions back-to-back, as if it was a single combined assessment.
- Questions should be displayed one at a time on a given page/screen
- Each page/screen should display:
  - The assessment `title`
  - The assessment `display_name`
  - The question `title`
  - All answer options for the given assessment, as buttons that just display the answer `title` as text
  - The question number out of the total number of questions in all assessments (e.g. `1 out of 16`)
- Tapping on an answer option should automatically advance the user to the next question
- Upon answering the final question, simply log/print out the data as you would submit it to the backend POST endpoint (no need to actually make this POST request)


### Bonus Points:
- Create a progress bar that shows where a user is in the overall assessment experience (i.e. how much they've completed so far, how much is left)
- Design the experience (e.g. buttons, animations, etc) in a way that makes it feel quick and efficient
- Create and share additional test cases to ensure your code can handle a wide range of scenarios and edge cases

### Logistics
- We anticipate this challenge should take 3 hours or less. Please
- Feel free to leverage online documentation, stack-overflow, etc to help guide you if needed, but all code you write should be your own
- You are welcome to use packages such as Lodash, but try to be as efficient as possible

