---
title: ref (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.ref
dev_langs:
- C++
helpviewer_keywords:
- ref attribute
ms.assetid: 67e82d3e-07d9-4ef8-bf2b-0a4491d12557
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f266c263fea33254cb8b0c706982a6d2453eed97
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881476"
---
# <a name="ref-c"></a>ref (C++)
Identifica un puntero de referencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
[ref]  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El `ref` atributo C++ tiene la misma funcionalidad que la [ref](http://msdn.microsoft.com/library/windows/desktop/aa367153) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo utilizar el `ref` atributo:  
  
```  
// cpp_attr_ref_ref.cpp  
// compile with: /LD  
#include <windows.h>   
[module(name="ATLFIRELib")];  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   [id(1), unique] char * GetFirstName([in, ref] char * pszFullName );   
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`typedef`, parámetro de interfaz, el método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributos de parámetro](../windows/parameter-attributes.md)   
