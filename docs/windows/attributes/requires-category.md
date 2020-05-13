---
title: requires_category (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requires_category
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
ms.openlocfilehash: 19a454a8bfc959d7d97959d765dbf68d0f766ca1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214557"
---
# <a name="requires_category"></a>requires_category

Especifica las categorías de componente necesarias de la clase de destino.

## <a name="syntax"></a>Sintaxis

```cpp
[ requires_category(
  requires_category) ]
```

### <a name="parameters"></a>Parámetros

*requires_category*<br/>
IDENTIFICADOR de la categoría requerida.

## <a name="remarks"></a>Observaciones

El atributo **requires_category** C++ especifica las categorías de componentes que requiere la clase de destino. Para obtener más información, vea [REQUIRED_CATEGORY](../../atl/reference/category-macros.md#required_category).

Este atributo requiere que el atributo [coclass](coclass.md), [progid](progid.md)o [vi_progid](vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento.

## <a name="example"></a>Ejemplo

El código siguiente requiere que el objeto implemente la categoría de control.

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
|**Atributos requeridos**|Uno o varios de los siguientes: `coclass`, `progid`o `vi_progid`.|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos COM](com-attributes.md)<br/>
[implements_category](implements-category.md)
