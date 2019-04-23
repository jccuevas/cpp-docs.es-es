---
title: TypeDef, Enum, Union y Struct (atributos) (COM de C++)
ms.date: 10/02/2018
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
ms.openlocfilehash: 2b56ada13a0c597866d538991ed1e83078924ac9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029588"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Typedef, Enum, Union y Struct (Atributos)

Los siguientes atributos se aplican a la [typedef](../../cpp/aliases-and-typedefs-cpp.md), [struct](../../cpp/struct-cpp.md), y [enum](../../cpp/enumerations-cpp.md) palabras clave de C++.

### <a name="typedef"></a>typedef

|Atributo|Descripción|
|---------------|-----------------|
|[case](case-cpp.md)|Puede usar con el [switch_type](switch-type.md) atributo en un **union**.|
|[custom](custom-cpp.md)|Le permite definir su propio atributo.|
|[export](export.md)|Hace que una estructura de datos que se colocarán en el archivo. idl.|
|[first_is](first-is.md)|Especifica el índice del primer elemento de matriz que se transmitan.|
|[helpcontext](helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el archivo de ayuda.|
|[helpfile](helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|
|[helpstring](helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|
|[library_block](library-block.md)|Coloca una construcción dentro del bloque de biblioteca del archivo. idl.|
|[ptr](ptr.md)|Designa un puntero como un puntero completo.|
|[public](public-cpp-attributes.md)|Garantiza que una definición de tipo pasará a la biblioteca de tipos aunque no se hace referencia desde dentro del archivo. idl.|
|[ref](ref-cpp.md)|Identifica un puntero de referencia.|
|[switch_is](switch-is.md)|Especifica la expresión o el identificador que actúa como la unión discriminante que selecciona al miembro de unión.|
|[switch_type](switch-type.md)|Identifica el tipo de la variable utilizada como la unión discriminante.|
|[unique](unique-cpp.md)|Especifica un puntero único.|
|[wire_marshal](wire-marshal.md)|Especifica un tipo de datos que se usará para la transmisión en lugar de un tipo de datos específicos de la aplicación.|

### <a name="enum"></a>enum

|Atributo|Descripción|
|---------------|-----------------|
|[custom](custom-cpp.md)|Le permite definir su propio atributo.|
|[export](export.md)|Hace que una estructura de datos que se colocarán en el archivo. idl.|
|[uuid](uuid-cpp-attributes.md)|Especifica el identificador único para una clase o interfaz.|
|[v1_enum](v1-enum.md)|Indica que el tipo enumerado especificado se transmite como una entidad de 32 bits, en lugar de con el valor predeterminado de 16 bits.|

### <a name="union"></a>union

|Atributo|Descripción|
|---------------|-----------------|
|[custom](custom-cpp.md)|Le permite definir su propio atributo.|
|[export](export.md)|Hace que una estructura de datos que se colocarán en el archivo. idl.|
|[first_is](first-is.md)|Especifica el índice del primer elemento de matriz que se transmitan.|
|[last_is](last-is.md)|Especifica el índice del último elemento de matriz que se transmitan.|
|[length_is](length-is.md)|Especifica el número de elementos de matriz que se transmitan.|
|[max_is](max-is.md)|Designa el valor máximo para un índice de matriz válida.|
|[size_is](size-is.md)|Especifica el tamaño de memoria asignada para los punteros de tamaño, tamaño de punteros a punteros de tamaño y solo - o matrices multidimensionales.|
|[unique](unique-cpp.md)|Especifica un puntero único.|
|[uuid](uuid-cpp-attributes.md)|Especifica el identificador único para una clase o interfaz.|

### <a name="nonencapsulated-union"></a>Unión nonencapsulated

|Atributo|Descripción|
|---------------|-----------------|
|[ms_union](ms-union.md)|Controla la alineación de representación de datos de red de uniones nonencapsulated.|
|[no_injected_text](no-injected-text.md)|Impide que el compilador inserte el código como resultado el uso de atributo.|

### <a name="struct"></a>struct

|Atributo|Descripción|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indica que la clase admite agregación.|
|[aggregates](aggregates.md)|Indica que un control agrega la clase de destino.|
|[appobject](appobject.md)|Identifica la coclase como un objeto de aplicación, que está asociado a una aplicación completa .exe e indica que las funciones y propiedades de la coclase están disponibles globalmente en esta biblioteca de tipos.|
|[coclase](coclass.md)|Crea un control ActiveX.|
|[com_interface_entry](com-interface-entry-cpp.md)|Agrega una entrada de la interfaz a un mapa COM.|
|[control](control.md)|Especifica que el tipo definido por el usuario es un control.|
|[custom](custom-cpp.md)|Le permite definir su propio atributo.|
|[db_column](db-column.md)|Enlaza una columna especificada para el conjunto de filas.|
|[db_command](db-command.md)|Crea un comando OLE DB.|
|[db_param](db-param.md)|La variable de miembro especificado se asocia con un parámetro de entrada o salido y delimita la variable.|
|[db_source](db-source.md)|Crea una conexión a un origen de datos.|
|[db_table](db-table.md)|Se abre una tabla de OLE DB.|
|[default](default-cpp.md)|Indica que la interfaz personalizada o dispinterface definida en una coclase representa la interfaz de programación predeterminada.|
|[defaultvtable](defaultvtable.md)|Define una interfaz que la interfaz de vtable predeterminada para un control.|
|[event_receiver](event-receiver.md)|Crea un receptor de eventos.|
|[event_source](event-source.md)|Crea un origen de eventos.|
|[export](export.md)|Hace que una estructura de datos que se colocarán en el archivo. idl.|
|[first_is](first-is.md)|Especifica el índice del primer elemento de matriz que se transmitan.|
|[hidden](hidden.md)|Indica que el elemento existe pero no debe mostrarse en un explorador orientado al usuario.|
|[implements_category](implements-category.md)|Especifica las categorías de componentes implementados para la clase.|
|[last_is](last-is.md)|Especifica el índice del último elemento de matriz que se transmitan.|
|[length_is](length-is.md)|Especifica el número de elementos de matriz que se transmitan.|
|[max_is](max-is.md)|Designa el valor máximo para un índice de matriz válida.|
|[requires_category](requires-category.md)|Especifica las categorías de los componentes necesarios de la clase de destino.|
|[size_is](size-is.md)|Especifica el tamaño de memoria asignada para los punteros de tamaño, tamaño de punteros a punteros de tamaño y solo - o matrices multidimensionales.|
|[source](source-cpp.md)|En una clase, especifica las interfaces de origen del objeto COM para puntos de conexión. En una propiedad o método, indica que el miembro devuelve un objeto o una variante de un origen de eventos.|
|[threading](threading-cpp.md)|Especifica el modelo de subprocesos para un objeto COM.|
|[unique](unique-cpp.md)|Especifica un puntero único.|
|[uuid](uuid-cpp-attributes.md)|Especifica el identificador único para una clase o interfaz.|
|[version](version-cpp.md)|Identifica una versión determinada entre varias versiones de una clase.|
|[vi_progid](vi-progid.md)|Especifica una forma independiente de la versión de ProgID.|

## <a name="see-also"></a>Vea también

[Atributos por uso](attributes-by-usage.md)