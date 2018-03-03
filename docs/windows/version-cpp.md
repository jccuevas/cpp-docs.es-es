---
title: "versión (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.version
dev_langs:
- C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db6c31df932890799f68e2ae466b0a927f0f999f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="version-c"></a>version (C++)
Identifica una versión determinada entre varias versiones de una clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ version(  
   "version"  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *version*  
 El número de versión de la coclase. Si no se especifica, se colocará en el archivo .idl 1.0.  
  
## <a name="remarks"></a>Comentarios  
 El **versión** atributo C++ tiene la misma funcionalidad que la [versión](http://msdn.microsoft.com/library/windows/desktop/aa367306) atributo MIDL y se pasa a través del archivo .idl generado.  
  
## <a name="example"></a>Ejemplo  
 Consulte la [enlazables](../windows/bindable.md) ejemplo para un ejemplo de uso de **versión**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**class**, `struct`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|**coclass**|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos de compilador](../windows/compiler-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
