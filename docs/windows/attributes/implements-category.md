---
title: implements_category (C++ atributo COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.implements_category
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
ms.openlocfilehash: beca804fae8d6e82b4664102b39d76a23e66ca59
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409413"
---
# <a name="implementscategory"></a>implements_category

Especifica las categorías de componente que implementa la clase de destino.

## <a name="syntax"></a>Sintaxis

```cpp
[ implements_category(implements_category="uuid") ]
```

### <a name="parameters"></a>Parámetros

*implements_category*<br/>
El identificador de la categoría implementada.

## <a name="remarks"></a>Comentarios

El **implements_category** C++ atributo especifica las categorías de componente que implementa la clase de destino. Esto se hace creando una asignación de categoría y agregando entradas independientes especificadas por el **implements_category** atributo. Para obtener más información, consulte [¿cuáles son las categorías del componente y cómo hacer They Work?](https://msdn.microsoft.com/library/windows/desktop/ms694322).

Este atributo requiere que el atributo [coclass](coclass.md), [progid](progid.md)o [vi_progid](vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si `progid` se aplica, `vi_progid` y `coclass` también se aplican.

## <a name="example"></a>Ejemplo

El código siguiente especifica que el siguiente objeto implementa la `Control` categoría.

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
|**Atributos requeridos**|Uno de los siguientes: `coclass`, `progid`, o `vi_progid`|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos COM](com-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[IMPLEMENTED_CATEGORY](../../atl/reference/category-macros.md#implemented_category)