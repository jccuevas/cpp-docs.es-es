---
title: cadena (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.string
dev_langs:
- C++
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6bdcdc6557253f8be9c6ecb20300f2338ab35d07
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889025"
---
# <a name="string-c"></a>string (C++)
Indica que unidimensional `char`, `wchar_t`, **bytes** (o equivalente) matriz o el puntero a una matriz de este tipo debe tratarse como una cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
[string]  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El **cadena** atributo C++ tiene la misma funcionalidad que la [cadena](http://msdn.microsoft.com/library/windows/desktop/aa367270) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo utilizar **cadena** en una interfaz y en una definición de tipo:  
  
```  
// cpp_attr_ref_string.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export, string] typedef char a[21];  
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   [id(1)] HRESULT Method3([in, string] char *pC);  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Matriz o un puntero a una matriz, el parámetro de interfaz, el método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de la matriz](../windows/array-attributes.md)   
 [export](../windows/export.md)   
