---
title: Error del compilador C2599
ms.date: 11/04/2016
f1_keywords:
- C2599
helpviewer_keywords:
- C2599
ms.assetid: 88515f36-7589-47e2-862e-0de8b18d6668
ms.openlocfilehash: c722335660653df7e533ec25d4708f42c16846ef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740772"
---
# <a name="compiler-error-c2599"></a>Error del compilador C2599

' ENUM ': no se permite una declaración adelantada de tipo enum

El compilador ya no admite la declaración adelantada de una enumeración administrada.

No se permite la declaración adelantada de un tipo de enumeración con [/za](../../build/reference/za-ze-disable-language-extensions.md).

En el ejemplo siguiente se genera C2599:

```cpp
// C2599.cpp
// compile with: /clr /c
enum class Status;   // C2599

enum class Status2 { stop2, hold2, go2};

ref struct MyStruct {
   // Delete the following line to resolve.
   Status m_status;

   Status2 m_status2;   // OK
};

enum class Status { stop, hold, go };
```
