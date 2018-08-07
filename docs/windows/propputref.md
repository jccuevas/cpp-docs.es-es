---
title: propputref | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propputref
dev_langs:
- C++
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc11561401ff34b629fecdc31a00ffb845d6a2d8
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606805"
---
# <a name="propputref"></a>propputref
Especifica una función de la configuración de propiedad que utiliza una referencia en lugar de un valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[propputref]  
```  
  
## <a name="remarks"></a>Comentarios  
 El **propputref** atributo de C++ tiene la misma funcionalidad que el [propputref](http://msdn.microsoft.com/library/windows/desktop/aa367147) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [enlazable](../windows/bindable.md) para un ejemplo de uso de **propputref**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Método|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|`propget`, `propput`|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de método](../windows/method-attributes.md)   
 [propget](../windows/propget.md)   
 [propput](../windows/propput.md)   