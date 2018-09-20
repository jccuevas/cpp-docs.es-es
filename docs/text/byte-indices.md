---
title: Índices de byte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11f7f78e87ddd40fd3cf85fc294e8fadac5dbe45
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423798"
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