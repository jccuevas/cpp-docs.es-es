---
title: Atributos de método (COM de C++)
ms.date: 10/02/2018
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
ms.openlocfilehash: aa67d45dfc0fadd300caeaaeb8a7c25bb1c38bcb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023573"
---
# <a name="method-attributes"></a>Atributos de método

Los siguientes atributos se aplican a los métodos en una clase, coclase o interfaz.

|Atributo|Descripción|
|---------------|-----------------|
|[bindable](bindable.md)|Indica que la propiedad admite enlace de datos.|
|[call_as](call-as.md)|Permite que una función utilizables para asignarse a una función remota.|
|[custom](custom-cpp.md)|Le permite definir su propio atributo.|
|[db_column](db-column.md)|Enlaza una columna especificada para el conjunto de filas.|
|[db_command](db-command.md)|Crea un comando OLE DB.|
|[db_param](db-param.md)|La variable de miembro especificado se asocia con un parámetro de entrada o salido y delimita la variable.|
|[db_source](db-source.md)|Crea una conexión a un origen de datos.|
|[db_table](db-table.md)|Se abre una tabla de OLE DB.|
|[defaultbind](defaultbind.md)|Indica la única propiedad enlazable que mejor representa al objeto.|
|[defaultcollelem](defaultcollelem.md)|Se usa para la optimización de código de Visual Basic.|
|[displaybind](displaybind.md)|Indica una propiedad que debe mostrarse al usuario como enlazable.|
|[helpcontext](helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el **ayuda** archivo.|
|[helpfile](helpfile.md)|Establece el nombre de la **ayuda** archivo para una biblioteca de tipos.|
|[helpstring](helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|
|[helpstringcontext](helpstringcontext.md)|Especifica el identificador de un tema de ayuda en un archivo .hlp o chm.|
|[helpstringdll](helpstringdll.md)|Especifica el nombre del archivo DLL a utilizar para realizar la búsqueda de cadenas de documento (localización).|
|[hidden](hidden.md)|Indica que el elemento existe pero no debe mostrarse en un explorador orientado al usuario.|
|[identificador](id.md)|Especifica un DISPID para una función miembro (una propiedad o un método en una interfaz o interfaz dispinterface).|
|[immediatebind](immediatebind.md)|Indica que la base de datos será notificada inmediatamente de todos los cambios a una propiedad de un objeto enlazado a datos.|
|[in](in-cpp.md)|Indica que es un parámetro que se pasan desde el procedimiento que realiza la llamada al procedimiento llamado.|
|[local](local-cpp.md)|Permite usar el compilador de MIDL como un generador de encabezado cuando se utiliza en el encabezado de la interfaz. Cuando se utiliza en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.|
|[nonbrowsable](nonbrowsable.md)|Indica que un miembro de interfaz no debe mostrarse en un explorador de propiedades.|
|[propget](propget.md)|Especifica una función de descriptor de acceso de propiedad.|
|[propput](propput.md)|Especifica una función de la configuración de la propiedad.|
|[propputref](propputref.md)|Especifica una función de la configuración de la propiedad que utiliza una referencia en lugar de un valor.|
|[ptr](ptr.md)|Designa un puntero como un puntero completo.|
|[range](range-cpp.md)|Especifica un intervalo de valores permitidos para los argumentos o los campos cuyos valores se establecen en tiempo de ejecución.|
|[requestedit](requestedit.md)|Indica que la propiedad admite la notificación `OnRequestEdit`.|
|[restricted](restricted.md)|Especifica que un miembro de un módulo, interfaz o dispinterface no se puede llamar arbitrariamente.|
|[satype](satype.md)|Especifica el tipo de datos de la `SAFEARRAY` estructura.|
|[source](source-cpp.md)|Especifica las interfaces de origen del control de puntos de conexión en una clase. En una propiedad o método, el `source` atributo indica que el miembro devuelve un objeto o una variante de un origen de eventos.|
|[synchronize](synchronize.md)|Sincroniza el acceso al método de destino.|
|[vararg](vararg.md)|Especifica que la función toma un número variable de argumentos.|

## <a name="see-also"></a>Vea también

[Atributos por uso](attributes-by-usage.md)