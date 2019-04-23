---
title: requires_category (C++ atributo COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requires_category
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
ms.openlocfilehash: ec35a1958d9fbcf77fef7f498c6c0dba3ab17df9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59022144"
---
# <a name="requirescategory"></a>requires_category

Especifica las categorías de los componentes necesarios de la clase de destino.

## <a name="syntax"></a>Sintaxis

```cpp
[ requires_category(
  requires_category) ]
```

### <a name="parameters"></a>Parámetros

*requires_category*<br/>
El identificador de la categoría necesaria.

## <a name="remarks"></a>Comentarios

El **requires_category** C++ atributo especifica las categorías de componentes requeridas por la clase de destino. Para obtener más información, consulte [REQUIRED_CATEGORY](../../atl/reference/category-macros.md#required_category).

Este atributo requiere que el atributo [coclass](coclass.md), [progid](progid.md)o [vi_progid](vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento.

## <a name="example"></a>Ejemplo

El código siguiente requiere que el objeto implementa la categoría de Control.

```cpp
// cpp_attr_ref_requires_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLibrary")];

[ coclass, requires_category("CATID_Control"),
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]
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

[Atributos COM](com-attributes.md)<br/>
[implements_category](implements-category.md)