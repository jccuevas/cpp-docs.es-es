---
title: Error del compilador C2130
ms.date: 11/04/2016
f1_keywords:
- C2130
helpviewer_keywords:
- C2130
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
ms.openlocfilehash: aee0931926cad2ac30631c152aeb94bfd24befd2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579752"
---
# <a name="compiler-error-c2130"></a>Error del compilador C2130

\#línea esperaba una cadena que contiene el nombre de archivo, que pero se encontró 'token'

El token de nombre de archivo opcional que se encuentra después de [#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` debe ser una cadena.

El ejemplo siguiente genera la advertencia C2130:

```
// C2130.cpp
int main() {
   #line 1000 test   // C2130
   #line 1000 "test"   // OK
}
```