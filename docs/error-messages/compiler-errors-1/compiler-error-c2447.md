---
title: Error del compilador C2447
ms.date: 11/04/2016
f1_keywords:
- C2447
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
ms.openlocfilehash: 64dca8313af8b640b7b03c1ab27a1a31fa90de09
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638534"
---
# <a name="compiler-error-c2447"></a>Error del compilador C2447

'{': falta el encabezado de función (¿lista formal de estilo anterior?)

El compilador encontró una llave de apertura inesperada en el ámbito global. En la mayoría de los casos, la causa está en un encabezado de función que tiene un formato incorrecto, una declaración mal colocada o carácter de punto y coma desubicado. Para resolver este problema, compruebe que la llave de apertura va detrás de un encabezado con formato correcto y no va precedida de una declaración o un carácter de punto y coma desubicado.

Este error también puede deberse a una lista de argumentos formales del lenguaje C de estilo anterior. Para resolver este problema, refactorice la lista de argumentos para que utilice un estilo moderno; es decir, que vaya entre paréntesis.

El ejemplo siguiente genera C2447:

```
// C2447.cpp
int c;
{}       // C2447
```