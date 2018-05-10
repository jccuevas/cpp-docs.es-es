---
title: versión (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.version
dev_langs:
- C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 43da63d75d3541915eba3e561ee08fe1048fa579
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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
