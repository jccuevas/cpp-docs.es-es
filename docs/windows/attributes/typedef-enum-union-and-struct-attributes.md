---
title: TypeDef, ENUM, Union y struct (atributos)C++ (com)
ms.date: 10/02/2018
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
ms.openlocfilehash: fdc380cdc207361a145862f87d809a4bcea01c27
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214479"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Typedef, Enum, Union y Struct (Atributos)

Los siguientes atributos se aplican a las palabras clave [typedef](../../cpp/aliases-and-typedefs-cpp.md), [struct](../../cpp/struct-cpp.md)y [enum](../../cpp/enumerations-cpp.md) C++ .

### <a name="typedef"></a>typedef

|Atributo|Descripción|
|---------------|-----------------|
|[case](case-cpp.md)|Se usa con el [switch_type](switch-type.md) atributo de una **Unión**.|
|[custom](custom-cpp.md)|Permite definir su propio atributo.|
|[export](export.md)|Hace que una estructura de datos se coloque en el archivo. idl.|
|[first_is](first-is.md)|Especifica el índice del primer elemento de la matriz que se va a transmitir.|
|[helpcontext](helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información sobre este elemento en el archivo de ayuda.|
|[helpfile](helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|
|[helpstring](helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|
|[library_block](library-block.md)|Coloca una construcción dentro del bloque de biblioteca del archivo. idl.|
|[ptr](ptr.md)|Designa un puntero como un puntero completo.|
|[public](public-cpp-attributes.md)|Garantiza que una definición de tipo se incluirá en la biblioteca de tipos aunque no se haga referencia a ella desde el archivo. idl.|
|[ref](ref-cpp.md)|Identifica un puntero de referencia.|
|[switch_is](switch-is.md)|Especifica la expresión o el identificador que actúa como discriminante de Unión que selecciona el miembro de Unión.|
|[switch_type](switch-type.md)|Identifica el tipo de la variable utilizada como discriminante de Unión.|
|[unique](unique-cpp.md)|Especifica un puntero único.|
|[wire_marshal](wire-marshal.md)|Especifica un tipo de datos que se utilizará para la transmisión en lugar de un tipo de datos específico de la aplicación.|

### <a name="enum"></a>enum

|Atributo|Descripción|
|---------------|-----------------|
|[custom](custom-cpp.md)|Permite definir su propio atributo.|
|[export](export.md)|Hace que una estructura de datos se coloque en el archivo. idl.|
|[uuid](uuid-cpp-attributes.md)|Especifica el identificador único de una clase o interfaz.|
|[v1_enum](v1-enum.md)|Indica que el tipo enumerado especificado se va a transmitir como una entidad de 32 bits, en lugar del valor predeterminado de 16 bits.|

### <a name="union"></a>union

|Atributo|Descripción|
|---------------|-----------------|
|[custom](custom-cpp.md)|Permite definir su propio atributo.|
|[export](export.md)|Hace que una estructura de datos se coloque en el archivo. idl.|
|[first_is](first-is.md)|Especifica el índice del primer elemento de la matriz que se va a transmitir.|
|[last_is](last-is.md)|Especifica el índice del último elemento de la matriz que se va a transmitir.|
|[length_is](length-is.md)|Especifica el número de elementos de matriz que se van a transmitir.|
|[max_is](max-is.md)|Designa el valor máximo de un índice de matriz válido.|
|[size_is](size-is.md)|Especifica el tamaño de la memoria asignada para punteros de tamaño, punteros de tamaño a punteros de tamaño y matrices de un solo o multidimensionales.|
|[unique](unique-cpp.md)|Especifica un puntero único.|
|[uuid](uuid-cpp-attributes.md)|Especifica el identificador único de una clase o interfaz.|

### <a name="nonencapsulated-union"></a>Unión no encapsulada

|Atributo|Descripción|
|---------------|-----------------|
|[ms_union](ms-union.md)|Controla la alineación de la representación de datos de red de las uniones no encapsuladas.|
|[no_injected_text](no-injected-text.md)|Impide que el compilador Inserte código como resultado del uso de atributos.|

### <a name="struct"></a>struct

|Atributo|Descripción|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indica que la clase admite la agregación.|
|[aggregates](aggregates.md)|Indica que un control agrega la clase de destino.|
|[appobject](appobject.md)|Identifica la coclase como un objeto de aplicación, que está asociado a una aplicación completa. exe e indica que las funciones y propiedades de la coclase están disponibles globalmente en esta biblioteca de tipos.|
|[coclass](coclass.md)|Crea un control ActiveX.|
|[com_interface_entry](com-interface-entry-cpp.md)|Agrega una entrada de interfaz a un mapa COM.|
|[control](control.md)|Especifica que el tipo definido por el usuario es un control.|
|[custom](custom-cpp.md)|Permite definir su propio atributo.|
|[db_column](db-column.md)|Enlaza una columna especificada al conjunto de filas.|
|[db_command](db-command.md)|Crea un comando OLE DB.|
|[db_param](db-param.md)|Asocia la variable miembro especificada a un parámetro de entrada o de salida y delimita la variable.|
|[db_source](db-source.md)|Crea una conexión a un origen de datos.|
|[db_table](db-table.md)|Abre una tabla de OLE DB.|
|[valor predeterminado](default-cpp.md)|Indica que la interfaz personalizada o dispinterface definida en una coclase representa la interfaz de programación predeterminada.|
|[defaultvtable](defaultvtable.md)|Define una interfaz como la interfaz vtable predeterminada de un control.|
|[event_receiver](event-receiver.md)|Crea un receptor de eventos.|
|[event_source](event-source.md)|Crea un origen de eventos.|
|[export](export.md)|Hace que una estructura de datos se coloque en el archivo. idl.|
|[first_is](first-is.md)|Especifica el índice del primer elemento de la matriz que se va a transmitir.|
|[hidden](hidden.md)|Indica que el elemento existe, pero no se debe mostrar en un explorador orientado al usuario.|
|[implements_category](implements-category.md)|Especifica las categorías de componentes implementados para la clase.|
|[last_is](last-is.md)|Especifica el índice del último elemento de la matriz que se va a transmitir.|
|[length_is](length-is.md)|Especifica el número de elementos de matriz que se van a transmitir.|
|[max_is](max-is.md)|Designa el valor máximo de un índice de matriz válido.|
|[requires_category](requires-category.md)|Especifica las categorías de componente necesarias de la clase de destino.|
|[size_is](size-is.md)|Especifica el tamaño de la memoria asignada para punteros de tamaño, punteros de tamaño a punteros de tamaño y matrices de un solo o multidimensionales.|
|[de origen](source-cpp.md)|En una clase, especifica las interfaces de origen del objeto COM para los puntos de conexión. En una propiedad o un método, indica que el miembro devuelve un objeto o una variante que es un origen de eventos.|
|[threading](threading-cpp.md)|Especifica el modelo de subprocesos para un objeto COM.|
|[unique](unique-cpp.md)|Especifica un puntero único.|
|[uuid](uuid-cpp-attributes.md)|Especifica el identificador único de una clase o interfaz.|
|[version](version-cpp.md)|Identifica una versión concreta entre varias versiones de una clase.|
|[vi_progid](vi-progid.md)|Especifica una forma independiente de la versión del identificador de programa (ProgID).|

## <a name="see-also"></a>Consulte también

[Atributos por uso](attributes-by-usage.md)
