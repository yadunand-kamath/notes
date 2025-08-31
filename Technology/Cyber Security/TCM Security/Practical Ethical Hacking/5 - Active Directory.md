
#activedirectory

## Contents :-

#### [[#5.01 - What is AD?]]


---

## 5.01 - What is AD?

- **Active Directory** is like a phone book for windows. They are directory services developed by Microsoft to manage Windows domain networks.
- It authenticates using Kerberos tickets.
- It is the most commonly used identity management service in the world.

---

## 5.02 - AD Components


### Physical

- **Domain Controller** - it is a server with the AD DS server role installed that has specifically been promoted to a domain controller. It hosts the AD DS store, and provides authentication and authorization services.
- **AD DS Data Store** - contains database files and processes that store and manage directory information. It contains the `Ntds.dit` file.

### Logical

- **AD DS Schema** - defines every type of object that can be stored within the directory, and enforces rules regarding object creation and configuration.
- **Domains** - used to group and manage operations in an organization.
- **Trees** - it is a hierarchy of domains.
- **Forests** - a collection of domain trees.
- **OU** (***Organizational Units***) - containers that contain and manage objects.
- **Trusts** - provides a mechanism for users to gain access to resources in other domains. It can be *Directional* or *Transitive*. All domains in a forest trust all other domains in the forest.
- **Objects** - users, contacts, computers, groups, printers, shared folders, etc.