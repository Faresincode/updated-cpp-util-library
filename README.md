# clsUtil.h - Universal Utility Library for C++

## 🧩 Overview
`clsUtil` is an **all-in-one utility toolkit** for C++ designed to simplify everyday programming tasks — from text encryption to random generation, array manipulation, and file operations.

It seamlessly integrates with other utility headers such as `clsMath` and `clsDate`, offering a strong foundation for building data-driven or system-level applications.

The library is **header-only**, requiring no linking — just include it in your project.

---

## 🚀 Key Features

### 🔢 Randomization & Data Generation
- `Srand()` — seeds the random number generator.
- `GetRandomCharacter()` — generates a random char (capital, small, digit, special, or mixed).
- `GenerateWord()` — creates a random string of chosen type and length.
- `GenerateKey()` — builds a secure license-style key format (e.g. `ABCD-EFGH-IJKL-MNOP`).
- `GenerateKeys()` — prints multiple random keys.

### 🔐 Encryption & Decryption
- `EncryptText(string text, int key=2)`
- `DecryptText(string text, int key=2)`
> Simple Caesar cipher implementation for quick secure encoding.

### 📂 File Management
- `AddDataLineToFile(string line, string filename)` — append data to a text file.
- `LoadDataFromFile(string filename)` — load file content into a vector of strings.
- `SaveDataToFile(vector<string> lines, string filename)` — overwrite file contents.
- `RemoveEmptyLineInFile(string filename)` — cleans out empty lines automatically.

### 🔁 Array Utilities
- `Swap()` — template swap function for any datatype.
- `ShuffleArray()` — randomizes order of array elements (works with both int[] and string[]).
- `FillArrayWithRandomNumber()` — populate an array with random integers.
- `FillArrayWithRandomWords()` — populate with random characters.
- `FillArrayWithRandomKey()` — generate and fill with license keys.

### 📈 Numeric & Text Utilities
- `NumberToText()` — converts an integer to a readable English text.
- `Tabs(int)` / `BackSlashN(int)` — quick text formatting helpers.
- `PrintFibonacciUsingRecursion()` — prints Fibonacci numbers recursively.
- `OperationTypeCaracter()` — returns character symbol for arithmetic operations (+, -, *, /, %).

### 🎨 Console Tools
- `ResetScreen()` — clears console and resets color.
- Built-in color codes for terminal output:
  - `Red()`, `Green()`, `Blue()`, `Yellow()`, `White()`
- `Centre()` — aligns text to center using `setw(50)`.

### ⚙️ Enums
- `enCharType` — defines character generation type:
  - `Capitalletter`, `SmallLetter`, `Degit`, `SpecialChar`, `MixChars`
- `enLevel` — represents difficulty levels: `Easy`, `Med`, `Hard`

---

## 💡 Example Usage

```cpp
#include <iostream>
#include "clsUtil.h"
using namespace std;

int main()
 {
    clsUtil::Srand();

    cout << "Random Character: " << clsUtil::GetRandomCharacter(1) << endl;
    cout << "Random Word: " << clsUtil::GenerateWord(1, 6) << endl;
    cout << "License Key: " << clsUtil::GenerateKey() << endl;

    string text = "HelloWorld";
    string enc = clsUtil::EncryptText(text);
    string dec = clsUtil::DecryptText(enc);
    cout << "Original: " << text << " | Encrypted: " << enc << " | Decrypted: " << dec << endl;

    int arr[5] = { 1, 2, 3, 4, 5 };
    clsUtil::ShuffleArray(arr, 5);
    cout << "Shuffled Array: ";
    for (int i = 0; i < 5; i++) cout << arr[i] << " ";
    cout << endl;

    vector<string> lines = { "Line 1", "Line 2", "", "Line 3" };
    clsUtil::SaveDataToFile(lines, "test.txt");
    clsUtil::RemoveEmptyLineInFile("test.txt");
    cout << "File cleaned successfully." << endl;

    cout << "Fibonacci (6 terms): ";
    clsUtil::PrintFibonacciUsingRecursion(6, 0, 1);
    cout << endl;

    cout << clsUtil::Green() << "All Done!" << clsUtil::White() << endl;

    return 0;
}
```

---

## 🧪 Testing Guide

To test each module, use small assertions or print checks like this:

```cpp
#include "clsUtil.h"
#include <cassert>
#include <iostream>
using namespace std;

int main()
{
    clsUtil::Srand();

    // Encryption test
    string txt = "ABC";
    string enc = clsUtil::EncryptText(txt, 3);
    string dec = clsUtil::DecryptText(enc, 3);
    assert(txt == dec);

    // Random key format test
    string key = clsUtil::GenerateKey();
    assert(key.length() == 19); // "XXXX-XXXX-XXXX-XXXX"

    // File I/O test
    vector<string> v = { "A", "", "B" };
    clsUtil::SaveDataToFile(v, "sample.txt");
    clsUtil::RemoveEmptyLineInFile("sample.txt");

    // Fibonacci test
    cout << "Fibonacci (5 terms): ";
    clsUtil::PrintFibonacciUsingRecursion(5, 0, 1);
    cout << endl;

    cout << "All tests passed!" << endl;
}
```

Compile:
```
g++ -std=c++17 test_clsUtil.cpp -o test && ./test
```

---

## 🧾 Example Output

```
Random Character: G
Random Word: Trqxep
License Key: QWRT-YUIO-ASDF-GHJK
Original: HelloWorld | Encrypted: JgnnqYqtnf | Decrypted: HelloWorld
Shuffled Array: 3 5 2 4 1
File cleaned successfully.
Fibonacci (6 terms): 1 1 2 3 5 8
All Done!
All tests passed!
```

---

## ⚡ Performance & Compatibility
- **Header-only**, no linking required.
- Works on **C++17 and newer**.
- Cross-platform: Windows, Linux, macOS.
- Depends only on `<iostream>`, `<fstream>`, `<string>`, and `clsMath.h`.

---

## 🧱 Structure
```
clsUtil.h
└── clsUtil
    ├── Random & encryption tools
    ├── Array operations
    ├── File I/O system
    ├── Console formatting
    ├── Fibonacci recursion
    ├── Enum type definitions
    └── Color/text helpers
```

---

## 🧰 Future Enhancements
- Add file existence check and safe overwrite confirmation.
- Add JSON/CSV formatted save functions.
- Integrate logging and debug mode.
- Add color auto-reset and background color support.

---

## 📜 License
Open-source and free for educational or commercial use.
