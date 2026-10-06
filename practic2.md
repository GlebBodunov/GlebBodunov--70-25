# practic1

## Task1

```mkdir ~/pract2 && cd ~/pract2
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
