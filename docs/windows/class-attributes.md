---
title: "Class Attributes | Microsoft Docs"
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
  - "attributes [C++], class attributes"
  - "class attributes"
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Class Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los atributos siguientes se aplican a la palabra clave de [clase](../cpp/class-cpp.md) C\+\+.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|[aggregatable](../Topic/aggregatable.md)|indica que la clase admite la agregación.|  
|[agregados](../windows/aggregates.md)|Indica que un control agrega la clase de destino.|  
|[appobject](../Topic/appobject.md)|Identifica la coclase como objeto application, que está asociado a una aplicación completa .exe, e indica que las funciones y propiedades coclass son globalmente disponible en esta biblioteca de tipos.|  
|[case](../windows/case-cpp.md)|Utilizado con el atributo de [switch\_type](../windows/switch-type.md) en una combinación.|  
|[CoClass](../windows/coclass.md)|crea un control ActiveX.|  
|[com\_interface\_entry](../Topic/com_interface_entry%20\(C++\).md)|Agrega una entrada de interfaz a un mapa COM.|  
|[Control](../windows/control.md)|especifica que el tipo definido por el usuario es un control.|  
|[custom](../windows/custom-cpp.md)|Permite definir dispone de atributo.|  
|[db\_command](../windows/db-command.md)|Crea un comando OLE DB.|  
|[db\_param](../windows/db-param.md)|Asociado a la variable miembro especificada a una entrada o parámetro de salida y delimita la variable.|  
|[db\_source](../windows/db-source.md)|crea una conexión a un origen de datos.|  
|[db\_table](../windows/db-table.md)|Abra una tabla de OLE DB.|  
|[default](../windows/default-cpp.md)|Indica que la personalizado o el dispinterface definido dentro de una coclase representa la interfaz predeterminada de la programación.|  
|[defaultvtable](../windows/defaultvtable.md)|Define una interfaz como interfaz vtable predeterminada de un control.|  
|[event\_receiver](../windows/event-receiver.md)|Crea un receptor de eventos.|  
|[event\_source](../windows/event-source.md)|crea un origen de eventos.|  
|[helpcontext](../windows/helpcontext.md)|Especifica un Id. de contexto que deje la información de la vista de usuario sobre este elemento en el archivo de Ayuda.|  
|[helpfile](../Topic/helpfile.md)|Establece el nombre del archivo de Ayuda para una biblioteca de tipos.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Especifica el identificador de un tema de Ayuda en un archivo de .hlp o .chm.|  
|[helpstring](../windows/helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|  
|[hidden](../Topic/hidden.md)|Indica que el elemento existe pero no se debe mostrar en un explorador del usuario.|  
|[implements](../Topic/implements%20\(C++\).md)|Especifica las interfaces de distribución que se convierten para ser miembros coclass IDL.|  
|[implements\_category](../Topic/implements_category.md)|Especifica implementó categorías componentes para la clase.|  
|[módulo](../windows/module-cpp.md)|Define la biblioteca bloqueado en el archivo .idl.|  
|[noncreatable](../windows/noncreatable.md)|Define un objeto que no se puede crear instancias en sí mismo.|  
|[ProgID](../Topic/progid.md)|define ProgID para un control.|  
|[registration\_script](../windows/registration-script.md)|Ejecuta el script especificado del registro.|  
|[requestedit](../windows/requestedit.md)|indica que la propiedad admite la notificación de **OnRequestEdit** .|  
|[source](../Topic/source%20\(C++\).md)|Especifica las interfaces del origen del control para los puntos de conexión en una clase.  En una propiedad o método, el atributo de **origen** indica que el miembro devuelve un objeto o un VARIANT que son un origen de eventos.|  
|[support\_error\_information](../windows/support-error-info.md)|Admite informes de error para el objeto de destino.|  
|[subprocesamiento](../windows/threading-cpp.md)|Especifica el modelo de subprocesos de un control.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Especifica el identificador único para una clase o interfaz.|  
|[version](../windows/version-cpp.md)|Identifica una determinada versión entre varias versiones de una clase.|  
|[vi\_progid](../windows/vi-progid.md)|especifica un formulario de la versión\-independiente de ProgID.|  
  
## Vea también  
 [Attributes by Usage](../windows/attributes-by-usage.md)