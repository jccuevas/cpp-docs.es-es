---
title: Error del compilador C2766
ms.date: 11/04/2016
f1_keywords:
- C2766
helpviewer_keywords:
- C2766
ms.assetid: 8032f4ca-6827-4f04-9c61-c44643c85cc4
ms.openlocfilehash: 48faee02bba18754972954a2ca464417bd552758
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759807"
---
# <a name="compiler-error-c2766"></a>Error del compilador C2766

especialización explícita; ' especialización ' ya se ha definido

No se permiten especializaciones explícitas duplicadas. Para obtener más información, vea [especialización explícita de plantillas de función](../../cpp/explicit-specialization-of-function-templates.md).

En el ejemplo siguiente se genera C2766:

```cpp
// C2766.cpp
// compile with: /c
template<class T>
struct A {};

template<>
struct A<int> {};

template<>
struct A<int> {};   // C2766
// try the following line instead
// struct A<char> {};
```
