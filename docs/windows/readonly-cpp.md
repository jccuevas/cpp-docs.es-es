---
title: ReadOnly (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.readonly
dev_langs: C++
helpviewer_keywords: readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 829ca2126ec43be54d96a98b2ada4f5952626e21
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="readonly-c"></a>readonly (C++)
Prohíbe la asignación a un miembro de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
[readonly]  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El atributo de C++ **readonly** tiene la misma funcionalidad que el atributo MIDL [readonly](http://msdn.microsoft.com/library/windows/desktop/aa367152) .  
  
 Si quiere prohibir la modificación de un parámetro de método, use el atributo [in](../windows/in-cpp.md) .  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra el uso del atributo **readonly** :  
  
```  
// cpp_attr_ref_readonly.cpp  
// compile with: /LD  
[idl_quote("midl_pragma warning(disable:2461)")];  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
  
[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]  
__interface IFireTabCtrl  
{  
   [readonly, id(1)] int i();  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de miembros de datos](../windows/data-member-attributes.md)   
