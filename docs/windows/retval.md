---
title: retval | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.retval
dev_langs:
- C++
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cf7aa0cf8dd9767f603807ee18e23fe02d3446c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="retval"></a>retval
Designa el parámetro que recibe el valor devuelto del miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
[retval]  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El **retval** atributo C++ tiene la misma funcionalidad que la [retval](http://msdn.microsoft.com/library/windows/desktop/aa367158) atributo MIDL.  
  
 **retval** debe aparecer en el último argumento en la declaración de una función.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [enlazables](../windows/bindable.md) para un ejemplo de uso de **retval**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Parámetro de interfaz, el método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|**out**|  
|**Atributos no válidos**|**in**|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de parámetro](../windows/parameter-attributes.md)   
 [Atributos de método](../windows/method-attributes.md)   
