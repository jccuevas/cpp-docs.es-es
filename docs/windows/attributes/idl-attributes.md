---
title: Atributos IDL (COM de C++)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- IDL attributes
- .idl files [C++], attributes
- IDL files [C++], attributes
- .idl files [C++]
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
ms.openlocfilehash: a699e327eec056bbb36747840990bb9c7ccc259b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039517"
---
# <a name="idl-attributes"></a>Atributos IDL

Tradicionalmente, el mantenimiento de un archivo .idl significaba que debía para:

- Estar familiarizado con la estructura y la sintaxis de un archivo IDL para poder modificarlo.

- Se basan en un asistente, lo que le permitiría modificar algunos aspectos del archivo. idl.

Ahora, puede modificar el archivo .idl desde un archivo de código fuente con atributos IDL de Visual C++. En muchos casos, los atributos IDL de Visual C++ tienen el mismo nombre que los atributos MIDL. Cuando el nombre de un atributo IDL de Visual C++ y un atributo MIDL son los mismos, significa que dará como resultado colocando el atributo de Visual C++ en el archivo de código fuente en un archivo .idl que contenga su atributo MIDL homónimo en inglés. Sin embargo, un atributo IDL de Visual C++ puede proporcionar toda la funcionalidad de un atributo MIDL.

Cuando no se usa con [atributos COM](com-attributes.md), los atributos IDL le permiten definir interfaces. Cuando se compila el código fuente, los atributos se usan para definir el archivo .idl generado. Cuando se usa con atributos COM en un proyecto ATL, algunos atributos IDL, tales como `coclass`, para insertarse en el proyecto de código.

Tenga en cuenta que [idl_quote](idl-quote.md) permite usar construcciones MIDL que no se admiten en la versión actual de Visual C++. Este y otros atributos como [importlib](importlib.md) y [includelib](includelib-cpp.md) le ayudarán a utilizar los archivos .idl existentes en el proyecto actual de Visual C++.

|Atributo|Descripción|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indica que se puede agregar un control por otro control.|
|[appobject](appobject.md)|Identifica la coclase como un objeto de aplicación, que está asociado a una aplicación completa del archivo EXE e indica que las funciones y propiedades de la coclase están disponibles globalmente en esta biblioteca de tipos.|
|[async_uuid](async-uuid.md)|Especifica el UUID que indica al compilador MIDL para definir las versiones sincrónicas y asincrónicas de una interfaz COM.|
|[bindable](bindable.md)|Indica que la propiedad admite enlace de datos.|
|[call_as](call-as.md)|Permite que una función utilizables para asignarse a una función remota.|
|[case](case-cpp.md)|Puede usar con el [switch_type](switch-type.md) atributo en una unión.|
|[coclase](coclass.md)|Sitios de la clase definición en un archivo .idl como coclase.|
|[control](control.md)|Especifica que el tipo definido por el usuario es un control.|
|[cpp_quote](cpp-quote.md)|Emite la cadena especificada, sin los caracteres de comillas en el archivo de encabezado generado.|
|[defaultbind](defaultbind.md)|Indica la única propiedad enlazable que mejor representa al objeto.|
|[defaultcollelem](defaultcollelem.md)|Se usa para la optimización de código de Visual Basic.|
|[defaultvalue](defaultvalue.md)|Permite especificar un valor predeterminado para un parámetro opcional con tipo.|
|[default](default-cpp.md)|Indica que la interfaz personalizada o dispinterface definida en una coclase representa la interfaz de programación predeterminada.|
|[defaultvtable](defaultvtable.md)|Define una interfaz que la interfaz de vtable predeterminada para un control.|
|[dispinterface](dispinterface.md)|Coloca una interfaz en el archivo .idl como interfaz de envío.|
|[displaybind](displaybind.md)|Indica una propiedad que debe mostrarse al usuario como enlazable.|
|[dual](dual.md)|Coloca una interfaz en el archivo .idl como una interfaz dual.|
|[entry](entry.md)|Especifica una constante o una función exportada de un módulo mediante la identificación de punto de entrada en el archivo DLL.|
|[first_is](first-is.md)|Especifica el índice del primer elemento de matriz que se transmitan.|
|[helpcontext](helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el archivo de ayuda.|
|[helpfile](helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|
|[helpstringcontext](helpstringcontext.md)|Especifica el identificador de un tema de ayuda en un archivo .hlp o chm.|
|[helpstringdll](helpstringdll.md)|Especifica el nombre del archivo DLL a utilizar para realizar la búsqueda de cadenas de documento (localización).|
|[helpstring](helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|
|[hidden](hidden.md)|Indica que el elemento existe pero no debe mostrarse en un explorador orientado al usuario.|
|[idl_module](idl-module.md)|Especifica un punto de entrada en un archivo DLL.|
|[idl_quote](idl-quote.md)|Le permite usar los atributos o IDL construcciones que no se admiten en la versión actual de Visual C++.|
|[identificador](id.md)|Especifica un DISPID para una función miembro (una propiedad o un método en una interfaz o interfaz dispinterface).|
|[iid_is](iid-is.md)|Especifica el IID de la interfaz COM que apunta a un puntero de interfaz.|
|[immediatebind](immediatebind.md)|Indica que la base de datos será notificada inmediatamente de todos los cambios a una propiedad de un objeto enlazado a datos.|
|[importlib](importlib.md)|Hace que los tipos que ya se han compilado en otra biblioteca de tipos estén disponibles en la biblioteca de tipos que se está creando.|
|[import](import.md)|Especifica otro archivo .idl, .odl o encabezado que contiene las definiciones que desea hacer referencia desde el archivo .idl principal.|
|[include](include-cpp.md)|Especifica uno o varios archivos de encabezado que se incluirán en el archivo .idl generado.|
|[includelib](includelib-cpp.md)|Hace que un archivo IDL o .h para incluirse en el archivo .idl generado.|
|[in](in-cpp.md)|Indica que es un parámetro que se pasan desde el procedimiento que realiza la llamada al procedimiento llamado.|
|[last_is](last-is.md)|Especifica el índice del último elemento de matriz que se transmitan.|
|[lcid](lcid.md)|Le permite pasar un identificador de configuración regional a una función.|
|[length_is](length-is.md)|Especifica el número de elementos de matriz que se transmitan.|
|[licensed](licensed.md)|Indica que la coclase al que se aplica con licencia y se debe crear instancias mediante `IClassFactory2`.|
|[local](local-cpp.md)|Permite usar el compilador de MIDL como un generador de encabezado cuando se utiliza en el encabezado de la interfaz. Cuando se utiliza en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.|
|[max_is](max-is.md)|Designa el valor máximo para un índice de matriz válida.|
|[module](module-cpp.md)|Define el bloque de biblioteca en el archivo .idl.|
|[ms_union](ms-union.md)|Controla la alineación de representación de datos de red de uniones nonencapsulated.|
|[no_injected_text](no-injected-text.md)|Impide que el compilador inserte el código como resultado el uso de atributo.|
|[nonbrowsable](nonbrowsable.md)|Indica que un miembro de interfaz no debe mostrarse en un explorador de propiedades.|
|[noncreatable](noncreatable.md)|Define un objeto que no pueden crearse instancias por sí mismo.|
|[nonextensible](nonextensible.md)|Especifica que el `IDispatch` implementación incluye solo las propiedades y los métodos enumeran en la descripción de la interfaz y no se pueden ampliar con miembros adicionales en tiempo de ejecución.|
|[object](object-cpp.md)|Identifica una interfaz personalizada; es sinónimo de atributo personalizado.|
|[odl](odl.md)|Identifica una interfaz como una interfaz de lenguaje de descripción de objetos (ODL).|
|[oleautomation](oleautomation.md)|Indica que una interfaz es compatible con la automatización.|
|[optional](optional-cpp.md)|Especifica un parámetro opcional para una función miembro.|
|[out](out-cpp.md)|Identifica los parámetros de puntero devueltos desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).|
|[pointer_default](pointer-default.md)|Especifica el atributo de puntero predeterminado para todos los punteros, excepto los punteros de nivel superior que aparecen en las listas de parámetros.|
|[pragma](pragma.md)|Emite la cadena especificada, sin los caracteres de comillas en el archivo .idl generado.|
|[progid](progid.md)|Especifica el ProgID de un objeto COM.|
|[propget](propget.md)|Especifica una función de descriptor de acceso (get) de la propiedad.|
|[propputref](propputref.md)|Especifica una función de la configuración de propiedad que utiliza una referencia en lugar de un valor.|
|[propput](propput.md)|Especifica una función de valor de propiedad.|
|[ptr](ptr.md)|Designa un puntero como un puntero completo.|
|[public](public-cpp-attributes.md)|Garantiza que una definición de tipo pasará a la biblioteca de tipos aunque no se hace referencia desde dentro del archivo. idl.|
|[range](range-cpp.md)|Especifica un intervalo de valores permitidos para los argumentos o los campos cuyos valores se establecen en tiempo de ejecución.|
|[readonly](readonly-cpp.md)|Prohíbe la asignación a una variable.|
|[ref](ref-cpp.md)|Identifica un puntero de referencia.|
|[requestedit](requestedit.md)|Indica que la propiedad admite la notificación `OnRequestEdit`.|
|[restricted](restricted.md)|Especifica que una biblioteca o miembro de un módulo, interfaz o dispinterface no se puede llamar arbitrariamente.|
|[retval](retval.md)|Designa el parámetro que recibe el valor devuelto del miembro.|
|[size_is](size-is.md)|Especifica el tamaño de memoria asignada para los punteros de tamaño, tamaño de punteros a punteros de tamaño y solo - o matrices multidimensionales.|
|[source](source-cpp.md)|Indica que un miembro de clase, propiedad o método es un origen de eventos.|
|[string](string-cpp.md)|Indica que unidimensional **char**, **wchar_t**, `byte`, o matriz equivalente o el puntero a este tipo de matriz debe tratarse como una cadena.|
|[switch_is](switch-is.md)|Especifica la expresión o el identificador que actúa como la unión discriminante que selecciona al miembro de unión.|
|[switch_type](switch-type.md)|Identifica el tipo de la variable utilizada como la unión discriminante.|
|[transmit_as](transmit-as.md)|Indica al compilador para asociar un tipo presentado, manipulan las aplicaciones cliente y servidor, con un tipo transmitido.|
|[uidefault](uidefault.md)|Indica que el miembro de la información de tipo es el miembro predeterminado para su presentación en la interfaz de usuario.|
|[unique](unique-cpp.md)|Especifica un puntero único.|
|[usesgetlasterror](usesgetlasterror.md)|Indica que el llamador que si se produce un error al llamar a esa función, el llamador puede, a continuación, llamar a `GetLastError` para recuperar el código de error.|
|[uuid](uuid-cpp-attributes.md)|Especifica el identificador único para una clase o interfaz.|
|[v1_enum](v1-enum.md)|Indica que el tipo enumerado especificado se transmite como una entidad de 32 bits, en lugar de con el valor predeterminado de 16 bits.|
|[vararg](vararg.md)|Especifica que la función toma un número variable de argumentos.|
|[vi_progid](vi-progid.md)|Especifica una forma independiente de la versión de ProgID.|
|[wire_marshal](wire-marshal.md)|Especifica un tipo de datos que se usará para la transmisión en lugar de un tipo de datos específicos de la aplicación.|

## <a name="see-also"></a>Vea también

[Atributos por grupo](attributes-by-group.md)
