---
title: Error del compilador C2086 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2086
dev_langs:
- C++
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0e0d8b105d58b0585bc31b8d340d3d7ba5fb29e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029850"
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