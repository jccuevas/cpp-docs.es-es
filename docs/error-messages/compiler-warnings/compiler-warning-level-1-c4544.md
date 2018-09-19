---
title: Compilador advertencia (nivel 1) C4544 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4544
dev_langs:
- C++
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c7cd274f0d1b595d374e1b108db40a51395b968
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084281"
---
# <a name="compiler-warning-level-1-c4544"></a>Advertencia del compilador (nivel 1) C4544

'declaration': se omitió el argumento de plantilla predeterminado de esta declaración de plantilla

Se especificó un argumento de plantilla predeterminado en una ubicación incorrecta y se omitió. Un argumento de plantilla predeterminado de una plantilla de clase solo puede especificarse en la declaración o definición de la plantilla de clase y no en un miembro de la plantilla de clase.

Este ejemplo genera el error C4545 y el ejemplo siguiente muestra cómo corregirlo:

```
// C4544.cpp
// compile with: /W1 /LD
template <class T>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T=int>
template <class T1>
struct S<T>::S1 {};   // C4544
```

En este ejemplo, el parámetro predeterminado se aplica a la plantilla de clase `S`:

```
// C4544b.cpp
// compile with: /LD
template <class T = int>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1 {};
```