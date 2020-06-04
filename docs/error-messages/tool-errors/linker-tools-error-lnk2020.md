---
title: Error de las herramientas del vinculador LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 9c6be2548e277af08f1069a70b26cd761db835bc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988760"
---
# <a name="linker-tools-error-lnk2020"></a>Error de las herramientas del vinculador LNK2020

token sin resolver ' token '

Similar a un error externo sin definir, salvo que la referencia se realiza a través de metadatos. En los metadatos, se deben definir todas las funciones y los datos.

Para resolver este problema:

- Definir la función o los datos que faltan, o

- Incluya el archivo objeto o biblioteca en el que ya se ha definido la función o los datos que faltan.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera LNK2020.

```cpp
// LNK2020.cpp
// compile with: /clr /LD
ref struct A {
   A(int x);   // LNK2020
   static int f();   // LNK2020
};

// OK
ref struct B {
   B(int x) {}
   static int f() { return 0; }
};
```

## <a name="example"></a>Ejemplo

También se producirá LNK2020 si crea una variable de un tipo de plantilla administrada, pero tampoco crea instancias del tipo.

En el ejemplo siguiente se genera LNK2020.

```cpp
// LNK2020_b.cpp
// compile with: /clr

template <typename T>
ref struct Base {
   virtual void f1() {};
};

template <typename T>
ref struct Base2 {
   virtual void f1() {};
};

int main() {
   Base<int>^ p;   // LNK2020
   Base2<int>^ p2 = gcnew Base2<int>();   // OK
};
```
