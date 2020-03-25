---
title: 'ODBC: Biblioteca de cursores ODBC'
ms.date: 11/04/2016
helpviewer_keywords:
- cursor library [ODBC]
- snapshots, support in ODBC
- timestamps, ODBC timestamp columns
- ODBC cursor library [ODBC]
- static cursors
- ODBC drivers, Level 1
- ODBC drivers, cursor support
- positioned updates
- cursors, ODBC cursor library
- Level 1 ODBC drivers
- cursor library [ODBC], snapshots
- ODBC, timestamp
- positioning cursors
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
ms.openlocfilehash: 51524604cad34ace18ffda2b5f48cc3c5fd89ad7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213101"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: Biblioteca de cursores ODBC

En este tema se describe la biblioteca de cursores ODBC y se explica cómo utilizarla. Para más información, consulte:

- [Biblioteca de cursores y controladores ODBC de nivel 1](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [Actualizaciones posicionadas y columnas de marca de tiempo](#_core_positioned_updates_and_timestamp_columns)

- [Usar la biblioteca de cursores](#_core_using_the_cursor_library)

La biblioteca de cursores ODBC es una biblioteca de vínculos dinámicos (DLL) que reside entre el administrador de controladores ODBC y el controlador. En términos ODBC, un controlador mantiene un cursor para realizar un seguimiento de su posición en el conjunto de registros. El cursor marca la posición en el conjunto de registros al que ya se ha desplazado, el registro actual.

##  <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>Biblioteca de cursores y controladores ODBC de nivel 1

La biblioteca de cursores ODBC proporciona a los controladores de nivel 1 las siguientes capacidades nuevas:

- Desplazamiento hacia delante y hacia atrás. Los controladores de nivel 2 no necesitan la biblioteca de cursores porque ya se pueden desplazar.

- Compatibilidad con instantáneas. La biblioteca de cursores administra un búfer que contiene los registros de la instantánea. Este búfer refleja las eliminaciones y las ediciones de los registros de su programa, pero no las adiciones, eliminaciones o ediciones de otros usuarios. Por lo tanto, la instantánea solo es tan actual como el búfer de la biblioteca de cursores. El búfer tampoco refleja sus propias adiciones hasta que llame a `Requery`. Los conjuntos de registros dinámicos no usan la biblioteca de cursores.

La biblioteca de cursores proporciona instantáneas (cursores estáticos) aunque el controlador no las admita normalmente. Si el controlador ya es compatible con cursores estáticos, no es necesario cargar la biblioteca de cursores para obtener compatibilidad con las instantáneas. Si usa la biblioteca de cursores, solo puede usar instantáneas y conjuntos de registros solo hacia delante. Si el controlador admite dynasets (KEYSET_DRIVEN cursores) y desea usarlos, no debe utilizar la biblioteca de cursores. Si desea utilizar las instantáneas y los conjuntos de registros dinámicos, debe basarlos en dos objetos de `CDatabase` diferentes (dos conexiones diferentes) a menos que el controlador admita ambos.

##  <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>Actualizaciones posicionadas y columnas de marca de tiempo

> [!NOTE]
>  Mediante las clases ODBC de MFC, como se describe en este tema, o las clases DAO de MFC se puede tener acceso a los orígenes de datos ODBC.

> [!NOTE]
>  Si el controlador ODBC admite `SQLSetPos`, que MFC usa si está disponible, este tema no se aplica a usted.

La mayoría de los controladores de nivel 1 no admiten las actualizaciones posicionadas. Estos controladores se basan en la biblioteca de cursores para emular las capacidades de los controladores de nivel 2 en este sentido. La biblioteca de cursores emula la compatibilidad con las actualizaciones posicionadas mediante la realización de una actualización de búsqueda en los campos que no cambian.

En algunos casos, un conjunto de registros podría contener una columna TIMESTAMP como uno de los campos que no cambian. En el uso de conjuntos de registros MFC con tablas que contienen columnas de marca de tiempo se producen dos problemas.

El primer problema se refiere a las instantáneas actualizables de las tablas con columnas de marca de tiempo. Si la tabla a la que está enlazada la instantánea contiene una columna TIMESTAMP, debe llamar a `Requery` después de llamar a `Edit` y `Update`. Si no es así, es posible que no pueda volver a editar el mismo registro. Cuando se llama a `Edit` y, a continuación, `Update`, el registro se escribe en el origen de datos y se actualiza la columna de marca de tiempo. Si no llama a `Requery`, el valor de marca de tiempo del registro de la instantánea ya no coincide con la marca de tiempo correspondiente en el origen de datos. Al intentar actualizar el registro de nuevo, es posible que el origen de datos no permita la actualización debido a la falta de coincidencia.

El segundo problema se refiere a las limitaciones de la clase [ctime](../../atl-mfc-shared/reference/ctime-class.md) cuando se usa con la función `RFX_Date` para transferir información de fecha y hora a o desde una tabla. El procesamiento del objeto de `CTime` impone cierta sobrecarga en forma de procesamiento intermedio adicional durante la transferencia de datos. El intervalo de fechas de `CTime` objetos también podría ser demasiado limitado para algunas aplicaciones. Una nueva versión de la función `RFX_Date` toma un parámetro de *TIMESTAMP_STRUCT* ODBC en lugar de un objeto `CTime`. Para obtener más información, vea `RFX_Date` en [macros y globales](../../mfc/reference/mfc-macros-and-globals.md) en la *referencia de MFC*.

##  <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>Usar la biblioteca de cursores

Cuando se conecta a un origen de datos (llamando a [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) o [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) ), puede especificar si desea utilizar la biblioteca de cursores para el origen de datos. Si va a crear instantáneas en ese origen de datos, especifique la opción `CDatabase::useCursorLib` en el parámetro `dwOptions` para `OpenEx` o especifique TRUE para el parámetro *bUseCursorLib* en `Open` (el valor predeterminado es true). Si el controlador ODBC admite dynasets y desea abrir conjuntos de registros dinámicos en el origen de datos, no utilice la biblioteca de cursores (enmascara la funcionalidad de controlador necesaria para los dynasets). En ese caso, no especifique `CDatabase::useCursorLib` en `OpenEx` o especifique FALSE para el parámetro *bUseCursorLib* en `Open`.

## <a name="see-also"></a>Consulte también

[Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)
