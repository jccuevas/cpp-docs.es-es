---
title: Comparación de caracteres | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3412939bac9dace6f3abaacda75ed73d6e60f21
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428075"
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