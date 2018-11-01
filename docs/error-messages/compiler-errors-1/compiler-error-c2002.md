---
title: Error del compilador C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: 30f472aa7a9475a19eea0e92fe5c2ea0d54e382b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442853"
---
# <a name="compiler-error-c2002"></a>Error del compilador C2002

constante de caracteres anchos no válida

La constante de caracteres multibyte no es válida.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. La constante de caracteres anchos contiene más bytes de lo esperado.

1. No se incluye el encabezado estándar STDDEF.h.

1. Caracteres anchos no se pueden concatenar con literales de cadena normal.

1. Una constante de caracteres anchos debe ir precedida por el carácter 'L':

    ```
    L'mbconst'
    ```

1. En Microsoft C++, los argumentos de texto de una directiva de preprocesador deben ser ASCII. Por ejemplo, la directiva, `#pragma message(L"string")`, no es válido.