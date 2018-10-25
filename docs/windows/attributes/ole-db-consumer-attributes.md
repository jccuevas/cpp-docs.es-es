---
title: Atributos de consumidor OLE DB (COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], database
- attributes [C++/CLI], data access
- databases [C++], attributes
- OLE DB consumers [C++], attributes
- database attributes [C++/CLI]
- attributes [C++/CLI], OLE DB consumer
ms.assetid: 017b591f-8f9a-42b4-84d5-cc42a21ab0cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19c3e441ff4130d30f3aeb7957c5af85576fb9e1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065868"
---
# <a name="ole-db-consumer-attributes"></a>Atributos del consumidor OLE DB
Los atributos de consumidor OLE DB inyectar código, según la [plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md), para crear un trabajo OLE DB consumidor que realiza tareas como abrir tablas, ejecutar comandos y obtener acceso a datos.

|Atributo|Descripción|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|Enlaza las columnas de un conjunto de filas y se enlazan a las asignaciones de descriptor de acceso correspondiente.|
|[db_column](db-column.md)|Enlaza una columna especificada para el conjunto de filas.|
|[db_command](db-command.md)|Ejecuta un comando de OLE DB.|
|[db_param](db-param.md)|La variable de miembro especificado se asocia con un parámetro de entrada o salido.|
|[db_source](db-source.md)|Crea y encapsula una conexión a través de un proveedor a un origen de datos.|
|[db_table](db-table.md)|Se abre una tabla de OLE DB.|

## <a name="see-also"></a>Vea también

[Atributos por grupo](attributes-by-group.md)