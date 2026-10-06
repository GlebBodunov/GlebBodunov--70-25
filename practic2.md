# practic2

## Task1
```
mkdir ~/pract2 && cd ~/pract2
python3 -m venv venv
source venv/bin/activate

pip install matplotlib
pip show matplotlib | grep -E "^(Name|Version|Summary|Author|Location|Requires|Required-by):"

ls venv/lib/python3*/site-packages/matplotlib-*.dist-info/
grep -E "^(Metadata-Version|Name|Version|Requires-Python|Requires-Dist|Project-URL)" venv/lib/python3*/site-packages/matplotlib-*.dist-info/METADATA

git clone --depth 1 https://github.com/matplotlib/matplotlib.git matplotlib_git
ls matplotlib_git
grep -A 12 "^dependencies" matplotlib_git/pyproject.toml
```

## Task2
```
mkdir ~/pract2/express_test && cd ~/pract2/express_test
npm init -y
npm install express
npm view express name version description license engines

ls node_modules/express
grep -A 29 '"dependencies"' node_modules/express/package.json

cd ~/pract2
git clone --depth 1 https://github.com/expressjs/express.git express_git
ls express_git
grep -A 29 '"dependencies"' express_git/package.json
```

## Task3
```
cd ~/pract2
source venv/bin/activate
brew install graphviz
dot -V

pip show contourpy python-dateutil | grep -E "^(Name|Requires):"

cat > matplotlib.dot << 'EOF'
digraph matplotlib {
    rankdir=LR;
    node [shape=box];
    matplotlib -> {
        contourpy cycler fonttools kiwisolver numpy
        packaging pillow pyparsing "python-dateutil"
    };
    contourpy -> numpy;
    "python-dateutil" -> six;
}
EOF

cat > express.dot << 'EOF'
digraph express {
    rankdir=LR;
    node [shape=box];
    express -> {
        accepts "body-parser" "content-disposition" "content-type"
        cookie "cookie-signature" debug depd encodeurl "escape-html"
        etag finalhandler fresh "http-errors" "merge-descriptors"
        "mime-types" "on-finished" once parseurl "proxy-addr" qs
        "range-parser" router send "serve-static" statuses "type-is" vary
    };
}
EOF

dot -Tpng matplotlib.dot -o matplotlib.png
dot -Tpng express.dot -o express.png
open matplotlib.png express.png
```

## Task4
```
include "globals.mzn";

array[1..6] of var 0..9: d;

constraint all_different(d);
constraint d[1] + d[2] + d[3] = d[4] + d[5] + d[6];

solve minimize d[1] + d[2] + d[3];

output ["Билет: \(d[1])\(d[2])\(d[3]) \(d[4])\(d[5])\(d[6])\n",
        "Сумма: \(d[1] + d[2] + d[3])\n"];
```

## Task5
```
var {100, 110, 120, 130, 140, 150}: menu;
var {180, 200, 210, 220, 230}: dropdown;
var {100, 200}: icons;

constraint icons = 100;

constraint menu >= 110 -> dropdown >= 200;
constraint menu = 100 -> dropdown = 180;

constraint dropdown >= 200 -> icons = 200;

solve satisfy;

output ["menu = \(menu)\n",
        "dropdown = \(dropdown)\n",
        "icons = \(icons)\n"];
```

## Task6
```
var {100, 110}: foo;
var {0, 100}: left;
var {0, 100}: right;
var {0, 100, 200}: shared;
var {100, 200}: target;

constraint target = 200;

constraint foo = 110 -> (left = 100 /\ right = 100);
constraint left = 100 -> shared >= 100;
constraint right = 100 -> shared = 100;
constraint shared = 100 -> target = 100;

constraint left > 0 -> foo = 110;
constraint right > 0 -> foo = 110;
constraint shared > 0 -> (left > 0 \/ right > 0);

solve satisfy;

output ["foo = \(foo)\nleft = \(left)\nright = \(right)\nshared = \(shared)\ntarget = \(target)\n"];
```
