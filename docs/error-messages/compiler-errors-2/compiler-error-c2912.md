---
title: Error del compilador C2912
ms.date: 11/04/2016
f1_keywords:
- C2912
helpviewer_keywords:
- C2912
ms.assetid: bd55cecd-ab1a-4636-ab8a-a00393fe7b3d
ms.openlocfilehash: 254252bfd21aa28c87810f1e21b4864e2775a71b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761090"
---
# <a name="compiler-error-c2912"></a>Error del compilador C2912

la especialización explícita; 'declaration' no es una especialización de una plantilla de función

No se puede especializar una función que no es de plantilla.

El código siguiente genera el error C2912:

```cpp
// C2912.cpp
// compile with: /c
void f(char);
template<> void f(char);   // C2912
template<class T> void f(T);   // OK
```

Este error también se generará como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: para cada especialización explícita debe elegir los parámetros de la especialización explícita, de modo que coincidan con los parámetros de la plantilla principal.

```cpp
// C2912b.cpp
class CF {
public:
   template <class A> CF(const A& a) {}   // primary template

   // attempted explicit specialization
   template <> CF(const char* p) {}   // C2912

   // try the following line instead
   // template <> CF(const char& p) {}
};
```
