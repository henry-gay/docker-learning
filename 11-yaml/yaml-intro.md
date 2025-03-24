# Introduction to YAML

## What is YAML?
YAML (YAML Ain't Markup Language) is a human-readable data format commonly used for configuration files. It is simpler than XML and JSON, making it easy to read and write.

If you are familiar with **XML** or **JSON**, you will find YAML intuitive. If not, don’t worry! This guide will help you understand the basics through examples.

---

## YAML Basics
### **Key-Value Pairs**
YAML represents data in **key-value pairs**:
```yaml
fruit: apple
vegetable: carrot
liquid: water
meat: chicken
```
> **Note:** There must be a space after the colon (`:`) separating the key and value.

### **Lists (Arrays)**
Lists in YAML use a **dash (`-`)** before each item:
```yaml
fruits:
  - apple
  - banana
  - cherry
```

### **Dictionaries (Maps)**
Dictionaries group related properties together:
```yaml
banana:
  calories: 105
  fat: 0.3g
  carbs: 27g
```
> **Indentation Matters!** Use consistent spaces to structure the hierarchy correctly.

---

## Indentation Rules
YAML **relies on spaces** for structure; incorrect indentation causes errors.

✅ **Correct Indentation:**
```yaml
banana:
  calories: 105
  fat: 0.3g
  carbs: 27g
```
❌ **Incorrect Indentation (Syntax Error!):**
```yaml
banana:
  calories: 105
    fat: 0.3g  # Incorrect spacing
    carbs: 27g
```

---

## Combining Lists and Dictionaries
YAML can represent complex data structures like **lists of dictionaries**:
```yaml
cars:
  - model: Tesla Model 3
    color: red
    transmission: automatic
  - model: Ford Mustang
    color: blue
    transmission: manual
```
Each item in the **list** (`-`) contains a **dictionary** with multiple properties.

---

## Dictionaries vs. Lists
- **Dictionaries** (`key: value`) are **unordered collections**.
- **Lists** (`- item`) are **ordered collections**.
- **Lists of dictionaries** allow structured data storage.

### **Example: Dictionaries Are Unordered**
These two YAML dictionaries are **identical**, even though the order differs:
```yaml
banana:
  calories: 105
  fat: 0.3g
  carbs: 27g
```
```yaml
banana:
  fat: 0.3g
  carbs: 27g
  calories: 105
```
> Order does **not** matter in dictionaries.

### **Example: Lists Are Ordered**
The following two lists are **different** because order matters:
```yaml
fruits:
  - apple
  - banana
  - cherry
```
```yaml
fruits:
  - banana
  - cherry
  - apple
```
> Order **does** matter in lists.

---

## Comments in YAML
Use `#` to write comments in YAML:
```yaml
# This is a comment
fruit: apple  # This is an inline comment
```

---

## Summary
- **YAML is used for configuration files**.
- Uses **key-value pairs**, **lists**, and **dictionaries**.
- **Indentation matters**—use spaces, not tabs.
- **Dictionaries are unordered**, but **lists are ordered**.
- **Lists of dictionaries** allow structured data representation.
- **Comments** begin with `#`.

Now you are ready to start working with YAML!