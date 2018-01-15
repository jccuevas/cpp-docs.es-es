---
title: Id. | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.id
dev_langs: C++
helpviewer_keywords: id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9225a87f32c3c7bf42ca5fc7de98dd0ab8f12639
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="id"></a>id
Especifica un `dispid` parámetro para una función miembro (una propiedad o un método en una interfaz o dispinterface).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ id(  
   dispid  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dispid`  
 El identificador de envío para el método de interfaz.  
  
## <a name="remarks"></a>Comentarios  
 El **Id. de** atributo C++ tiene la misma funcionalidad que la [identificador](http://msdn.microsoft.com/library/windows/desktop/aa367040) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [enlazables](../windows/bindable.md) para obtener un ejemplo de cómo usar **identificador**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de método](../windows/method-attributes.md)   
 [Atributos de miembro de datos](../windows/data-member-attributes.md)   
 [DefaultValue](../windows/defaultvalue.md)   
 [in (Modificador genérico)](../windows/in-cpp.md)   
 [out](../windows/out-cpp.md)   
