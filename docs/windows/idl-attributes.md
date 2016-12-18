---
title: "IDL Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributes [C++], reference topics"
  - "IDL attributes"
  - ".idl files, attributes"
  - "IDL files, attributes"
  - ".idl files"
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDL Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Tradicionalmente, mantener un archivo .idl significaba que tuvo que:  
  
-   Está familiarizado con la estructura y la sintaxis de un archivo .idl poder modificarlo.  
  
-   Confíe en un asistente, que le permitiría modificar algunos aspectos del archivo .idl.  
  
 Ahora, puede modificar el archivo .idl de un archivo de código fuente utilizando los atributos de Visual C\+\+ IDL.  En muchos casos, los atributos de Visual C\+\+ IDL tienen el mismo nombre que los atributos MIDL.  Cuando el nombre de un atributo de Visual C\+\+ IDL y un atributo MIDL son iguales, significa que colocar el atributo de Visual C\+\+ en el archivo de código fuente dará lugar a un archivo .idl que contiene el atributo de MIDL de homónimo.  Sin embargo, un atributo de Visual C\+\+ IDL no puede proporcionar toda la funcionalidad de un atributo MIDL.  
  
 Cuando no estaban utilizados con [atributos COM](../Topic/COM%20Attributes.md), atributos IDL permiten definir interfaces.  Cuando el código fuente se compila, los atributos se utilizan para definir el archivo generado .idl.  Cuando se usa con atributos COM en un proyecto ATL, los atributos de algún IDL, como **CoClass**, hacen que el código en el proyecto.  
  
 Observe que [idl\_quote](../windows/idl-quote.md) permite utilizar las construcciones de MIDL que no se admiten en la versión actual de Visual C\+\+.  Éste y otros atributos como [importlib](../windows/importlib.md) y [includelib](../windows/includelib-cpp.md) ayudan a utilizar los archivos existentes .idl del proyecto actual de Visual C\+\+.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|[aggregatable](../Topic/aggregatable.md)|Indica que un control se puede agregar a otro control.|  
|[appobject](../Topic/appobject.md)|Identifica la coclase como objeto application, que está asociado a una aplicación completa EXE, e indica que las funciones y propiedades coclass son globalmente disponible en esta biblioteca de tipos.|  
|[async\_uuid](../Topic/async_uuid.md)|Especifica el identificador UUID que indica al compilador de MIDL definir versiones sincrónicas y asincrónicas de una interfaz COM.|  
|[bindable](../windows/bindable.md)|Indica que la propiedad admite enlace de datos.|  
|[call\_as](../windows/call-as.md)|Permite a una función de uso no remoto que se va a asignar a una función remota.|  
|[case](../windows/case-cpp.md)|Utilizado con el atributo de [switch\_type](../windows/switch-type.md) en una combinación.|  
|[CoClass](../windows/coclass.md)|Coloca la definición de clase en un archivo .idl como coclase.|  
|[Control](../windows/control.md)|especifica que el tipo definido por el usuario es un control.|  
|[cpp\_quote](../Topic/cpp_quote.md)|Emite la cadena especificada, sin los caracteres de la expresión, el archivo de encabezado generado.|  
|[defaultbind](../windows/defaultbind.md)|Indica la propiedad única, enlazable que mejor representa el objeto.|  
|[defaultcollelem](../windows/defaultcollelem.md)|Se utiliza para la optimización del código de Visual Basic.|  
|[defaultvalue](../Topic/defaultvalue.md)|Permite la especificación de un valor predeterminado de un parámetro opcional con tipo.|  
|[default](../windows/default-cpp.md)|Indica que la personalizado o el dispinterface definido dentro de una coclase representa la interfaz predeterminada de la programación.|  
|[defaultvtable](../windows/defaultvtable.md)|Define una interfaz como interfaz vtable predeterminada de un control.|  
|[dispinterface](../windows/dispinterface.md)|Coloca una interfaz en el archivo .idl como interfaz de envío.|  
|[displaybind](../windows/displaybind.md)|Indica una propiedad que se debe mostrar al usuario como enlazable.|  
|[dual](../Topic/dual.md)|Coloca una interfaz en el archivo .idl como interfaz dual.|  
|[entrada](../windows/entry.md)|Especifica una función o una constante exportada en un módulo identifica el punto de entrada en el archivo DLL.|  
|[first\_is](../windows/first-is.md)|Especifica el índice del primer elemento de matriz que se transmitirá.|  
|[helpcontext](../windows/helpcontext.md)|Especifica un Id. de contexto que deje la información de la vista de usuario sobre este elemento en el archivo de Ayuda.|  
|[helpfile](../Topic/helpfile.md)|Establece el nombre del archivo de Ayuda para una biblioteca de tipos.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Especifica el identificador de un tema de Ayuda en un archivo de .hlp o .chm.|  
|[helpstringdll](../windows/helpstringdll.md)|Especifica el nombre de DLL para utilizar para realizar la búsqueda de la cadena del documento \(localización\).|  
|[helpstring](../windows/helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|  
|[hidden](../Topic/hidden.md)|Indica que el elemento existe pero no se debe mostrar en un explorador del usuario.|  
|[idl\_module](../windows/idl-module.md)|Especifica un punto de entrada en el archivo DLL.|  
|[idl\_quote](../windows/idl-quote.md)|Permite usar los atributos o construcciones IDL que no se admiten en la versión actual de Visual C\+\+.|  
|[id](../windows/id.md)|Especifica un DISPID para una función miembro \(una propiedad o método, en una interfaz o dispinterface\).|  
|[iid\_is](../windows/iid-is.md)|Especifica el IID de la interfaz COM indicada por un puntero de interfaz.|  
|[immediatebind](../windows/immediatebind.md)|Indica que la base de datos se notifique inmediatamente de todos los cambios de una propiedad de un objeto enlazado a datos.|  
|[importlib](../windows/importlib.md)|Muestra tipos que han sido ya compilados en otra biblioteca de tipos disponible a la biblioteca de tipos que se creó.|  
|[import](../windows/import.md)|Especifica otro .idl, .odl, o archivo de encabezado que contiene definiciones que desea hacer referencia en el archivo principal .idl.|  
|[incluir](../windows/include-cpp.md)|Especifica uno o más archivos de encabezado que se incluirán en el archivo generado .idl.|  
|[includelib](../windows/includelib-cpp.md)|Produce un archivo .idl o .h que se incluirá en el archivo generado .idl.|  
|[in](../Topic/in%20\(C++\).md)|Indica que un parámetro debe ser el último procedimiento de llamada al procedimiento.|  
|[last\_is](../windows/last-is.md)|Especifica el índice del elemento de la matriz pasado que se transmitirá.|  
|[LCID](../windows/lcid.md)|Permite pasar un Id. de configuración regional a una función.|  
|[length\_is](../windows/length-is.md)|especifica el número de elementos de matriz que se transmitirán.|  
|[licencia](../windows/licensed.md)|Indica que la coclase a los que se aplica es el licencia, y debe crearse instancias mediante **IClassFactory2**.|  
|[local](../windows/local-cpp.md)|Permite utilizar el compilador MIDL como generador de encabezado cuando se usa en el encabezado de la interfaz.  Cuando se utiliza en una función individual, elija un procedimiento local para el que no se genera ningún códigos auxiliares.|  
|[max\_is](../windows/max-is.md)|Indica el valor máximo de un índice válido de la matriz.|  
|[módulo](../windows/module-cpp.md)|Define la biblioteca bloqueado en el archivo .idl.|  
|[ms\_union](../windows/ms-union.md)|controla la alineación de la representación de datos de la red de uniones nonencapsulated.|  
|[no\_injected\_text](../windows/no-injected-text.md)|Evita que el compilador inserte código como resultado de uso del atributo.|  
|[nonbrowsable](../Topic/nonbrowsable.md)|Indica que un miembro de interfaz no debería mostrarse en un explorador de propiedades.|  
|[noncreatable](../windows/noncreatable.md)|Define un objeto que no se puede crear instancias en sí mismo.|  
|[nonextensible](../Topic/nonextensible.md)|Especifica que la implementación de `IDispatch` incluye únicamente las propiedades y los métodos mostrados en la descripción de la interfaz y no se puede extender con miembros adicionales en tiempo de ejecución.|  
|[Objeto.](../Topic/object%20\(C++\).md)|identifica una interfaz personalizada; sinónimo con atributos personalizados.|  
|[odl](../windows/odl.md)|Identifica una interfaz como una interfaz \(ODL\) del Lenguaje de descripción de objetos.|  
|[oleautomation](../windows/oleautomation.md)|Indica que una interfaz es compatible con automatización.|  
|[opcional](../windows/optional-cpp.md)|Especifica un parámetro opcional de una función miembro.|  
|[out](../Topic/out%20\(C++\).md)|Identifica los parámetros del puntero que se devuelven de procedimiento denominado al procedimiento de llamada \(servidor al cliente\).|  
|[pointer\_default](../windows/pointer-default.md)|Especifica el atributo predeterminado de puntero para todos los punteros excepto los punteros de nivel superior que aparecen en listas de parámetros.|  
|[pragma](../windows/pragma.md)|Emite la cadena especificada, sin los caracteres de la expresión, el archivo generado .idl.|  
|[ProgID](../Topic/progid.md)|especifica ProgID para un objeto COM.|  
|[propget](../windows/propget.md)|Especifica una función de descriptor de acceso de la propiedad \(get\).|  
|[propputref](../windows/propputref.md)|Especifica una función de la configuración de propiedades que utilice una referencia en lugar de un valor.|  
|[propput](../windows/propput.md)|Especifica una función de la configuración de propiedades.|  
|[PTR](../windows/ptr.md)|Elija un puntero como puntero completo.|  
|[public](../windows/public-cpp-attributes.md)|Garantiza que una definición entre la biblioteca de tipos aunque no se haga referencia dentro del archivo .idl.|  
|[intervalo](../Topic/range%20\(C++\).md)|Especifica un intervalo de valores permitidos para los argumentos o campos cuyos valores se establecen en tiempo de ejecución.|  
|[readonly](../windows/readonly-cpp.md)|prohíbe la asignación a una variable.|  
|[ref](../windows/ref-cpp.md)|Identifica un puntero de referencia.|  
|[requestedit](../windows/requestedit.md)|indica que la propiedad admite la notificación de **OnRequestEdit** .|  
|[restricted](../windows/restricted.md)|Especifica que una biblioteca, o miembro de módulo, interfaz, o de dispinterface no se puede llamar arbitrariamente.|  
|[retval](../windows/retval.md)|Designa el parámetro que recibe el valor devuelto del miembro.|  
|[size\_is](../Topic/size_is.md)|Especifica el tamaño de memoria asignado para punteros ordenados, punteros a punteros ordenados, y solo ordenados o matrices multidimensionales.|  
|[source](../Topic/source%20\(C++\).md)|Indica que un miembro de una clase, una propiedad, o un método es un origen de eventos.|  
|[string](../windows/string-cpp.md)|Indica que `char`unidimensional, `wchar_t`, **byte**, matriz o equivalente o el puntero a este tipo de matriz se deben tratar como una cadena.|  
|[switch\_is](../windows/switch-is.md)|Especifica la expresión o el identificador que actúa como la combinación discriminante que selecciona a la union.|  
|[switch\_type](../windows/switch-type.md)|Identifica el tipo de la variable utilizada como unión discriminante.|  
|[transmit\_as](../windows/transmit-as.md)|Indica al compilador para asociar un tipo actual, que las aplicaciones cliente y servidor manipulan, con un tipo transmitido.|  
|[uidefault](../Topic/uidefault.md)|Indica que el miembro de la información de tipos es el miembro predeterminado para la presentación en la interfaz de usuario.|  
|[único](../windows/unique-cpp.md)|especifica un puntero único.|  
|[usesgetlasterror](../windows/usesgetlasterror.md)|Indica al llamador que si hay un error al llamar a la función, el llamador puede llamar `GetLastError` para recuperar el código de error.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Especifica el identificador único para una clase o interfaz.|  
|[v1\_enum](../windows/v1-enum.md)|Dirige que transmiten al tipo enumerado especificado como entidad de 32 bits, en lugar del valor predeterminado de 16 bits.|  
|[vararg](../windows/vararg.md)|especifica que la función toma un número variable de argumentos.|  
|[vi\_progid](../windows/vi-progid.md)|especifica un formulario de la versión\-independiente de ProgID.|  
|[wire\_marshal](../windows/wire-marshal.md)|Especifica un tipo de datos que se usará para la transmisión en lugar de un tipo de datos específico de la aplicación.|  
  
## Vea también  
 [Attributes by Group](../windows/attributes-by-group.md)   
 [Attribute Limitations](http://msdn.microsoft.com/es-es/6e6c4329-f667-4869-b991-cbe9cb7a8f61)