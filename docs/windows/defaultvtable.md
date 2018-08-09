---
title: defaultvtable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.defaultvtable
dev_langs:
- C++
helpviewer_keywords:
- defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 34850646e40ffa9cbd3185b13fdaa93d7c873787
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651445"
---
# <a name="defaultvtable"></a>defaultvtable
Define una interfaz que la interfaz de vtable predeterminada para un objeto COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
[ defaultvtable(  
   interface  
) ]  
```  
  
### <a name="parameters"></a>Parámetros  
 *interface*  
 La interfaz designada que se desea tener la vtable predeterminado para el objeto COM.  
  
## <a name="remarks"></a>Comentarios  
 El **defaultvtable** atributo de C++ tiene la misma funcionalidad que el [defaultvtable](http://msdn.microsoft.com/library/windows/desktop/aa366795) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra los atributos en una clase que utilice **defaultvtable** para especificar una interfaz predeterminada:  
  
```cpp  
// cpp_attr_ref_defaultvtable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI1 {  
   HRESULT x();  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000002")]  
__interface IMyI2 {  
   HRESULT x();  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000003")]  
__interface IMyI3 {  
   HRESULT x();  
};  
  
[coclass, source(IMyI3, IMyI1), default(IMyI3, IMyI2), defaultvtable(IMyI1),  
uuid("00000000-0000-0000-0000-000000000004")]  
class CMyC3 : public IMyI3 {};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, **struct**|  
|**Reiterativo**|No|  
|**Atributos requeridos**|**coclass**|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   