---
title: importlib | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.importlib
dev_langs: C++
helpviewer_keywords: importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 27c74785f56d7cb339eff25a645191ece1e14b32
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="importlib"></a>importlib
Hace que los tipos que ya se han compilado en otra biblioteca de tipos estén disponibles en la biblioteca de tipos que se está creando.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ importlib(  
   "tlb_file"  
) ];  
```  
  
#### <a name="parameters"></a>Parámetros  
 *tlb_file*  
 El nombre de un archivo .tlb, entre comillas, que desea importar en la biblioteca de tipos del proyecto actual.  
  
## <a name="remarks"></a>Comentarios  
 El **importlib** C++ atributo da lugar a un `importlib` instrucción que se colocarán en el bloque de biblioteca del archivo .idl generado. El **importlib** atributo tiene la misma funcionalidad que la [importlib](http://msdn.microsoft.com/library/windows/desktop/aa367050) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra un ejemplo de cómo usar **importlib**:  
  
```  
// cpp_attr_ref_importlib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importlib("importlib.tlb")];  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|En cualquier lugar|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos de compilador](../windows/compiler-attributes.md)   
 [Atributos independientes](../windows/stand-alone-attributes.md)   
 [importar](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [incluir](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)