---
title: helpstring | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.helpstring
dev_langs:
- C++
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f3df545f5d87d36c26d999dc3a5fbee8720830c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="helpstring"></a>helpstring
Especifica una cadena de caracteres que se utiliza para describir el elemento al que se aplica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ helpstring(  
   "string"  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `string`  
 El texto de la cadena de ayuda.  
  
## <a name="remarks"></a>Comentarios  
 El **helpstring** atributo C++ tiene la misma funcionalidad que la [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [defaultvalue](../windows/defaultvalue.md) para obtener un ejemplo de cómo usar **helpstring**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`interface`, `typedef`, **clase**, método, propiedad|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de interfaz](../windows/interface-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
 [Atributos de método](../windows/method-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [HelpFile](../windows/helpfile.md)   
 [helpcontext](../windows/helpcontext.md)   
