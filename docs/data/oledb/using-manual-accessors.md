---
title: Utilizar descriptores de acceso manuales
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: 4a7e2dcde20cdb06a2f4e708149e24ee7144597c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312000"
---
# <a name="using-manual-accessors"></a>Utilizar descriptores de acceso manuales

Hay cuatro aspectos que debe hacer cuando se controla un comando desconocido:

- Determinar los parámetros

- Ejecute el comando

- Determinar las columnas de salida

- Si hay varios conjuntos de filas devuelto

Para realizar estas operaciones con las plantillas de consumidor OLE DB, utilice el `CManualAccessor` clase y siga estos pasos:

1. Abra un `CCommand` objeto con `CManualAccessor` como un parámetro de plantilla.

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. Consultar la sesión para el `IDBSchemaRowset` interfaz y utilizar el conjunto de filas de parámetros de procedimiento. Si el `IDBSchemaRowset` no está disponible, la interfaz de consulta para el `ICommandWithParameters` interfaz. Llame a `GetParameterInfo` para obtener información. Si ninguna de estas interfaces está disponible, puede asumir que no hay ningún parámetro.

1. Para cada parámetro, llame a `AddParameterEntry` para agregar los parámetros y establecerlos.

1. Abra el conjunto de filas, pero establece el parámetro de enlace en **false**.

1. Llame a `GetColumnInfo` para recuperar las columnas de salida. Use `AddBindEntry` para agregar la columna de salida para el enlace.

1. Llame a `GetNextResult` para determinar si están disponibles más conjuntos de filas. Repita los pasos 2 a 5.

Para obtener un ejemplo de un descriptor de acceso manual, consulte `CDBListView::CallProcedure` en el [DBVIEWER](https://github.com/Microsoft/VCSamples) ejemplo.

## <a name="see-also"></a>Vea también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)