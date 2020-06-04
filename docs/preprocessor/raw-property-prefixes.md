---
title: atributo de importación raw_property_prefixes
ms.date: 08/29/2019
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: d4d91470781e7c5f673fd228c24904322d1db8b3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216038"
---
# <a name="raw_property_prefixes-import-attribute"></a>atributo de importación raw_property_prefixes

**C++Cuestión**

Especifica los prefijos alternativos para tres métodos de propiedad.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **raw_property_prefixes (** "*GetPrefix*" **,** "*PutPrefix*" **,** "*PutRefPrefix*" **)**

### <a name="parameters"></a>Parámetros

*GetPrefix*\
Prefijo que se va `propget` a usar para los métodos.

*PutPrefix*\
Prefijo que se va `propput` a usar para los métodos.

*PutRefPrefix*\
Prefijo que se va `propputref` a usar para los métodos.

## <a name="remarks"></a>Comentarios

De forma predeterminada, los métodos `propget`, `propput`y `propputref` de bajo nivel se exponen mediante funciones de miembro denominadas `put_`con prefijos de `get_`, y `putref_`, respectivamente. Estos prefijos son compatibles con los nombres que se usan en los archivos de encabezado generados por MIDL.

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
