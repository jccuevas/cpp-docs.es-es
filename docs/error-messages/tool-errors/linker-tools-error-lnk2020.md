---
title: Error de las herramientas del vinculador LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 7290a90dfd92d84c4632e7f9dd38d36eccd4ac27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386335"
---
# <a name="linker-tools-error-lnk2020"></a>Error de las herramientas del vinculador LNK2020

símbolo (token) sin resolver 'token'

Es similar a un error externo no definido, excepto en que la referencia es a través de metadatos. En los metadatos, se deben definir todas las funciones y datos.

Para resolver:

- Definir la función o los datos, que faltan o

- Incluya el archivo objeto o biblioteca en el que la función o los datos que faltan ya está definidos.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error LNK2020.

```
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

También se producirá el error LNK2020 si se crea una variable de un tipo de plantilla administrado, pero no también una instancia del tipo.

El ejemplo siguiente genera el error LNK2020.

```
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