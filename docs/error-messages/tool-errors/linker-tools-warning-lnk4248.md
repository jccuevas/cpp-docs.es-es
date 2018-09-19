---
title: Las herramientas del vinculador LNK4248 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4248
dev_langs:
- C++
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ff2c3edd942eb0d38d16a6986044f90358c4e9f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062168"
---
# <a name="linker-tools-warning-lnk4248"></a>Advertencia de las herramientas del vinculador LNK4248

símbolo (token) de typeref sin resolver de 'type'; imagen no se puede ejecutar

Un tipo no tiene una definición en metadatos MSIL.

LNK4248 puede producirse cuando hay solo una declaración adelantada para un tipo en un módulo MSIL (compilado con **/CLR**), donde se hace referencia al tipo en el módulo MSIL, y el módulo MSIL se vincula con un módulo nativo que tiene una definición para el tipo.

En esta situación, el vinculador proporcionará la definición de tipo nativo en los metadatos MSIL y se pueden proporcionar el comportamiento correcto.

Sin embargo, si una declaración de tipo de enrutamiento es un tipo CLR, a continuación, definición de tipo nativo del vinculador puede no ser correcta

Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Para corregir este error

1. Proporcionar la definición de tipo en el módulo MSIL.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia LNK4248. Definir un struct a resolver.

```
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

El ejemplo siguiente tiene una definición de hacia delante de un tipo.

```
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

El ejemplo siguiente genera la advertencia LNK4248.

```
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