---
title: v1_enum | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.v1_enum
dev_langs:
- C++
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b3156554f5d2b799a9e1ef5a067d1f2e8e600d38
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890666"
---
# <a name="v1enum"></a>v1_enum
Indica que el tipo enumerado especificado se transmiten como una entidad de 32 bits en lugar de con el valor predeterminado de 16 bits.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
[v1_enum]  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El **v1_enum** atributo C++ tiene la misma funcionalidad que la [v1_enum](http://msdn.microsoft.com/library/windows/desktop/aa367303) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra un uso de **v1_enum**:  
  
```  
// cpp_attr_ref_v1_enum.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export, v1_enum]   
enum eList {   
   e1 = 1,   
   e2 = 2  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Tipo enumerado|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Typedef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
