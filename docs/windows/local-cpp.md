---
title: local (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.local
dev_langs:
- C++
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3543adfe0cb25f7946e6ed6c81c4bd66a7b60324
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="local-c"></a>local (C++)
Cuando se utiliza en el encabezado de la interfaz, puede usar el compilador MIDL como un generador de encabezado. Cuando se utiliza en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
[local]  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El `local` atributo C++ tiene la misma funcionalidad que la [local](http://msdn.microsoft.com/library/windows/desktop/aa367071) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Vea [call_as](../windows/call-as.md) para obtener un ejemplo de cómo usar `local`.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`interface`, métodos de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|**dispinterface**|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de interfaz](../windows/interface-attributes.md)   
 [Atributos de método](../windows/method-attributes.md)   
 [call_as](../windows/call-as.md)   
