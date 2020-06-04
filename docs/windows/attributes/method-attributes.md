---
title: Atributos de métodoC++ (com)
ms.date: 10/02/2018
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
ms.openlocfilehash: c9823869be96f53a3c4fbc36c7b56e1bea0a1303
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166775"
---
# <a name="method-attributes"></a>Atributos de método

Los siguientes atributos se aplican a los métodos de una clase, coclase o interfaz.

|Atributo|Descripción|
|---------------|-----------------|
|[bindable](bindable.md)|Indica que la propiedad admite enlace de datos.|
|[call_as](call-as.md)|Habilita una función no utilizables que se va a asignar a una función remota.|
|[custom](custom-cpp.md)|Permite definir su propio atributo.|
|[db_column](db-column.md)|Enlaza una columna especificada al conjunto de filas.|
|[db_command](db-command.md)|Crea un comando OLE DB.|
|[db_param](db-param.md)|Asocia la variable miembro especificada a un parámetro de entrada o de salida y delimita la variable.|
|[db_source](db-source.md)|Crea una conexión a un origen de datos.|
|[db_table](db-table.md)|Abre una tabla de OLE DB.|
|[defaultbind](defaultbind.md)|Indica la única propiedad enlazable que mejor representa el objeto.|
|[defaultcollelem](defaultcollelem.md)|Se usa para Visual Basic la optimización del código.|
|[displaybind](displaybind.md)|Indica una propiedad que se debe mostrar al usuario como enlazable.|
|[helpcontext](helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información sobre este elemento en el archivo de **ayuda** .|
|[helpfile](helpfile.md)|Establece el nombre del archivo de **ayuda** para una biblioteca de tipos.|
|[helpstring](helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|
|[helpstringcontext](helpstringcontext.md)|Especifica el identificador de un tema de ayuda en un archivo. hlp o. chm.|
|[helpstringdll](helpstringdll.md)|Especifica el nombre del archivo DLL que se va a usar para realizar la búsqueda de cadenas de documento (localización).|
|[hidden](hidden.md)|Indica que el elemento existe, pero no se debe mostrar en un explorador orientado al usuario.|
|[id](id.md)|Especifica un DISPID para una función miembro (ya sea una propiedad o un método, en una interfaz o dispinterface).|
|[immediatebind](immediatebind.md)|Indica que se notificará inmediatamente a la base de datos todos los cambios efectuados en una propiedad de un objeto enlazado a datos.|
|[in](in-cpp.md)|Indica que se va a pasar un parámetro del procedimiento que realiza la llamada al procedimiento llamado.|
|[local](local-cpp.md)|Permite usar el compilador MIDL como generador de encabezados cuando se usa en el encabezado de la interfaz. Cuando se usa en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.|
|[nonbrowsable](nonbrowsable.md)|Indica que un miembro de interfaz no se debe mostrar en un explorador de propiedades.|
|[propget](propget.md)|Especifica una función de descriptor de acceso de propiedad.|
|[propput](propput.md)|Especifica una función de configuración de propiedades.|
|[propputref](propputref.md)|Especifica una función de configuración de propiedades que usa una referencia en lugar de un valor.|
|[ptr](ptr.md)|Designa un puntero como un puntero completo.|
|[range](range-cpp.md)|Especifica un intervalo de valores permitidos para los argumentos o campos cuyos valores se establecen en tiempo de ejecución.|
|[requestedit](requestedit.md)|Indica que la propiedad admite la notificación `OnRequestEdit`.|
|[restricted](restricted.md)|Especifica que no se puede llamar a un miembro de un módulo, interfaz o dispinterface arbitrariamente.|
|[satype](satype.md)|Especifica el tipo de datos de la estructura de `SAFEARRAY`.|
|[de origen](source-cpp.md)|Especifica las interfaces de origen del control para los puntos de conexión de una clase. En una propiedad o método, el atributo `source` indica que el miembro devuelve un objeto o una variante que es un origen de eventos.|
|[synchronize](synchronize.md)|Sincroniza el acceso al método de destino.|
|[vararg](vararg.md)|Especifica que la función toma un número variable de argumentos.|

## <a name="see-also"></a>Consulte también

[Atributos por uso](attributes-by-usage.md)
