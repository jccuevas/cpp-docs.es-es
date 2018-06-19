---
title: length_is | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.length_is
dev_langs:
- C++
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6d41c2c4747f69b5ddfae4cd5863c072cd2316ec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879612"
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
 *Expresión*  
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
