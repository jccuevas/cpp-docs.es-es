---
title: "emitidl | Microsoft Docs"
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
  - "vc-attr.emitidl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "emitidl attribute"
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# emitidl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Determina si todos los atributos siguientes IDL se procesarán y colocados en el archivo generado .idl.  
  
## Sintaxis  
  
```  
  
      [ emitidl([boolean],  
   defaultimports=[boolean]  
) ] ;  
```  
  
#### Parámetros  
 `boolean`  
 valores posibles: **TRUE**, **Falso**, **forzado**, **Restringido**, **inserción**, o **pop**.  
  
-   Si **TRUE**, algunos atributos de categoría IDL encontrados en un archivo de código fuente lo coloca en el archivo generado .idl.  Esta es la configuración predeterminada para **emitidl**.  
  
-   Si **Falso**, ningún atributo category IDL encontrada en un archivo de código fuente no está situado en el archivo generado .idl.  
  
-   Si **Restringido**, permite que los atributos IDL están en el archivo sin un atributo de [módulo](../windows/module-cpp.md) .  El compilador no generará un archivo .idl.  
  
-   Si **forzado**, reemplazar un atributo posterior de **Restringido** , que requiere un archivo tener un atributo de **módulo** si hay atributos IDL en el archivo.  
  
-   **inserción** permite guardar los valores actuales de **emitidl** una pila interna de **emitidl** , y **pop** permite **emitidl** establecido en el valor existente en la parte superior de la pila interna de **emitidl** .  
  
 **defaultimports** *\=*\[ `boolean`\] \(opcional\)  
 -   Si `boolean` es **TRUE**, docobj.idl se importará en el archivo generado .idl.  Además, si un archivo .idl con el mismo nombre que un archivo .h que le `#include` en el código fuente se encuentra en el mismo directorio que el archivo .h, el archivo generado .idl contendrá una instrucción import para el archivo .idl.  
  
-   Si `boolean` es **Falso**, docobj.idl no se importará en el archivo generado .idl.  Necesitará explícitamente importar archivos .idl con [importación](../windows/import.md).  
  
## Comentarios  
 Después de que el atributo de **emitidl** C\+\+ se encuentra en un archivo de código fuente, los atributos de la categoría IDL se colocarán en el archivo generado .idl.  Si no hay ningún atributo de **emitidl** , atributos IDL en el archivo de código fuente se generarán al archivo generado .idl.  
  
 Es posible tener varios atributos de **emitidl** en un archivo de código fuente.  Si `[emitidl(false)];` se encuentra en un archivo sin `[emitidl(true)];`subsiguiente, no se procesará ningún atributo en el archivo generado .idl.  
  
 Cada vez que el compilador encuentra un nuevo archivo, **emitidl** se establece implícitamente en **TRUE**.  
  
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
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Stand\-Alone Attributes](../Topic/Stand-Alone%20Attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)