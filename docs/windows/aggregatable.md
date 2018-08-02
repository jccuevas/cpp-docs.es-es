---
title: agregables | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.aggregatable
dev_langs:
- C++
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b5d94a1e66043a83e2ffb2aa8c1d44d9cbd16cc
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467201"
---
# <a name="aggregatable"></a>aggregatable
Indica que la clase admite agregación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[ aggregatable(   
   value  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *valor* (opcional)  
 Un parámetro para indicar cuándo se puede agregar el objeto COM:  
  
-   **nunca** el objeto COM no se puede agregar.  
  
-   **permite** se puede crear directamente el objeto COM o puede agregarse. Este es el valor predeterminado.  
  
-   **siempre** el objeto COM no se puede crear directamente y solo se pueden agregar. Cuando se llama a `CoCreateInstance` para este objeto, debe especificar el objeto de agregación `IUnknown` interfaz (el control `IUnknown`).  
  
## <a name="remarks"></a>Comentarios  
 El **agregables** atributo de C++ tiene la misma funcionalidad que el [agregables](http://msdn.microsoft.com/library/windows/desktop/aa366721) atributo MIDL. Esto significa que el compilador pasará el **agregables** a través del atributo en el archivo .idl generado.  
  
 Este atributo requiere que el atributo [coclass](../windows/coclass.md), [progid](../windows/progid.md)o [vi_progid](../windows/vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si `progid` se aplica, `vi_progid` y `coclass` también se aplican.  
  
 **Proyectos ATL**  
  
 Si este atributo se usa en un proyecto que usa ATL, el comportamiento del atributo cambiará. Además del comportamiento descrito anteriormente, el atributo también agrega una de las macros siguientes a la clase de destino:  
  
|Valor de parámetro|Macro insertado|  
|---------------------|--------------------|  
|*Nunca*|[DECLARE_NOT_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|  
|*Permitido*|[DECLARE_POLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|  
|*Siempre*|[DECLARE_ONLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|  
  
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
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Agregación](http://msdn.microsoft.com/library/windows/desktop/ms686558)   