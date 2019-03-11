---
title: Índices de byte
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
ms.openlocfilehash: 5305a977c23d7a978a89c84809cc6fab8c5731eb
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751601"
---
# <a name="byte-indices"></a>Índices de byte

Use las sugerencias siguientes:

- Trabajar con un índice de byte a byte en una cadena presenta problemas similares a los que suponen la manipulación de puntero. Considere este ejemplo, que busca una cadena con un carácter de barra diagonal inversa:

    ```cpp
    while ( rgch[ i ] != '\\' )
        i++;
    ```

   Esto es posible que la indización de un byte final, no es un byte inicial, y por lo tanto, no es posible que apunte a un `character`.

- Use la [_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) función para resolver el problema anterior:

    ```cpp
    while ( rgch[ i ] != '\\' )
        i += _mbclen ( rgch + i );
    ```

   Esto se indiza correctamente a un byte inicial, por lo tanto, para un `character`. El `_mbclen` función determina el tamaño de un carácter (1 o 2 bytes).

## <a name="see-also"></a>Vea también

[Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)<br/>
[Último carácter de una cadena](../text/last-character-in-a-string.md)
