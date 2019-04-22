---
title: Atributos de clase (COM de C++)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
ms.openlocfilehash: d0913d09c51734f5255271c0d06e639810e0cb58
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025421"
---
# <a name="class-attributes"></a>Atributos de clase

Los siguientes atributos se aplican a la [clase](../../cpp/class-cpp.md) palabra clave de C++.

|Atributo|Descripción|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indica que la clase admite agregación.|
|[aggregates](aggregates.md)|Indica que un control agrega la clase de destino.|
|[appobject](appobject.md)|Identifica la coclase como un objeto de aplicación, que está asociado a una aplicación completa .exe e indica que las funciones y propiedades de la coclase están disponibles globalmente en esta biblioteca de tipos.|
|[case](case-cpp.md)|Puede usar con el [switch_type](switch-type.md) atributo en una unión.|
|[coclase](coclass.md)|Crea un control ActiveX.|
|[com_interface_entry](com-interface-entry-cpp.md)|Agrega una entrada de la interfaz a un mapa COM.|
|[control](control.md)|Especifica que el tipo definido por el usuario es un control.|
|[custom](custom-cpp.md)|Le permite definir su propio atributo.|
|[db_command](db-command.md)|Crea un comando OLE DB.|
|[db_param](db-param.md)|La variable de miembro especificado se asocia con un parámetro de entrada o salido y delimita la variable.|
|[db_source](db-source.md)|Crea una conexión a un origen de datos.|
|[db_table](db-table.md)|Se abre una tabla de OLE DB.|
|[default](default-cpp.md)|Indica que la interfaz personalizada o dispinterface definida en una coclase representa la interfaz de programación predeterminada.|
|[defaultvtable](defaultvtable.md)|Define una interfaz que la interfaz de vtable predeterminada para un control.|
|[event_receiver](event-receiver.md)|Crea un receptor de eventos.|
|[event_source](event-source.md)|Crea un origen de eventos.|
|[helpcontext](helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el **ayuda** archivo.|
|[helpfile](helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|
|[helpstringcontext](helpstringcontext.md)|Especifica el identificador de un tema de ayuda en un archivo .hlp o chm.|
|[helpstring](helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|
|[hidden](hidden.md)|Indica que el elemento existe pero no debe mostrarse en un explorador orientado al usuario.|
|[implements](implements-cpp.md)|Especifica las interfaces de envío que se ven obligadas a ser miembros de la coclase IDL.|
|[implements_category](implements-category.md)|Especifica las categorías de componentes implementados para la clase.|
|[module](module-cpp.md)|Define el bloque de biblioteca en el archivo .idl.|
|[noncreatable](noncreatable.md)|Define un objeto que no pueden crearse instancias por sí mismo.|
|[progid](progid.md)|Define el ProgID de un control.|
|[registration_script](registration-script.md)|Ejecuta el script de registro especificado.|
|[requestedit](requestedit.md)|Indica que la propiedad admite la notificación `OnRequestEdit`.|
|[source](source-cpp.md)|Especifica las interfaces de origen del control de puntos de conexión en una clase. En una propiedad o método, el `source` atributo indica que el miembro devuelve un objeto o `VARIANT` que es un origen de eventos.|
|[support_error_info](support-error-info.md)|Admite informes de errores para el objeto de destino.|
|[threading](threading-cpp.md)|Especifica el modelo de subprocesos para un control.|
|[uuid](uuid-cpp-attributes.md)|Especifica el identificador único para una clase o interfaz.|
|[version](version-cpp.md)|Identifica una versión determinada entre varias versiones de una clase.|
|[vi_progid](vi-progid.md)|Especifica una forma independiente de la versión de ProgID.|

## <a name="see-also"></a>Vea también

[Atributos por uso](attributes-by-usage.md)