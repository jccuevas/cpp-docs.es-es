---
title: HelpContext | Microsoft Docs
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
ms.openlocfilehash: 2089bca316fb37304765ac14475b73cadaf79342
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571365"
---
# <a name="helpcontext"></a>helpcontext
Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el archivo de ayuda.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[ helpcontext(  
   id  
) ]  
```  
  
### <a name="parameters"></a>Parámetros  
 *identificador*  
 Identificador de contexto del tema de ayuda. Consulte [ayuda HTML: ayuda contextual para los programas](../mfc/html-help-context-sensitive-help-for-your-programs.md) para obtener más información sobre identificadores de contexto.  
  
## <a name="remarks"></a>Comentarios  
 El **helpcontext** atributo de C++ tiene la misma funcionalidad que el [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [defaultvalue](../windows/defaultvalue.md) para obtener un ejemplo de cómo usar **helpcontext**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**interfaz**, **typedef**, **clase**, método, propiedad|  
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