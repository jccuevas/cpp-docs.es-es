---
title: last_is | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.last_is
dev_langs:
- C++
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0519409e71457ca025318a591772faf33592abe
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606073"
---
# <a name="lastis"></a>last_is
Especifica el índice del último elemento de matriz que se transmitan.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[ last_is(  
   "expression"  
) ]  
```  
  
### <a name="parameters"></a>Parámetros  
 *Expresión*  
 Una o varias expresiones de lenguaje C. Se permiten las ranuras de argumentos vacía.  
  
## <a name="remarks"></a>Comentarios  
 El **last_is** atributo de C++ tiene la misma funcionalidad que el [last_is](http://msdn.microsoft.com/library/windows/desktop/aa367066) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Consulte [first_is](../windows/first-is.md) para obtener un ejemplo de cómo especificar una sección de una matriz.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Campo de **struct** o **unión**, parámetro de interfaz, el método de interfaz|  
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
 [length_is](../windows/length-is.md)   
 [size_is](../windows/size-is.md)   