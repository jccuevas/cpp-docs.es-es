---
title: no se pueden crear | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.noncreatable
dev_langs:
- C++
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4055d541fa60c714262a64466734bc2b2323775b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877828"
---
# <a name="noncreatable"></a>noncreatable
Define un objeto que no se pueden crear instancias por sí mismo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
[noncreatable]  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El **noncreatable** atributo C++ tiene la misma funcionalidad que la [noncreatable](http://msdn.microsoft.com/library/windows/desktop/aa367118) atributo MIDL y se pasa automáticamente a los botones generados. Este archivo IDL por el compilador.  
  
 Cuando este atributo se utiliza dentro de un proyecto que usa ATL, cambia el comportamiento del atributo. Además el comportamiento anterior, el atributo también inserta la [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro. Esta macro se indica a ATL que no se puede crear el objeto externamente.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cpp_attr_ref_noncreatable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("11111111-1111-1111-1111-111111111111")]  
__interface A   
{  
};  
  
[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]  
class CMyClass : public A   
{  
   HRESULT xx();  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**class**, `struct`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|**coclass**|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
