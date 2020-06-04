---
title: implements_category (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.implements_category
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
ms.openlocfilehash: dd55c7474a0a8a273ddfab212b3ebcaa6e3b4a65
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166867"
---
# <a name="implements_category"></a>implements_category

Especifica las categorías de componentes implementadas por la clase de destino.

## <a name="syntax"></a>Sintaxis

```cpp
[ implements_category(implements_category="uuid") ]
```

### <a name="parameters"></a>Parámetros

*implements_category*<br/>
IDENTIFICADOR de la categoría implementada.

## <a name="remarks"></a>Observaciones

El atributo **implements_category** C++ especifica las categorías de componentes implementadas por la clase de destino. Esto se hace creando un mapa de categorías y agregando entradas independientes especificadas por el atributo **implements_category** . Para obtener más información, vea [categorías de componentes y cómo funcionan](/windows/win32/com/component-categories-and-how-they-work).

Este atributo requiere que el atributo [coclass](coclass.md), [progid](progid.md)o [vi_progid](vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si se aplica `progid`, también se aplican `vi_progid` y `coclass`.

## <a name="example"></a>Ejemplo

El código siguiente especifica que el siguiente objeto implementa la categoría `Control`.

```cpp
// cpp_attr_ref_implements_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLib")];
[ coclass, implements_category("CATID_Control"),
  uuid("20a0d0cc-5172-40f5-99ae-5e032f3205ae")]
class CMyClass {};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|Sí|
|**Atributos requeridos**|Uno de los siguientes: `coclass`, `progid`o `vi_progid`|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos COM](com-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[IMPLEMENTED_CATEGORY](../../atl/reference/category-macros.md#implemented_category)
