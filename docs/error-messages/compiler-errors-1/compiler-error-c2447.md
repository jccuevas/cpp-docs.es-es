---
title: Error del compilador C2447 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2447
dev_langs:
- C++
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9cc18c8e6ffb31de062957e16f6f3a6573379ee
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035141"
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