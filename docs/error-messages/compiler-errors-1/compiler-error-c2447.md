---
title: Error del compilador C2447
ms.date: 11/04/2016
f1_keywords:
- C2447
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
ms.openlocfilehash: 14fec374927fc798956a249773d9bec814e7a823
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744191"
---
# <a name="compiler-error-c2447"></a>Error del compilador C2447

'{': falta el encabezado de función (¿lista formal de estilo anterior?)

El compilador encontró una llave de apertura inesperada en el ámbito global. En la mayoría de los casos, la causa está en un encabezado de función que tiene un formato incorrecto, una declaración mal colocada o carácter de punto y coma desubicado. Para resolver este problema, compruebe que la llave de apertura va detrás de un encabezado con formato correcto y no va precedida de una declaración o un carácter de punto y coma desubicado.

Este error también puede deberse a una lista de argumentos formales del lenguaje C de estilo anterior. Para resolver este problema, refactorice la lista de argumentos para que utilice un estilo moderno; es decir, que vaya entre paréntesis.

En el ejemplo siguiente se genera C2447:

```cpp
// C2447.cpp
int c;
{}       // C2447
```
