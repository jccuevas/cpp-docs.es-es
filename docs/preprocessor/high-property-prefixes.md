---
title: atributo de importación high_property_prefixes
ms.date: 08/29/2019
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: 9e44f6f1afae479f803f4c6d866ef3ee38744561
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219008"
---
# <a name="high_property_prefixes-import-attribute"></a>atributo de importación high_property_prefixes

**C++Cuestión**

Especifica los prefijos alternativos para tres métodos de propiedad.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **high_property_prefixes (** "*GetPrefix*" **,** "*PutPrefix*" **,** "*PutRefPrefix*" **)**

### <a name="parameters"></a>Parámetros

*GetPrefix*\
Prefijo que se va a `propget` usar para los métodos.

*PutPrefix*\
Prefijo que se va a `propput` usar para los métodos.

*PutRefPrefix*\
Prefijo que se va a `propputref` usar para los métodos.

## <a name="remarks"></a>Comentarios

De forma predeterminada, los `propget`métodos, `propput`y `propputref` de control de errores de alto nivel se `Get`exponen mediante funciones de miembro `Put`denominadas con prefijos, y `PutRef`, respectivamente.

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
