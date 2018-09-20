---
title: agregados | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.aggregates
dev_langs:
- C++
helpviewer_keywords:
- aggregates attribute
- aggregation [C++]
- aggregate objects [C++], aggregates attribute
- aggregates [C++]
ms.assetid: 67a084c9-941f-474b-a029-9c93b38ebe9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4bbb5c62fb53d1246c1b8cc282b4ee36f0fcf58e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377323"
---
# <a name="aggregates"></a>agregados

Indica que el objeto agrega el objeto especificado por el CLSID.

## <a name="syntax"></a>Sintaxis

```cpp
[ aggregates(
   clsid,
   variable_name
) ]
```

### <a name="parameters"></a>Parámetros

*CLSID*<br/>
Especifica el CLSID del objeto agregable.

*variable_name*<br/>
El nombre de la variable que se va a insertar. Esta variable contiene el `IUnknown` del objeto que se va a agregar.

## <a name="remarks"></a>Comentarios

Cuando se aplica a un objeto, el atributo C++ **aggregates** implementa un contenedor externo para el objeto que se va a agregar (especificado por `clsid`).

Este atributo requiere que el atributo [coclass](../windows/coclass.md), [progid](../windows/progid.md)o [vi_progid](../windows/vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si `progid` se aplica, `vi_progid` y `coclass` también se aplican.

### <a name="atl-projects"></a>Proyectos ATL

Si este atributo se usa en un proyecto que usa ATL, el comportamiento del atributo cambiará. Primero se agrega la siguiente entrada al mapa COM del objeto de destino:

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(_m_spAttrXXX, clsid)  
```

Después, también se agrega la macro [DECLARE_GET_CONTROLLING_UNKNOWN](../atl/reference/aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) .

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_aggregates.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

// requires 'aggregatable.dll'
// see aggregatable attribute to create 'aggregatable.dll'
class DECLSPEC_UUID("1a8369cc-1c91-42c4-befa-5a5d8c9d2529") CMyClass;

[module (name="MYObject")];
[object, uuid("ab006d85-e754-47c5-9ef4-2744ff32a20c")]
__interface IObject
{
};

[ coclass, aggregates(__uuidof(CMyClass)),
  uuid("91cb2c06-8931-432a-baac-206e55c4edfb")]
struct CObject : IObject
{
   int i;
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|Sí|
|**Atributos requeridos**|Una o varias de las siguientes acciones: `coclass`, `progid`, o `vi_progid`.|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos COM](../windows/com-attributes.md)<br/>
[Atributos de clase](../windows/class-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[Agregación](/windows/desktop/com/aggregation)<br/>
[Agregables](/windows/desktop/Midl/aggregatable)<br/>
[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](../atl/reference/com-interface-entry-macros.md#com_interface_entry_autoaggregate_blind)  