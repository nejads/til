# Gitattributes

Add always gitattribute to the projects. It helps contributer can work easily with different type of machines.
Link for more description: [https://dev.to/deadlybyte/please-add-gitattributes-to-your-git-repository-1jld](https://dev.to/deadlybyte/please-add-gitattributes-to-your-git-repository-1jld)

### Sample for an gitattribute file
```
* text=auto

## Java

# These files are text and should be normalized (Convert crlf => lf)

*.bash          text eol=lf
*.css           text diff=css
*.df            text
*.htm           text diff=html
*.html          text diff=html
*.java          text diff=java
*.js            text
*.json          text
*.jsp           text
*.jspf          text
*.jspx          text
*.properties    text
*.sh            text eol=lf
*.tld           text
*.txt           text
*.tag           text
*.tagx          text
*.xml           text
*.yml           text

# These files are binary and should be left untouched
# (binary is a macro for -text -diff)

*.class         binary
*.dll           binary
*.ear           binary
*.gif           binary
*.ico           binary
*.jar           binary
*.jpg           binary
*.jpeg          binary
*.png           binary
*.so            binary
*.war           binary

# Documents

*.md            text

# Exclude files from exporting

.gitattributes  export-ignore
.gitignore      export-ignore

```
