---
title: _variant_t (Clase)
ms.date: 11/04/2016
f1_keywords:
- _variant_t
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
ms.openlocfilehash: 69976cab9caed653a8278f80821569b613f690eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502744"
---
# <a name="variantt-class"></a>_variant_t (Clase)

**Específicos de Microsoft**

Un **_variant_t** objeto encapsula el `VARIANT` tipo de datos. La clase administra la asignación de recursos y la desasignación y realiza llamadas de función a `VariantInit` y `VariantClear` según corresponda.

### <a name="construction"></a>Construcción

|||
|-|-|
|[_variant_t](../cpp/variant-t-variant-t.md)|Construye un **_variant_t** objeto.|

### <a name="operations"></a>Operaciones

|||
|-|-|
|[Asociar](../cpp/variant-t-attach.md)|Asocia un `VARIANT` objeto en el **_variant_t** objeto.|
|[Borrar](../cpp/variant-t-clear.md)|Borra el encapsulado `VARIANT` objeto.|
|[ChangeType](../cpp/variant-t-changetype.md)|Cambia el tipo de la **_variant_t** objeto del `VARTYPE`.|
|[Desasociar](../cpp/variant-t-detach.md)|Desasocia el objeto encapsulado `VARIANT` objeto desde este **_variant_t** objeto.|
|[SetString](../cpp/variant-t-setstring.md)|Asigna una cadena a este **_variant_t** objeto.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](../cpp/variant-t-operator-equal.md)|Asigna un nuevo valor a una existente **_variant_t** objeto.|
|[operador ==,! =](../cpp/variant-t-relational-operators.md)|Comparar dos **_variant_t** objetos para la igualdad o desigualdad.|
|[Extractores de datos](../cpp/variant-t-extractors.md)|Extraer datos de encapsulado `VARIANT` objeto.|

**FIN de Específicos de Microsoft**

## <a name="requirements"></a>Requisitos

**Encabezado:** \<comutil.h >

**Lib:** omsuppw.lib o comsuppwd.lib (vea [/Zc: wchar_t (wchar_t es tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información)

## <a name="see-also"></a>Vea también

[Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)