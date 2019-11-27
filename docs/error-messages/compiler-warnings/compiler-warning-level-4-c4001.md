---
title: ADVERTENCIA del compilador (nivel 4) C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: fc4ae55c5d25719e930a7435e0f9bf3ee2071a21
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541629"
---
# <a name="compiler-warning-level-4-c4001"></a>ADVERTENCIA del compilador (nivel 4) C4001

se usó la extensión no estándar ' comentario de una sola línea '

> [!NOTE]
> Esta advertencia se quita en la versión 15,5 de Visual 2017 Studio, ya que los comentarios de una sola línea son estándar en C99.

Los comentarios de una sola línea son C++ estándar en y estándar en C a partir de C99.
En compatibilidad con ANSI estricto ([/za](../../build/reference/za-ze-disable-language-extensions.md)), los archivos de C que contienen comentarios de una sola línea, generan C4001 debido al uso de una extensión no estándar. Dado que los comentarios de una sola línea C++son estándar en, los archivos de C que contienen comentarios de una sola línea no generan C4001 al compilar con las extensiones de Microsoft (/ZE).

## <a name="example"></a>Ejemplo

Para deshabilitar la advertencia, quite la marca de comentario [#pragma ADVERTENCIA (disable: 4001)](../../preprocessor/warning.md).

```cpp
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```