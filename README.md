# aurelia-validatejs

[![npm Version](https://img.shields.io/npm/v/aurelia-validatejs.svg)](https://www.npmjs.com/package/aurelia-validatejs)
[![ZenHub](https://raw.githubusercontent.com/ZenHubIO/support/master/zenhub-badge.png)](https://zenhub.io)
[![Join the chat at https://gitter.im/aurelia/discuss](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/aurelia/discuss?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

This is a plugin that will allow using validate.js in your Aurelia application for expressive validation. Karma/Jasmine testing is also configured.

> To keep up to date on [Aurelia](http://www.aurelia.io/), please visit and subscribe to [the official blog](http://blog.durandal.io/) and [our email list](http://durandal.us10.list-manage1.com/subscribe?u=dae7661a3872ee02b519f6f29&id=3de6801ccc). We also invite you to [follow us on twitter](https://twitter.com/aureliaeffect). If you have questions, please [join our community on Gitter](https://gitter.im/aurelia/discuss). If you would like to have deeper insight into our development process, please install the [ZenHub](https://zenhub.io) Chrome or Firefox Extension and visit any of our repository's boards. You can get an overview of all Aurelia work by visiting [the framework board](https://github.com/aurelia/framework#boards).

## Validation Rules

Validation is performed using [validate.js](https://validatejs.org/).  You can visit their official site to get more information about how to use all of the validation rules.  Here are the base rules -

### Date

Ensure it is a date

```es6
export class Model {
  @date myDate = new Date();
}

export class Model {
  static inject = [Validator];
  constructor(validator) {
    this.validator = validator
      .ensure(this, 'myDate')
        .date();
  }
}
```

### Datetime

Ensure it is a datetime

```es6
export class Model {
  @datetime myDate = new Date();
}

export class Model {
  static inject = [Validator];
  constructor(validator) {
    this.validator = validator
      .ensure(this, 'myDate')
        .datetime();
  }
}
```

### Email

Ensure it is a valid e-mail format

```es6
export class Model {
  @email email = 'patrick@example.com';
}

export class Model {
  static inject = [Validator];
  constructor(validator) {
    this.validator = validator
      .ensure(this, 'email')
        .email();
  }
}
```

### Equality

Ensure it matches another property on the same object

```es6
export class Model {
  @equality('password') confirmPassword = 'password1';
}

export class Model {
  static inject = [Validator];
  constructor(validator) {
    this.validator = validator
      .ensure(this, 'confirmPassword')
        .equality('password');
  }
}
```

### Exclusion

Disallow a set of values

```es6
export class Model {
  @exclusion(['blue']) color = 'red';
}

export class Model {
  static inject = [Validator];
  constructor(validator) {
    this.validator = validator
      .ensure(this, 'color')
        .exclusion(['blue']);
  }
}
```

### Format

Ensure it matches a regex

```es6
export class Model {
  @format(/\d{5}(-\d{4})?/) zipCode = '90210';
}

export class Model {
  static inject = [Validator];
  constructor(validator) {
    this.validator = validator
      .ensure(this, 'zipCode')
        .format(/\d{5}(-\d{4})?/);
  }
}
```

### Inclusion

Ensure it is included a set of values

```es6
export class Model {
  @inclusion(['blue', 'red']) blueOrRed = 'yellow';
}

export class Model {
  static inject = [Validator];
  constructor(validator) {
    this.validator = validator
      .ensure(this, 'blueOrRed')
        .format(['blue', 'red']);
  }
}
```

### Length

Ensure it is a certain length

```es6
export class Model {
  @length({ minimum: 5, maximum: 25 }) password = 'equal';
}

export class Model {
  static inject = [Validator];
  constructor(validator) {
    this.validator = validator
      .ensure(this, 'password')
        .length({ minimum: 5, maximum: 25 });
  }
}
```

### Numericality

Ensure it is a number (additional validation available, check validate.js documentation for more options)

```es6
export class Model {
  @numericality({ onlyInteger: true, lessThan: 115, greaterThan: 0 }) age = 25;
}

export class Model {
  static inject = [Validator];
  constructor(validator) {
    this.validator = validator
      .ensure(this, 'age')
        .length({ onlyInteger: true, lessThan: 115, greaterThan: 0 });
  }
}
```

### Presence / Required

Ensure it is a number (additional validation available, check validate.js documentation for more options)

```es6
export class Model {
  @presence lastName = 'Skywalker';
  @required lastName = 'Skywalker';
}

export class Model {
  static inject = [Validator];
  constructor(validator) {
    this.validator = validator
      .ensure(this, 'firstName')
        .required();
  }
}
```

### URL

Ensure it is a valid URL

```es6
export class Model {
  @url website = 'http://www.google.com';
}

export class Model {
  static inject = [Validator];
  constructor(validator) {
    this.validator = validator
      .ensure(this, 'website')
        .url();
  }
}
```

## Building The Code

To build the code, follow these steps.

1. Ensure that [NodeJS](http://nodejs.org/) is installed. This provides the platform on which the build tooling runs.
2. From the project folder, execute the following command:

  ```shell
  npm install
  ```
3. Ensure that [Gulp](http://gulpjs.com/) is installed. If you need to install it, use the following command:

  ```shell
  npm install -g gulp
  ```
4. To build the code, you can now run:

  ```shell
  gulp build
  ```
5. You will find the compiled code in the `dist` folder, available in three module formats: AMD, CommonJS and ES6.

6. See `gulpfile.js` for other tasks related to generating the docs and linting.

## Running The Tests

To run the unit tests, first ensure that you have followed the steps above in order to install all dependencies and successfully build the library. Once you have done that, proceed with these additional steps:

1. Ensure that the [Karma](http://karma-runner.github.io/) CLI is installed. If you need to install it, use the following command:

  ```shell
  npm install -g karma-cli
  ```
2. Ensure that [jspm](http://jspm.io/) is installed. If you need to install it, use the following commnand:

  ```shell
  npm install -g jspm
  ```
3. Install the client-side dependencies with jspm:

  ```shell
  jspm install
  ```

4. You can now run the tests with this command:

  ```shell
  karma start
  ```

## Running the Sample App

There is a sample application provided that runs using the plugin itself.  To run this application -

1. Change to the sample directory

  ```shell
  cd sample
  ```
2. Install all of the sample application's dev dependencies:

  ```shell
  npm install
  ```
3. Install all of the sample application's client-side dependencies with jspm:

  ```shell
  jspm install
  ```

4. You can now run sample application:

  ```shell
  gulp start
  ```
