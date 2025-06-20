- A library in python
- A light weighted web Framework
- Use to create [[API]]
- We make server and Client Architecture by [[REST API]] 
- We mention route of each function using app.route(/...)
- In **flask** library *Flask* is a Python class which initializes the web application, think it like a **Engine**
- Flask works by mapping URLs to Functions using app.route('/relative path')
	- @app.route() is a **decorator** that tells Flask to run the following fn when visits the present page in the web app
	- And whatever that python function returns flask sends that back to the browser

### What is __name__ and __main__?
- name is a special built-in variable in **every Python File** 
	- **Behavior**:
		  1. When a py file is executed directly, _____name_____ == __ __main__ __
		  2. When a py file is imported, name == module_name
	Very well. You're asking the right question—and refusing shallow understanding. Let’s build this concept from **first principles**, like a true engineer.

---

## 🎯 Objective:

To understand:

- What is `__name__`?
- What does `if __name__ == '__main__'` mean?
- Why do we need it?

---

## 🧱 Prerequisite Knowledge (Fundamental Python)

If you want to fully understand this concept, ensure you know:

|Concept|Why it’s Needed|
|---|---|
|Python modules and scripts|To grasp when a file is "run" vs "imported"|
|How Python executes a script|Understand how Python assigns `__name__`|
|Functions and conditionals|Understand the `if` logic|
|`print()` and debugging basics|To experiment with values|

If you're unclear on **what happens when you run a `.py` file** vs when you **import it**, that's the gap we’ll now fix.

---

## 🔍 What is `__name__`?

### It is a special **built-in variable** in every Python file.

### Behavior:

- When a Python file is **executed directly**, `__name__ == '__main__'`
    
- When a Python file is **imported**, `__name__ == 'module_name'`
    

---

## 🧪 Proof by Example

Create two Python files:

### `file1.py`

```python
print("file1 __name__:", __name__)
```

### `file2.py`

```python
import file1
print("file2 __name__:", __name__)
```

---

### 🔁 Now Run:

```bash
python file1.py
```

**Output:**

```
file1 __name__: __main__
```

✅ Because `file1.py` is run **directly**, so its `__name__ == '__main__'`

---

### Now Run:

```bash
python file2.py
```

**Output:**

```
file1 __name__: file1
file2 __name__: __main__
```

📌 Because:

- `file2.py` is the main script → its `__name__ == '__main__'`
    
- It **imported** `file1` → so `file1.__name__ == 'file1'`
    

---

## 🔑 Now the Meaning of `if __name__ == '__main__'`

```python
if __name__ == '__main__':
    do_something()
```

Means:

> “Only run this code if this file is executed directly.  
> Not when it is imported somewhere else.”

### ⚙️ In Flask:

This lets Flask know:

> “Run the web server **only when this file is the entry point.**  
> Don’t run the server just because someone imported this app.”

---

## ✅ Why This Matters

|Use Case|What Happens|
|---|---|
|Running your app directly|Web server starts (`__name__ == '__main__'`)|
|Importing the app in another file|Server does **not** start automatically|

This avoids accidental side effects. It’s a safety mechanism.

---

## 🧠 Analogy:

> Think of `__name__` as your **passport stamp**.  
> When you're the **main traveler**, you're marked `"__main__"` and go straight through.  
> When you're just **accompanying someone** (being imported), you're tagged with your **name**, and the guards stop extra activity.

---

## 🏁 Final Thoughts

You now understand:

|Concept|Meaning|
|---|---|
|`__name__`|Tells Python who the file is: `'__main__'` or `'module_name'`|
|`if __name__ == '__main__'`|A conditional to **only run code if the file is the starting point**|
|Why Flask uses it|So the app doesn’t auto-run if imported (e.g., for unit testing or production configs)|

---

### 📌 Your Assignment:

1. Create the `file1.py` and `file2.py` experiment above and observe `__name__`.
    
2. Modify your Flask app to add a `print(__name__)` just before `app.run()` and re-run it.
    

Let me know what you observe—I’ll confirm your understanding or correct it.