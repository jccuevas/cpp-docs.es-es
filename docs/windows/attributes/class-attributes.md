---
title: Atributos de claseC++ (com)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
ms.openlocfilehash: 5e10b7831e59211b73ce947ac21e43bc1a8af1c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167321"
---
# <a name="class-attributes"></a>Atributos de clase

Los siguientes atributos se aplican a la palabra clave [Class](../../cpp/class-cpp.md) C++ .

|Atributo|Descripción|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indica que la clase admite la agregación.|
|[aggregates](aggregates.md)|Indica que un control agrega la clase de destino.|
|[appobject](appobject.md)|Identifica la coclase como un objeto de aplicación, que está asociado a una aplicación completa. exe e indica que las funciones y propiedades de la coclase están disponibles globalmente en esta biblioteca de tipos.|
|[case](case-cpp.md)|Se usa con el [switch_type](switch-type.md) atributo de una Unión.|
|[coclass](coclass.md)|Crea un control ActiveX.|
|[com_interface_entry](com-interface-entry-cpp.md)|Agrega una entrada de interfaz a un mapa COM.|
|[control](control.md)|Especifica que el tipo definido por el usuario es un control.|
|[custom](custom-cpp.md)|Permite definir su propio atributo.|
|[db_command](db-command.md)|Crea un comando OLE DB.|
|[db_param](db-param.md)|Asocia la variable miembro especificada a un parámetro de entrada o de salida y delimita la variable.|
|[db_source](db-source.md)|Crea una conexión a un origen de datos.|
|[db_table](db-table.md)|Abre una tabla de OLE DB.|
|[valor predeterminado](default-cpp.md)|Indica que la interfaz personalizada o dispinterface definida en una coclase representa la interfaz de programación predeterminada.|
|[defaultvtable](defaultvtable.md)|Define una interfaz como la interfaz vtable predeterminada de un control.|
|[event_receiver](event-receiver.md)|Crea un receptor de eventos.|
|[event_source](event-source.md)|Crea un origen de eventos.|
|[helpcontext](helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información sobre este elemento en el archivo de **ayuda** .|
|[helpfile](helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|
|[helpstringcontext](helpstringcontext.md)|Especifica el identificador de un tema de ayuda en un archivo. hlp o. chm.|
|[helpstring](helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|
|[hidden](hidden.md)|Indica que el elemento existe, pero no se debe mostrar en un explorador orientado al usuario.|
|[implements](implements-cpp.md)|Especifica las interfaces de distribución que se fuerzan a ser miembros de la coclase IDL.|
|[implements_category](implements-category.md)|Especifica las categorías de componentes implementados para la clase.|
|[module](module-cpp.md)|Define el bloque de biblioteca en el archivo .idl.|
|[noncreatable](noncreatable.md)|Define un objeto del que no se pueden crear instancias de sí mismo.|
|[progid](progid.md)|Define el identificador de programa (ProgID) para un control.|
|[registration_script](registration-script.md)|Ejecuta el script de registro especificado.|
|[requestedit](requestedit.md)|Indica que la propiedad admite la notificación `OnRequestEdit`.|
|[de origen](source-cpp.md)|Especifica las interfaces de origen del control para los puntos de conexión de una clase. En una propiedad o método, el atributo `source` indica que el miembro devuelve un objeto o `VARIANT` que es un origen de eventos.|
|[support_error_info](support-error-info.md)|Admite informes de errores para el objeto de destino.|
|[threading](threading-cpp.md)|Especifica el modelo de subprocesos para un control.|
|[uuid](uuid-cpp-attributes.md)|Especifica el identificador único de una clase o interfaz.|
|[version](version-cpp.md)|Identifica una versión concreta entre varias versiones de una clase.|
|[vi_progid](vi-progid.md)|Especifica una forma independiente de la versión del identificador de programa (ProgID).|

## <a name="see-also"></a>Consulte también

[Atributos por uso](attributes-by-usage.md)
