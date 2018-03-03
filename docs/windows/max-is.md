---
title: max_is | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.max_is
dev_langs:
- C++
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d43ed06797ed79942a43612ab4c9ae774c4fcf17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="maxis"></a>max_is
Designa el valor máximo para un índice de matriz válida.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ max_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *expresión*  
 Una o varias expresiones de lenguaje C. Se permiten las ranuras de argumento vacío.  
  
## <a name="remarks"></a>Comentarios  
 El **max_is** atributo C++ tiene la misma funcionalidad que la [max_is](http://msdn.microsoft.com/library/windows/desktop/aa367074) atributo MIDL.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Campo de `struct` o **union**, la interfaz de parámetro, el método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|**size_is**|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [first_is](../windows/first-is.md) para obtener un ejemplo de cómo especificar una sección de una matriz.  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributos de parámetro](../windows/parameter-attributes.md)   
 [first_is](../windows/first-is.md)   
 [last_is](../windows/last-is.md)   
 [length_is](../windows/length-is.md)   
 [size_is](../windows/size-is.md)   
