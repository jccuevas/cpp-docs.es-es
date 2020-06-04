---
title: ADVERTENCIA del compilador (nivel 4) C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: ceb7e65a292e5b9e9ef960ca9553183b703c93f0
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991684"
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
