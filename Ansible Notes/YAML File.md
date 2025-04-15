#ansible #yaml

A YAML file is a human-readable data serialization language. It stands for **YAML Ain't Markup Language** (a recursive acronym), emphasizing its focus on data rather than document markup.

- [[YAML - Choosing the Right Data Structure]]
- [[YAML  - Anchors and Aliases]]
- 

Here's a breakdown of its key characteristics:

- **Human-Readable:** YAML is designed to be easily read and written by humans. It uses indentation and simple syntax to structure data.
- **Data Serialization:** Its primary purpose is to represent data structures in a text format that can be easily understood by both humans and computers.
- **Language-Agnostic:** YAML is not tied to any specific programming language and can be used to exchange data between different systems.
- **Hierarchy through Indentation:** Unlike markup languages like XML or JSON that use tags or braces, YAML uses whitespace (spaces, not tabs) to define the hierarchy and nesting of data. Consistent indentation is crucial.
- **Key-Value Pairs:** Data is often represented as key-value pairs, similar to dictionaries or associative arrays in programming languages.
- **Lists:** YAML supports ordered lists (arrays) of items.
- **Scalar Types:** It supports various basic data types like strings, numbers (integers and floats), Booleans (true/false, yes/no, on/off), and null values (null, ~).
- **Comments:** Lines starting with `#` are treated as comments and are ignored by the parser.

**Common Uses of YAML:**

- **Configuration Files:** Widely used for configuration files in various applications and systems (e.g., Ansible playbooks, Docker Compose, Kubernetes manifests).
- **Data Exchange:** Used for exchanging data between applications, although JSON is often preferred for web APIs due to its simplicity and browser compatibility.
- **Object Serialization:** Can represent complex data structures and objects.
- **Inter-process Communication:** Sometimes used for communication between different processes.

**Simple YAML Example:**

YAML

```
name: John Doe
age: 30
isStudent: false
address:
  street: 123 Main St
  city: Anytown
  zip: 12345
hobbies:
  - reading
  - hiking
  - coding
```

**Explanation of the Example:**

- `name: John Doe` is a key-value pair where `name` is the key and `John Doe` is the string value.
- `age: 30` is another key-value pair with a numeric value.
- `isStudent: false` is a key-value pair with a Boolean value.
- `address:` indicates a nested mapping (dictionary). The indented lines below it are key-value pairs within the `address` mapping.
- `hobbies:` indicates a list. The lines starting with `-` are the items in the list.

**In summary, YAML is a clean and readable data serialization format that leverages indentation to define structure, making it particularly well-suited for configuration files and representing structured data in a human-friendly way.**

![[Pasted image 20250415205056.png]]
![[Pasted image 20250415205237.png]]

![[Pasted image 20250415210841.png]]


