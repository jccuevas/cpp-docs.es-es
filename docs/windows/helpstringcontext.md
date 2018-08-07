---
title: helpstringcontext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringcontext
dev_langs:
- C++
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 16f113610beb4c6427af5627ea8dfd725e02600d
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570004"
---
# <a name="helpstringcontext"></a>helpstringcontext
Especifica el identificador de un tema de ayuda en un archivo .hlp o chm.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[ helpstringcontext(  
   contextID  
) ]  
```  
  
### <a name="parameters"></a>Parámetros  
 *contextID*  
 Un identificador de contexto de Ayuda de 32 bits en el archivo de ayuda.  
  
## <a name="remarks"></a>Comentarios  
 El **helpstringcontext** atributo de C++ tiene la misma funcionalidad que el [helpstringcontext](http://msdn.microsoft.com/library/windows/desktop/aa366858) ODL (atributo).  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// cpp_attr_ref_helpstringcontext.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[   object,   
   helpstring("help string"),   
   helpstringcontext(1),   
   uuid="11111111-1111-1111-1111-111111111111"  
]  
__interface IMyI   
{  
   HRESULT xx();  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, **interfaz**, método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de interfaz](../windows/interface-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
 [Atributos de método](../windows/method-attributes.md)   
 [módulo](../windows/module-cpp.md)   