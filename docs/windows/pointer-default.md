---
title: pointer_default | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pointer_default
dev_langs:
- C++
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98e3b9e78f46b14dfeca18a8e69538111d3ba219
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010320"
---
# <a name="pointerdefault"></a>pointer_default
Especifica el atributo de puntero predeterminado para todos los punteros, excepto los punteros de nivel superior que aparecen en las listas de parámetros.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
[ pointer_default(  
   value  
) ]  
```  
  
### <a name="parameters"></a>Parámetros  
 *valor*  
 Un valor que describe el tipo de puntero: **ptr**, **ref**, o **único**.  
  
## <a name="remarks"></a>Comentarios  
 El **pointer_default** atributo de C++ tiene la misma funcionalidad que el [pointer_default](http://msdn.microsoft.com/library/windows/desktop/aa367141) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [defaultvalue](../windows/defaultvalue.md) para un ejemplo de uso de **pointer_default**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**interface**|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de interfaz](../windows/interface-attributes.md)   