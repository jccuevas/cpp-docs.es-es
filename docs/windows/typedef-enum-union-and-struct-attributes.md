---
title: "Typedef, Enum, Union, and Struct Attributes | Microsoft Docs"
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
  - "union attributes"
  - "attributes [C++], reference topics"
  - "struct attributes"
  - "typedef attributes"
  - "enum attributes"
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Typedef, Enum, Union, and Struct Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los atributos siguientes se aplican a [typedef](http://msdn.microsoft.com/es-es/cc96cf26-ba93-4179-951e-695d1f5fdcf1), a [struct](../cpp/struct-cpp.md), y palabras clave de [enumeración](../cpp/enumerations-cpp.md) C\+\+.  
  
### definición de tipos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|[case](../windows/case-cpp.md)|utilizado con el atributo de [switch\_type](../windows/switch-type.md) en **union**.|  
|[custom](../windows/custom-cpp.md)|Permite definir dispone de atributo.|  
|[export](../windows/export.md)|Genera una estructura de datos que se almacena en el archivo .idl.|  
|[first\_is](../windows/first-is.md)|Especifica el índice del primer elemento de matriz que se transmitirá.|  
|[helpcontext](../windows/helpcontext.md)|Especifica un Id. de contexto que deje la información de la vista de usuario sobre este elemento en el archivo de Ayuda.|  
|[helpfile](../Topic/helpfile.md)|Establece el nombre del archivo de Ayuda para una biblioteca de tipos.|  
|[helpstring](../windows/helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|  
|[library\_block](../windows/library-block.md)|Coloca una construcción dentro del bloque de la biblioteca del archivo .idl.|  
|[PTR](../windows/ptr.md)|Elija un puntero como puntero completo.|  
|[public](../windows/public-cpp-attributes.md)|Garantiza que una definición entre la biblioteca de tipos aunque no se haga referencia dentro del archivo .idl.|  
|[ref](../windows/ref-cpp.md)|Identifica un puntero de referencia.|  
|[switch\_is](../windows/switch-is.md)|Especifica la expresión o el identificador que actúa como la combinación discriminante que selecciona a la union.|  
|[switch\_type](../windows/switch-type.md)|Identifica el tipo de la variable utilizada como unión discriminante.|  
|[único](../windows/unique-cpp.md)|especifica un puntero único.|  
|[wire\_marshal](../windows/wire-marshal.md)|Especifica un tipo de datos que se usará para la transmisión en lugar de un tipo de datos específico de la aplicación.|  
  
### enum  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|[custom](../windows/custom-cpp.md)|Permite definir dispone de atributo.|  
|[export](../windows/export.md)|Genera una estructura de datos que se almacena en el archivo .idl.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Especifica el identificador único para una clase o interfaz.|  
|[v1\_enum](../windows/v1-enum.md)|Dirige que transmiten al tipo enumerado especificado como entidad de 32 bits, en lugar del valor predeterminado de 16 bits.|  
  
### union  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|[custom](../windows/custom-cpp.md)|Permite definir dispone de atributo.|  
|[export](../windows/export.md)|Genera una estructura de datos que se almacena en el archivo .idl.|  
|[first\_is](../windows/first-is.md)|Especifica el índice del primer elemento de matriz que se transmitirá.|  
|[last\_is](../windows/last-is.md)|Especifica el índice del elemento de la matriz pasado que se transmitirá.|  
|[length\_is](../windows/length-is.md)|especifica el número de elementos de matriz que se transmitirán.|  
|[max\_is](../windows/max-is.md)|Indica el valor máximo de un índice válido de la matriz.|  
|[size\_is](../Topic/size_is.md)|Especifica el tamaño de memoria asignado para punteros ordenados, punteros a punteros ordenados, y solo ordenados o matrices multidimensionales.|  
|[único](../windows/unique-cpp.md)|especifica un puntero único.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Especifica el identificador único para una clase o interfaz.|  
  
### unión de Nonencapsulated  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|[ms\_union](../windows/ms-union.md)|controla la alineación de la representación de datos de la red de uniones nonencapsulated.|  
|[no\_injected\_text](../windows/no-injected-text.md)|Evita que el compilador inserte código como resultado de uso del atributo.|  
  
### struct  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|[aggregatable](../Topic/aggregatable.md)|indica que la clase admite la agregación.|  
|[agregados](../windows/aggregates.md)|Indica que un control agrega la clase de destino.|  
|[appobject](../Topic/appobject.md)|Identifica la coclase como objeto application, que está asociado a una aplicación completa .exe, e indica que las funciones y propiedades coclass son globalmente disponible en esta biblioteca de tipos.|  
|[CoClass](../windows/coclass.md)|crea un control ActiveX.|  
|[com\_interface\_entry](../Topic/com_interface_entry%20\(C++\).md)|Agrega una entrada de interfaz a un mapa COM.|  
|[Control](../windows/control.md)|especifica que el tipo definido por el usuario es un control.|  
|[custom](../windows/custom-cpp.md)|Permite definir dispone de atributo.|  
|[db\_column](../windows/db-column.md)|Enlaza una columna especificada al conjunto de filas.|  
|[db\_command](../windows/db-command.md)|Crea un comando OLE DB.|  
|[db\_param](../windows/db-param.md)|Asociado a la variable miembro especificada a una entrada o parámetro de salida y delimita la variable.|  
|[db\_source](../windows/db-source.md)|crea una conexión a un origen de datos.|  
|[db\_table](../windows/db-table.md)|Abra una tabla de OLE DB.|  
|[default](../windows/default-cpp.md)|Indica que la personalizado o el dispinterface definido dentro de una coclase representa la interfaz predeterminada de la programación.|  
|[defaultvtable](../windows/defaultvtable.md)|Define una interfaz como interfaz vtable predeterminada de un control.|  
|[event\_receiver](../windows/event-receiver.md)|Crea un receptor de eventos.|  
|[event\_source](../windows/event-source.md)|crea un origen de eventos.|  
|[export](../windows/export.md)|Genera una estructura de datos que se almacena en el archivo .idl.|  
|[first\_is](../windows/first-is.md)|Especifica el índice del primer elemento de matriz que se transmitirá.|  
|[hidden](../Topic/hidden.md)|Indica que el elemento existe pero no se debe mostrar en un explorador del usuario.|  
|[implements\_category](../Topic/implements_category.md)|Especifica implementó categorías componentes para la clase.|  
|[last\_is](../windows/last-is.md)|Especifica el índice del elemento de la matriz pasado que se transmitirá.|  
|[length\_is](../windows/length-is.md)|especifica el número de elementos de matriz que se transmitirán.|  
|[max\_is](../windows/max-is.md)|Indica el valor máximo de un índice válido de la matriz.|  
|[requires\_category](../windows/requires-category.md)|Especifica las categorías componentes necesarias de la clase de destino.|  
|[size\_is](../Topic/size_is.md)|Especifica el tamaño de memoria asignado para punteros ordenados, punteros a punteros ordenados, y solo ordenados o matrices multidimensionales.|  
|[source](../Topic/source%20\(C++\).md)|En una clase, especifica las interfaces del origen de objetos COM de los puntos de conexión.  En una propiedad o método, indica que el miembro devuelve un objeto o un VARIANT que son un origen de eventos.|  
|[subprocesamiento](../windows/threading-cpp.md)|Especifica el modelo de subprocesos de un objeto COM.|  
|[único](../windows/unique-cpp.md)|especifica un puntero único.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Especifica el identificador único para una clase o interfaz.|  
|[version](../windows/version-cpp.md)|Identifica una determinada versión entre varias versiones de una clase.|  
|[vi\_progid](../windows/vi-progid.md)|especifica un formulario de la versión\-independiente de ProgID.|  
  
## Vea también  
 [Attributes by Usage](../windows/attributes-by-usage.md)