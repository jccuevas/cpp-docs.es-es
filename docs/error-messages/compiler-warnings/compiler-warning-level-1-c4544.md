---
title: Advertencia del compilador (nivel 1) C4544
ms.date: 11/04/2016
f1_keywords:
- C4544
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
ms.openlocfilehash: 6aee8ba6b07e02f012755f609d8a5089cea280b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186288"
---
# <a name="compiler-warning-level-1-c4544"></a>Advertencia del compilador (nivel 1) C4544

'declaration': se omitió el argumento de plantilla predeterminado de esta declaración de plantilla

Se especificó un argumento de plantilla predeterminado en una ubicación incorrecta y se omitió. Un argumento de plantilla predeterminado de una plantilla de clase solo puede especificarse en la declaración o definición de la plantilla de clase y no en un miembro de la plantilla de clase.

Este ejemplo genera el error C4545 y el ejemplo siguiente muestra cómo corregirlo:

```cpp
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

```cpp
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
