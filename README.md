Hospital Check-in with AI Triage Assistant

A single-page prototype that lets intake nurses check patients in, get an AI-suggested acuity level, and assign each patient a nurse and a bed. Built for the AI Innovators capstone.

This is a classroom demo, not medical software. It must not be used for real patient care or real patient information. The AI model is trained on synthetic data.

What it does
Check-in form: name, date of birth, MRN, reason for visit, pain level (0 to 10), mental status (alert, confused, disoriented, drowsy, unresponsive), acuity, nurse and bed.
AI triage suggestion: a model suggests Routine, Urgent or Critical, with a confidence bar for each level and a plain-language explanation. The nurse can accept it with one click or override it.
Auto-assignment: leave nurse and bed on Auto to pick the least-busy nurse (max 4 patients each) and the first open bed. Critical patients go to Bay A, nearest the nurses' station.
65+ priority: patients aged 65 or older, from the date of birth or a checkbox, get a badge, rank higher in the patient list, and trigger an alert for the assigned nurse.
Explanations: each patient shows why they are or are not prioritized, based on pain, mental status, age and red-flag words in the reason for visit.
Live board: bed map, nurse workload meters, and a patient list with discharge.
How the AI works

The model is a softmax logistic regression (supervised learning) that trains in the browser when the page loads.

Inputs: pain level, mental status, age 65 or older, red-flag words in the reason (for example "chest pain"), and routine-visit words (for example "refill").
Output: probabilities for Routine, Urgent and Critical.
Training data: 900 synthetic cases. Labels come from a scoring rule written for this demo, so the roughly 84% held-out accuracy shows the model learned that rule, not that it is clinically valid.
Human in the loop: the AI only suggests. A nurse makes the final call. A header stat shows how often the nurse and the AI agreed.
Run it

It is one self-contained file with no build step and no server.

Download index.html.
Open it in any modern browser.

Patient data is kept only in your own browser (localStorage). It is never sent anywhere and is not shared between devices.

Publish it with GitHub Pages
Put index.html in the root of this repository.
Go to Settings, then Pages.
Set the source to Deploy from a branch, choose main and / (root), and save.
After a minute or two, the site is live at https://YOURUSERNAME.github.io/REPOSITORY-NAME/.
Limitations
Alerts and patient data are not shared between devices. A real system would need a shared database and notifications.
The model is trained on synthetic data and has not been checked for bias.
Nurse names, beds and the unit layout are placeholders.
Next steps
Train on real, de-identified check-in data with proper approval.
Test for bias across age and other groups.
Add a shared backend, user accounts and nurse notifications.
Run a clinical pilot and safety review.
