# Friage: Get the Patient, the Right Care, Right now

## **Inspiration**

Have you ever spent a whole night waiting in the ER for an injury? Every 9 minutes, someone in Los Angeles dies waiting for emergency care. Ambulances get diverted. ERs receive patients blindly. Dispatchers have nothing but a panicked voice on the phone to work with. No image nor available triage. No clinical picture. Studies in the Annals of Emergency Medicine directly link ambulance diversion to a 9% increase in patient mortality. At Centinela Hospital in Inglewood, EMTs spend an average of 60 minutes offloading a single patient, 30 minutes above the county standard, while the next emergency waits. We built Friage because regular people driving themselves to the ER have no real-time way to know which hospitals are on diversion or disaster status right now, and we believe this is the solution.

## **What it does**

Friage is not just a symptom checker or a generic injury detector. It is a dispatch routing engine that solves a specific operational problem: a 911 dispatcher has a patient on the ground, a bystander on the phone, and no visual information to work with.

Friage turns a bystander photo into a full clinical routing decision in under 3 seconds. A dispatcher or first responder uploads a photo of the patient. Cloudinary's AI Vision analyzes runs it against 190+ purpose-built medical tag definitions, using clinical descriptors like decorticate posturing, unequal pupils, hemorrhagic pooling, circumferential burns, and more. This gives a dispatcher and a receiving ER something they can actually act on.

Combined with a typed symptom description, this data is passed to Groq's cutting edge Llama AI model, along with real licensed bed and treatment capability data pulled from official government and verified sources, such as the California CDPH dataset, and cross-references the information against the nearest hospitals from Google Maps and Places API. Friage does not just pick the closest hospital. It matches the patient's clinical picture to the facility that can actually treat them, surfacing trauma centers for TBI indicators, cardiac units for chest presentations, and pediatric ERs when the scene warrants it.

The final output is a ranked hospital list with Emergency Severity Index (ESI) triage levels 1 through 5, ETAs, treatment types, open status, bed capacity, and a fully-ready PDF Patient Care Report (PCR) for EMTs and first-responders before they arrive, directly available via a QR code. **This way, the no time is wasted sending patients to full or overcrowded ER rooms.**

## **How we built it**

- AI Injury and Accident Tagging: Upload a photo of the patient and Friage uses Cloudinary's cutting-edge AI Vision to automatically analyze it against 190+ purpose-built medical tag definitions, detecting hemorrhage, altered consciousness, fractures, burns, posturing, and mechanism of injury. 

- Automatic ESI Triage Scoring and Reporting: Every case is instantly synthesized and assigned an Emergency Severity Index level 1 through 5, with clinical reasoning, immediate action steps, and what not to delay for, using Groq's cutting-edge Llama AI Model, giving first responders a structured assessment in the severity of the injury, the appropriate treatment needed, and which and what hospitals suit the patient best the fastest. Information on the availability and 

- Real Hospital Matching: Friage cross-references every nearby hospital against real licensed bed and treatment capability data from live and updated government provided official data, such as the California Department of Public Health's CKAN API for hospital data, facility information, and specialty treatment information, finding the right specialty centers for head injuries, cardiac units for chest presentations, and pediatric ERs when the patient is a child, not just the closest location on the map. It then cross-checks this information with Google Maps Routes and Places APIs to determine the shortest ETAs and determine the availability of each hospital.

## **Challenges we ran into**

Real-time hospital bed availability has no public API in the US; systems such as HBEDS exist, but many are restricted to government officials. It was difficult to get around this, and we ended building an estimation model using official datasets, such as the CDPH monthly bed data, crowdsourced ETA and bed availability data, and using Cloudinary's AI Vision tagging to return tags from photography models, which required us to manually define specific medically meaningful information in order to generate an accurate report.

## **Accomplishments that we're proud of**

Building a working end-to-end pipeline, from photo upload to hospital recommendation, in under 36 hours was very difficult but also eye-opening for us as high-school students. We are proud of our use of real data from many sources: we pulled very real data from sources such as licensed specialty information and using Cloudinary AI Vision tagging pipeline processes on **real  LA hospitals right now is something we are very proud of (yes, even UCLA!).**

## **What we learned**

We learned that the hardest part of health tech isn't really the AI but the availability of data. Through one of our team member's, Pranav, and his experiences in assisting first-responders in ER rooms was very eye-opening to us on how long people across the US have to wait to receive the healthcare they need. Many lives could be saved by more streamlined and efficient processes, and we believe that using AI and recent technological innovations could greatly help this industry and the problems that many people face daily. Over 250,000+ people unfortunately pass away every year due to ER accidents or just long wait times, and most of this could be improved by faster and easier prioritization of injuries and improved routing for patients.

Public health infrastructure data is very fragmented, inconsistently formatted, and rarely designed for open-access. We also learned that using new and modern solutions, such as Cloudinary's AI Vision addon is incredibly powerful in its auto-tagging feature for many domain-specific applications, the ability to define custom tag descriptions and extracting data from just normal photos is incredibly useful and we hope we can help develop more tools like these in the future.

## **What's next for Friage**

For the future, we want to integrate CAD system integration so Friage can feed into 911 dispatch infrastructure, EHR pre-notifications so any trauma teams are notified before arrival, and predictive bed forecasting using historical admission patterns for more accurate 