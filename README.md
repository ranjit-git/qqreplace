# qqreplace

Accept URLs on stdin, replace all query string values with a user-supplied value, only output
each combination of query string parameters once per host and path.

## Usage

Example input file:
```
▶ cat urls.txt 
https://example.com/path?one=1&two=2
https://example.com/path?two=2&one=1
https://example.com/pathtwo?two=2&one=1
https://example.net/a/path?two=2&one=1
```

### Replace Query String Values

```
▶ cat urls.txt | qqreplace newval
https://example.com/path?one=newval&two=newval
https://example.com/pathtwo?one=newval&two=newval
https://example.net/a/path?one=newval&two=newval
```

### Append to Query String Values

```
▶ cat urls.txt | qqreplace -a newval
https://example.com/path?one=1newval&two=2newval
https://example.com/pathtwo?one=1newval&two=2newval
https://example.net/a/path?one=1newval&two=2newval
```

### Remove Duplicate URL and Parameter Combinations

You can omit the argument to `-a` to only output each combination of URL and query string parameters once:
```
▶ cat urls.txt | qqreplace -a 
https://example.com/path?one=1&two=2
https://example.com/pathtwo?one=1&two=2
https://example.net/a/path?one=1&two=2
```

## Install

With Go:

```
▶ go install github.com/ranjit-git/qqreplace@latest
```


