---
title: Utilizar descriptores de acceso manuales
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: a6c0e5236702229a61a828344ba5d0d288898aee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209331"
---
# <a name="using-manual-accessors"></a>Utilizar descriptores de acceso manuales

Hay cuatro cosas que hay que hacer al controlar un comando desconocido:

- Determinar los parámetros

- Ejecutar el comando

- Determinar las columnas de salida

- Ver si hay varios conjuntos de filas devueltos

Para hacer esto con las plantillas de consumidor OLE DB, utilice la clase `CManualAccessor` y siga estos pasos:

1. Abra un objeto de `CCommand` con `CManualAccessor` como parámetro de plantilla.

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. Consulte la sesión de la interfaz `IDBSchemaRowset` y utilice el conjunto de filas de parámetros de procedimiento. Si la interfaz de `IDBSchemaRowset` no está disponible, consulte la interfaz de `ICommandWithParameters`. Llame a `GetParameterInfo` para obtener información. Si ninguna de las interfaces está disponible, puede suponer que no hay parámetros.

1. Para cada parámetro, llame a `AddParameterEntry` para agregar los parámetros y establecerlos.

1. Abra el conjunto de filas, pero establezca el parámetro BIND en **false**.

1. Llame a `GetColumnInfo` para recuperar las columnas de salida. Utilice `AddBindEntry` para agregar la columna de salida al enlace.

1. Llame a `GetNextResult` para determinar si hay más conjuntos de filas disponibles. Repita los pasos del 2 al 5.

Para obtener un ejemplo de un descriptor de acceso manual, vea `CDBListView::CallProcedure` en el ejemplo [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) .

## <a name="see-also"></a>Consulte también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)
