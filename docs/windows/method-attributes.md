---
title: Los atributos de método | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 27540db2da7aecbe7a4b70b786bbf05bf608e889
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317438"
---
# <a name="method-attributes"></a>Atributos de método

Los siguientes atributos se aplican a los métodos en una clase, coclase o interfaz.

|Atributo|Descripción|
|---------------|-----------------|
|[bindable](../windows/bindable.md)|Indica que la propiedad admite enlace de datos.|
|[call_as](../windows/call-as.md)|Permite que una función utilizables para asignarse a una función remota.|
|[Personalizado](../windows/custom-cpp.md)|Le permite definir su propio atributo.|
|[db_column](../windows/db-column.md)|Enlaza una columna especificada para el conjunto de filas.|
|[db_command](../windows/db-command.md)|Crea un comando OLE DB.|
|[db_param](../windows/db-param.md)|La variable de miembro especificado se asocia con un parámetro de entrada o salido y delimita la variable.|
|[db_source](../windows/db-source.md)|Crea una conexión a un origen de datos.|
|[db_table](../windows/db-table.md)|Se abre una tabla de OLE DB.|
|[defaultbind](../windows/defaultbind.md)|Indica la única propiedad enlazable que mejor representa al objeto.|
|[defaultcollelem](../windows/defaultcollelem.md)|Se usa para la optimización de código de Visual Basic.|
|[displaybind](../windows/displaybind.md)|Indica una propiedad que debe mostrarse al usuario como enlazable.|
|[helpcontext](../windows/helpcontext.md)|Especifica un identificador de contexto que permite al usuario ver información acerca de este elemento en el **ayuda** archivo.|
|[helpfile](../windows/helpfile.md)|Establece el nombre de la **ayuda** archivo para una biblioteca de tipos.|
|[helpstring](../windows/helpstring.md)|Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.|
|[helpstringcontext](../windows/helpstringcontext.md)|Especifica el identificador de un tema de ayuda en un archivo .hlp o chm.|
|[helpstringdll](../windows/helpstringdll.md)|Especifica el nombre del archivo DLL a utilizar para realizar la búsqueda de cadenas de documento (localización).|
|[hidden](../windows/hidden.md)|Indica que el elemento existe pero no debe mostrarse en un explorador orientado al usuario.|
|[identificador](../windows/id.md)|Especifica un DISPID para una función miembro (una propiedad o un método en una interfaz o interfaz dispinterface).|
|[immediatebind](../windows/immediatebind.md)|Indica que la base de datos será notificada inmediatamente de todos los cambios a una propiedad de un objeto enlazado a datos.|
|[in](../windows/in-cpp.md)|Indica que es un parámetro que se pasan desde el procedimiento que realiza la llamada al procedimiento llamado.|
|[local](../windows/local-cpp.md)|Permite usar el compilador de MIDL como un generador de encabezado cuando se utiliza en el encabezado de la interfaz. Cuando se utiliza en una función individual, designa un procedimiento local para el que no se genera ningún código auxiliar.|
|[nonbrowsable](../windows/nonbrowsable.md)|Indica que un miembro de interfaz no debe mostrarse en un explorador de propiedades.|
|[propget](../windows/propget.md)|Especifica una función de descriptor de acceso de propiedad.|
|[propput](../windows/propput.md)|Especifica una función de la configuración de la propiedad.|
|[propputref](../windows/propputref.md)|Especifica una función de la configuración de la propiedad que utiliza una referencia en lugar de un valor.|
|[ptr](../windows/ptr.md)|Designa un puntero como un puntero completo.|
|[intervalo](../windows/range-cpp.md)|Especifica un intervalo de valores permitidos para los argumentos o los campos cuyos valores se establecen en tiempo de ejecución.|
|[requestedit](../windows/requestedit.md)|Indica que la propiedad admite la `OnRequestEdit` notificación.|
|[restricted](../windows/restricted.md)|Especifica que un miembro de un módulo, interfaz o dispinterface no se puede llamar arbitrariamente.|
|[satype](../windows/satype.md)|Especifica el tipo de datos de la `SAFEARRAY` estructura.|
|[source](../windows/source-cpp.md)|Especifica las interfaces de origen del control de puntos de conexión en una clase. En una propiedad o método, el `source` atributo indica que el miembro devuelve un objeto o una variante de un origen de eventos.|
|[synchronize](../windows/synchronize.md)|Sincroniza el acceso al método de destino.|
|[vararg](../windows/vararg.md)|Especifica que la función toma un número variable de argumentos.|

## <a name="see-also"></a>Vea también

[Atributos por uso](../windows/attributes-by-usage.md)