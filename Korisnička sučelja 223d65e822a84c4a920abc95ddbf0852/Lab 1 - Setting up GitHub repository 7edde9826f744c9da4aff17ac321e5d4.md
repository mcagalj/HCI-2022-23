# Lab 1 - Setting up Next and Git hooks

To follow the crash course on Next.js students should create a public GitHub repo. 

1. To simplify interaction with Git repositories we suggest the following applications:
    - [GitHub Desktop](https://desktop.github.com/)
    - [Sourcetree](https://www.sourcetreeapp.com/)
    
2. [Create a Next.js App](https://nextjs.org/learn/basics/create-nextjs-app)
    
    Development environment requirements:
    
    - [Node.js LTS](https://nodejs.org/) (at the time of this writing the latest version was v14.18.0)
    - Some IDE such as [Visual Studio Code](https://code.visualstudio.com/)
    
    To create a Next.js application, run the following command (name your project **next-course-app**):
    
    ```powershell
    npx create-next-app --use-npm
    √ What is your project named? ... next-course-app
    **...**
    ```
    
    To start the Next.js development server run the following command:
    
    ```powershell
    npm run dev
    ```
    
3. [Git **hooks**](https://www.atlassian.com/git/tutorials/git-hooks)
    
    ```bash
    .git
    ├── HEAD
    ├── config
    ├── description
    ├── hooks
    │   ├── applypatch-msg.sample
    │   ├── commit-msg.sample
    │   ├── fsmonitor-watchman.sample
    │   ├── post-update.sample
    │   ├── pre-applypatch.sample
    │   ├── pre-commit.sample
    │   ├── pre-merge-commit.sample
    │   ├── pre-push.sample
    │   ├── pre-rebase.sample
    │   ├── pre-receive.sample
    │   ├── prepare-commit-msg.sample
    │   └── update.sample
    ```
    
    ### Publishing messy code
    
    To better appreciate Git hooks, we will make a small demo. Please take the following steps:
    
    - Create and checkout a new branch `git-hooks`
    - Disable automatic code formatting in VSC ([`Format on Save` option](https://www.digitalocean.com/community/tutorials/how-to-format-code-with-prettier-in-visual-studio-code))
    - Try to make a portion of your code messy.
    - Commit and push your new branch to the remote repository.
    - Enjoy your result 🙂
        
        ![messy_code.png](Lab%201%20-%20Setting%20up%20GitHub%20repository%207edde9826f744c9da4aff17ac321e5d4/messy_code.png)
        
    
    ### Using Git hooks to prevent messy code
    
    To avoid such problems we will use [husky](https://github.com/typicode/husky) and [Prettier](https://prettier.io/docs/en/precommit.html).  Take the following steps:
    
    - Add and install husky
    - Install prettier and pretty-quick
    - Add a pre-commit script by running the following command:
        
        ```powershell
        npx husky set .husky/pre-commit "npx pretty-quick --staged"
        ```
        
    - To exclude processing - *prettifying* - irrelevant files you can ignore them by adding them to `.prettierignore` file.
    - To configure prettier formatting, please check [Prettier playground](https://prettier.io/playground/).
