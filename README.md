# ABAC-vs-RBAC


## Role-based Access Control (RBAC)

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

a typical implementation of a user/admin is to store this role in the users table in the database.

we map the role to a set of permissions, in other words what the role is allowed to do.

here's a small illustration:

```
+---------+-----------------+
| role_id | role_name       |
+---------+-----------------+
|    1    | Admin           |
|    2    | Customer        |
+---------+-----------------+

+--------------+-------------------+
| permission_id| permission_name   |
+--------------+-------------------+
|      1       | View Orders       |
|      2       | Manage Orders     |
|      3       | Manage Users      |
|      4       | View Products     |
|      5       | Manage Products   |
+--------------+-------------------+

+---------+--------------+
| role_id | permission_id|
+---------+--------------+
|    1    |      1       |  -- Admin can View Orders
|    1    |      2       |  -- Admin can Manage Orders
|    1    |      3       |  -- Admin can Manage Users
|    1    |      4       |  -- Admin can View Products
|    1    |      5       |  -- Admin can Manage Products
|    2    |      1       |  -- Customer can View Orders
|    2    |      4       |  -- Customer can View Products
+---------+--------------+
```

when the user tries to do something we check what role the user has and whether the action is in the set of permissions for their role.

anyhow, RBAC is kind of limited when the project grows and when new complex roles are needed, and when hierarchy is introduced.

---

## Attribute-based Access Control (ABAC)

its a way of controlling access to data based on properties/attributes of the user and the resource he's trying to access.

an example can be:

- "all users can read *public* data", in this case, "is public" is an attribute of the data.

- "only users who are *staff* can read documents that are *confidential*, here we give both the user and the document an attribute, *staff* and *confidential*, respectively.

ABAC is also a way of controlling access based on who the user is *in relation to* the resource or data he wants to access. "users can edit their own files" is an example of the above.

we could use ABAC to implement access control for any of the following:

- collaboration applications - e.g, "a user can edit a file if he owns it or someone has given him editing privileges".

- a multi-tenant application - e.g, "a user can read this data if he belongs to this company".

- free vs paid tiers - e.g "a user can access these features is he is a paid subscriber".

- hierarchies - e.g

