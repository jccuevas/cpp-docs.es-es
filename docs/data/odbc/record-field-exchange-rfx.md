---
title: Intercambio de campos de registros (RFX)
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
ms.openlocfilehash: 6f965b90e1e0bbcfd3ad04bb5b40644d61050b2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367161"
---
# <a name="record-field-exchange-rfx"></a>Intercambio de campos de registros (RFX)

Las clases de base de datos ODBC de MFC automatizan el movimiento de datos entre el origen de datos y un objeto de [conjunto de registros.](../../data/odbc/recordset-odbc.md) Cuando se deriva una clase de [CRecordset](../../mfc/reference/crecordset-class.md) y no se utiliza la obtención masiva de filas, los datos se transfieren mediante el mecanismo de intercambio de campos de registros (RFX).

> [!NOTE]
> Si ha implementado la obtención masiva `CRecordset` de filas en una clase derivada, el marco de trabajo utiliza el mecanismo de intercambio de campos de registros masivos (RFX masivo) para transferir datos. Para obtener más información, vea [Conjunto de registros: obtención de registros en masa (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

RFX es similar al intercambio de datos de cuadro de diálogo (DDX). Mover datos entre un origen de datos y los miembros de datos de campo de un conjunto de registros requiere varias llamadas a la función [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) del conjunto de registros y una interacción considerable entre el marco de trabajo y [ODBC.](../../data/odbc/odbc-basics.md) El mecanismo RFX es seguro para tipos y le ahorra `::SQLBindCol`el trabajo de llamar a funciones ODBC como . Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

RFX es en su mayoría transparente para usted. Si declara las clases de conjunto de registros con el Asistente para aplicaciones MFC o **Agregar clase** (como se describe en Agregar un consumidor ODBC de [MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)), RFX se integra automáticamente. La clase de conjunto de registros debe derivarse de la clase `CRecordset` base proporcionada por el marco de trabajo. El Asistente para aplicaciones MFC le permite crear una clase de conjunto de registros inicial. **Agregar clase** le permite agregar otras clases de conjunto de registros según las necesite. Para obtener más información y ejemplos, vea [Agregar un consumidor ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)de MFC .

Debe agregar manualmente una pequeña cantidad de código RFX en tres casos, cuando desee:

- Utilice consultas parametrizadas. Para obtener más información, vea [Conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

- Realizar combinaciones (mediante un conjunto de registros para columnas de dos o más tablas). Para obtener más información, vea [Conjunto de registros: realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Enlazar columnas de datos dinámicamente. Esto es menos común que la parametrización. Para obtener más información, vea [Conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Si necesita una comprensión más avanzada de RFX, vea Intercambio de campos de [registros: Cómo funciona RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

En los temas siguientes se explican los detalles del uso de objetos de conjunto de registros:

- [Intercambio de campos de registros: Utilizar RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [Intercambio de campos de registros: Utilizar las funciones de RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>Consulte también

[Conectividad de base de datos abierta (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Consumidor ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Compatibilidad con bases de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[Clase CRecordset](../../mfc/reference/crecordset-class.md)
