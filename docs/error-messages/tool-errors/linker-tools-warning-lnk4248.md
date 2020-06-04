---
title: Advertencia de las herramientas del vinculador LNK4248
ms.date: 11/04/2016
f1_keywords:
- LNK4248
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
ms.openlocfilehash: 4ba05ef067c539dc9c0aca6dc2a395748fd217a2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988099"
---
# <a name="linker-tools-warning-lnk4248"></a>Advertencia de las herramientas del vinculador LNK4248

token de TypeRef sin resolver (token) para ' tipo '; es posible que la imagen no se ejecute

Un tipo no tiene una definición en los metadatos de MSIL.

LNK4248 se puede producir cuando solo hay una declaración adelantada para un tipo en un módulo MSIL (compilado con **/CLR**), donde se hace referencia al tipo en el módulo MSIL y donde el módulo MSIL está vinculado a un módulo nativo que tiene una definición para el tipo.

En esta situación, el vinculador proporcionará la definición de tipo nativo en los metadatos de MSIL y esto puede proporcionar el comportamiento correcto.

Sin embargo, si una declaración de tipo de avance es un tipo CLR, es posible que la definición de tipo nativo del enlazador no sea correcta.

Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Para corregir este error

1. Proporcione la definición de tipo en el módulo MSIL.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera LNK4248. Defina el struct a que se va a resolver.

```cpp
// LNK4248.cpp
// compile with: /clr /W1
// LNK4248 expected
struct A;
void Test(A*){}

int main() {
   Test(0);
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente tiene una definición hacia delante de un tipo.

```cpp
// LNK4248_2.cpp
// compile with: /clr /c
class A;   // provide a definition for A here to resolve
A * newA();
int valueA(A * a);

int main() {
   A * a = newA();
   return valueA(a);
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera LNK4248.

```cpp
// LNK4248_3.cpp
// compile with: /c
// post-build command: link LNK4248_2.obj LNK4248_3.obj
class A {
public:
   int b;
};

A* newA() {
   return new A;
}

int valueA(A * a) {
   return (int)a;
}
```
