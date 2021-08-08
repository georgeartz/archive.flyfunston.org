# archive.flyfunston.org


## Steps taken to create

Download the entire website

```
httrack "http://flyfunston.org/" -O "/tmp/flyfunston.org" "+*.flyfunston.org/*" -v -%A php=text/html
```

Merge the flyfunston.org and www.flyfunston.org directories, then update references

```
grep -lr -e 'www.flyfunston.org' * | xargs sed -i 's/www.flyfunston.org/flyfunston.org/g'
```

Replace all .php files with .html
```
# Update filenames
for f in `find ./ | grep .php`; do mv $f $f.html; done;

# Update references
grep -lr -e '.php' * | xargs sed -i 's/.php/.php.html/g'
```

