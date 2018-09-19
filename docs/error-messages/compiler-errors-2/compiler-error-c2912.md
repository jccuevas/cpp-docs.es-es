---
title: Error del compilador C2912 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2912
dev_langs:
- C++
helpviewer_keywords:
- C2912
ms.assetid: bd55cecd-ab1a-4636-ab8a-a00393fe7b3d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1eb3a1aef43033c57f50cadda79bae3035aea978
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091925"
---
# <a name="compiler-error-c2912"></a>Error del compilador C2912

la especialización explícita; 'declaration' no es una especialización de una plantilla de función

No se puede especializar una función que no es de plantilla.

El código siguiente genera el error C2912:

```
// C2912.cpp
// compile with: /c
void f(char);
template<> void f(char);   // C2912
template<class T> void f(T);   // OK
```

Este error también se generará como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: para cada especialización explícita debe elegir los parámetros de la especialización explícita, de modo que coincidan con los parámetros de la plantilla principal.

```
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