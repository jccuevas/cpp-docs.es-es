---
title: max_is | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.max_is
dev_langs:
- C++
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 697eff3264c7e4a627086b072ae45b3c7ffedac2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878975"
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
 *Expresión*  
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
