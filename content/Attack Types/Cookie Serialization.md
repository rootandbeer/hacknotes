
#### PHP Serialization Format

In PHP, serialization transforms objects into a string format that is mostly human-readable. Each part of the string indicates the data type and the length of the entries. For instance, let’s say we have a User object with some attributes:

```php
$user->name = "carlos";
$user->isLoggedIn = true;
```

When this User object is serialized, it might look something like this:

```
O:4:"User":2:{s:4:"name";s:6:"carlos";s:10:"isLoggedIn";b:1;}
```

Breaking it down, here’s what each part means:

- **O:4:"User"**: This tells us it’s an object of the class named "User," which is 4 characters long.
- **2**: This indicates that the object has two attributes.
- **s:4:"name"**: The first attribute has a key named "name," which is 4 characters long.
- **s:6:"carlos"**: The value for the "name" attribute is "carlos," and it's 6 characters long.
- **s:10:"isLoggedIn"**: The second attribute is "isLoggedIn," a 10-character string.
- **b:1**: The value for "isLoggedIn" is true (represented as 1).

In PHP, the methods you’ll use for serialization are `serialize()` and `unserialize()`. If you have access to the source code, start by searching for `unserialize()`—that’s where the deserialization happens, and it’s worth investigating further.

#### Java Serialization Format

On the other hand, some languages like Java use a binary serialization format. While this format is less readable, there are still ways to recognize serialized data. For example, serialized Java objects always start with specific bytes: in hexadecimal, it’s `ac ed`, and in Base64, it looks like `rO0`.

Any class that implements the `java.io.Serializable` interface can be serialized. If you have access to the source code, pay attention to the `readObject()` method, as it reads and deserializes data from an InputStream.

#### Manipulating Serialized Objects

One of the interesting aspects of deserialization vulnerabilities is how easy it can be to exploit them—sometimes, all it takes is modifying an attribute in a serialized object. Since the object state is saved in a serialized format, you can inspect this data to find and change attribute values that seem important. After making your changes, you can submit the altered object back to the web application during its deserialization process. This is often the first step in launching a deserialization attack.

There are two main strategies for manipulating serialized objects. You can either modify the object directly in its byte stream form, or you can write a short script in the respective programming language to create and serialize a new object yourself. The second approach tends to be simpler, especially with binary serialization formats.

#### Modifying Object Attributes

When tampering with serialized data, as long as the attacker ensures the modified object remains valid, the deserialization process will create a server-side object with the new attribute values.

Let’s consider a simple example: imagine a website that uses a serialized User object to keep track of a user's session in a cookie. If an attacker spots this serialized object in an HTTP request, they might decode it and see something like this:

```
O:4:"User":2:{s:8:"username";s:6:"carlos";s:7:"isAdmin";b:0;}
```

The `isAdmin` attribute is an obvious target. The attacker could easily change its boolean value from `0` (false) to `1` (true), re-encode the object, and then replace their existing cookie with this altered version. While this change doesn’t seem impactful on its own, consider this piece of code the website uses to check for admin access:

```php
$user = unserialize($_COOKIE);
if ($user->isAdmin === true) {
    // allow access to admin interface
}
```

Here, the application unserializes the cookie and creates a User object, including the attacker-modified `isAdmin` attribute. Since the application never checks if the serialized object is legitimate, this can lead to unauthorized access to the admin interface.

While this exact scenario may not be commonly found in the wild, it illustrates how even a small change in attribute values can expose significant vulnerabilities due to insecure deserialization. By understanding how serialization works, attackers can find various ways to exploit these weaknesses.

## Referenced In
```dataview
list from [[]] and !outgoing([[]])
```