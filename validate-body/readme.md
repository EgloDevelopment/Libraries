# How to use

Import the file as you normally would:

```
const { validateBody } = require("./validate-body");
```

And then you can call it like this:

```
const errors = await validateBody(req.body, [
    {
      username: {
        type: "string",
        empty: false,
        email: false,
        max_length: 0,
        alphanumeric: true,
        strong_password: false,
      },
    },
    {
      password: {
        type: "string",
        empty: false,
        email: false,
        max_length: 0,
        alphanumeric: false,
        strong_password: true,
      },
    },
  ]);

  if (errors) {
    res.status(400).json(errors);
    return;
  }
```

You can see that you have to pass the request body to the function first, then you can parse it and pass the fields you want to check

Please do note that it will break if you do not use common sense, obviously the type for something with email set to true can not be an integer, or a object, just dont be stupid



> Types are the default Javascript types (string, int, object, etc...)
> Empty is if the value can be empty
> Email is if the value needs to be a valid email
> Max length is how many characters long the value can be (0 is unlimited)
> Alphanumeric is if the value needs to be alphanumeric
> Strong Password is if the value needs to be a strong password (8+ characters, 1+ symbols, 1+ numbers)