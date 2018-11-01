---
title: raw_property_prefixes
ms.date: 10/18/2018
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: 1e44b5265e486f0e5b5896bed41b62ebbdaa4fd3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647142"
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes

**Específicos de C++**

Especifica los prefijos alternativos para tres métodos de propiedad.

## <a name="syntax"></a>Sintaxis

```
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")
```

### <a name="parameters"></a>Parámetros

*GetPrefix*<br/>
Prefijo que se usará para el `propget` métodos.

*PutPrefix*<br/>
Prefijo que se usará para el `propput` métodos.

*PutRefPrefix*<br/>
Prefijo que se usará para el `propputref` métodos.

## <a name="remarks"></a>Comentarios

De forma predeterminada, de bajo nivel `propget`, `propput`, y `propputref` métodos expuestos por funciones miembro denominadas con prefijos de **get_**, **put_**, y **putref_** respectivamente. Estos prefijos son compatibles con los nombres que se usan en los archivos de encabezado generados por MIDL.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)