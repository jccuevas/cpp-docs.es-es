---
title: Error irrecuperable C1022 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1022
dev_langs:
- C++
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ddeea660515ea0a71e4807a34d2172413796046
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036740"
---
# <a name="fatal-error-c1022"></a>Error irrecuperable C1022

se esperaba #endif

Una directiva `#if`, `#ifdef`o `#ifndef` no tiene una directiva `#endif` coincidente. Asegúrese de que cada `#if`, `#ifdef`o `#ifndef` tenga una `#endif`coincidente.

El ejemplo siguiente genera la advertencia C1022:

```
// C1022.cpp
#define true 1

#if (true)
#else
#else    // C1022
```

Posible resolución:

```
// C1022b.cpp
// compile with: /c
#define true 1

#if (true)
#else
#endif
```