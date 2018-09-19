---
title: Error del compilador C2130 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2130
dev_langs:
- C++
helpviewer_keywords:
- C2130
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 954930522651fcee6c29bf019f366e056fe681ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071535"
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