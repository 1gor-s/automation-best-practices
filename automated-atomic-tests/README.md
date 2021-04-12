# Automated Atomic Tests


An automated atomic test (AAT) is one that tests only a single feature or component. An AAT should form a single irreducible unit. An automated test should not do something like end-to-end automation. As an aside, this concept is already well understood in unit and integration tests, but UI tests continue to lag behind.

We can usually tell that a test is atomic when:
1. The test will have a handful of assertions at most. 
2. Atomic tests have very few UI interactions and typically touch a maximum of two screens.  

## ❓Is this test atomic❓

```js

/// <reference types="cypress" />
import ProductsPage from '../page-objects/ProductsPage';
import AppHeader from '../page-objects/AppHeaderPage';
import LoginPage from '../page-objects/LoginPage'
import {LOGIN_USERS} from "../support/e2eConstants";

describe('Shopping cart', () => {
  beforeEach(() => {
      cy.visit('https://www.saucedemo.com/v1');
      cy.window().then((win) => {
          win.sessionStorage.clear()
        });
    });

  it('should add item to cart', () => {
      LoginPage.signIn(LOGIN_USERS.STANDARD);
      ProductsPage.screen.should('be.visible');
      ProductsPage.addItemToCart(0);
      AppHeader.cart.should('have.text', '1');
  });
});

```

❓So how many tests is this really❓

### 🏋️‍♀️ Get started with Cypress

1. `npm install`
2. `npx cypress open`
3. Open `exercise.spec.js`. Please don't peek at the `solution.spec.js`🙏. The workshop is more fun when we struggle together 😁

### 🏋️‍♀️ Automated atomic tests exercise

We're going to break down this test into atomic ones.

🏋️‍♀️ Code a suite of atomic tests

> Keep in mind that this is a really small test and larger tests will be even
> more of a hinderance to your testing

1. 
2. Go to the `cypress/integration/exercise.spec.js`
3. Create AATs for all of the features
4. There's a hint for how to handle the login in `spec.js`

