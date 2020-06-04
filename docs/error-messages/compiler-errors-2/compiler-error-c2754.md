---
title: Error del compilador C2754
ms.date: 11/04/2016
f1_keywords:
- C2754
helpviewer_keywords:
- C2754
ms.assetid: 1cab66c5-da9d-4b81-b7fb-9cdc48ff1ccc
ms.openlocfilehash: 179cbaf65bf6440a13da6b35c073af981b074c71
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759573"
---
# <a name="compiler-error-c2754"></a>Error del compilador C2754

' especialización ': una especialización parcial no puede tener un parámetro de plantilla dependiente que no sea de tipo

Se intentó especializar parcialmente una clase de plantilla que tiene un parámetro de plantilla dependiente sin tipo. Esto no está permitido.

En el ejemplo siguiente se genera C2754:

```cpp
// C2754.cpp
// compile with: /c

template<class T, T t>
struct A {};

template<class T, int N>
struct B {};

template<class T> struct A<T,5> {};   // C2754
template<> struct A<int,5> {};   // OK
template<class T> struct B<T,5> {};   // OK
```
