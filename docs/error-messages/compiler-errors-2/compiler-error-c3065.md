---
title: Error del compilador C3065
ms.date: 11/04/2016
f1_keywords:
- C3065
helpviewer_keywords:
- C3065
ms.assetid: e7a0bc69-1c68-459e-a7c4-93c65609ff7c
ms.openlocfilehash: 026a6d5191f5bf7969dd2c8217b624d44b8ca345
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761434"
---
# <a name="compiler-error-c3065"></a>Error del compilador C3065

no se permite la declaración de propiedad en un ámbito que no es de clase

El modificador __declspec de [propiedad](../../cpp/property-cpp.md) se usó fuera de una clase.  Una propiedad solo puede declararse dentro de una clase.

El ejemplo siguiente genera la advertencia C3065:

```cpp
// C3065.cpp
// compile with: /c
__declspec(property(get=get_i)) int i;   // C3065

class x {
public:
   __declspec(property(get=get_i)) int i;   // OK
};
```
