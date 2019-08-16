---
title: Error del compilador C3382
ms.date: 11/04/2016
f1_keywords:
- C3382
helpviewer_keywords:
- C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
ms.openlocfilehash: c262ea963ae739fbb76211aae2622e98d5a9b6f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328788"
---
# <a name="compiler-error-c3382"></a>Error del compilador C3382

'sizeof' no se admite con /clr:safe

El archivo de resultados de una compilación **/clr:safe** es un archivo de seguridad de tipos comprobable y el operador sizeof no se admite porque el valor devuelto del operador sizeof es size_t, cuyo tamaño varía según el sistema operativo.

Para obtener más información, vea

- [sizeof (operador)](../../cpp/sizeof-operator.md)

- [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Problemas comunes de migración a 64 bits en Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3382:

```
// C3382.cpp
// compile with: /clr:safe
int main() {
   sizeof( char );   // C3382
}
```