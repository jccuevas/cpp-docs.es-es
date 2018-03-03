---
title: iid_is | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.iid_is
dev_langs:
- C++
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2caa675f222ad1e2940117c60eb5a83d6a4f976f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="iidis"></a>iid_is
Especifica el IID de la interfaz COM que señala un puntero de interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ iid_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *expresión*  
 Una expresión de lenguaje C que especifica un IID de una interfaz COM que señala un puntero de interfaz.  
  
## <a name="remarks"></a>Comentarios  
 El **iid_is** atributo C++ tiene la misma funcionalidad que la [iid_is](http://msdn.microsoft.com/library/windows/desktop/aa367044) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra el uso de **iid_is**:  
  
```  
// cpp_attr_ref_iid_is.cpp  
// compile with: /LD  
#include "wtypes.h"  
#include "unknwn.h"  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl : IDispatch  
{  
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]   
   IUnknown ** ppvObject);  
};  
  
[module(name="ATLFIRELib")];  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Parámetro de interfaz, miembro de datos|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de parámetro](../windows/parameter-attributes.md)   
