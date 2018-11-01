---
title: Error del compilador C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: 094a794627b886abc7db5ba4d74c6fe97ff82461
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649749"
---
# <a name="compiler-error-c2086"></a>Error del compilador C2086

'identifier': nueva definición

El identificador está definido varias veces o una declaración difiere de uno anterior.

C2086 también puede ser el resultado de una generación incremental para un ensamblado de C# que se hace referencia. Vuelva a generar el ensamblado de C# para resolver este error.

El ejemplo siguiente genera C2086:

```
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```