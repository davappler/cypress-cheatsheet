## CYPRESS CHEATSHEET

This is a cheat-sheet for writing cypress test, you can find a list of commands here 🚀


```
cy.get('.action-btn').click() // for getting a button with class .action-btn

cy.get('.action-btn').as('myBtn')  // storing the found element in a variable, which can then be accessed later on
cy.get('myBtn').click()

```

## Intercepting requests

```
// For mocking a get or post request
cy.intercept('GET', '/something/more/anything', {anything: true,}).as('getRoute')
cy.intercept('POST', '/something/more/anything', {anything: true,}).as('postRoute')


// In order to mock a request that is called on page load, we first intercept the request
  cy.intercept('GET', '/something/more/anything', {anything: true,}).as('getRoute')

// Then mount the component
  cy.mount(
    <Wrapper>
      <MyComponentName/>
    </Wrapper>
  )

// Then wait for the request to be finished
  cy.wait('@getRoute')
```


## Expecting a request to be called on a button click

```
cy.intercept('POST', '/something/more/anything', {anything: true,}).as('postRoute')
cy.get('.action-btn').as('myBtn')
cy.get('myBtn').click()
cy.wait('@postRoute')

```