---
title: ReadOnly (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.readonly
dev_langs:
- C++
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05a46e099643602867aaa807e915e419054a8d60
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016010"
---
# <a name="readonly-c"></a>readonly (C++)
Prohíbe la asignación a un miembro de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
[readonly]  
```  
  
## <a name="remarks"></a>Comentarios  
 El atributo de C++ **readonly** tiene la misma funcionalidad que el atributo MIDL [readonly](http://msdn.microsoft.com/library/windows/desktop/aa367152) .  
  
 Si quiere prohibir la modificación de un parámetro de método, use el atributo [in](../windows/in-cpp.md) .  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra el uso del atributo **readonly** :  
  
```cpp  
// cpp_attr_ref_readonly.cpp  
// compile with: /LD  
[idl_quote("midl_pragma warning(disable:2461)")];  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
  
[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]  
__interface IFireTabCtrl  
{  
   [readonly, id(1)] int i();  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de miembros de datos](../windows/data-member-attributes.md)   