---
title: Error del compilador C3369
ms.date: 11/04/2016
f1_keywords:
- C3369
helpviewer_keywords:
- C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
ms.openlocfilehash: ee936f4921369b1d59d81b51dcb3e81c69be083c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755608"
---
# <a name="compiler-error-c3369"></a>Error del compilador C3369

'module name': idl_module ya se definió

El uso de [idl_module](../../windows/idl-module.md) donde se define la DLL solo puede aparecer una vez en un programa.

El ejemplo siguiente genera la advertencia C3369:

```cpp
// C3369.cpp
// compile with: /c
[idl_module(name="name1", dllname="x.dll")]; // C3369
[idl_module(name="name1", dllname="x.dll")];
```
