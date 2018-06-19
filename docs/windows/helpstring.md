---
title: helpstring | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstring
dev_langs:
- C++
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 81a3e45c5636fd193b7880e093711b5cc584bf99
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879011"
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
