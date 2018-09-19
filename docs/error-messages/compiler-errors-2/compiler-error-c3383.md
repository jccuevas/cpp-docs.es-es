---
title: Error del compilador C3383 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3383
dev_langs:
- C++
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e35aa05dd037c7d8a5dfd9f7e8328f3644b901e8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109397"
---
# <a name="compiler-error-c3383"></a>Error del compilador C3383

'operator new' no se admite con /clr:safe

El archivo de salida de una compilación **/clr:safe** es un archivo de seguridad de tipos comprobable y no se admiten punteros.

Para obtener más información, vea

- [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Problemas comunes de migración a 64 bits en Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3383.

```
// C3383.cpp
// compile with: /clr:safe
int main() {
   char* pCharArray = new char[256];  // C3383
}
```