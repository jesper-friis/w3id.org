# EMMO
This [W3ID](https://w3id.org) provides a persistent URI namespace for the [Elementary Multiperspective Material Ontology (EMMO)](https://github.com/emmo-repo/EMMO/) and its domain ontologies.


## Redirection Rules
This section contains a general summary of the logic behind the redirection rules.

1. `https://w3id.org/emmo --> https://emmo-repo.github.io/EMMO/emmo{.html|.ttl}`
   - If the user is accessing this from a browser, redirect to html documentation on GitHub Pages.
   - Otherwise, redirect to the squashed `.ttl` file on GitHub Pages.
   - Special case for inferred ontology `https://w3id.org/emmo/emmo-inferred --> https://emmo-repo.github.io/EMMO/emmo-inferred.ttl`

2. `https://w3id.org/emmo/ --> https://raw.githubusercontent.com/emmo-repo/EMMO/master/emmo.ttl`
   - `emmo.ttl` file in the root of the master branch.

3. `https://w3id.org/emmo/{VERSION} --> https://emmo-repo.github.io/EMMO/versions/{VERSION}/emmo{.html|.ttl}`
   - If the user is accessing this from a browser, redirect to html documentation for given version on GitHub Pages.
   - Otherwise, redirect to squashed `.ttl` file for given version on GitHub Pages.
   - Special case for inferred ontology `https://w3id.org/emmo/{VERSION}/emmo-inferred --> https://emmo-repo.github.io/EMMO/versions/{VERSION}/emmo-inferred.ttl`

4. `https://w3id.org/emmo/{VERSION}/ --> https://raw.githubusercontent.com/emmo-repo/EMMO/{VERSION}/emmo.ttl`
   - `emmo.ttl` file in the root of branch/tag for the given version.

5. `https://w3id.org/emmo/{PATH}/{MODULE} --> https://raw.githubusercontent.com/emmo-repo/EMMO/{PATH}/{MODULE}.ttl`
   - Turtle file for given EMMO module.

6. `https://w3id.org/emmo/{VERSION}/{PATH}/{MODULE} --> https://raw.githubusercontent.com/emmo-repo/EMMO/{VERSION}/{PATH}/{MODULE}.ttl`
   - Turtle file for given version and module of EMMO.

7. `https://w3id.org/emmo/{DOMAIN} --> https://emmo-repo.github.io/{REPO_NAME}/{DOMAIN}{.html|.ttl}`
   - If the user is accessing this from a browser, redirect to html documentation on GitHub Pages.
   - Otherwise, redirect to squashed .ttl file on GitHub Pages.
   - Special case for inferred ontology `https://w3id.org/{DOMAIN}/{DOMAIN}-inferred --> https://emmo-repo.github.io/{REPO_NAME}/{DOMAIN}-inferred.ttl`

8. `https://w3id.org/emmo/{DOMAIN}/ --> https://raw.githubusercontent.com/emmo-repo/{REPO_NAME}/master/{DOMAIN}.ttl`
   - `{DOMAIN}.ttl` file in the root of the master branch.

9. `https://w3id.org/emmo/{DOMAIN}/{VERSION} --> https://raw.githubusercontent.com/emmo-repo/{REPO_NAME}/{VERSION}/{DOMAIN}{.html|.ttl}`
   - If the user is accessing this from a browser, redirect to html documentation for given version on GitHub Pages.
   - Otherwise, redirect to squashed .ttl file for given version on GitHub Pages.
   - Special case for inferred ontology `https://w3id.org/{DOMAIN}/{VERSION}/{DOMAIN}-inferred --> https://emmo-repo.github.io/{REPO_NAME}/versions/{VERSION}/{DOMAIN}-inferred.ttl`

10. `https://w3id.org/emmo/{DOMAIN}/{VERSION}/ --> https://raw.githubusercontent.com/emmo-repo/{REPO_NAME}/{VERSION}/{DOMAIN}.ttl`
   - `{DOMAIN}.ttl` file in the root of GitHub branch for the given version.

11. `https://w3id.org/emmo/{DOMAIN}/{PATH}/{MODULE} --> https://raw.githubusercontent.com/emmo-repo/{REPO_NAME}/master/{PATH}/{MODULE}.ttl`
    - `{PATH}/{MODULE}.ttl` file in master branch.

12. `https://w3id.org/emmo/{DOMAIN}/{VERSION}/{PATH}/{MODULE} --> https://raw.githubusercontent.com/emmo-repo/{REPO_NAME}/{VERSION}/{PATH}/{MODULE}.ttl`
    - `{PATH}/{MODULE}.ttl` file for given version and module.


### Meaning of placeholders
- `{NAME}`: Name part of an IRI, i.e. what follows after the hash sign.
- `{VERSION}`; Version number. Must start with a digit to distinguish it from domain or path names.
- `{PATH}`: Directory path within a github repository
- `{MODULE}`: Filename of turtle file with the final .ttl stripped off
- `{DOMAIN}`: Name of domain ontology. Initial `domain-` is stripped off.
- `{REPO_NAME}`: Name of GitHub repository for domain ontology.


## Expected organisation of repositories for domain ontologies

### GitHub repository
In the root of the repository we should have a file called {DOMAIN}.ttl. This should be the main file for the ontology. It should exist to make the ontology FAIR.

### GitHub Pages
Using GitHub pages is optional.
There are several use cases for using cases for using GitHub Pages:
- The main turtle file is generated from another semantic source.
  In this case it make sense to distribute the ontology on GitHub pages to avoid polluting your GitHub repository.
- Your ontology consists of many modules importing each other.
  Loading them recursively from GitHub may be very slow.
  To speed up the loading process, you could merge (squash) all modules into a single turtle file, which you could store on GitHub Pages.
- You want to publish the inferred ontology, so that the user have full to the full inferred ontology without having to first running a reasoner.
- Reference html documenting of classes and relations in the ontology.
  The main aim of this document is to making the IRIs resolvable in a browser as human readable documentation of the concepts.

Expected structure of GitHub pares:

```
.
├── index.html                    # Optional landing page
├── {DOMAIN}.ttl                  # Latest version of squashed ontology
├── {DOMAIN}-inferred.ttl         # Latest version of inferred ontology
├── {DOMAIN}.html                 # Latest version of html reference documentation
└── versions/{VERSION}/
    ├── {DOMAIN}.ttl              # Squashed ontology for given version
    ├── {DOMAIN}-inferred.ttl     # Inferred ontology for given version
    └── {DOMAIN}.html             # html reference documentation for given version
```



## Contacts
This space is maintained by the [European Materials Modelling Council (EMMC)](http://emmc.eu).
You can contact the EMMO Authors via emmo@emmc.eu.

Current maintainers:
[Jesper Friis](https://github.com/jesper-friis),
[Simon Clark](https://github.com/jsimonclark) and
[Emanuele Ghedini](https://github.com/emanueleghedini).