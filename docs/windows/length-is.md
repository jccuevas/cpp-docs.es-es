---
title: length_is | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.length_is
dev_langs:
- C++
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a40132e793bc444547eefefa70ed3b146cafadc2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="lengthis"></a>length_is
Especifica el número de elementos de la matriz que se transmitan.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ length_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *expresión*  
 Una o varias expresiones de lenguaje C. Se permiten las ranuras de argumento vacío.  
  
## <a name="remarks"></a>Comentarios  
 El **length_is** atributo C++ tiene la misma funcionalidad que la [length_is](http://msdn.microsoft.com/library/windows/desktop/aa367068) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Vea [first_is](../windows/first-is.md) para obtener un ejemplo de cómo especificar una sección de una matriz.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Campo de `struct` o **union**, la interfaz de parámetro, el método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributos de parámetro](../windows/parameter-attributes.md)   
 [first_is](../windows/first-is.md)   
 [max_is](../windows/max-is.md)   
 [last_is](../windows/last-is.md)   
 [size_is](../windows/size-is.md)   
