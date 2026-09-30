# practic1

## Task1

​```bash
cut -d: -f1 /etc/passwd | sort
​```

## Task2

​```bash
grep -v '^#' /etc/protocols | grep -v '^$' | awk '{print $2, $1}' | sort -rn | head -n 5
​```

## Task3

​```bash
#!/usr/bin/env bash
text="$1"
len=${#text}
border=$(printf '%*s' "$((len + 2))" '' | tr ' ' '-')

printf '+%s+\n' "$border"
printf '| %s |\n' "$text"
printf '+%s+\n' "$border"
​```

## Task4

​```bash
grep -oE '[A-Za-z_][A-Za-z0-9_]*' hello.c | sort -u | tr '\n' ' '
​```

## Task5

​```bash
#!/usr/bin/env bash
prog="$1"

if [ -z "$prog" ] || [ ! -f "$prog" ]; then
    echo "Использование: ./reg <имя_программы>"
    exit 1
fi

chmod 755 "$prog"
cp "$prog" /usr/local/bin/
​```

## Task6

​```bash
#!/usr/bin/env bash
for f in *.c *.js *.py; do
    [ -e "$f" ] || continue

    first_line=$(head -n 1 "$f")

    case "$f" in
        *.py)
            comment_symbol="#"
            ;;
        *)
            comment_symbol="//"
            ;;
    esac

    case "$first_line" in
        "$comment_symbol"*)
            echo "$f: комментарий есть"
            ;;
        *)
            echo "$f: комментария нет"
            ;;
    esac
done
​```

## Task7

​```bash
#!/usr/bin/env bash
path="$1"

find "$path" -type f -exec md5sum {} \; | sort | uniq -w32 --all-repeated=separate -D
​```

## Task8

​```bash
#!/usr/bin/env bash
ext="$1"

if [ -z "$ext" ]; then
    echo "Использование: ./task8_archive.sh <расширение>"
    exit 1
fi

find . -maxdepth 1 -type f -name "*.$ext" -print0 \
    | tar --null -czvf "archive_$ext.tar.gz" --files-from -
​```

## Task9

​```bash
#!/usr/bin/env bash
input="$1"
output="$2"

sed 's/ /\t/g' "$input" > "$output"
​```

## Task10

​```bash
#!/usr/bin/env bash
dir="$1"

find "$dir" -maxdepth 1 -type f -empty -print
​```

