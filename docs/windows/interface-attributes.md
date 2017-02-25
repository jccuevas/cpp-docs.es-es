---
title: "Interface Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributes [C++], reference topics"
  - "interface attributes"
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Interface Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los atributos siguientes se aplican a la palabra clave de [interfaz \(o \_\_interface\)](../cpp/interface.md) C\+\+.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|[async\_uuid](../Topic/async_uuid.md)|Especifica el identificador UUID que indica al compilador de MIDL definir versiones sincrónicas y asincrónicas de una interfaz COM.|  
|[custom](../windows/custom-cpp.md)|Permite definir dispone de atributos.|  
|[dispinterface](../windows/dispinterface.md)|Coloca una interfaz en el archivo .idl como interfaz de envío.|  
|[dual](../Topic/dual.md)|Coloca una interfaz en el archivo .idl como interfaz dual.|  
|[export](../windows/export.md)|Genera una estructura de datos que se almacena en el archivo .idl.|  
|[helpcontext](../windows/helpcontext.md)|Especifica un Id. de contexto que deje la información de la vista de usuario sobre este elemento en el archivo de Ayuda.|  
|[helpfile](../Topic/helpfile.md)|Establece el nombre del archivo de Ayuda para una biblioteca de tipos.|  
|[helpstring](../windows/helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Especifica el identificador de un tema de Ayuda en un archivo de .hlp o .chm.|  
|[helpstringdll](../windows/helpstringdll.md)|Especifica el nombre de DLL para utilizar para realizar la búsqueda de la cadena del documento \(localización\).|  
|[hidden](../Topic/hidden.md)|Indica que el elemento existe pero no se debe mostrar en un explorador del usuario.|  
|[library\_block](../windows/library-block.md)|Coloca una construcción dentro del bloque de la biblioteca del archivo .idl.|  
|[local](../windows/local-cpp.md)|Permite utilizar el compilador MIDL como generador de encabezado cuando se usa en el encabezado de la interfaz.  Cuando se utiliza en una función individual, elija un procedimiento local para el que no se genera ningún códigos auxiliares.|  
|[nonextensible](../Topic/nonextensible.md)|Especifica que la implementación de `IDispatch` incluye únicamente las propiedades y los métodos mostrados en la descripción de la interfaz y no se puede extender con miembros adicionales en tiempo de ejecución.  Este atributo sólo es válido en una interfaz de [dual](../Topic/dual.md) .|  
|[odl](../windows/odl.md)|Identifica una interfaz como una interfaz \(ODL\) del Lenguaje de descripción de objetos.|  
|[Objeto.](../Topic/object%20\(C++\).md)|identifica una interfaz personalizada.|  
|[oleautomation](../windows/oleautomation.md)|Indica que una interfaz es compatible con automatización.|  
|[pointer\_default](../windows/pointer-default.md)|Especifica el atributo predeterminado de puntero para todos los punteros excepto los punteros de nivel superior que aparecen en listas de parámetros.|  
|[PTR](../windows/ptr.md)|Elija un puntero como puntero completo.|  
|[restricted](../windows/restricted.md)|Seleccione qué miembros de la biblioteca no pueden ser llamados arbitrariamente.|  
|[uuid](../windows/uuid-cpp-attributes.md)|proporciona el identificador único para la biblioteca|  
  
 Observará estas reglas para definir una interfaz:  
  
-   la convención de llamada predeterminada es [\_\_stdcall](../cpp/stdcall.md).  
  
-   GUID se proporciona automáticamente si no se proporciona uno.  
  
-   No se permite ningún métodos sobrecargados.  
  
 Cuando no se especifica el atributo de [uuid](../windows/uuid-cpp-attributes.md) y no utilizar el mismo nombre de interfaz en otro atributo proyectos, se genera el mismo GUID.  
  
## Vea también  
 [Attributes by Usage](../windows/attributes-by-usage.md)