---
title: Compilador (nivel 4) de la advertencia C4061 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4061
dev_langs:
- C++
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d0086ea5e590c7183024bc4dcc93e2f2522f483
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4061"></a>Compilador (nivel 4) de la advertencia C4061

> enumerador '*identificador*'en el modificador de enum'*enumeración*' no está controlada de forma explícita por una etiqueta de caso

El enumerador tiene asociado ningún controlador un `switch` instrucción.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4061; Agregar un caso del enumerador falta corregir:

```cpp
// C4061.cpp
// compile with: /W4
#pragma warning(default : 4061)

enum E { a, b, c };
void func ( E e )
{
   switch(e)
   {
      case a:
      case b:
      default:
         break;
   }   // C4061 c' not handled
}

int main()
{
}
```