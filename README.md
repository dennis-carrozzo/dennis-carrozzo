```javascript
/**
 * The function takes an array of strings and returns a concatenated string with commas and "and"
 * before the last element.
 * @returns The `getStringFromArray` function is returning a string that concatenates all the elements
 * of the input array `arr` separated by commas, except for the last element which is preceded by the
 * word "and".
 */
const getStringFromArray = arr => {
  return arr.reduce((prev, cur, idx, arr) => {
    if (idx === arr.length - 1) {
      return (prev += ` and ${cur}`)
    }
    if (idx === 0) {
      return cur
    }
    return (prev += `, ${cur}`)
  }, '')
}

/* The below class defines a Human object with properties such as name, current location, country of
origin, spoken languages, and interests, and a method to introduce themselves. */
class Human {
  constructor (
    name,
    currentLocation,
    countryOfOrigin,
    spokenLanguages,
    interests
  ) {
    this.name = name
    this.currentLocation = currentLocation
    this.countryOfOrigin = countryOfOrigin
    this.spokenLanguages = spokenLanguages
    this.interests = interests
  }

  /* `introduceSelf` is a method of the `Human` class that returns a string introducing the human object.
It uses template literals to concatenate the values of the `name`, `countryOfOrigin`,
`currentLocation`, `spokenLanguages`, and `interests` properties of the object, along with some
fixed text, into a formatted string. The `getStringFromArray` function is used to format the
`spokenLanguages` and `interests` arrays into comma-separated strings with "and" before the last
element. The resulting string is then returned. */
  introduceSelf = () => {
    const spokenLanguagesString = getStringFromArray(this.spokenLanguages)
    const interestsString = getStringFromArray(this.interests)  
    return `
Hi there,

My name is ${this.name}, I'm from ${this.countryOfOrigin} and 
I'm currently based in ${this.currentLocation}. I speak
${spokenLanguagesString}. My interests are
${interestsString}.`
  }
}

/* class FullStackWebDeveloper is creating a new class `FullStackWebDeveloper` that
extends the `Human` class. This means that the `FullStackWebDeveloper` class inherits all the
properties and methods of the `Human` class, and can also have its own properties and methods. In
this case, the `FullStackWebDeveloper` class has an additional property `usedTechnologies` and two
methods `getUsedTechnologies` and `doFullIntroduction`. */
class FullStackWebDeveloper extends Human {
  constructor (usedTechnologies, humanProps) {
    super(...humanProps)
    this.usedTechnologies = usedTechnologies
  }

  /* `getUsedTechnologies` is a method of the `FullStackWebDeveloper` class that returns a string
  listing the technologies used by the developer. It does this by iterating over the
  `usedTechnologies` object and concatenating the keys and values into a formatted string using the
  `getStringFromArray` function. The resulting string is then returned. */
  getUsedTechnologies = () => {
    let intro = `
This are the technologies i use:\n`
    for (const [key, value] of Object.entries(this.usedTechnologies)) {
      intro += `
 - ${key} ~> ${getStringFromArray(value)}.\n`
    }
    return intro
  }

  /* `doFullIntroduction` is a method of the `FullStackWebDeveloper` class that returns a string that
  includes the introduction of the developer and the list of technologies they use. It does this by
  calling the `introduceSelf` method of the `Human` class to get the introduction string, and then
  calling the `getUsedTechnologies` method of the `FullStackWebDeveloper` class to get the string
  listing the technologies used. The resulting strings are concatenated using template literals and
  returned as a single string. */
  doFullIntroduction = () => {
    return `
      ${this.introduceSelf()}
      ${this.getUsedTechnologies()}
    `
  }
}

const dennisUsedTechnologies = {
  frontend: [
    'HTML',
    'CSS',
    'Javascript',
    'React',
    'TailwindCSS',
    '@MUI/material',
    'Pug',
    'EJS'
  ],
  backend: ['Nodejs', 'ExpressJS', 'NestJS', 'NextJS'],
  database: ['MongoDB', 'MySQL'],
  devTools: [
    'Typescript',
    'VSCode',
    'Git',
    'Github',
    'Eslint',
    'Prettier',
    'stylelint',
    'Postman',
    'Figma'
  ]
}

const dennisHumanProps = [
  'Dennis',
  'London, UK',
  'Italy',
  ['english', 'italian'],
  ['coding', 'cooking', 'cycling', 'swimming']
]

const dennis = new FullStackWebDeveloper(
  dennisUsedTechnologies,
  dennisHumanProps
)

const dennisIntro = dennis.doFullIntroduction()

console.log(dennisIntro)

// Hi there 👋,

// My name is Dennis, I'm from Italy and
// I'm currently based in London, UK. I speak
// english and italian. My interests are
// coding, cooking, cycling and swimming.

// This are the technologies i use:

//  - frontend ~> HTML, CSS, Javascript, React, TailwindCSS, @MUI/material, Pug and EJS.

//  - backend ~> Nodejs, ExpressJS, NestJS and NextJS.

//  - database ~> MongoDB and MySQL.

//  - devTools ~> Typescript, VSCode, Git, Github, Eslint, Prettier, stylelint, Postman and Figma.

```

<!--
**denniswebdel/denniswebdel** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
