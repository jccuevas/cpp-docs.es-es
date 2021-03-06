---
title: agregable (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregatable
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
ms.openlocfilehash: d929543f699dcd20471ff9a9b45f54119f82a40a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168530"
---
# <a name="aggregatable"></a>aggregatable

Indica que la clase admite la agregación.

## <a name="syntax"></a>Sintaxis

```cpp
[ aggregatable(value) ]
```

### <a name="parameters"></a>Parámetros

*value*<br/>
Opta Un parámetro para indicar cuándo se puede Agregar el objeto COM:

- `never` el objeto COM no se puede Agregar.

- `allowed` el objeto COM se puede crear directamente o se puede Agregar. Este es el valor predeterminado.

- `always` el objeto COM no se puede crear directamente y solo se puede Agregar. Cuando llame a `CoCreateInstance` para este objeto, debe especificar la interfaz de `IUnknown` del objeto de agregado (control `IUnknown`).

## <a name="remarks"></a>Observaciones

El **aggregatable** C++ atributo agregable tiene la misma funcionalidad que el atributo MIDL [agregable](/windows/win32/Midl/aggregatable) . Esto significa que el compilador pasará el atributo **agregable** a través del archivo. idl generado.

Este atributo requiere que el atributo [coclass](coclass.md), [progid](progid.md)o [vi_progid](vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si se aplica `progid`, también se aplican `vi_progid` y `coclass`.

### <a name="atl-projects"></a>Proyectos ATL

Si este atributo se usa en un proyecto que usa ATL, el comportamiento del atributo cambiará. Además del comportamiento descrito anteriormente, el atributo también agrega una de las macros siguientes a la clase de destino:

|Valor del parámetro|Macro insertada|
|---------------------|--------------------|
|`Never`|[DECLARE_NOT_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|
|`Allowed`|[DECLARE_POLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|
|`Always`|[DECLARE_ONLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_aggregatable.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyModule")];

[ coclass, aggregatable(allowed),
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]
class CMyClass {};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|Uno o varios de los siguientes: `coclass`, `progid`o `vi_progid`.|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Agregación](/windows/win32/com/aggregation)
