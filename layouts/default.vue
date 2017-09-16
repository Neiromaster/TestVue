<template>
  <div>
    <nuxt/>
  </div>
</template>

<style>
  html {
    font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    font-size: 16px;
    word-spacing: 1px;
    -ms-text-size-adjust: 100%;
    -webkit-text-size-adjust: 100%;
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    box-sizing: border-box;
  }

  *, *:before, *:after {
    box-sizing: border-box;
    margin: 0;
  }

  .form input[type="text"],
  .form input[type="password"],
  .form input[type="email"],
  .form input[type="url"],
  .form input[type="date"],
  .form input[type="month"],
  .form input[type="time"],
  .form input[type="datetime"],
  .form input[type="datetime-local"],
  .form input[type="week"],
  .form input[type="number"],
  .form input[type="search"],
  .form input[type="tel"],
  .form input[type="color"],
  .form select,
  .form textarea {
    box-sizing: border-box;
    display: inline-block;
    padding: .4em .5em;
    font-size: 14px;
    vertical-align: middle;
    border: 1px solid #706f6f;
    border-radius: 6px;
  }

  .button--green {
    display: inline-block;
    border-radius: 4px;
    border: 1px solid #3b8070;
    color: #3b8070;
    text-decoration: none;
    padding: 10px 30px;
  }

  .button--green:hover {
    color: #fff;
    background-color: #3b8070;
  }

  .button--grey {
    display: inline-block;
    border-radius: 4px;
    border: 1px solid #35495e;
    color: #35495e;
    text-decoration: none;
    padding: 10px 30px;
    margin-left: 15px;
  }

  .button--grey:hover {
    color: #fff;
    background-color: #35495e;
  }
</style>
