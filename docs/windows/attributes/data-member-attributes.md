---
title: Atributos de miembro de datos (COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- data members [C++], attributes
- data members [C++]
ms.assetid: 95b2397d-1daf-4ae4-8cd0-06956d005b13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5019503bed9dd0012d8aafc1ade4abd3107335ac
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792167"
---
# <a name="data-member-attributes"></a>Atributos de miembros de datos

Los siguientes atributos se aplican a los miembros de datos en una clase, coclase o interfaz.

|Atributo|Descripción|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|Grupos `db_column` atributos que participan en `IAccessor`-enlace basado en.|
|[db_column](db-column.md)|Enlaza una columna especificada para el conjunto de filas.|
|[db_command](db-command.md)|Crea un comando OLE DB.|
|[db_param](db-param.md)|La variable de miembro especificado se asocia con un parámetro de entrada o salido y delimita la variable.|
|[db_source](db-source.md)|Crea una conexión a un origen de datos.|
|[db_table](db-table.md)|Se abre una tabla de OLE DB.|
|[defaultbind](defaultbind.md)|Indica la única propiedad enlazable que mejor representa al objeto.|
|[displaybind](displaybind.md)|Indica una propiedad que debe mostrarse al usuario como enlazable.|
|[identificador](id.md)|Especifica un DISPID para una función miembro (una propiedad o un método en una interfaz o interfaz dispinterface).|
|[intervalo](range-cpp.md)|Especifica un intervalo de valores permitidos para los argumentos o los campos cuyos valores se establecen en tiempo de ejecución.|
|[rdx](rdx.md)|Crea una clave del registro o modifica una clave del registro existente.|
|[readonly](readonly-cpp.md)|Prohíbe la asignación a un miembro de datos.|
|[requestedit](requestedit.md)|Indica que la propiedad admite la `OnRequestEdit` notificación.|

## <a name="see-also"></a>Vea también

[Atributos por uso](attributes-by-usage.md)