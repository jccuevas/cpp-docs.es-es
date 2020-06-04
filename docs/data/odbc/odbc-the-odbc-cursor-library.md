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
ms.openlocfilehash: 13640dd2a8593057bef708a45dfc8471ba212563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367180"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: Biblioteca de cursores ODBC

En este tema se describe la biblioteca de cursores ODBC y se explica cómo usarla. Para más información, consulte:

- [Biblioteca de cursores y controladores ODBC de nivel 1](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [Actualizaciones posicionadas y columnas de marca de tiempo](#_core_positioned_updates_and_timestamp_columns)

- [Uso de la biblioteca de cursores](#_core_using_the_cursor_library)

La biblioteca de cursores ODBC es una biblioteca de vínculos dinámicos (DLL) que reside entre el Administrador de controladores ODBC y el controlador. En términos ODBC, un controlador mantiene un cursor para realizar un seguimiento de su posición en el conjunto de registros. El cursor marca la posición del conjunto de registros al que ya se ha desplazado: el registro actual.

## <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>Biblioteca de cursores y controladores ODBC de nivel 1

La biblioteca de cursores ODBC proporciona a los controladores de nivel 1 las siguientes capacidades nuevas:

- Desplazamiento hacia delante y hacia atrás. Los controladores de nivel 2 no necesitan la biblioteca de cursores porque ya se pueden desplazar.

- Compatibilidad con instantáneas. La biblioteca de cursores administra un búfer que contiene los registros de la instantánea. Este búfer refleja las eliminaciones y ediciones del programa en los registros, pero no en las adiciones, eliminaciones o ediciones de otros usuarios. Por lo tanto, la instantánea es tan actual como el búfer de la biblioteca de cursores. El búfer tampoco refleja sus propias `Requery`adiciones hasta que llame a . Los conjuntos de registros dinámicos no utilizan la biblioteca de cursores.

La biblioteca de cursores proporciona instantáneas (cursores estáticos) incluso si el controlador normalmente no las admite. Si el controlador ya admite cursores estáticos, no es necesario cargar la biblioteca de cursores para obtener compatibilidad con instantáneas. Si utiliza la biblioteca de cursores, solo puede utilizar instantáneas y conjuntos de registros de solo avance. Si el controlador admite conjuntos de registros dinámicos (cursores KEYSET_DRIVEN) y desea utilizarlos, no debe utilizar la biblioteca de cursores. Si desea utilizar instantáneas y conjuntos de registros `CDatabase` dinámicos, debe basarlos en dos objetos diferentes (dos conexiones diferentes) a menos que el controlador admita ambos.

## <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>Actualizaciones posicionadas y columnas de marca de tiempo

> [!NOTE]
> Mediante las clases ODBC de MFC, como se describe en este tema, o las clases DAO de MFC se puede tener acceso a los orígenes de datos ODBC.

> [!NOTE]
> Si el controlador `SQLSetPos`ODBC admite , que MFC usa si está disponible, este tema no se aplica a usted.

La mayoría de los controladores de nivel 1 no admiten actualizaciones posicionadas. Estos controladores se basan en la biblioteca de cursores para emular las capacidades de los controladores de nivel 2 en este sentido. La biblioteca de cursores emula la compatibilidad de actualización posicionada realizando una actualización buscada en los campos que no cambian.

En algunos casos, un conjunto de registros puede contener una columna de marca de tiempo como uno de esos campos invariables. Se producen dos problemas al usar conjuntos de registros MFC con tablas que contienen columnas de marca de tiempo.

El primer problema se refiere a las instantáneas actualizables en tablas con columnas de marca de tiempo. Si la tabla a la que está enlazada `Requery` la instantánea `Edit` `Update`contiene una columna de marca de tiempo, debe llamar después de llamar y . De lo contrario, es posible que no pueda volver a editar el mismo registro. Cuando se `Edit` llama `Update`y, a continuación, , el registro se escribe en el origen de datos y se actualiza la columna de marca de tiempo. Si no llama `Requery`a , el valor de marca de tiempo para el registro de la instantánea ya no coincide con la marca de tiempo correspondiente en el origen de datos. Cuando intenta actualizar el registro de nuevo, el origen de datos podría no permitir la actualización debido a la discordancia.

El segundo problema se refiere a las `RFX_Date` limitaciones de la clase [CTime](../../atl-mfc-shared/reference/ctime-class.md) cuando se utiliza con la función para transferir información de fecha y hora a o desde una tabla. El `CTime` procesamiento del objeto impone cierta sobrecarga en forma de procesamiento intermedio adicional durante la transferencia de datos. El intervalo `CTime` de fechas de los objetos también puede ser demasiado limitador para algunas aplicaciones. Una nueva versión de la `RFX_Date` función toma un parámetro ODBC *TIMESTAMP_STRUCT* en lugar de un `CTime` objeto. Para obtener más `RFX_Date` información, vea macros [y globales](../../mfc/reference/mfc-macros-and-globals.md) en la *referencia de MFC*.

## <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>Uso de la biblioteca de cursores

Cuando se conecta a un origen de datos, mediante una llamada a [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) o [CDatabase::Open,](../../mfc/reference/cdatabase-class.md#open) puede especificar si desea utilizar la biblioteca de cursores para el origen de datos. Si va a crear instantáneas en ese `CDatabase::useCursorLib` origen `dwOptions` de `OpenEx` datos, especifique la opción en `Open` el parámetro o especifique TRUE para el parámetro *bUseCursorLib* (el valor predeterminado es TRUE). Si el controlador ODBC admite conjuntos de registros dinámicos y desea abrir conjuntos de registros dinámicos en el origen de datos, no utilice la biblioteca de cursores (enmascara algunas funciones de controlador necesarias para los conjuntos de registros dinámicos). En ese caso, `CDatabase::useCursorLib` no `OpenEx` especifique en ni especifique FALSE `Open`para el parámetro *bUseCursorLib* en .

## <a name="see-also"></a>Consulte también

[Fundamentos de ODBC](../../data/odbc/odbc-basics.md)
