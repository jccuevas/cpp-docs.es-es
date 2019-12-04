---
title: Error del compilador C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: d47d99962d089d873cb9bbdf9baac7eab706fc16
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746895"
---
# <a name="compiler-error-c2504"></a>Error del compilador C2504

' Class ': clase base sin definir

La clase base se declara pero nunca se define.  Posibles causas:

1. Falta el archivo de inclusión.

1. Clase base externa no declarada con [extern](../../cpp/using-extern-to-specify-linkage.md).

En el ejemplo siguiente se genera C2504:

```cpp
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

Vale

```
class C{};
class D : public C {};
```
