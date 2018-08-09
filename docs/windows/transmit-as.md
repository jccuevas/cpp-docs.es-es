---
title: transmit_as | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.transmit_as
dev_langs:
- C++
helpviewer_keywords:
- transmit_as attribute
ms.assetid: 53d0b8ab-5b06-423e-83eb-3d01a10424b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c1e1ecfb118fb391cf392b411a4664513972ed42
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642530"
---
# <a name="transmitas"></a>transmit_as
Indica al compilador para asociar un tipo presentado que manipulan las aplicaciones cliente y servidor, con un tipo transmitido.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[ transmit_as(  
   type  
) ]  
```  
  
### <a name="parameters"></a>Parámetros  
 *type*  
 Especifica el tipo de datos que se transmite entre el cliente y servidor.  
  
## <a name="remarks"></a>Comentarios  
 El **transmit_as** atributo de C++ tiene la misma funcionalidad que el [transmit_as](http://msdn.microsoft.com/library/windows/desktop/aa367286) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra un uso de la **transmit_as** atributo:  
  
```cpp  
// cpp_attr_ref_transmit_as.cpp  
// compile with: /LD  
#include "windows.h"  
[module(name="MyLibrary")];  
  
[export] typedef struct _TREE_NODE_TYPE {  
unsigned short data;   
struct _TREE_NODE_TYPE * left;  
struct _TREE_NODE_TYPE * right;   
} TREE_NODE_TYPE;  
  
[export] struct PACKED_NODE {  
   unsigned short data;   // same as normal node  
   int index;   // array index of parent  
};  
  
// A left node recursive built array of  
// the nodes in the tree.  Can be unpacked with  
// that knowledge  
[export] typedef struct _TREE_XMIT_TYPE {  
   int count;  
   [size_is(count)] PACKED_NODE node[];  
} TREE_XMIT_TYPE;  
  
[transmit_as(TREE_XMIT_TYPE)] typedef TREE_NODE_TYPE * TREE_TYPE;  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**typedef**|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   