---
title: implements_category | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.implements_category
dev_langs:
- C++
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e566e50cc0fed4b17b085451410a1d0c3f81fb38
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597552"
---
# <a name="implementscategory"></a>implements_category

Especifica las categorías de componente que implementa la clase de destino.

## <a name="syntax"></a>Sintaxis

```cpp
[ implements_category(
   implements_category="uuid"
) ]
```

### <a name="parameters"></a>Parámetros

*implements_category*  
El identificador de la categoría implementada.

## <a name="remarks"></a>Comentarios

El **implements_category** atributo de C++ especifica las categorías de componente que implementa la clase de destino. Esto se hace creando una asignación de categoría y agregando entradas independientes especificadas por el **implements_category** atributo. Para obtener más información, consulte [¿cuáles son las categorías del componente y cómo hacer They Work?](http://msdn.microsoft.com/library/windows/desktop/ms694322).

Este atributo requiere que el atributo [coclass](../windows/coclass.md), [progid](../windows/progid.md)o [vi_progid](../windows/vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si `progid` se aplica, `vi_progid` y `coclass` también se aplican.

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

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos COM](../windows/com-attributes.md)  
[Atributos de clase](../windows/class-attributes.md)  
[IMPLEMENTED_CATEGORY](../atl/reference/category-macros.md#implemented_category)  