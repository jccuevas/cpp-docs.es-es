---
title: Atributos IDL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], reference topics
- IDL attributes
- .idl files, attributes
- IDL files, attributes
- .idl files
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5c522c039a0471240ba319561485e8cc7f348aaa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881554"
---
# <a name="idl-attributes"></a>Atributos IDL
Tradicionalmente, el mantenimiento de un archivo .idl significaba que tenía que:  
  
-   Estar familiarizado con la estructura y la sintaxis de un archivo IDL para poder modificarlo.  
  
-   Se basan en un asistente que permita modificar algunos aspectos del archivo .idl.  
  
 Ahora, puede modificar el archivo .idl desde dentro de un archivo de código fuente con atributos IDL de Visual C++. En muchos casos, los atributos IDL de Visual C++ tienen el mismo nombre que los atributos MIDL. Cuando el nombre de un atributo IDL de Visual C++ y un atributo MIDL son iguales, significa que la colocación del atributo de Visual C++ en el archivo de código fuente dará como resultado un archivo .idl que contiene el atributo MIDL homónimo. Sin embargo, un atributo IDL de Visual C++ no puede proporcionar toda la funcionalidad de un atributo MIDL.  
  
 Cuando no se utiliza con [atributos COM](../windows/com-attributes.md), atributos IDL le permiten definir interfaces. Cuando se compila el código fuente, los atributos se utilizan para definir el archivo .idl generado. Cuando se usa con atributos de COM en un proyecto ATL, algunos atributos IDL, como **coclase**, hacer código se insertará en el proyecto.  
  
 Tenga en cuenta que [idl_quote](../windows/idl-quote.md) permite usar las construcciones de MIDL no se admiten en la versión actual de Visual C++. Este y otros atributos como [importlib](../windows/importlib.md) y [includelib](../windows/includelib-cpp.md) le ayudarán a utilizar los archivos .idl existentes en el proyecto actual de Visual C++.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|Indica que se puede agregar un control de otro control.|  
|[appobject](../windows/appobject.md)|Identifica la coclase como un objeto de aplicación, que está asociado a una aplicación completa del archivo EXE e indica que las funciones y propiedades de la coclase que están disponibles globalmente en esta biblioteca de tipos.|  
|[async_uuid](../windows/async-uuid.md)|Especifica el UUID que hace que el compilador MIDL para definir versiones sincrónicas y asincrónicas de una interfaz COM.|  
|[bindable](../windows/bindable.md)|Indica que la propiedad admite enlace de datos.|  
|[call_as](../windows/call-as.md)|Permite que una función utilizables que debe asignarse a una función remota.|  
|[case](../windows/case-cpp.md)|Usar con el [switch_type](../windows/switch-type.md) atributo en una unión.|  
|[coclass](../windows/coclass.md)|Definición en un archivo .idl como coclase de sitios de la clase.|  
|[control](../windows/control.md)|Especifica que el tipo definido por el usuario es un control.|  
|[cpp_quote](../windows/cpp-quote.md)|Emite la cadena especificada, sin los caracteres de comillas, en el archivo de encabezado generado.|  
|[defaultbind](../windows/defaultbind.md)|Indica la única propiedad enlazable que mejor representa el objeto.|  
|[defaultcollelem](../windows/defaultcollelem.md)|Se usa para la optimización de código de Visual Basic.|  
|[defaultvalue](../windows/defaultvalue.md)|Permite la especificación de un valor predeterminado para un parámetro opcional con tipo.|  
|[default](../windows/default-cpp.md)|Indica que la interfaz personalizada o dispinterface definida en una coclase representa la interfaz de programación predeterminada.|  
|[defaultvtable](../windows/defaultvtable.md)|Define una interfaz como la interfaz de vtable predeterminada para un control.|  
|[dispinterface](../windows/dispinterface.md)|Coloca una interfaz en el archivo .idl como interfaz de envío.|  
|[displaybind](../windows/displaybind.md)|Indica una propiedad que se debe mostrar al usuario como enlazable.|  
|[dual](../windows/dual.md)|Coloca una interfaz en el archivo .idl como una interfaz dual.|  
|[entry](../windows/entry.md)|Especifica una función exportada o constante en un módulo mediante la identificación de punto de entrada en el archivo DLL.|  
|[first_is](../windows/first-is.md)|Especifica el índice del primer elemento de matriz que se transmitan.|  
|[helpcontext](../windows/helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el archivo de ayuda.|  
|[helpfile](../windows/helpfile.md)|Establece el nombre del archivo de ayuda para una biblioteca de tipos.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Especifica el identificador de un tema de ayuda en un archivo .hlp o .chm.|  
|[helpstringdll](../windows/helpstringdll.md)|Especifica el nombre de la DLL a utilizar para realizar la búsqueda de cadena de documento (localización).|  
|[helpstring](../windows/helpstring.md)|Especifica una cadena de caracteres que se utiliza para describir el elemento al que se aplica.|  
|[hidden](../windows/hidden.md)|Indica que el elemento existe pero no se debe mostrar en un explorador orientado al usuario.|  
|[idl_module](../windows/idl-module.md)|Especifica un punto de entrada en un archivo DLL.|  
|[idl_quote](../windows/idl-quote.md)|Le permite usar atributos o IDL construcciones que no se admiten en la versión actual de Visual C++.|  
|[identificador](../windows/id.md)|Especifica un identificador DISPID de una función miembro (una propiedad o un método en una interfaz o dispinterface).|  
|[iid_is](../windows/iid-is.md)|Especifica el IID de la interfaz COM que señala un puntero de interfaz.|  
|[immediatebind](../windows/immediatebind.md)|Indica que se notificará inmediatamente a la base de datos de todos los cambios a una propiedad de un objeto enlazado a datos.|  
|[importlib](../windows/importlib.md)|Hace que los tipos que ya se han compilado en otra biblioteca de tipos estén disponibles en la biblioteca de tipos que se está creando.|  
|[import](../windows/import.md)|Especifica otro archivo de encabezado, .odl o .idl que contiene las definiciones que desea hacer referencia desde el archivo .idl principal.|  
|[include](../windows/include-cpp.md)|Especifica uno o más archivos de encabezado que se incluirá en el archivo .idl generado.|  
|[includelib](../windows/includelib-cpp.md)|Hace que un archivo IDL o .h para incluirse en el archivo .idl generado.|  
|[in](../windows/in-cpp.md)|Indica que es un parámetro que se pasan desde el procedimiento que realiza la llamada a procedimiento llamado.|  
|[last_is](../windows/last-is.md)|Especifica el índice del último elemento de matriz que se transmitan.|  
|[lcid](../windows/lcid.md)|Le permite pasar un identificador de configuración regional a una función.|  
|[length_is](../windows/length-is.md)|Especifica el número de elementos de la matriz que se transmitan.|  
|[licensed](../windows/licensed.md)|Indica que la coclase al que se aplica se autoriza el uso y se debe crear instancias con **IClassFactory2**.|  
|[Local](../windows/local-cpp.md)|Permite usar el compilador MIDL como un generador de encabezado cuando se utiliza en el encabezado de la interfaz. Cuando se utiliza en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.|  
|[max_is](../windows/max-is.md)|Designa el valor máximo para un índice de matriz válida.|  
|[Módulo](../windows/module-cpp.md)|Define el bloque de biblioteca en el archivo .idl.|  
|[ms_union](../windows/ms-union.md)|Controla la alineación de representación de datos de red de uniones nonencapsulated.|  
|[no_injected_text](../windows/no-injected-text.md)|Evita que el compilador inserte código como resultado del uso de atributos.|  
|[nonbrowsable](../windows/nonbrowsable.md)|Indica que un miembro de interfaz no debe mostrarse en un explorador de propiedades.|  
|[noncreatable](../windows/noncreatable.md)|Define un objeto que no se pueden crear instancias por sí mismo.|  
|[nonextensible](../windows/nonextensible.md)|Especifica que el `IDispatch` implementación incluye solo las propiedades y métodos aparecen en la descripción de interfaz y no se puede ampliar con miembros adicionales en tiempo de ejecución.|  
|[object](../windows/object-cpp.md)|Identifica una interfaz personalizada; es sinónimo de atributo personalizado.|  
|[odl](../windows/odl.md)|Identifica una interfaz como una interfaz de lenguaje de descripción de objetos (ODL).|  
|[oleautomation](../windows/oleautomation.md)|Indica que una interfaz es compatible con la automatización.|  
|[Opcional](../windows/optional-cpp.md)|Especifica un parámetro opcional para una función miembro.|  
|[out](../windows/out-cpp.md)|Identifica los parámetros de puntero devueltos desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).|  
|[pointer_default](../windows/pointer-default.md)|Especifica el atributo de puntero predeterminado para todos los punteros excepto los punteros de nivel superior que aparecen en las listas de parámetros.|  
|[pragma](../windows/pragma.md)|Emite la cadena especificada, sin los caracteres de comillas, en el archivo .idl generado.|  
|[progid](../windows/progid.md)|Especifica el ProgID de un objeto COM.|  
|[propget](../windows/propget.md)|Especifica una función de descriptor de acceso (get) de la propiedad.|  
|[propputref](../windows/propputref.md)|Especifica una función de valor de propiedad que utiliza una referencia en lugar de un valor.|  
|[propput](../windows/propput.md)|Especifica una función de valor de propiedad.|  
|[ptr](../windows/ptr.md)|Designa un puntero como un puntero completo.|  
|[public](../windows/public-cpp-attributes.md)|Garantiza que una definición de tipo pasará a la biblioteca de tipos aunque no se hace referencia desde dentro del archivo .idl.|  
|[intervalo](../windows/range-cpp.md)|Especifica un intervalo de valores permitidos para argumentos o los campos cuyos valores se establecen en tiempo de ejecución.|  
|[readonly](../windows/readonly-cpp.md)|Prohíbe la asignación a una variable.|  
|[ref](../windows/ref-cpp.md)|Identifica un puntero de referencia.|  
|[requestedit](../windows/requestedit.md)|Indica que la propiedad admite la **OnRequestEdit** notificación.|  
|[restricted](../windows/restricted.md)|Especifica que una biblioteca o miembro de un módulo, interfaz o dispinterface no se puede llamar arbitrariamente.|  
|[retval](../windows/retval.md)|Designa el parámetro que recibe el valor devuelto del miembro.|  
|[size_is](../windows/size-is.md)|Especifica el tamaño de memoria asignada para los punteros de tamaño, tamaño de punteros a punteros de tamaño y solo o matrices multidimensionales.|  
|[Origen](../windows/source-cpp.md)|Indica que un miembro de una clase, propiedad o método es un origen de eventos.|  
|[string](../windows/string-cpp.md)|Indica que unidimensional `char`, `wchar_t`, **bytes**, o equivalente matriz o el puntero a una matriz de este tipo debe tratarse como una cadena.|  
|[switch_is](../windows/switch-is.md)|Especifica la expresión o el identificador que actúa como la unión discriminante que selecciona al miembro de unión.|  
|[switch_type](../windows/switch-type.md)|Identifica el tipo de la variable utilizada como la unión discriminante.|  
|[transmit_as](../windows/transmit-as.md)|Indica al compilador para asociar un tipo presentado, manipulan las aplicaciones cliente y servidor, con un tipo de la información transmitido.|  
|[uidefault](../windows/uidefault.md)|Indica que el miembro de la información de tipo es el miembro predeterminado para su presentación en la interfaz de usuario.|  
|[unique](../windows/unique-cpp.md)|Especifica un puntero único.|  
|[usesgetlasterror](../windows/usesgetlasterror.md)|Indica que el llamador que si se produce un error al llamar a esa función, el llamador puede, a continuación, llamar a `GetLastError` para recuperar el código de error.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Especifica el identificador único para una clase o interfaz.|  
|[v1_enum](../windows/v1-enum.md)|Indica que el tipo enumerado especificado se transmiten como una entidad de 32 bits, en lugar de con el valor predeterminado de 16 bits.|  
|[vararg](../windows/vararg.md)|Especifica que la función toma un número variable de argumentos.|  
|[vi_progid](../windows/vi-progid.md)|Especifica una forma independiente de la versión de ProgID.|  
|[wire_marshal](../windows/wire-marshal.md)|Especifica un tipo de datos que se usará para la transmisión en lugar de un tipo de datos específicos de la aplicación.|  
  
## <a name="see-also"></a>Vea también  
 [Atributos por grupo](../windows/attributes-by-group.md)   
 [Limitaciones de los atributos](http://msdn.microsoft.com/en-us/6e6c4329-f667-4869-b991-cbe9cb7a8f61)