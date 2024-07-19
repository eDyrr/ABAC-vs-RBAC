# ABAC-vs-RBAC


## What is Role-based Access Control (RBAC) ?

it is a method thats defined by the app developer for the user to access in-app resources.

roles can provide a structure for assigning sets of permissions for users.

in a typical application, there's always a regular user and a Super user or an Admin.

in this type of application each role holder (admin and/or user) has certain resources/actions that can or cant access/do.

any permission we have can be grouped into a set, this set can be named to become a **role**.

now's the time I expand on the example of an admin:

imagine this e-com platform, where there's customers and obviously like any IRL store, there's the shop-keeper/owner.

the owner obviously has some permissions that a customer wont have, to list some of these permissions:

- the option to add goods.
- the option to set a product's price.
- the option to remove a product.

and many other actions.

obviously the customer has some sort of actions like:

- order a product.
- maybe contact the shop-owner.
