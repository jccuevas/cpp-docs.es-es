---
title: nonextensible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 812f5e2462236faef1b2b13d5fb25320319e773e
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015734"
---
# <a name="nonextensible"></a>nonextensible
Especifica que el `IDispatch` implementación incluye solo las propiedades y los métodos enumeran en la descripción de la interfaz y no se pueden ampliar con miembros adicionales en tiempo de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
[nonextensible]  
```  
  
## <a name="remarks"></a>Comentarios  
 El **nonextensible** atributo de C++ tiene la misma funcionalidad que el [nonextensible](http://msdn.microsoft.com/library/windows/desktop/aa367120) atributo MIDL.  
  
 El uso de **nonextensible** también requiere la [oleautomation](../windows/oleautomation.md) atributo.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra un uso de la **nonextensible** atributo:  
  
```cpp  
// cpp_attr_ref_nonextensible.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export] typedef long HRESULT;  
  
[dual, nonextensible, ms_union, oleautomation,   
uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   HRESULT procedure (int i);   
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**interface**|  
|**Reiterativo**|No|  
|**Atributos requeridos**|`dual` y `oleautomation`, o `dispinterface`|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de interfaz](../windows/interface-attributes.md)   