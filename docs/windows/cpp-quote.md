---
title: cpp_quote | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.cpp_quote
dev_langs: C++
helpviewer_keywords: cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cc91c884bb58ce21e4419a8082f15792a0fc2246
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cppquote"></a>cpp_quote
Emite la cadena especificada, sin los caracteres de comillas, en el archivo .idl generado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ cpp_quote(  
   "statement"  
) ];  
```  
  
#### <a name="parameters"></a>Parámetros  
 *statement*  
 Una instrucción de C.  
  
## <a name="remarks"></a>Comentarios  
 El **cpp_quote** atributo de C++ es útil si desea colocar una directiva de preprocesador en un archivo IDL.  
  
 También puede usar **cpp_quote** y generar un archivo .h como parte de la compilación de MIDL. Por ejemplo, si tiene un archivo de encabezado de C++ que utiliza atributos IDL de C++ pero no puede utilizar este archivo para alguna tarea, a continuación, puede compilar para crear un archivo .h generados por MIDL, que debe ser capaz de usar.  
  
 El **cpp_quote** atributo tiene la misma funcionalidad que la [cpp_quote](http://msdn.microsoft.com/library/windows/desktop/aa366765) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [dual](../windows/dual.md) para obtener un ejemplo, usar cómo usar **cpp_quote**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|En cualquier lugar|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos independientes](../windows/stand-alone-attributes.md)   
