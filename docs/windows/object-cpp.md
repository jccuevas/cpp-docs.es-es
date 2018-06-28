---
title: objeto (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.object
dev_langs:
- C++
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 601d67fb48f0ae826474d33e7dca0fbffff9478c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879713"
---
# <a name="object-c"></a>object (C++)
Identifica una interfaz personalizada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
[object]  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando precede a una definición de interfaz, el **objeto** atributo C++ hace que la interfaz que se colocarán en el archivo .idl como una interfaz personalizada.  
  
 Cualquier interfaz marcada con el objeto debe heredar de **IUnknown**. Esta condición se cumple si cualquiera de las interfaces base se hereda de **IUnknown**. Si no hay ninguna interfaz base se hereda de **IUnknown**, el compilador hará que la interfaz marcada con **objeto** pueden derivar **IUnknown**.  
  
## <a name="example"></a>Ejemplo  
 Vea [nonbrowsable](../windows/nonbrowsable.md) para obtener un ejemplo de cómo usar **objeto**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`interface`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de interfaz](../windows/interface-attributes.md)   
 [Doble](../windows/dual.md)   
 [Dispinterface](../windows/dispinterface.md)   
 [Personalizada](../windows/custom-cpp.md)   
 [__interface](../cpp/interface.md)   
