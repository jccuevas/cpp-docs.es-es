---
title: Acelerador de la propiedad de clave (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Key property
ms.assetid: d1570cd9-b414-4cd6-96bd-47c38281eaca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e0594e5b9e2d092330664546cbd05ccfb0060c42
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428972"
---
# <a name="accelerator-key-property-c"></a>Acelerador de la propiedad de clave (C++)

Las entradas siguientes son válidas para la propiedad de clave en la tabla de aceleradores:

- Un entero entre 0 y 255 en formato decimal. El valor determina si el valor se trata como ASCII o ANSI como sigue:

   - Números de un solo dígito se interpretan siempre como la clave correspondiente, en lugar de como valores ASCII o ANSI.

   - Los valores de 1 a 26, si van precedidos de ceros, se interpretan como ^ A ^ Z, que representa el valor ASCII de las letras del alfabeto cuando se presiona con la **Ctrl** clave se mantiene presionada.

   - Los valores de 27-32 siempre se interpretan como valores de tres dígitos decimales comprendidos entre 032 027.

   - Los valores de 033 a 255, ya sea precedido de 0 o no se interpretan como valores ANSI.

- Un carácter único teclado. Mayúscula A - Z o los números 0 - 9 pueden ser ASCII o valores de clave virtuales; cualquier otro carácter solo es ASCII.

- Un carácter único teclado en el intervalo A - Z (sólo mayúsculas), precedida por un símbolo de intercalación (^) (por ejemplo, ^ C). Esto entra en el valor ASCII de la clave cuando se presiona con la **Ctrl** tecla presionada.

   > [!NOTE]
   > Cuando escribe un valor ASCII, las opciones de la propiedad modificador son limitadas. La única clave de control disponible para su uso es la **Alt** clave.

- Cualquier identificador de clave virtual válido. El cuadro de lista desplegable clave en la tabla de aceleradores contiene una lista de identificadores de clave virtuales estándares.

   > [!TIP]
   > Es otra manera de definir una tecla de aceleración para el botón derecho en una o varias entradas en la tabla de aceleradores, elija **tecla siguiente** en el menú contextual y, a continuación, presione cualquiera de las claves o combinaciones de teclas del teclado. El **tecla siguiente** comando también está disponible desde el **editar** menú.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Establecimiento de las propiedades de los aceleradores](../windows/setting-accelerator-properties.md)<br/>
[Edición en una tabla de aceleradores](../windows/editing-in-an-accelerator-table.md)<br/>
[Editor de aceleradores](../windows/accelerator-editor.md)