---
title: importar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.import
dev_langs:
- C++
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 011cabb37f388d4be6a9a69f685a7c711f0209a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="import"></a>importación
Especifica otro archivo de encabezado, .odl o .idl que contiene las definiciones que desea hacer referencia desde la principal IDL.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ import(  
   idl_file  
) ];  
```  
  
#### <a name="parameters"></a>Parámetros  
 `idl_file`  
 El nombre de un archivo .idl que desea importar en la biblioteca de tipos del proyecto actual.  
  
## <a name="remarks"></a>Comentarios  
 El **importar** C++ atributo da lugar a un `#import` instrucción que se coloca debajo del `import "docobj.idl"` instrucción en el archivo .idl generado. El **importar** atributo tiene la misma funcionalidad que la [importar](http://msdn.microsoft.com/library/windows/desktop/aa367047) atributo MIDL.  
  
 El **importar** atributo sólo coloca el archivo especificado en el archivo .idl que se generará el proyecto; el **importar** atributo no permite llamar a las construcciones en el archivo especificado desde el código fuente en el proyecto.  Para llamar a las construcciones en el archivo especificado desde el código fuente del proyecto, utilice [#import](../preprocessor/hash-import-directive-cpp.md) y `embedded_idl` atributo o se puede incluir el archivo .h para el `idl_file`, si existe un archivo .h.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente:  
  
```  
// cpp_attr_ref_import.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[import(import.idl)];  
```  
  
 produce el siguiente código en el archivo .idl generado:  
  
```  
import "docobj.idl";  
import "import.idl";  
  
[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]  
library MyLib {  
   importlib("stdole2.tlb");  
   importlib("olepro32.dll");  
...  
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
 [importidl](../windows/importidl.md)   
 [importlib](../windows/importlib.md)   
 [incluir](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)   
