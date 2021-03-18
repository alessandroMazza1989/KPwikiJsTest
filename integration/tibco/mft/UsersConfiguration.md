---
title: Users Configuration
description: 
published: true
date: 2021-03-18T10:50:50.366Z
tags: 
editor: markdown
dateCreated: 2021-03-18T10:34:09.845Z
---

# Users and Segregation

MFT offers the possibility to expand the user network and implement segregation strategies. The admin user is actually the "super admin", the only user who has full powers and who can first create other users. He cannot be part of any department and is the only one who can create departments, servers and modify system and infrastructure configurations. In summary, he is the only user who can do everything that is possible in MFT.

## Departments

Departments are used to decentralize the Administrative task. By assigning users, groups, transfers and servers to departments, you can limit the Department Administrators to List, Add and Update a subset of the definitions.

Why is it convenient to have a departmental structure?

- For reasons of order: creating departments is like dividing MFT in parts; this allows each team, together with the creation of multiple users, to be able to work on their own projects without risking impacting the work of others.

- For more control: no user in a department can have the same powers as the super admin. In this way, the super admin will be the only responsible for the most important actions. Each user will be able to do and see only what has been assigned to him. By creating groups, a user will only be able to perform operations for the servers and transfers assigned to the group.

The departments must be created by the super admin in the *Users>Departments*  section; he can then assign existing users to departments.
A department can be assigned transfers, users, servers and jobs; in this case only the users of the department will be able to use them.

## Groups

Groups are used to enable multiple users to be able to perform file transfer functions on a single transfer definition. After entering the Required Group Properties, you can then assign one or more users to the group. When you create a transfer definition, you can authorize a user and/or a group for that transfer. If you authorize a group, then every member of the group will have access to the transfer definition.

# Users

Users can be assigned or not to groups or departments, it is convenient to create technical users and customer's users.
Technical users can be used to perform all the transfers configured by the corporate team: for example is useful creating a secific user for every projet, this will help in the maintenance and the search of audits.
Customer's users can be created to give external customer the possibility to perform the specific transfers created and assigned to them.

