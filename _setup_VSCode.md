````markdown
# PyPSA Setup Guide on macOS (Apple Silicon, Python 3.11)

This guide walks you through a **clean, working setup** of:

- Python **3.11**  
- A **virtual environment** (`venv`)  
- **PyPSA** (with SciPy installed **safely**, without freezes)

---

## Why SciPy Freezes on macOS (Apple Silicon)

PyPSA depends on **SciPy**, and SciPy can be **difficult to install on macOS** via `pip` because it needs compiled C/Fortran libraries.

To avoid hangs or freezes:

- ✅ Install a **pre-built SciPy wheel first**  
- ✅ Then install **PyPSA** and the rest of the scientific stack  
- ✅ Then verify everything works

---

## ✅ Step 0 — Confirm Python 3.11

In **Terminal**, run:

```bash
python3.11 --version
````

You should see something like:

```text
Python 3.11.x
```

If that works, continue.

---

## ✅ Step 1 — Go to Your Project Folder

```bash
cd /Users/huilingoh/Documents/programming/Power
```

Delete any old virtual environment:

```bash
rm -rf venv
```

---

## ✅ Step 2 — Create a Fresh Virtual Environment

Create a new `venv` using Python 3.11:

```bash
python3.11 -m venv venv
```

Activate it:

```bash
source venv/bin/activate
```

Your prompt should now show something like:

```text
(venv) huilingoh@Huis-MacBook-Pro Power %
```

If you see the `(venv)` prefix → you’re in the virtual environment.

---

## ❗ Step 3 — Install SciPy **First** (Key Freeze Fix)

This is the **critical step** to avoid SciPy and PyPSA import freezes.

Upgrade packaging tools and install a compatible SciPy:

```bash
pip install --upgrade pip wheel setuptools
pip install "scipy==1.12.0"
```

> 💡 SciPy **1.12.0** has stable wheels for **Python 3.11 + macOS ARM**, which prevents the freezing you previously saw.

Test that SciPy works:

```bash
python3 -c "import scipy; print(scipy.__version__)"
```

If it prints:

```text
1.12.0
```

…you’re good to proceed.

---

## ✅ Step 4 — Install the Rest of the Scientific Stack

Now install **NumPy**, **pandas**, **matplotlib**, and **seaborn**:

```bash
pip install numpy pandas matplotlib seaborn
```

---

## ✅ Step 5 — Install PyPSA

With SciPy already installed and working, you can safely install PyPSA:

```bash
pip install pypsa
```

Because SciPy is already set up, **PyPSA should not freeze** on import.

---

## 🎯 Step 6 — Verify PyPSA Import

Run:

```bash
python3 -c "import pypsa; print('PyPSA imported successfully')"
```

If you see:

```text
PyPSA imported successfully
```

…then PyPSA is installed and importing correctly.

---

## ✅ Step 7 — Open the Project in VS Code

1. Open **VS Code**
2. Go to **File → Open Folder**
3. Select:

   ```text
   /Users/huilingoh/Documents/programming/Power
   ```

---

## ✅ Step 8 — Select the `venv` Interpreter in VS Code

1. Press: `Cmd` + `Shift` + `P`
2. Type: `Python: Select Interpreter`
3. Choose:

   ```text
   /Users/huilingoh/Documents/programming/Power/venv/bin/python3
   ```

VS Code should show **`(venv)`** or the venv name in the bottom status bar.

---

## ⭐ Step 9 — Create a Test Script

Create a file called `test.py` in your project folder with the following contents:

```python
import pypsa
import scipy
import numpy as np

print("PyPSA:", pypsa.__version__)
print("SciPy:", scipy.__version__)
print("NumPy:", np.__version__)
```

Run it inside the virtual environment:

```bash
python3 test.py
```

You should see normal version numbers printed, for example:

```text
PyPSA: x.y.z
SciPy: 1.12.0
NumPy: x.y.z
```

No freezing, no errors.

---

## 🎉 You’re Fully Set Up

With this setup you should **not** see:

* SciPy freezes
* PyPSA freezing on import
* `KeyboardInterrupt` from hanging imports
* General import hangs in your environment

You now have a **stable, working PyPSA environment** on macOS (Apple Silicon, Python 3.11).

---

> 👉 Want to continue?
> Try creating your first PyPSA script, e.g. a tiny example power network model.

```
```
