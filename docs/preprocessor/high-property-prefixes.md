---
title: high_property_prefixes
ms.date: 10/18/2018
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: 130d19f275612e153955ae49f299fe2f36d098bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579821"
---
# <a name="highpropertyprefixes"></a>high_property_prefixes

**Específicos de C++**

Especifica los prefijos alternativos para tres métodos de propiedad.

## <a name="syntax"></a>Sintaxis

```
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")
```

### <a name="parameters"></a>Parámetros

*GetPrefix*<br/>
Prefijo que se usará para el `propget` métodos.

*PutPrefix*<br/>
Prefijo que se usará para el `propput` métodos.

*PutRefPrefix*<br/>
Prefijo que se usará para el `propputref` métodos.

## <a name="remarks"></a>Comentarios

De forma predeterminada, control de errores de alto nivel `propget`, `propput`, y `propputref` métodos expuestos por funciones miembro denominadas con prefijos `Get`, `Put`, y `PutRef`, respectivamente.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)