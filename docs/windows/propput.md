---
title: propput | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propput
dev_langs:
- C++
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 679b019c15d72586b5ca186e0b54c9a9172db53a
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608461"
---
# <a name="propput"></a>propput
Especifica una función de valor de propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[propput]  
```  
  
## <a name="remarks"></a>Comentarios  
 El **propput** atributo de C++ tiene la misma funcionalidad que el [propput](http://msdn.microsoft.com/library/windows/desktop/aa367146) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [enlazable](../windows/bindable.md) para un ejemplo de uso de **propput**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Método|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|`propget`, `propputref`|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de método](../windows/method-attributes.md)   
 [propget](../windows/propget.md)   
 [propputref](../windows/propputref.md)