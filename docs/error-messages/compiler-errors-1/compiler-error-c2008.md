---
title: Error del compilador C2008
ms.date: 11/04/2016
f1_keywords:
- C2008
helpviewer_keywords:
- C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
ms.openlocfilehash: 0bd9193d6e305a4b6c6851ef2524a68ecc056816
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565716"
---
# <a name="compiler-error-c2008"></a>Error del compilador C2008

'carácter': no se esperaba en la definición de macro

Aparece el carácter inmediatamente después del nombre de macro. Para resolver el error, debe haber un espacio después del nombre de macro.

El ejemplo siguiente genera C2008:

```
// C2008.cpp
#define TEST1"mytest1"    // C2008
```

Posible resolución:

```
// C2008b.cpp
// compile with: /c
#define TEST2 "mytest2"
```