---
title: en (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.in
dev_langs:
- C++
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8522b3af527267706a2e2697b88049a38b0f092f
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017196"
---
# <a name="in-c"></a>in (C++)
Indica que es un parámetro que se pasan desde el procedimiento que realiza la llamada al procedimiento llamado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
[in]  
```  
  
## <a name="remarks"></a>Comentarios  
 El **en** atributo de C++ tiene la misma funcionalidad que el [en](http://msdn.microsoft.com/library/windows/desktop/aa367051) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Consulte [enlazable](../windows/bindable.md) para obtener un ejemplo de cómo usar **en**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Parámetro de interfaz, el método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|**retval**|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de parámetro](../windows/parameter-attributes.md)   
 [Atributos de método](../windows/method-attributes.md)   
 [DefaultValue](../windows/defaultvalue.md)   
 [Id.](../windows/id.md)   
 [out](../windows/out-cpp.md)   