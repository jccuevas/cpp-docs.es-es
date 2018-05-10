---
title: helpstringdll | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringdll
dev_langs:
- C++
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d7cb3ab5fc624494d3292cd7a47031782ce7da70
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="helpstringdll"></a>helpstringdll
Especifica el nombre de la DLL a utilizar para realizar la búsqueda de cadena de documento (localización).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ helpstringdll(  
   "string"  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `string`  
 DLL que se va a utilizar para realizar la búsqueda de cadena de documento.  
  
## <a name="remarks"></a>Comentarios  
 El **helpstringdll** atributo C++ tiene la misma funcionalidad que la [helpstringdll](http://msdn.microsoft.com/library/windows/desktop/aa366860) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cpp_attr_ref_helpstringdll.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib", helpstringdll="xx.dll")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI   
{  
   HRESULT xxx();  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `interface`, métodos de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de interfaz](../windows/interface-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
 [Atributos de método](../windows/method-attributes.md)   
