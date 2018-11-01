---
title: Comparación de caracteres
ms.date: 11/04/2016
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
ms.openlocfilehash: 206910d4b76f93a92ee5230a227d6f0346a85e61
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615415"
---
# <a name="character-comparison"></a>Comparación de caracteres

Use las sugerencias siguientes:

- Comparación de un byte inicial conocido con un carácter ASCII funciona correctamente:

    ```cpp
    if( *sz1 == 'A' )
    ```

- Comparación de dos caracteres desconocidos requiere el uso de una de las macros definidas en Mbstring.h:

    ```cpp
    if( !_mbccmp( sz1, sz2) )
    ```

   Esto garantiza que los bytes de un carácter de doble byte se comparan la igualdad.

## <a name="see-also"></a>Vea también

[Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)<br/>
[Desbordamiento de búfer](../text/buffer-overflow.md)