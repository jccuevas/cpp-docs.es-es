---
title: pragma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pragma
dev_langs:
- C++
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a9c9d347b319afc3ee84818e74029a98b1aa5484
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014304"
---
# <a name="pragma"></a>pragma
Emite la cadena especificada en el archivo .idl generado sin el uso de comillas. 
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
[ pragma(  
   pragma_statement  
) ];  
```  
  
### <a name="parameters"></a>Parámetros  
 *pragma_statement*  
 La pragma que desea entrar en el archivo .idl generado.  
  
## <a name="remarks"></a>Comentarios  
 El **pragma** atributo de C++ tiene la misma funcionalidad que el [pragma](http://msdn.microsoft.com/library/windows/desktop/aa367143) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// cpp_attr_ref_pragma.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
[pragma(pack(4))];  
  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface A  
{  
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|En cualquier lugar|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos independientes](../windows/stand-alone-attributes.md)   
 [pack](../preprocessor/pack.md)   