---
title: Advertencia del compilador (nivel 1) C4002
ms.date: 11/04/2016
f1_keywords:
- C4002
helpviewer_keywords:
- C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
ms.openlocfilehash: cb1e36a606f5c8bb0a1622260d64124264f0db32
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164773"
---
# <a name="compiler-warning-level-1-c4002"></a>Advertencia del compilador (nivel 1) C4002

hay demasiados parámetros reales para la macro 'identifier'

El número de parámetros reales de la macro supera el número de parámetros formales de la definición de macro. El preprocesador obtiene los parámetros adicionales pero los omite durante la expansión de macro.

La advertencia C4002 puede aparecer al usar [Variadic Macros](../../preprocessor/variadic-macros.md)de manera incorrecta.

El ejemplo siguiente genera la advertencia C4002:

```cpp
// C4002.cpp
// compile with: /W1
#define test(a) (a)

int main() {
   int a = 1;
   int b = 2;
   a = test(a,b);   // C4002
   // try..
   a = test(a);
}
```

Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio. NET 2003: ya no se acepta el uso de comas adicionales en la macro.

El compilador ya no aceptará comas adicionales en una macro. Para que el código sea válido en las versiones de Visual Studio .NET 2003 y de Visual Studio .NET de Visual C++, quite las comas adicionales.

```cpp
// C4002b.cpp
// compile with: /W1
#define F(x,y)
int main()
{
   F(2,,,,,,3,,,,,,)   // C4002
   // Try the following line instead:
   // F(2,3)
}
```
