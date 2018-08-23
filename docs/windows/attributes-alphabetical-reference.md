---
title: Referencia alfabética de atributos | Microsoft Docs
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.attributes
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++]
ms.assetid: fb2216ef-9fbd-44f4-afed-732aa99450e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1203c871b67c8bd87faef92c840c6236fb028cd3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595813"
---
# <a name="attributes-alphabetical-reference"></a>Referencia alfabética de los atributos

Los siguientes atributos están disponibles en Visual C++.

|Atributo|Descripción|
|---------------|-----------------|
|[aggregatable](../windows/aggregatable.md)|Indica que se puede agregar un control por otro control.|
|[aggregates](../windows/aggregates.md)|Indica que un control agrega la clase de destino.|
|[appobject](../windows/appobject.md)|Identifica la coclase como un objeto de aplicación, que está asociado a una aplicación completa del archivo EXE e indica que las funciones y propiedades de la coclase están disponibles globalmente en esta biblioteca de tipos.|
|[async_uuid](../windows/async-uuid.md)|Especifica el UUID que indica al compilador MIDL para definir las versiones sincrónicas y asincrónicas de una interfaz COM.|
|[attribute](../windows/attribute.md)|Le permite crear un atributo personalizado.|
|[bindable](../windows/bindable.md)|Indica que la propiedad admite enlace de datos.|
|[call_as](../windows/call-as.md)|Permite que una función utilizables para asignarse a una función remota.|
|[case](../windows/case-cpp.md)|Puede usar con el [switch_type](../windows/switch-type.md) atributo en una unión.|
|[coclass](../windows/coclass.md)|Crea un objeto COM, que puede implementar una interfaz COM.|
|[COM_INTERFACE_ENTRY](../windows/com-interface-entry-cpp.md)|Agrega una entrada de la interfaz a un mapa COM.|
|[control](../windows/control.md)|Especifica que el tipo definido por el usuario es un control.|
|[cpp_quote](../windows/cpp-quote.md)|Emite la cadena especificada, sin los caracteres de comillas en el archivo de encabezado generado.|
|[Personalizado](../windows/custom-cpp.md)|Le permite definir sus propios atributos.|
|[db_accessor](../windows/db-accessor.md)|Enlaza las columnas de un conjunto de filas y se enlazan a las asignaciones de descriptor de acceso correspondiente.|
|[db_column](../windows/db-column.md)|Enlaza una columna especificada para el conjunto de filas.|
|[db_command](../windows/db-command.md)|Ejecuta un comando de OLE DB.|
|[db_param](../windows/db-param.md)|La variable de miembro especificado se asocia con un parámetro de entrada o salido.|
|[db_source](../windows/db-source.md)|Crea y encapsula una conexión a través de un proveedor a un origen de datos.|
|[db_table](../windows/db-table.md)|Se abre una tabla de OLE DB.|
|[default](../windows/default-cpp.md)|Indica que la interfaz personalizada o dispinterface definida en una coclase representa la interfaz de programación predeterminada.|
|[defaultbind](../windows/defaultbind.md)|Indica la única propiedad enlazable que mejor representa al objeto.|
|[defaultcollelem](../windows/defaultcollelem.md)|Se usa para la optimización de código de Visual Basic.|
|[defaultvalue](../windows/defaultvalue.md)|Permite especificar un valor predeterminado para un parámetro opcional con tipo.|
|[defaultvtable](../windows/defaultvtable.md)|Define una interfaz que la interfaz de vtable predeterminada para un control.|
|[dispinterface](../windows/dispinterface.md)|Coloca una interfaz en el archivo .idl como interfaz de envío.|
|[displaybind](../windows/displaybind.md)|Indica una propiedad que debe mostrarse al usuario como enlazable.|
|[dual](../windows/dual.md)|Coloca una interfaz en el archivo .idl como una interfaz dual.|
|[emitidl](../windows/emitidl.md)|Determina si todos los atributos IDL posteriores se procesará y se coloca en el archivo .idl generado.|
|[entry](../windows/entry.md)|Especifica una constante o una función exportada de un módulo mediante la identificación de punto de entrada en el archivo DLL.|
|[event_receiver](../windows/event-receiver.md)|Crea un receptor de eventos.|
|[event_source](../windows/event-source.md)|Crea un origen de eventos.|
|[export](../windows/export.md)|Hace que una estructura de datos que se colocarán en el archivo. idl.|
|[first_is](../windows/first-is.md)|Especifica el índice del primer elemento de matriz que se transmitan.|
|[helpcontext](../windows/helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el archivo de ayuda.|
|[helpfile](../windows/helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|
|[helpstring](../windows/helpstring.md)|Especifica el identificador de un tema de ayuda en un archivo .hlp o chm.|
|[helpstringdll](../windows/helpstringdll.md)|Especifica el nombre del archivo DLL a utilizar para realizar la búsqueda de cadenas de documento (localización).|
|[hidden](../windows/hidden.md)|Indica que el elemento existe pero no debe mostrarse en un explorador orientado al usuario.|
|[identificador](../windows/id.md)|Especifica un DISPID para una función miembro (una propiedad o un método en una interfaz o interfaz dispinterface).|
|[idl_module](../windows/idl-module.md)|Especifica un punto de entrada en un archivo DLL.|
|[idl_quote](../windows/idl-quote.md)|Le permite usar los atributos o IDL construcciones que no se admiten en la versión actual de Visual C++.|
|[iid_is](../windows/iid-is.md)|Especifica el IID de la interfaz COM que apunta a un puntero de interfaz.|
|[immediatebind](../windows/immediatebind.md)|Indica que la base de datos será notificada inmediatamente de todos los cambios a una propiedad de un objeto enlazado a datos.|
|[Implementa](../windows/implements-cpp.md)|Especifica las interfaces de envío que se ven obligadas a ser miembros de la coclase IDL.|
|[implements_category](../windows/implements-category.md)|Especifica las categorías de componentes implementados para la clase.|
|[import](../windows/import.md)|Especifica otro archivo .idl, .odl o encabezado que contiene las definiciones que desea hacer referencia desde el archivo .idl principal.|
|[importidl](../windows/importidl.md)|Inserta el archivo .idl especificado en el archivo .idl generado.|
|[importlib](../windows/importlib.md)|Hace que los tipos que ya se han compilado en otra biblioteca de tipos estén disponibles en la biblioteca de tipos que se está creando.|
|[in](../windows/in-cpp.md)|Indica que es un parámetro que se pasan desde el procedimiento que realiza la llamada al procedimiento llamado.|
|[include](../windows/include-cpp.md)|Especifica uno o varios archivos de encabezado que se incluirán en el archivo .idl generado.|
|[includelib](../windows/includelib-cpp.md)|Hace que un archivo IDL o .h para incluirse en el archivo .idl generado.|
|[last_is](../windows/last-is.md)|Especifica el índice del último elemento de matriz que se transmitan.|
|[lcid](../windows/lcid.md)|Le permite pasar un identificador de configuración regional a una función.|
|[length_is](../windows/length-is.md)|Especifica el número de elementos de matriz que se transmitan.|
|[library_block](../windows/library-block.md)|Coloca una construcción dentro del bloque de biblioteca del archivo. idl.|
|[licensed](../windows/licensed.md)|Indica que la coclase al que se aplica con licencia y se debe crear instancias mediante `IClassFactory2`.|
|[local](../windows/local-cpp.md)|Permite usar el compilador de MIDL como un generador de encabezado cuando se utiliza en el encabezado de la interfaz. Cuando se utiliza en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.|
|[max_is](../windows/max-is.md)|Designa el valor máximo para un índice de matriz válida.|
|[módulo](../windows/module-cpp.md)|Define el bloque de biblioteca en el archivo .idl.|
|[ms_union](../windows/ms-union.md)|Controla la alineación de representación de datos de red de uniones nonencapsulated.|
|[no_injected_text](../windows/no-injected-text.md)|Impide que el compilador inserte el código como resultado el uso de atributo.|
|[nonbrowsable](../windows/nonbrowsable.md)|Indica que un miembro de interfaz no debe mostrarse en un explorador de propiedades.|
|[noncreatable](../windows/noncreatable.md)|Define un objeto que no pueden crearse instancias por sí mismo.|
|[nonextensible](../windows/nonextensible.md)|Especifica que el `IDispatch` implementación incluye solo las propiedades y los métodos enumeran en la descripción de la interfaz y no se pueden ampliar con miembros adicionales en tiempo de ejecución.|
|[object](../windows/object-cpp.md)|Identifica una interfaz personalizada; es sinónimo de atributo personalizado.|
|[odl](../windows/odl.md)|Identifica una interfaz como una interfaz de lenguaje de descripción de objetos (ODL).|
|[oleautomation](../windows/oleautomation.md)|Indica que una interfaz es compatible con la automatización.|
|[Opcional](../windows/optional-cpp.md)|Especifica un parámetro opcional para una función miembro.|
|[out](../windows/out-cpp.md)|Identifica los parámetros de puntero devueltos desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).|
|[pointer_default](../windows/pointer-default.md)|Especifica el atributo de puntero predeterminado para todos los punteros, excepto los punteros de nivel superior que aparecen en las listas de parámetros.|
|[pragma](../windows/pragma.md)|Emite la cadena especificada, sin los caracteres de comillas en el archivo .idl generado.|
|[progid](../windows/progid.md)|Especifica el ProgID de un objeto COM.|
|[propget](../windows/propget.md)|Especifica una función de descriptor de acceso (get) de la propiedad.|
|[propput](../windows/propput.md)|Especifica una función de valor de propiedad.|
|[propputref](../windows/propputref.md)|Especifica una función de la configuración de propiedad que utiliza una referencia en lugar de un valor.|
|[ptr](../windows/ptr.md)|Designa un puntero como un puntero completo.|
|[public](../windows/public-cpp-attributes.md)|Garantiza que una definición de tipo pasará a la biblioteca de tipos aunque no se hace referencia desde dentro del archivo. idl.|
|[intervalo](../windows/range-cpp.md)|Especifica un intervalo de valores permitidos para los argumentos o los campos cuyos valores se establecen en tiempo de ejecución.|
|[rdx](../windows/rdx.md)|Crea o modifica una clave del registro.|
|[readonly](../windows/readonly-cpp.md)|Prohíbe la asignación a una variable.|
|[ref](../windows/ref-cpp.md)|Identifica un puntero de referencia.|
|[registration_script](../windows/registration-script.md)|Ejecuta el script de registro especificado.|
|[requestedit](../windows/requestedit.md)|Indica que la propiedad admite la `OnRequestEdit` notificación.|
|[requires_category](../windows/requires-category.md)|Especifica las categorías de los componentes necesarios para la clase.|
|[restricted](../windows/restricted.md)|Especifica que una biblioteca o miembro de un módulo, interfaz o dispinterface no se puede llamar arbitrariamente.|
|[retval](../windows/retval.md)|Designa el parámetro que recibe el valor devuelto del miembro.|
|[satype](../windows/satype.md)|Especifica el tipo de datos de la `SAFEARRAY`.|
|[size_is](../windows/size-is.md)|Especifica el tamaño de memoria asignada para los punteros de tamaño, tamaño de punteros a punteros de tamaño y solo - o matrices multidimensionales.|
|[source](../windows/source-cpp.md)|Indica que un miembro de clase, propiedad o método es un origen de eventos.|
|[string](../windows/string-cpp.md)|Indica que unidimensional **char**, **wchar_t**, `byte`, o matriz equivalente o el puntero a este tipo de matriz debe tratarse como una cadena.|
|[support_error_info](../windows/support-error-info.md)|Admite informes de errores para el objeto de destino.|
|[switch_is](../windows/switch-is.md)|Especifica la expresión o el identificador que actúa como la unión discriminante que selecciona al miembro de unión.|
|[switch_type](../windows/switch-type.md)|Identifica el tipo de la variable utilizada como la unión discriminante.|
|[synchronize](../windows/synchronize.md)|Sincroniza el acceso a un método.|
|[Subprocesamiento](../windows/threading-cpp.md)|Especifica el modelo de subprocesos para un objeto COM.|
|[transmit_as](../windows/transmit-as.md)|Indica al compilador para asociar un tipo presentado, manipulan las aplicaciones cliente y servidor, con un tipo transmitido.|
|[uidefault](../windows/uidefault.md)|Indica que el miembro de la información de tipo es el miembro predeterminado para su presentación en la interfaz de usuario.|
|[unique](../windows/unique-cpp.md)|Especifica un puntero único.|
|[usesgetlasterror](../windows/usesgetlasterror.md)|Indica que el llamador que si se produce un error al llamar a esa función, el llamador puede, a continuación, llamar a `GetLastError` para recuperar el código de error.|
|[uuid](../windows/uuid-cpp-attributes.md)|Especifica el identificador único para una clase o interfaz.|
|[v1_enum](../windows/v1-enum.md)|Indica que el tipo enumerado especificado se transmite como una entidad de 32 bits, en lugar de con el valor predeterminado de 16 bits.|
|[vararg](../windows/vararg.md)|Especifica que la función toma un número variable de argumentos.|
|[version](../windows/version-cpp.md)|Identifica una versión determinada entre varias versiones de una interfaz o clase.|
|[vi_progid](../windows/vi-progid.md)|Especifica una forma independiente de la versión de ProgID.|
|[wire_marshal](../windows/wire-marshal.md)|Especifica un tipo de datos que se usará para la transmisión en lugar de un tipo de datos específicos de la aplicación.|

## <a name="see-also"></a>Vea también

[Referencia de atributos de C++](../windows/cpp-attributes-reference.md)  
[Conceptos](../windows/attributed-programming-concepts.md)  
[Atributos por grupo](../windows/attributes-by-group.md)  
[Atributos por uso](../windows/attributes-by-usage.md)