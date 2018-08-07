---
title: retval | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.retval
dev_langs:
- C++
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d6f17f44e520018f82dc82abe88427a2410d68e7
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606356"
---
# <a name="retval"></a>retval
Designa el parámetro que recibe el valor devuelto del miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[retval]  
```  
  
## <a name="remarks"></a>Comentarios  
 El **retval** atributo de C++ tiene la misma funcionalidad que el [retval](http://msdn.microsoft.com/library/windows/desktop/aa367158) atributo MIDL.  
  
 **retval** debe aparecer en el último argumento en la declaración de una función.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [enlazable](../windows/bindable.md) para un ejemplo de uso de **retval**.  
  
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