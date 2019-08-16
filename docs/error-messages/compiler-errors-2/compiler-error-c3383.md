---
title: Error del compilador C3383
ms.date: 11/04/2016
f1_keywords:
- C3383
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
ms.openlocfilehash: 38aea188eeac90cd23d9203a53b4e630be2f115b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367348"
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