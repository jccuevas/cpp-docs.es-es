---
title: includelib (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.includelib
dev_langs:
- C++
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 252a5d953dd05edc494daf8c4a45322d5511f979
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878897"
---
# <a name="includelib-c"></a>includelib (C++)
Hace que un archivo IDL o .h para incluirse en el archivo .idl generado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ includelib(  
   name.idl  
) ];  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Name.idl*  
 El nombre del archivo .idl que desee incluir como parte del archivo .idl generado.  
  
## <a name="remarks"></a>Comentarios  
 El `includelib` C++ atributo da lugar a un archivo IDL o .h para incluirse en el archivo .idl generado, después de la `importlib` instrucción.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente se muestra en un archivo .cpp:  
  
```  
// cpp_attr_ref_includelib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[includelib("includelib.idl")];  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|En cualquier lugar|  
|**Reiterativo**|Sí|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos independientes](../windows/stand-alone-attributes.md)   
 [Importación](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [Incluir](../windows/include-cpp.md)   
 [importlib](../windows/importlib.md)   
