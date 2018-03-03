---
title: entrada | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.entry
dev_langs:
- C++
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9ffd90ccdcce39ab73f1c1b550b466541dacf8a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="entry"></a>entry
Especifica una función exportada o constante en un módulo mediante la identificación de punto de entrada en el archivo DLL.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ entry(  
   id  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `id`  
 El identificador del punto de entrada.  
  
## <a name="remarks"></a>Comentarios  
 El **entrada** atributo C++ tiene la misma funcionalidad que la [entrada](http://msdn.microsoft.com/library/windows/desktop/aa366815) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [idl_module](../windows/idl-module.md) para un ejemplo del uso de **entrada**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Atributo `idl_module`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
