---
title: '&lt;codecvt&gt; (Enumeraciones) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: 612570680bfacb2bc9c237c60b3e9f6c4f8266a8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725340"
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt; (Enumeraciones)

## <a name="codecvt_mode"></a>  codecvt_mode (Enumeración)

Especifica la información de configuración de las facetas de [configuración regional](../standard-library/locale-class.md).

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Comentarios

La enumeración define tres constantes que proporcionan información de configuración a las facetas de configuración regional declaradas en [\<codecvt>](../standard-library/codecvt.md). Los diferentes valores son:

- `consume_header`, para consumir una secuencia de encabezados iniciales al leer una secuencia multibyte y determinar los modos endian de la secuencia multibyte que se va a leer

- `generate_header`, para generar una secuencia de encabezados iniciales al escribir una secuencia multibyte para anunciar los modos endian de la secuencia multibyte siguiente que se va a escribir

- `little_endian`, para generar una secuencia multibyte en orden little endian, en lugar del orden big endian predeterminado

Estas constantes pueden usar OR en combinaciones arbitrarias.

## <a name="see-also"></a>Vea también

[\<codecvt>](../standard-library/codecvt.md)<br/>
