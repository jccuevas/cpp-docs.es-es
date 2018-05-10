---
title: incluir (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.include
dev_langs:
- C++
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a2c88dd610c1a0b8a8fee4e23da1b5ad844e989c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="include-c"></a>include (C++)
Especifica uno o más archivos de encabezado que se incluirá en el archivo .idl generado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ include(  
   header_file  
) ];  
```  
  
#### <a name="parameters"></a>Parámetros  
 *HEADER_FILE*  
 El nombre de un archivo que desee incluido en el archivo .idl generado.  
  
## <a name="remarks"></a>Comentarios  
 El **incluyen** C++ atributo da lugar a un `#include` instrucción que se coloca debajo del `import "docobj.idl"` instrucción en el archivo .idl generado.  
  
 El **incluyen** atributo C++ tiene la misma funcionalidad que la [incluyen](http://msdn.microsoft.com/library/windows/desktop/aa367052) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra un ejemplo de cómo usar **incluir**. En este ejemplo, el archivo include.h contiene solo un # instrucción include.  
  
```  
// cpp_attr_ref_include.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[include(cpp_attr_ref_include.h)];  
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
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos independientes](../windows/stand-alone-attributes.md)   
 [Importación](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [includelib](../windows/includelib-cpp.md)   
 [importlib](../windows/importlib.md)   
