# pass

passlib is a simple module providing functionality to:

* Generate passwords
* Validate if a password is secure
* Hash passwords
* Salt passwords

## Exampless

Import the module:

```cs
from "pass.du" import Pass;
```

Create a new Instance:

```cs
const pass = Password();
```

Generate a 24 character passsword:

```cs
pass.generate(24);
```

Generate a 24 character secure password:

```cs
pass.generate(24, true);
```

Retrieve the password:

```cs
const password = pass.get();
```

Setup an instance with a given password:

```cs
pass.set("Asdfasdfasdfasdf1!");
```

Check if the password is secure:

*Note*: This module defines a "secure" password by having:

1. Minimum of 12 characters
2. At least 1 upper case character
3. At least 1 lower case character
4. At lease 1 special character

```cs
pass.isSecure().match(
    def(result) => {
        print("secure!");
    },
    def(error) => {
        print(error);
    }
);
```

Get a hash of the password:

*Note*: only SHA256 and bcrypt currently supported.

```cs
pass.hash(pass.sha256).unwrap();
pass.hash(pass.bcrypt).unwrap();
```

Salt a password. Returns a dictionary containing the salt string itself as well as the hash of the salt and password.

```cs
const res = pass.salt();
```
