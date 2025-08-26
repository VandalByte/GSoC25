
# ☀️ Google Summer of Code 2025 - Final Report

## PROJECT - Implement Unified File dialog, Password Change UI, and Implement File dialog for Exclusions

|         |  |
|----------------------|-----------|
| **Contributor**      | [Vandal Byte](https://github.com/VandalByte) |
| **Sub-Organization** | [Borg Collective](https://github.com/borgbase) |
| **Organization**     | [Python Software Foundation](https://python-gsoc.org/) |
| **Project Link**     | [Project](https://summerofcode.withgoogle.com/programs/2025/projects/GQrztSUR) |
| **Mentors**          | [Manuel Riel (m3nu)](https://github.com/m3nu), [Dan Helfman (witten)](https://github.com/witten) |



## 🎯 Project Goals
[Borg](https://github.com/borgbackup/borg)  is a powerful file backup tool that performs tasks like compression, encryption, authentication, and data deduplication. It is a command-line tool, and is used by many users and organizations to back up their data.

[Vorta](https://github.com/borgbase/vorta)  is a desktop GUI for Borg that makes it easier to interact with it without knowing any CLI commands or other intricacies. It is a cross-platform application that is built using Python and Qt, and is used by beginners and advanced users alike.

[Borgmatic](https://github.com/borgmatic-collective/borgmatic)  is a CLI wrapper around Borg that stores all Borg settings and preferences inside a configuration file and makes it easy to automate backups. It also extends Borg's capabilities by adding support for running pre and post-backup hooks, setting up monitoring, backing up databases, and more.

The primary goal of this GSoC project was to improve the code quality, user experience, and functionality of the Vorta and Borgmatic applications. The project focused on three main areas:

1.  **Add Password Change UI** - Add a new UI for changing the passphrase of a borg repository, this has been a long requested feature and once implemented will allow users to directly change the passphrase from vorta UI instead of relying on borg commanline.
2.  **Implement Unified File dialog** - Create a custom Qt-based file selector (`VortaFileDialog`) to unify file and directory selection. Previously, Vorta used two separate dialogs due to limitations in Qt. This new dialog will streamline the process and improves consistency across the UI.
3.  **Implement File dialog for Exclusions** - Improve the exclusion dialog in Vorta by allowing users to select files and directories via the new unified file dialog instead of manually typing exclusion patterns.
4.  **Code Refactor, Cleanup, and Maintenance Tasks** - Refactored portions of the codebase for better maintainability, fixed broken tests, and reviewed community PRs to improve overall stability and consistency of the application.


## 🏆 Project Achievements

### [Change Repository Passphrase Feature](https://github.com/borgbase/vorta/pull/2224)  
- Created and integrated an entire passphrase changing UI in Vorta.  
- Added a new dropdown button in the UI to house the less-used functionalities, as well as a button for changing the passphrase.
- Created a new UI based on suggestions from discussions and previous unmerged PRs.  
- The new UI was integrated into the main application UI.
- Used existing passphrase fields to reduce code duplication.
- Added tests to cover my implementation and ran existing tests to ensure that no other features were broken as a result of this.

![Passphrase change](https://private-user-images.githubusercontent.com/86826719/465335310-0b3236e0-e951-4250-8d12-21919e7d4d46.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTYyMTA2ODUsIm5iZiI6MTc1NjIxMDM4NSwicGF0aCI6Ii84NjgyNjcxOS80NjUzMzUzMTAtMGIzMjM2ZTAtZTk1MS00MjUwLThkMTItMjE5MTllN2Q0ZDQ2LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA4MjYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwODI2VDEyMTMwNVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWU1NDM1YzlkYmIxZTFkOTA0OWU5MDQ2MzQ4MGQ0OGIyMDFkMDM4YTI0YTI1ZGQ1YjE5ZGJmYzQ0ZDAxODY1MTEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.Q8t_DN8bbXTm74tk7rJGh5pgBa5-gZ4mhWMZnYG6Ksw)

### [Unified File Dialog](https://github.com/borgbase/vorta/pull/2237)
- Built a custom Qt-based file selector (`VortaFileDialog`) to support both files and directories with `QTree`.  
- Replaced existing separate dialogs to simplify and standardize file selection.  
- Added a new UI for file dialog which included features like path selection, goto home button, goto parent button, tree view of the directories and files and an option to view/select hidden files.
- Verified working of the new dialog and it's addition to the source list.
- Improved overall consistency and reduced code duplication in the selection flow.
- Added tests to cover my implementation and ran existing tests to ensure that no other features were broken as a result of this.

![Unified File Dialog](https://private-user-images.githubusercontent.com/86826719/447232822-0686731d-9ad7-4efc-baa3-95c952ef9faf.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTYyMTA2ODYsIm5iZiI6MTc1NjIxMDM4NiwicGF0aCI6Ii84NjgyNjcxOS80NDcyMzI4MjItMDY4NjczMWQtOWFkNy00ZWZjLWJhYTMtOTVjOTUyZWY5ZmFmLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA4MjYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwODI2VDEyMTMwNlomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTk3OGFlYmE5ODhjYWUzZjRjMWU2ZDhjM2Y0ZTlhMDk3ZDA2YzZhMmI2OGRhMDZjOTNmNDViNjNlZDZjZjllZGMmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.VDtB0WAwLn63FnAxNT6acnIUgcjtP_atVUO6rw-qpqk)

### [New File Dialog Integration in Exclusion Dialog](https://github.com/borgbase/vorta/pull/2252)
- Implemented file dialog support for excluding files and directories from backup using exclusion patterns.  
- Allowed users to visually select exclusions rather than typing the patterns manually.  
- Integrated with the unified file selector to maintain consistency.  
- Ensured excluded paths persist across each backup.  
- Added tests to cover my implementation and ran existing tests to ensure that no other features were broken as a result of this.

![File Dialog Integration in Exclusion Dialog](https://private-user-images.githubusercontent.com/86826719/465325626-b5d9e7b9-45bf-4a65-acb7-3d52a75e9214.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTYyMTA2ODcsIm5iZiI6MTc1NjIxMDM4NywicGF0aCI6Ii84NjgyNjcxOS80NjUzMjU2MjYtYjVkOWU3YjktNDViZi00YTY1LWFjYjctM2Q1MmE3NWU5MjE0LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA4MjYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwODI2VDEyMTMwN1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWYwNjVkNDA2YmY2ZDM1M2E4MDY5MzkzMjk4MmI4MmFlYzEyOTY2YWU4ZGY2NDA3ZmQyZDlmZDYxOWYyNzliODkmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.eUE8Ki290RZfZG97vRJgg6c7KuDIjo96xNzaO2OXav0)

## 📌 Current State
All proposed tasks except PR [#2252](https://github.com/borgbase/vorta/pull/2252) have been successfully completed and merged upstream. The codebase is now cleaner and easier to maintain, and the overall user experience has seen noticeable improvements.

## ⚙️ What's Left to Do
Just need to finalize and merge the new file dialog for exclusions. After that, there's a bit of cleanup to do, tidying up the code and closing out any loose ends, then it'll be time to get things ready for the next Vorta release.

## ⭐ Pull Requests
A list of all the pull requests I made before and during GSoC, in chronological order of their creation.

### [Vorta Contribution](https://github.com/borgbase/vorta)
- [Improved GUI to clarify the passphrase field](https://github.com/borgbase/vorta/pull/2208)
- [Made clarity changes to exclude dialog](https://github.com/borgbase/vorta/pull/2209)
- [Notification timeout removed for critical errors](https://github.com/borgbase/vorta/pull/2210)
- [Fix bug with incorrect renaming of archives after aborting edit](https://github.com/borgbase/vorta/pull/2213)
- [Add the change passphrase feature](https://github.com/borgbase/vorta/pull/2224)
- [Add missing placeholder keys](https://github.com/borgbase/vorta/pull/2227)
- [Add a new unified file selector](https://github.com/borgbase/vorta/pull/2237)
- [Add file dialog to exclude patterns](https://github.com/borgbase/vorta/pull/2252)
- [Fix broken transifex link](https://github.com/borgbase/vorta/pull/2250)
- [Fix the blank entry in the Custom exclusion](https://github.com/borgbase/vorta/pull/2268)

### [Borgmatic Contribution](https://projects.torsion.org/borgmatic-collective/borgmatic)
- [Add the borg recreate](https://github.com/borgbase/vorta/pull/1030)
- [Move Pattern and Flag Methods from create.py into their own module](https://github.com/borgbase/vorta/pull/1056)
- [Add Borg 1.4.1 features](https://github.com/borgbase/vorta/pull/1081)


## 🤝 Acknowledgements
I want to convey my heartfelt thanks to my mentors for their significant assistance throughout this journey.  Special thanks to @m3nu for taking me through the Vorta projects and @witten for his technical advice on the Borgmatic work.  Your input and feedback were critical to the success of these projects. My gratitude goes to the Python Software Foundation and the Borg Collective for this opportunity.  The warm and helpful character of the Borg community was greatly appreciated.  I'd also like to thank Google for organizing GSoC and giving a platform to collaborate on relevant projects.
