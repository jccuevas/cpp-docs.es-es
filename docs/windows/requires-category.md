---
title: requires_category | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.requires_category
dev_langs:
- C++
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a1a7d656d307f6f0fcba446d3b58a625adfb8bc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612774"
---
# <a name="requirescategory"></a>requires_category

Especifica las categorías de los componentes necesarios de la clase de destino.

## <a name="syntax"></a>Sintaxis

```cpp
[ requires_category(
  requires_category
) ]
```

### <a name="parameters"></a>Parámetros

*requires_category*  
El identificador de la categoría necesaria.

## <a name="remarks"></a>Comentarios

El **requires_category** atributo de C++ especifica las categorías de componentes requeridas por la clase de destino. Para obtener más información, consulte [REQUIRED_CATEGORY](../atl/reference/category-macros.md#required_category).

Este atributo requiere que el atributo [coclass](../windows/coclass.md), [progid](../windows/progid.md)o [vi_progid](../windows/vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento.

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

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos COM](../windows/com-attributes.md)  
[implements_category](../windows/implements-category.md)  