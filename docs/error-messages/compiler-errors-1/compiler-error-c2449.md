---
title: Error del compilador C2449
ms.date: 11/04/2016
f1_keywords:
- C2449
helpviewer_keywords:
- C2449
ms.assetid: 544bf0b6-daa0-40e8-9f21-8e583d472a2d
ms.openlocfilehash: f674bbec7cee8c00792848ee7e51b1e46299dd58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655343"
---
# <a name="compiler-error-c2449"></a>Error del compilador C2449

¿se encontró ' {' en el ámbito de archivo (encabezado de función que faltan)?

Se produce una llave de apertura en el ámbito de archivo.

Este error puede deberse a un punto y coma entre un encabezado de función y la llave de apertura de la definición de función.

El ejemplo siguiente genera C2499:

```
// C2449.c
// compile with: /c
void __stdcall func(void) {}   // OK
void __stdcall func(void);  // extra semicolon on this line
{                         // C2449 detected here
```