---
title: "Method Attributes | Microsoft Docs"
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
  - "method attributes"
  - "attributes [C++], reference topics"
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Method Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los atributos siguientes se aplican a los métodos de una clase, una coclase, o interfaz.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|[bindable](../windows/bindable.md)|Indica que la propiedad admite enlace de datos.|  
|[call\_as](../windows/call-as.md)|Permite a una función de uso no remoto que se va a asignar a una función remota.|  
|[custom](../windows/custom-cpp.md)|Permite definir dispone de atributo.|  
|[db\_column](../windows/db-column.md)|Enlaza una columna especificada al conjunto de filas.|  
|[db\_command](../windows/db-command.md)|Crea un comando OLE DB.|  
|[db\_param](../windows/db-param.md)|Asociado a la variable miembro especificada a una entrada o parámetro de salida y delimita la variable.|  
|[db\_source](../windows/db-source.md)|crea una conexión a un origen de datos.|  
|[db\_table](../windows/db-table.md)|Abra una tabla de OLE DB.|  
|[defaultbind](../windows/defaultbind.md)|Indica la propiedad única, enlazable que mejor representa el objeto.|  
|[defaultcollelem](../windows/defaultcollelem.md)|Se utiliza para la optimización del código de Visual Basic.|  
|[displaybind](../windows/displaybind.md)|Indica una propiedad que se debe mostrar al usuario como enlazable.|  
|[helpcontext](../windows/helpcontext.md)|Especifica un Id. de contexto que deje la información de la vista de usuario sobre este elemento en el archivo de Ayuda.|  
|[helpfile](../Topic/helpfile.md)|Establece el nombre del archivo de Ayuda para una biblioteca de tipos.|  
|[helpstring](../windows/helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Especifica el identificador de un tema de Ayuda en un archivo de .hlp o .chm.|  
|[helpstringdll](../windows/helpstringdll.md)|Especifica el nombre de DLL para utilizar para realizar la búsqueda de la cadena del documento \(localización\).|  
|[hidden](../Topic/hidden.md)|Indica que el elemento existe pero no se debe mostrar en un explorador del usuario.|  
|[id](../windows/id.md)|Especifica un DISPID para una función miembro \(una propiedad o método, en una interfaz o dispinterface\).|  
|[immediatebind](../windows/immediatebind.md)|Indica que la base de datos se notifique inmediatamente de todos los cambios de una propiedad de un objeto enlazado a datos.|  
|[in](../Topic/in%20\(C++\).md)|Indica que un parámetro debe ser el último procedimiento de llamada al procedimiento.|  
|[local](../windows/local-cpp.md)|Permite utilizar el compilador MIDL como generador de encabezado cuando se usa en el encabezado de la interfaz.  Cuando se utiliza en una función individual, elija un procedimiento local para el que no se genera ningún códigos auxiliares.|  
|[nonbrowsable](../Topic/nonbrowsable.md)|Indica que un miembro de interfaz no debería mostrarse en un explorador de propiedades.|  
|[propget](../windows/propget.md)|Especifica una función de descriptor de acceso de la propiedad.|  
|[propput](../windows/propput.md)|Especifica una función de la configuración de propiedades.|  
|[propputref](../windows/propputref.md)|Especifica una función de la configuración de propiedades que utilice una referencia en lugar de un valor.|  
|[PTR](../windows/ptr.md)|Elija un puntero como puntero completo.|  
|[intervalo](../Topic/range%20\(C++\).md)|Especifica un intervalo de valores permitidos para los argumentos o campos cuyos valores se establecen en tiempo de ejecución.|  
|[requestedit](../windows/requestedit.md)|indica que la propiedad admite la notificación de **OnRequestEdit** .|  
|[restricted](../windows/restricted.md)|Especifica que un miembro de módulo, interfaz, o de dispinterface no puede ser llamado arbitrariamente.|  
|[satype](../windows/satype.md)|especifica el tipo de datos de la estructura de **SAFEARRAY** .|  
|[source](../Topic/source%20\(C++\).md)|Especifica las interfaces del origen del control para los puntos de conexión en una clase.  En una propiedad o método, el atributo de **origen** indica que el miembro devuelve un objeto o un VARIANT que son un origen de eventos.|  
|[sincronizar](../windows/synchronize.md)|Sincronizar el acceso al método de destino.|  
|[vararg](../windows/vararg.md)|especifica que la función toma un número variable de argumentos.|  
  
## Vea también  
 [Attributes by Usage](../windows/attributes-by-usage.md)