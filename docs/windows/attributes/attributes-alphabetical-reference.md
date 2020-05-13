---
title: Referencia alfabética de los atributos
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
f1_keywords:
- vc.attributes
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: fb2216ef-9fbd-44f4-afed-732aa99450e2
ms.openlocfilehash: dbbb406765c0664f2cd332524a61713f9c67cf9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167516"
---
# <a name="attributes-alphabetical-reference"></a>Referencia alfabética de los atributos

Los siguientes atributos están disponibles en el compilador de Microsoft C++ :

|Atributo|Descripción|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indica que otro control puede Agregar un control.|
|[aggregates](aggregates.md)|Indica que un control agrega la clase de destino.|
|[appobject](appobject.md)|Identifica la coclase como un objeto de aplicación, que está asociado a una aplicación completa de EXE e indica que las funciones y propiedades de la coclase están disponibles globalmente en esta biblioteca de tipos.|
|[async_uuid](async-uuid.md)|Especifica el UUID que dirige el compilador MIDL para definir versiones sincrónicas y asincrónicas de una interfaz COM.|
|[attribute](attribute.md)|Permite crear un atributo personalizado.|
|[bindable](bindable.md)|Indica que la propiedad admite enlace de datos.|
|[call_as](call-as.md)|Habilita una función no utilizables que se va a asignar a una función remota.|
|[case](case-cpp.md)|Se usa con el [switch_type](switch-type.md) atributo de una Unión.|
|[coclass](coclass.md)|Crea un objeto COM, que puede implementar una interfaz COM.|
|[com_interface_entry](com-interface-entry-cpp.md)|Agrega una entrada de interfaz a un mapa COM.|
|[control](control.md)|Especifica que el tipo definido por el usuario es un control.|
|[cpp_quote](cpp-quote.md)|Emite la cadena especificada, sin los caracteres de Comillas, en el archivo de encabezado generado.|
|[custom](custom-cpp.md)|Permite definir sus propios atributos.|
|[db_accessor](db-accessor.md)|Enlaza las columnas de un conjunto de filas y las enlaza con los mapas de descriptores de acceso correspondientes.|
|[db_column](db-column.md)|Enlaza una columna especificada al conjunto de filas.|
|[db_command](db-command.md)|Ejecuta un comando de OLE DB.|
|[db_param](db-param.md)|Asocia la variable miembro especificada a un parámetro de entrada o de salida.|
|[db_source](db-source.md)|Crea y encapsula una conexión, a través de un proveedor, a un origen de datos.|
|[db_table](db-table.md)|Abre una tabla de OLE DB.|
|[valor predeterminado](default-cpp.md)|Indica que la interfaz personalizada o dispinterface definida en una coclase representa la interfaz de programación predeterminada.|
|[defaultbind](defaultbind.md)|Indica la única propiedad enlazable que mejor representa el objeto.|
|[defaultcollelem](defaultcollelem.md)|Se usa para Visual Basic la optimización del código.|
|[defaultvalue](defaultvalue.md)|Permite la especificación de un valor predeterminado para un parámetro opcional con tipo.|
|[defaultvtable](defaultvtable.md)|Define una interfaz como la interfaz vtable predeterminada de un control.|
|[dispinterface](dispinterface.md)|Coloca una interfaz en el archivo .idl como interfaz de envío.|
|[displaybind](displaybind.md)|Indica una propiedad que se debe mostrar al usuario como enlazable.|
|[dual](dual.md)|Coloca una interfaz en el archivo. idl como una interfaz dual.|
|[emitidl](emitidl.md)|Determina si todos los atributos IDL subsiguientes se procesarán y colocarán en el archivo. idl generado.|
|[entry](entry.md)|Especifica una función o una constante exportadas en un módulo mediante la identificación del punto de entrada en el archivo DLL.|
|[event_receiver](event-receiver.md)|Crea un receptor de eventos.|
|[event_source](event-source.md)|Crea un origen de eventos.|
|[export](export.md)|Hace que una estructura de datos se coloque en el archivo. idl.|
|[first_is](first-is.md)|Especifica el índice del primer elemento de la matriz que se va a transmitir.|
|[helpcontext](helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información sobre este elemento en el archivo de ayuda.|
|[helpfile](helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|
|[helpstring](helpstring.md)|Especifica el identificador de un tema de ayuda en un archivo. hlp o. chm.|
|[helpstringdll](helpstringdll.md)|Especifica el nombre del archivo DLL que se va a usar para realizar la búsqueda de cadenas de documento (localización).|
|[hidden](hidden.md)|Indica que el elemento existe, pero no se debe mostrar en un explorador orientado al usuario.|
|[id](id.md)|Especifica un DISPID para una función miembro (ya sea una propiedad o un método, en una interfaz o dispinterface).|
|[idl_module](idl-module.md)|Especifica un punto de entrada en un archivo DLL.|
|[idl_quote](idl-quote.md)|Permite usar atributos o construcciones IDL que no se admiten en la versión actual de Visual C++.|
|[iid_is](iid-is.md)|Especifica el IID de la interfaz COM a la que apunta un puntero de interfaz.|
|[immediatebind](immediatebind.md)|Indica que se notificará inmediatamente a la base de datos todos los cambios efectuados en una propiedad de un objeto enlazado a datos.|
|[implements](implements-cpp.md)|Especifica las interfaces de distribución que se fuerzan a ser miembros de la coclase IDL.|
|[implements_category](implements-category.md)|Especifica las categorías de componentes implementados para la clase.|
|[import](import.md)|Especifica otro archivo. idl,. ODL o de encabezado que contiene las definiciones a las que se desea hacer referencia desde el archivo. idl principal.|
|[importidl](importidl.md)|Inserta el archivo. idl especificado en el archivo. idl generado.|
|[importlib](importlib.md)|Hace que los tipos que ya se han compilado en otra biblioteca de tipos estén disponibles en la biblioteca de tipos que se está creando.|
|[in](in-cpp.md)|Indica que se va a pasar un parámetro del procedimiento que realiza la llamada al procedimiento llamado.|
|[include](include-cpp.md)|Especifica uno o más archivos de encabezado que se van a incluir en el archivo. idl generado.|
|[includelib](includelib-cpp.md)|Hace que un archivo. idl o. h se incluya en el archivo. idl generado.|
|[last_is](last-is.md)|Especifica el índice del último elemento de la matriz que se va a transmitir.|
|[lcid](lcid.md)|Permite pasar un identificador de configuración regional a una función.|
|[length_is](length-is.md)|Especifica el número de elementos de matriz que se van a transmitir.|
|[library_block](library-block.md)|Coloca una construcción dentro del bloque de biblioteca del archivo. idl.|
|[licensed](licensed.md)|Indica que la coclase a la que se aplica tiene licencia y se debe crear una instancia de mediante `IClassFactory2`.|
|[local](local-cpp.md)|Permite usar el compilador MIDL como generador de encabezados cuando se usa en el encabezado de la interfaz. Cuando se usa en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.|
|[max_is](max-is.md)|Designa el valor máximo de un índice de matriz válido.|
|[module](module-cpp.md)|Define el bloque de biblioteca en el archivo .idl.|
|[ms_union](ms-union.md)|Controla la alineación de la representación de datos de red de las uniones no encapsuladas.|
|[no_injected_text](no-injected-text.md)|Impide que el compilador Inserte código como resultado del uso de atributos.|
|[nonbrowsable](nonbrowsable.md)|Indica que un miembro de interfaz no se debe mostrar en un explorador de propiedades.|
|[noncreatable](noncreatable.md)|Define un objeto del que no se pueden crear instancias de sí mismo.|
|[nonextensible](nonextensible.md)|Especifica que la implementación de `IDispatch` solo incluye las propiedades y los métodos enumerados en la descripción de la interfaz y no se puede extender con miembros adicionales en tiempo de ejecución.|
|[object](object-cpp.md)|Identifica una interfaz personalizada; Sinónimo de atributo personalizado.|
|[odl](odl.md)|Identifica una interfaz como una interfaz de lenguaje de descripción de objetos (ODL).|
|[oleautomation](oleautomation.md)|Indica que una interfaz es compatible con la automatización.|
|[opcional](optional-cpp.md)|Especifica un parámetro opcional para una función miembro.|
|[out](out-cpp.md)|Identifica los parámetros de puntero devueltos desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).|
|[pointer_default](pointer-default.md)|Especifica el atributo de puntero predeterminado para todos los punteros, excepto los punteros de nivel superior que aparecen en las listas de parámetros.|
|[pragma](pragma.md)|Emite la cadena especificada, sin los caracteres de Comillas, en el archivo. idl generado.|
|[progid](progid.md)|Especifica el ProgID para un objeto COM.|
|[propget](propget.md)|Especifica una función de descriptor de acceso de propiedad (GET).|
|[propput](propput.md)|Especifica una función de valor de propiedad.|
|[propputref](propputref.md)|Especifica una función de configuración de propiedades que usa una referencia en lugar de un valor.|
|[ptr](ptr.md)|Designa un puntero como un puntero completo.|
|[public](public-cpp-attributes.md)|Garantiza que una definición de tipo se incluirá en la biblioteca de tipos aunque no se haga referencia a ella desde el archivo. idl.|
|[range](range-cpp.md)|Especifica un intervalo de valores permitidos para los argumentos o campos cuyos valores se establecen en tiempo de ejecución.|
|[rdx](rdx.md)|Crea o modifica una clave del registro.|
|[readonly](readonly-cpp.md)|Prohíbe la asignación a una variable.|
|[ref](ref-cpp.md)|Identifica un puntero de referencia.|
|[registration_script](registration-script.md)|Ejecuta el script de registro especificado.|
|[requestedit](requestedit.md)|Indica que la propiedad admite la notificación `OnRequestEdit`.|
|[requires_category](requires-category.md)|Especifica las categorías de componentes necesarias para la clase.|
|[restricted](restricted.md)|Especifica que una biblioteca, o miembro de un módulo, interfaz o dispinterface, no se puede llamar arbitrariamente.|
|[retval](retval.md)|Designa el parámetro que recibe el valor devuelto del miembro.|
|[satype](satype.md)|Especifica el tipo de datos del `SAFEARRAY`.|
|[size_is](size-is.md)|Especifica el tamaño de la memoria asignada para punteros de tamaño, punteros de tamaño a punteros de tamaño y matrices de un solo o multidimensionales.|
|[de origen](source-cpp.md)|Indica que un miembro de una clase, propiedad o método es un origen de eventos.|
|[string](string-cpp.md)|Indica que la matriz **Char**, **wchar_t**, `byte`o equivalente unidimensional o el puntero a dicha matriz se debe tratar como una cadena.|
|[support_error_info](support-error-info.md)|Admite informes de errores para el objeto de destino.|
|[switch_is](switch-is.md)|Especifica la expresión o el identificador que actúa como discriminante de Unión que selecciona el miembro de Unión.|
|[switch_type](switch-type.md)|Identifica el tipo de la variable utilizada como discriminante de Unión.|
|[synchronize](synchronize.md)|Sincroniza el acceso a un método.|
|[threading](threading-cpp.md)|Especifica el modelo de subprocesos para un objeto COM.|
|[transmit_as](transmit-as.md)|Indica al compilador que asocie un tipo presentado, que las aplicaciones cliente y servidor manipulan, con un tipo transmitido.|
|[uidefault](uidefault.md)|Indica que el miembro de información de tipo es el miembro predeterminado que se va a mostrar en la interfaz de usuario.|
|[unique](unique-cpp.md)|Especifica un puntero único.|
|[usesgetlasterror](usesgetlasterror.md)|Indica al llamador que, si se produce un error al llamar a esa función, el llamador puede llamar a `GetLastError` para recuperar el código de error.|
|[uuid](uuid-cpp-attributes.md)|Especifica el identificador único de una clase o interfaz.|
|[v1_enum](v1-enum.md)|Indica que el tipo enumerado especificado se va a transmitir como una entidad de 32 bits, en lugar del valor predeterminado de 16 bits.|
|[vararg](vararg.md)|Especifica que la función toma un número variable de argumentos.|
|[version](version-cpp.md)|Identifica una versión determinada entre varias versiones de una interfaz o una clase.|
|[vi_progid](vi-progid.md)|Especifica una forma independiente de la versión del identificador de programa (ProgID).|
|[wire_marshal](wire-marshal.md)|Especifica un tipo de datos que se utilizará para la transmisión en lugar de un tipo de datos específico de la aplicación.|

## <a name="see-also"></a>Consulte también

[Atributos de C++ para COM y .NET](cpp-attributes-com-net.md)<br/>
[Atributos por grupo](attributes-by-group.md)<br/>
[Atributos por uso](attributes-by-usage.md)
