---
title: dispinterface | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.dispinterface
dev_langs: C++
helpviewer_keywords: dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cf7fb54b4059bc56aea967f03b9e4c2874f84e82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dispinterface"></a>dispinterface
Coloca una interfaz en el archivo .idl como interfaz de envío.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
[dispinterface]  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando el atributo de C++ **dispinterface** precede a una interfaz, hace que esta se coloque dentro del bloque de biblioteca del archivo .idl generado.  
  
 A menos que especifique una clase base, se derivará una interfaz de envío de `IDispatch`. Debe especificar un [id](../windows/id.md) para los miembros de una interfaz de envío.  
  
 El ejemplo de uso de [dispinterface](http://msdn.microsoft.com/library/windows/desktop/aa366802) en la documentación de MIDL:  
  
```  
dispinterface helloPro   
   { interface hello; };   
```  
  
 no es válido para el atributo **dispinterface** .  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo de [bindable](../windows/bindable.md) para ver un ejemplo de cómo usar **dispinterface**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`interface`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|**dual**, **object**, **oleautomation**, `local`, **ms_union**|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos por uso](../windows/attributes-by-usage.md)   
 [UUID](../windows/uuid-cpp-attributes.md)   
 [dual](../windows/dual.md)   
 [personalizado](../windows/custom-cpp.md)   
 [object](../windows/object-cpp.md)   
 [__interface](../cpp/interface.md)   
