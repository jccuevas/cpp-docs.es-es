---
title: Atributos de miembro de datos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 9fc5bfb34e2df0fad363e499cc5a7277d15d14d1
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318855"
---
# <a name="data-member-attributes"></a>Atributos de miembros de datos

Los siguientes atributos se aplican a los miembros de datos en una clase, coclase o interfaz.

|Atributo|Descripción|
|---------------|-----------------|
|[db_accessor](../windows/db-accessor.md)|Grupos `db_column` atributos que participan en `IAccessor`-enlace basado en.|
|[db_column](../windows/db-column.md)|Enlaza una columna especificada para el conjunto de filas.|
|[db_command](../windows/db-command.md)|Crea un comando OLE DB.|
|[db_param](../windows/db-param.md)|La variable de miembro especificado se asocia con un parámetro de entrada o salido y delimita la variable.|
|[db_source](../windows/db-source.md)|Crea una conexión a un origen de datos.|
|[db_table](../windows/db-table.md)|Se abre una tabla de OLE DB.|
|[defaultbind](../windows/defaultbind.md)|Indica la única propiedad enlazable que mejor representa al objeto.|
|[displaybind](../windows/displaybind.md)|Indica una propiedad que debe mostrarse al usuario como enlazable.|
|[identificador](../windows/id.md)|Especifica un DISPID para una función miembro (una propiedad o un método en una interfaz o interfaz dispinterface).|
|[intervalo](../windows/range-cpp.md)|Especifica un intervalo de valores permitidos para los argumentos o los campos cuyos valores se establecen en tiempo de ejecución.|
|[rdx](../windows/rdx.md)|Crea una clave del registro o modifica una clave del registro existente.|
|[readonly](../windows/readonly-cpp.md)|Prohíbe la asignación a un miembro de datos.|
|[requestedit](../windows/requestedit.md)|Indica que la propiedad admite la `OnRequestEdit` notificación.|

## <a name="see-also"></a>Vea también

[Atributos por uso](../windows/attributes-by-usage.md)