---
title: Error del compilador C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: c37a9b94be837248c8025a4fc069d8a242128542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208252"
---
# <a name="compiler-error-c2002"></a>Error del compilador C2002

constante de caracteres anchos no válida

La constante de caracteres multibyte no es válida.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. La constante de caracteres anchos contiene más bytes de lo esperado.

1. No se incluye el encabezado estándar STDDEF. h.

1. Los caracteres anchos no se pueden concatenar con literales de cadena normales.

1. Una constante de caracteres anchos debe ir precedida del carácter ' L ':

    ```
    L'mbconst'
    ```

1. En el C++caso de Microsoft, los argumentos de texto de una directiva de preprocesador deben ser ASCII. Por ejemplo, la Directiva, `#pragma message(L"string")`, no es válida.
