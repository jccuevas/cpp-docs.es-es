---
title: "idl_module | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.idl_module"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "idl_module attribute"
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# idl_module
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica un punto de entrada en un archivo .dll.  
  
## Sintaxis  
  
```  
  
      [ idl_module (   
   name=module_name,   
   dllname=dll,   
   uuid="uuid",   
   helpstring="help text",   
   helpstringcontext=helpcontextID,   
   helpcontext=helpcontext,   
   hidden,   
   restricted  
) ]  
function declaration  
```  
  
#### Parámetros  
 **nombre**  
 Un nombre definido por el usuario para el bloque de código que aparecerá en el archivo .idl.  
  
 **dllname** \(opcional\)  
 El archivo .dll que contiene la exportación.  
  
 `uuid` \(opcional\)  
 Identificador único.  
  
 **helpstring** \(opcional\)  
 Una cadena de caracteres que se usa para describir la biblioteca de tipos.  
  
 **helpstringcontext** \(opcional\)  
 El identificador de un tema de Ayuda en un archivo de .hlp o .chm.  
  
 **helpcontext** \(opcional\)  
 El identificador de Ayuda para esta biblioteca de tipos.  
  
 **Oculto** \(opcional\)  
 Un parámetro que evita que la biblioteca se mostrará.  Vea el atributo de [Oculto](http://msdn.microsoft.com/library/windows/desktop/aa366861) MIDL para obtener más información.  
  
 ***Restringido***  \(opcional\)  
 Los miembros de la biblioteca no pueden ser llamados arbitrariamente.  Vea el atributo de [Restringido](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL para obtener más información.  
  
 *declaración de función*  
 La función que definirá.  
  
## Comentarios  
 El atributo de `idl_module` C\+\+ permite especificar el punto de entrada en un archivo .dll, que permite importar de un archivo .dll.  
  
 El atributo de **idl\_module** tiene funcionalidad similar al atributo de [módulo](http://msdn.microsoft.com/library/windows/desktop/aa367099) MIDL.  
  
 Puede exportar desde un objeto COM que puede exportar desde un archivo .dll colocando un punto de entrada de DLL en el bloque de la biblioteca de un archivo .idl.  
  
 el uso `idl_module` de la necesidad en dos pasos.  Primero, debe definir un par de nombre\/DLL.  A continuación, cuando usa `idl_module` para especificar un punto de entrada, especifique el nombre y cualquier atributo adicional.  
  
## Ejemplo  
 el código siguiente muestra cómo utilizar el atributo de `idl_module` :  
  
```  
// cpp_attr_ref_idl_module.cpp  
// compile with: /LD  
[idl_quote("midl_pragma warning(disable:2461)")];  
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];  
[idl_module(name="MyLib"), entry(4), usesgetlasterror]  
void FuncName(int i);  
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
 [entry](../windows/entry.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)