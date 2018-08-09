---
title: size_is | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.size_is
dev_langs:
- C++
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c6b5309d62db094bf706fe7d3d1bcec99c3ec9a9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645456"
---
# <a name="sizeis"></a>size_is
Especifique el tamaño de memoria asignada para los punteros de tamaño, tamaño punteros a punteros de tamaño y solo - o matrices multidimensionales.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[ size_is(  
   "expression"  
) ]  
```  
  
### <a name="parameters"></a>Parámetros  
 *Expresión*  
 El tamaño de memoria asignada para un tamaño punteros.  
  
## <a name="remarks"></a>Comentarios  
 El **size_is** atributo de C++ tiene la misma funcionalidad que el [size_is](http://msdn.microsoft.com/library/windows/desktop/aa367164) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [first_is](../windows/first-is.md) para obtener un ejemplo de cómo especificar una sección de una matriz.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Campo de **struct** o **unión**, parámetro de interfaz, el método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|`max_is`|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributos de parámetro](../windows/parameter-attributes.md)   
 [first_is](../windows/first-is.md)   
 [last_is](../windows/last-is.md)   
 [max_is](../windows/max-is.md)   
 [length_is](../windows/length-is.md)   