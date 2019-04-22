---
title: raw_native_types
ms.date: 11/04/2016
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: 32b77905ef7025334e5101e76864da9a15c50cf6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024973"
---
# <a name="rawnativetypes"></a>raw_native_types
**Específicos de C++**

Deshabilita el uso de las clases de soporte de COM en las funciones de contenedor de alto nivel y, en su lugar, fuerza el uso de tipos de datos de bajo nivel.

## <a name="syntax"></a>Sintaxis

```
raw_native_types
```

## <a name="remarks"></a>Comentarios

De forma predeterminada, los métodos de control de errores de alto nivel utilizan las clases de soporte COM [_bstr_t](../cpp/bstr-t-class.md) y [_variant_t](../cpp/variant-t-class.md) en lugar de la `BSTR` y `VARIANT` punteros de interfaz COM sin formato y tipos de datos. Estas clases encapsulan los detalles de asignación y desasignación del almacenamiento de memoria para estos tipos de datos, y simplifican considerablemente la conversión de tipos y las operaciones de conversión.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)