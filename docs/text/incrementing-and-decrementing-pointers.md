---
title: Aumentar y disminuir punteros | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e220c138ebcbb9010aef78931b07c2b04b095ea7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447670"
---
# <a name="incrementing-and-decrementing-pointers"></a>Aumentar y disminuir punteros

Use las sugerencias siguientes:

- Seleccione bytes iniciales, bytes finales no. No es seguro suele tener un puntero a un byte final. Es más seguro analizar una cadena hacia delante en lugar de en orden inverso.

- Existen funciones de incremento y decremento de puntero y macros que se mueven a través de un carácter completo:

    ```cpp
    sz1++;
    ```

   se convierte en:

    ```cpp
    sz1 = _mbsinc( sz1 );
    ```

   El `_mbsinc` y `_mbsdec` funciones correctamente incremento y decremento en `character` unidades, independientemente del tamaño del carácter.

- Para disminuye, se necesita un puntero al principio de la cadena, como en el siguiente ejemplo:

    ```cpp
    sz2--;
    ```

   se convierte en:

    ```cpp
    sz2 = _mbsdec( sz2Head, sz2 );
    ```

   Como alternativa, el puntero principal podría ser un carácter válido en la cadena, tal que:

    ```cpp
    sz2Head < sz2
    ```

   Debe tener un puntero a un byte inicial válidos conocidos.

- Desea mantener un puntero al carácter anterior para las llamadas más rápidas a `_mbsdec`.

## <a name="see-also"></a>Vea también

[Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)<br/>
[Índices de byte](../text/byte-indices.md)