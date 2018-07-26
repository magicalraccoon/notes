# Active Directory Fundamentals
## How Objects Are Stored and Identified
Active Directory systems are presented in a hierarchy, similar to a filesystem.

Each entry is an Object. There are two types of objects:
  - Containers - may contain other containers or leaf nodes.
  - Non-containers - also known as leaf nodes. Cannot contain any other objects.

You can think of it like a parent-child relationship between containers and leaves.

### Uniquely Identifying Objects
Each object has a Globally Unique IDentifier (GUID) assigned at creation. A GUID is 128-bits an is assumed to be unique (statistically).

GUIDs stay with objects until deletion, regardless of naming or location changes. A GUID will also remain through domain transfer.

But no one wants to remember unique 128-bit names. So instead, Distinguished Names (DN) are used.

### Distinguished Names
This is a means of referring to any object in the directory.

The distinguished name for "mydomain.mycorp.com" would look like `dc=mydomain,dc=mycorp,dc=com`.


A Relative Distinguished Name (RDN) is a unique reference to an object within the parent container. For example, this is the DN for the default administrator account in the users container in the mycorp.com domain: `cn=Administrator,cn=Users,dc=mycorp,dc=com` with the RDN being `cd=Administrator`.

RDNs must be unique within the container they exist (similar to filesystems again).


- `CN` - Common name
- `L` - Locality name
- `ST` - State or province name
- `O` - Organization name
- `OU` - Organizational unit name
- `C` - Country name
- `STREET` - Street address
- `DC` - Domain component
- `UID` - User ID

## Building Blocks
### Domains and Domain Trees
A Domain Controller (DC) can be authoratative for only one domain. Multiple domains cannot be hosted on the same DC.

A domain is automatically created at the root of a domain tree. Domain trees trust each other with transitive trusts (A trusts B, B trusts C, so A trusts C).

### Forests
A "forest" is a collection of (one or more) domain trees. Fitting analogy, right? All the trees in a forest share a Schema and Configuration container, and are connected through the same sort of transitive trust.

The first domain created is the "forest root domain" and has special properties. It cannot be removed without also removing the forest. You can rename the root domain though.

Best practices: Keep your forest design simple. One domain tree and as few domains as possible.
