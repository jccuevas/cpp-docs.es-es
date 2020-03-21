---
title: Seleccionar y manipular registros
ms.date: 05/09/2019
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
ms.openlocfilehash: 8388cd5c8c53a4595dc9b44430077421ee8680bf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079795"
---
# <a name="selecting-and-manipulating-records"></a>Seleccionar y manipular registros

> [!NOTE]
> El Asistente para consumidores ODBC de MFC no está disponible en Visual Studio 2019 ni en versiones posteriores. Aun así, puede crear un consumidor de forma manual.

Normalmente, cuando selecciona registros de un origen de datos mediante una instrucción **SELECT** de SQL, obtiene un conjunto de resultados, que es un conjunto de registros de una tabla o una consulta. Con las clases de base de datos, usará un objeto de conjunto de registros para seleccionar el conjunto de resultados y tener acceso a él. Se trata de un objeto de una clase específica de la aplicación que se deriva de la clase [CRecordset](../../mfc/reference/crecordset-class.md). Al definir una clase de conjunto de registros, debe especificar el origen de datos con el que va a asociarla, la tabla que se va a usar y las columnas de la tabla. El Asistente para aplicaciones MFC o **Agregar clase** (como se describe en [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) crean una clase con una conexión a un origen de datos específico. Los asistentes escriben la función miembro [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) de la clase `CRecordset` para que devuelva el nombre de tabla.

Mediante el uso de un objeto [CRecordset](../../mfc/reference/crecordset-class.md) en tiempo de ejecución, puede hacer lo siguiente:

- Examinar los campos de datos del registro actual.

- Filtrar u ordenar el conjunto de registros.

- Personalizar la instrucción **SELECT** predeterminada de SQL.

- Desplazarse por los registros seleccionados.

- Agregar, actualizar o eliminar registros (si tanto el origen de datos como el conjunto de registros son actualizables).

- Comprobar si el conjunto de registros permite volver a consultar y actualizar el contenido del conjunto de registros.

Cuando acabe de usar el objeto de conjunto de registros, ciérrelo y destrúyalo. Para obtener más información sobre los conjuntos de registros, vea [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md).

## <a name="see-also"></a>Consulte también

[ODBC y MFC](../../data/odbc/odbc-and-mfc.md)