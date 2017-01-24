---
title: "import | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.import"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "import attribute"
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# import
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica otro .idl, .odl, o archivo de encabezado que contiene definiciones que desee hacer referencia IDL principal.  
  
## Sintaxis  
  
```  
  
      [ import(  
   idl_file  
) ];  
```  
  
#### Parámetros  
 `idl_file`  
 El nombre de un archivo .idl que desea importar en la biblioteca de tipos del proyecto actual.  
  
## Comentarios  
 El atributo de **importación** C\+\+ genera una instrucción de `#import` se coloque debajo de la instrucción de `import "docobj.idl"` en el archivo generado .idl.  el atributo de **importación** tiene la misma funcionalidad que el atributo de [importación](http://msdn.microsoft.com/library/windows/desktop/aa367047) MIDL.  
  
 El atributo de **importación** sólo coloca el archivo especificado en el archivo .idl que generará el proyecto; el atributo de **importación** no permite llamar a construcciones del archivo especificado de código fuente del proyecto.  Para llamar a construcciones del archivo especificado de código fuente del proyecto, el uso [\#import](../preprocessor/hash-import-directive-cpp.md) y el atributo de `embedded_idl` o puede incluir el archivo .h para `idl_file`, si existe un archivo .h.  
  
## Ejemplo  
 el código siguiente:  
  
```  
// cpp_attr_ref_import.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[import(import.idl)];  
```  
  
 muestra el código siguiente en el archivo generado .idl:  
  
```  
import "docobj.idl";  
import "import.idl";  
  
[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]  
library MyLib {  
   importlib("stdole2.tlb");  
   importlib("olepro32.dll");  
...  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Cualquier parte|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../Topic/Stand-Alone%20Attributes.md)   
 [importidl](../windows/importidl.md)   
 [importlib](../windows/importlib.md)   
 [include](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)