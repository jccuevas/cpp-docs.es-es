---
title: HelpContext | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpcontext
dev_langs:
- C++
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 317e204c7292c4a7cccb1f81f6bc9d2a2fbfd407
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="helpcontext"></a>helpcontext
Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el archivo de ayuda.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ helpcontext(  
   id  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `id`  
 El identificador de contexto del tema de ayuda. Vea [ayuda HTML: ayuda contextual para los programas](../mfc/html-help-context-sensitive-help-for-your-programs.md) para obtener más información sobre identificadores de contexto.  
  
## <a name="remarks"></a>Comentarios  
 El **helpcontext** atributo C++ tiene la misma funcionalidad que la [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [defaultvalue](../windows/defaultvalue.md) para obtener un ejemplo de cómo usar **helpcontext**.  
  
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
 [helpstring](../windows/helpstring.md)   
