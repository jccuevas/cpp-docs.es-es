---
title: Compilador advertencia (nivel 4) C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: dd18dc27ee13eab05ea0253c8ebcc990105c15c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562284"
---
# <a name="compiler-warning-level-4-c4001"></a>Compilador advertencia (nivel 4) C4001

se utilizó una extensión no estándar 'comentario de una única línea'

> [!NOTE]
> Esta advertencia se quita en Visual Studio 2017 versión 15.5 porque los comentarios de línea son estándar en C99.

Comentarios de una línea están en C++ estándar y en C a partir de C99.
Compatibilidad estricta con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), archivos de C que contienen comentarios multilínea, generan C4001 debido al uso de una extensión no estándar. Puesto que los comentarios de línea son estándar en C++, archivos de C que contienen comentarios de una línea no producen C4001 al compilar con las extensiones de Microsoft (/Ze).

## <a name="example"></a>Ejemplo

Para deshabilitar la advertencia, quite la marca de comentario [warning(disable:4001) #pragma](../../preprocessor/warning.md).

```
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```