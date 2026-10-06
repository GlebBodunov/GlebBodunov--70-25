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
