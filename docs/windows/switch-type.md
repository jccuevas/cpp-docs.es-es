---
title: switch_type | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_type
dev_langs:
- C++
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1870e1ee623d8495e9f19dd8f32ea9382070bc14
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890189"
---
# <a name="switchtype"></a>switch_type
Identifica el tipo de la variable utilizada como la unión discriminante.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
[switch_type(  
type  
}]  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `type`  
 El tipo de conmutador, puede ser un tipo entero, carácter, Boolean o enumeración.  
  
## <a name="remarks"></a>Comentarios  
 El **switch_type** atributo C++ tiene la misma funcionalidad que la [switch_type](http://msdn.microsoft.com/library/windows/desktop/aa367276) atributo MIDL.  
  
 Los atributos de C++ no admiten [encapsulado uniones](http://msdn.microsoft.com/library/windows/desktop/aa366811). [Uniones nonencapsulated](http://msdn.microsoft.com/library/windows/desktop/aa367119) solo se admiten en el formato siguiente:  
  
```  
// cpp_attr_ref_switch_type.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLibrary")];  
[ export ]  
struct SizedValue2 {  
   [switch_type("char"), switch_is(kind)] union {  
      [case(1), string]  
         wchar_t* wval;  
      [default, string]  
         char* val;  
   };  
   char kind;  
};  
```  
  
## <a name="example"></a>Ejemplo  
 Consulte la [caso](../windows/case-cpp.md) ejemplo para un ejemplo de uso de **switch_type**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`typedef`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   
