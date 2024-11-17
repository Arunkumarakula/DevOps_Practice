###  To push your new folder into a new GitHub repository:
1. Create a New Repository on GitHub
  * Go to your GitHub account.
  * Click the + icon in the top-right corner and select New repository.
  * Name the repository (e.g., New_Repo) and choose whether it should be public or private.
  * Click Create repository.

2. Open Terminal (or Command Prompt)
* Navigate to the folder you want to push.
```
cd /path/to/your/folder
```
3. Initialize Git
```
git init
```
4. Add Files to the Repository
```
git add .
```
5.commit changes
```
git commit -m "Initial commit"
```
6.  Link Your Local Repository to GitHub
```
git remote add origin https://github.com/Arunkumarakula/New_Repo.git
```
7.Push Your Folder to GitHub
```
git branch -M main
git push -u origin main
```