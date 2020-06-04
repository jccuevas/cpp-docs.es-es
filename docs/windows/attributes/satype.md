---
title: rgname (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: 4619deec6d5e4e9083fbc7bcab53caee0101285c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166281"
---
# <a name="satype"></a>satype

Especifica el tipo de datos de la estructura de `SAFEARRAY`.

## <a name="syntax"></a>Sintaxis

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>Parámetros

*data_type*<br/>
El tipo de datos para la estructura de datos de `SAFEARRAY` que se pasa como un parámetro a un método de interfaz.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz, método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

## <a name="remarks"></a>Observaciones

El atributo **rgname** C++ especifica el tipo de datos del `SAFEARRAY`.

> [!NOTE]
> Un nivel de direccionamiento indirecto se quita del puntero `SAFEARRAY` del archivo. idl generado de la forma en que se declara en el archivo. cpp.

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_satype.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyModule")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A {
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="see-also"></a>Consulte también

[Atributos de compilador](compiler-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[id](id.md)
