# Setting up and running curriculum

Live version: https://gk3000.github.io/programming-with-python/#/

---

## [Video tutorial](https://youtu.be/FFc-H52HtY0)

Make sure you have Node.js and Git ([GitBash](https://gitforwindows.org) for Windows) installed.

In the terminal:

Navigate to the folder where you want to have your curriculum installed. Then:

## To install (just once):
1. Clone this repo:
`git clone git@github.com:gk3000/programming-with-python.git` 
or with https if you do not have SSH key:
`git clone https://github.com/gk3000/programming-with-python.git` 

2. `cd python_curriculum`
3. `sudo npm run setup` on Mac (you will be asked for your laptop's password) or `npm install -g docsify-cli` on Windows

## To start:
From the terminal navigate to your `python_curriculum` folder and from there run

`npm start`

Open [localhost:13666](http://localhost:13666) in your browser