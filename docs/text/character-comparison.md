---
title: Comparación de caracteres
ms.date: 11/04/2016
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
ms.openlocfilehash: 075a22634f254c2ea634a1171ee157971fe5918e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410699"
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
