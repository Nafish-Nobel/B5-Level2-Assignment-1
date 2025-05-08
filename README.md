
# 📘 TypeScript Interview Blogs

---

## 🌟 **TypeScript Secrets: A Simple Comparison of Interfaces and Types**

Unlock the power of TypeScript by understanding the difference between **`interface`** and **`type`** in this blog post.

TypeScript helps catch errors and improve code quality. Both **`interface`** and **`type`** are used to define the structure of objects. They **commonly used**, but also they differ in flexibily usage. While similar, the **difference matters** for writing clean and maintainable code.

This blog post explores the **A Simple Comparison of Interfaces and Types** in TypeScript.

---

### 🔹 **What Are Interfaces?**

Are used to define the **structure of an object**. They provide a **clear contract** for what the object should look like.

✅ **Example:**

```typescript
interface User {
    name: string;
    age: number;
    greet(): string;
}

const user: User = {
    name: "Nobel",
    age: 20,
    greet() {
        return `Hello, my name is ${this.name}`;
    },
};
```

 Create a `User` object **without these properties**, TypeScript will Give an error and ensuring that object **adheres to the defined structure**.

---

### 🔹 **What Are Types?**

Are **more versatile**. They represent **object shapes**, **primitive types**, **unions**, **intersections**, and more.

✅ **Example:**

```typescript
type Point = {
    x: number;
    y: number;
};

const point: Point = {
    x: 10,
    y: 20,
};
```

Types can also handle **complex scenarios** like unions:

```typescript
type StringOrNumber = string | number;

const value: StringOrNumber = "Hello"; // valid
const anotherValue: StringOrNumber = 42; // valid
```

---

### 🚀 **Key Distinctions Between Interfaces and Types**

Both can define object shapes-let’s look at  **key differences**:

---

1️⃣ **Extensibility**

- **Interfaces** ➔ can be extended using `extends` → hierarchical structure.
  
    ```typescript
    interface Fruits {
        name: string;
    }
    
    interface Apple extends Fruits {
        bark(): void;
    }
    ```

- **Types** ➔ cannot extend, but can combine using intersections.

    ```typescript
    type Animal = {
        name: string;
    };

    type Cat = Animal & {
        bark(): void;
    };
    ```

---

2️⃣ **Declaration Merging**

- **Interfaces** ➔ ✅ **support declaration merging**.

    ```typescript
    interface User {
        name: string;
    }
    
    interface User {
        age: number;
    }

    const user: User = {
        name: "NAm",
        age: 20,
    };
    ```

- **Types** ➔ ❌ **do NOT support declaration merging** (defining the same type twice throws an error).

---

### 🔶 **Summary Table**

| Feature               | Interface ✅            | Type ✅                 |
|-----------------------|------------------------|-------------------------|
| Declaration merging   | ✅ Yes                 | ❌ No                  |
| Extending             | ✅ Yes (`extends`)     | ✅ Yes (with `&`)      |
| Best for objects      | ✅ Especially good     | ✅ Can, but broader    |
| Works with unions     | ❌ No                 | ✅ Yes                 |

---

### 🏁 **Conclusion**

✅ **Use interfaces** → when you need **extensibility** and **declaration merging**.  
✅ **Use types** → when require **more intricate or complex type definitions**.

By leveraging both, you can create **robust TypeScript applications** that are **easier to read, maintain, and scale**.

---

## 💎 **Keyof Type Operator**

---

### 🔹 **What is `keyof`?**

The `keyof` operator takes an object type and produces a **union** of its **keys** (`string` or `number` literals).

This is **super useful** when you want to work with object keys **type-safely**.

---

### 💡 **Why Use `keyof`?**

✨ Prevents accessing properties **that don’t exist**.  
✨ Enables **dynamic functions** or types that work with object keys.  
✨ If object keys change, TypeScript **catches errors** where keys are used.

---

### ✅ **Example:**

```typescript
interface Person {
    name: string;
    age: number;
    location: string;
}

// keyof creates: "name" | "age" | "location"
type PersonKeys = keyof Person;

function getProperty(obj: Person, key: PersonKeys) {
    return obj[key];
}

const person: Person = {
    name: "An",
    age: 20,
    location: "BD",
};

console.log(getProperty(person, "name"));  // Output: An
console.log(getProperty(person, "age"));   // Output: 20
// console.log(getProperty(person, "salary")); // ❌ Error!
```

---

### 🚀 **Advanced Use: Generics + keyof**

```typescript
function getPropertyGeneric<T, K extends keyof T>(obj: T, key: K): T[K] {
    return obj[key];
}

const personName = getPropertyGeneric(person, "name");  // Type: string
const personAge = getPropertyGeneric(person, "age");    // Type: number
```

In this case, the function works with **any object type** and the key is **strictly one of the object’s keys**.

---

### 🏁 **Conclusion**

The `keyof` keyword is a **hidden gem** in TypeScript’s toolbox.  

It allows you to **create types from object keys**, enabling **flexible** and **safe code** that enforces valid property access and **unlocks powerful patterns** in generic programming.

---

## 📚 **References**

- [TypeScript Handbook – Interfaces](https://www.typescriptlang.org/docs/handbook/interfaces.html)  
- [TypeScript Handbook – Advanced Types](https://www.typescriptlang.org/docs/handbook/advanced-types.html)
- [TypeScript Handbook – keyof Types](https://www.typescriptlang.org/docs/handbook/2/keyof-types.html)
- [Basic writing and formatting syntax (GitHub)](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)  
- [Gist by roachhd](https://gist.github.com/roachhd/1f029bd4b50b8a524f3c)

---

✨ **Happy coding! 🚀**
