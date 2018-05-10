---
title: agregable | Documentos de Microsoft
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
ms.openlocfilehash: 1d80b2fb707145f698e8d9bb883059478c3da10b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="aggregatable"></a>aggregatable
Indica que la clase compatible con la agregación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ aggregatable(   
   value  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *valor* (opcional)  
 Un parámetro para indicar cuándo se puede agregar el objeto COM:  
  
-   **nunca** no se puede agregar el objeto COM.  
  
-   **permite** se puede crear el objeto COM directamente o puede agregarse. Este es el valor predeterminado.  
  
-   **siempre** el objeto COM no se puede crear directamente y solo se pueden agregar. Cuando se llama a `CoCreateInstance` para este objeto, debe especificar el objeto de agregación **IUnknown** interfaz (el control **IUnknown**).  
  
## <a name="remarks"></a>Comentarios  
 El **agregable** atributo C++ tiene la misma funcionalidad que la [agregable](http://msdn.microsoft.com/library/windows/desktop/aa366721) atributo MIDL. Esto significa que el compilador pasará el **agregable** a través del atributo en el archivo .idl generado.  
  
 Este atributo requiere que el atributo [coclass](../windows/coclass.md), [progid](../windows/progid.md)o [vi_progid](../windows/vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si se aplica **progid** , también se aplicarán **vi_progid** y **coclass** .  
  
 **Proyectos ATL**  
  
 Si este atributo se usa en un proyecto que usa ATL, el comportamiento del atributo cambiará. Además del comportamiento descrito anteriormente, el atributo también agrega una de las macros siguientes a la clase de destino:  
  
|Valor de parámetro|Macro insertada|  
|---------------------|--------------------|  
|**Nunca**|[DECLARE_NOT_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|  
|**Permitido**|[DECLARE_POLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|  
|**Siempre**|[DECLARE_ONLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|  
  
## <a name="example"></a>Ejemplo  
  
```  
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
|**Se aplica a**|**class**, `struct`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Uno o varios de los siguientes: **coclass**, **progid**o **vi_progid**.|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Agregación](http://msdn.microsoft.com/library/windows/desktop/ms686558)   
