---
title: '&lt;codecvt&gt; (Enumeraciones)'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: e67290d8de0b8251191c4a93b66b7e19a293ed61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371941"
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt; (Enumeraciones)

## <a name="codecvt_mode-enumeration"></a><a name="codecvt_mode"></a>codecvt_mode (enumeración)

Especifica la información de configuración de las facetas [de configuración](../standard-library/locale-class.md) regional.

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Observaciones

La enumeración define tres constantes que proporcionan información de configuración a las facetas de configuración regional declaradas en [ \<codecvt>](../standard-library/codecvt.md). Los diferentes valores son:

- `consume_header`, para consumir una secuencia de encabezados iniciales al leer una secuencia multibyte y determinar los modos endian de la secuencia multibyte que se va a leer

- `generate_header`, para generar una secuencia de encabezados iniciales al escribir una secuencia multibyte para anunciar los modos endian de la secuencia multibyte siguiente que se va a escribir

- `little_endian`, para generar una secuencia multibyte en orden little endian, en lugar del orden big endian predeterminado

Estas constantes pueden usar OR en combinaciones arbitrarias.

## <a name="see-also"></a>Consulte también

[\<>codecvt](../standard-library/codecvt.md)
