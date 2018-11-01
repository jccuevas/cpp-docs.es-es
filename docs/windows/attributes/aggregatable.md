---
title: Aggregatable (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregatable
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
ms.openlocfilehash: 74a561b9b70c5aee36781d102835c73dec2c3ac2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582473"
---
# <a name="aggregatable"></a>aggregatable

Indica que la clase admite agregación.

## <a name="syntax"></a>Sintaxis

```cpp
[ aggregatable(value) ]
```

### <a name="parameters"></a>Parámetros

*valor*<br/>
(Opcional) Un parámetro para indicar cuándo se puede agregar el objeto COM:

- `never` No se puede agregar el objeto COM.

- `allowed` El objeto COM puede crearse directamente o puede agregarse. Este es el valor predeterminado.

- `always` El objeto COM no se puede crear directamente y solo se puede agregar. Cuando se llama a `CoCreateInstance` para este objeto, debe especificar el objeto de agregación `IUnknown` interfaz (el control `IUnknown`).

## <a name="remarks"></a>Comentarios

El **agregables** atributo de C++ tiene la misma funcionalidad que el [agregables](/windows/desktop/Midl/aggregatable) atributo MIDL. Esto significa que el compilador pasará el **agregables** a través del atributo en el archivo .idl generado.

Este atributo requiere que el atributo [coclass](coclass.md), [progid](progid.md)o [vi_progid](vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si `progid` se aplica, `vi_progid` y `coclass` también se aplican.

### <a name="atl-projects"></a>Proyectos ATL

Si este atributo se usa en un proyecto que usa ATL, el comportamiento del atributo cambiará. Además del comportamiento descrito anteriormente, el atributo también agrega una de las macros siguientes a la clase de destino:

|Valor de parámetro|Macro insertado|
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
|**Atributos requeridos**|Una o varias de las siguientes acciones: `coclass`, `progid`, o `vi_progid`.|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Agregación](/windows/desktop/com/aggregation)