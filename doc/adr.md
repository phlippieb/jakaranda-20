# Architecture decision record

Note: as this project is quite small and run by one developer, all architecture decisions are recorded in this one document for now.

## 001 Mobile application

Context: This project could have been implemented as a web application or as a mobile application. A web application could be easily accessible by all members of the wine tasting guild on any device. However, a mobile application has these advantages:

- I know mobile development better, so I can create the app faster.
- Once the app is installed on the member's mobile devices, they won't need to remember a URL. It can be easily shared with new members by simply sharing the name of the application.
- With the planned initial feature set, a mobile app won't require any backend services, so running costs will be zero.

Decision: The product will be a mobile application.

## 002 Flutter

Context: A decision must be made regarding the technology that the app will be written in. The main choices are hybrid (where Flutter is currently the strongest choice) or native. If going native, two separate sub-codebases are needed for each platform. 

Decision: Write a single Flutter codebase for both platforms.