# Ember Team Notes
Please feel free to add more categories.
The repo is private so feel free to add credentials or passwords here.

#### [General Notes](#general) | [Known Issues](#issues) | [Handlebars](#hbs) | [Resources & Credentials](#resources)

### <a id="general">General notes</a>
##### git:
* 20 files per PR or less.
* use gitflow workflow: Master > Develop > Epic > Feature. [more on gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
* Deployment: through slack bot, to s3 bucket, returns a branch key.
* Versioning: "semvers" (Semantic versioning i.e. 1.1.1).
* Open Source packages are published under British Gas engineering org.

##### Package management and building:
* Switch to Yarn for managing packages.
  * installing Yarn via npm:
  
    `npm i -g yarn`
  * installing Yarn natively (On Mac OS and Linux):
  
    `curl -o- -L https://yarnpkg.com/install.sh | bash`
* #Broccoli is used for building.

##### Routing
* Loading route and Error routes are utilised during loading data.
* Controllers are not used anymore > replaced with services.
* Promises: are handled through rsvp package.

##### Models
* Ember data/Ember store: SSOT.
* Customer model: Customer has_multiple Premises… Premises has_mutltiple Energy Accounts.. referencing each other in the relations property/object.
* Follows the reactive programming model.

##### Engines
* Seperate ember apps that loads seamlessly.

###### Styling
* BG-VI package is used (request access to GitHub/ centric email ASAP).
* Easiest method for adding Sass support:

  `ember install ember-cli-sass`

##### Testing
* Qunit is the testing framework and Mirage is used for mocking.
* All acceptance tests runs on mocks.

### <a id="hbs">Handlebars and Helpers</a>
*   
##### Helpers:
You don't need to close self-closing helpers like link-to:
```js
// Valid
{{#link-to "index"}}
  Link to Index
{{/link-to}}
// Also valid
{{link-to 'Link to Index' 'index'}}
```

### <a id="issues">Known Issues</a>
* Ember specific packages:

  When installing an ember specific package <ex: `ember-cli-bourbon`> that would change of overwrite some of the projects files, inspect the diff by choosing `d`(figure 1) and then choose to make the changes yourself or let cli overwrite the files (figure 2).
  ![figure 1](http://i64.tinypic.com/250tr9j.jpg)  

  ![figure 2](http://i64.tinypic.com/347ice9.jpg)
  
* Deprecated syntax:
  When defining child routes do not use `this.resource`. ex:
  
  Deprecated:
  ```js
  this.resource('posts', {path: 'posts'}, () => {
    this.route('new');
  });
  ```
  Valid:
  ```js
  this.route('posts', { resetNamespace: true }, function() {
    this.route('new', {path: 'new'});
  });
  ```

### <a id="resources">Resources & Credentials</a>
* [Frontend Masters](https://frontendmasters.com/):
  * Creds: `Username: deepan, Password: c3ntric@`