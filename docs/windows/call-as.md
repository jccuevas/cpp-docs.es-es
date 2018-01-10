---
title: call_as | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.call_as
dev_langs: C++
helpviewer_keywords: call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3df1cd801a82533592594618742b7727051bde53
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="callas"></a>call_as
Permite un [local](../windows/local-cpp.md) función que debe asignarse a una función remota para que cuando se llama a la función remota, se invoca la función local.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ call_as(  
   function  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *function*  
 La función local que desea que se llamará cuando se invoque una función remota.  
  
## <a name="remarks"></a>Comentarios  
 El **call_as** atributo C++ tiene la misma funcionalidad que la [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo puede usar **call_as** para asignar una función utilizables (**f1**) a una función remoto (**Remf1**):  
  
```  
// cpp_attr_ref_call_as.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
[dual, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMInterface {  
   [local] HRESULT f1 ( int i );  
   [call_as(f1)] HRESULT Remf1 ( int i );   
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
 [Atributos de método](../windows/method-attributes.md)   
 [local](../windows/local-cpp.md)   
