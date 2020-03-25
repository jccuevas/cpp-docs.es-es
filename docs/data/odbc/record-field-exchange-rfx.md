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
ms.openlocfilehash: e1ba9f29ebf2cb3b1f94620e815882c850bbc7cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213062"
---
# <a name="record-field-exchange-rfx"></a>Intercambio de campos de registros (RFX)

Las clases de base de datos ODBC de MFC automatizan el movimiento de datos entre el origen de datos y un objeto de [conjunto de registros](../../data/odbc/recordset-odbc.md) . Al derivar una clase de [CRecordset](../../mfc/reference/crecordset-class.md) y no utilizar la obtención masiva de filas, los datos se transfieren mediante el mecanismo de intercambio de campos de registros (RFX).

> [!NOTE]
>  Si ha implementado la obtención masiva de filas en una clase `CRecordset` derivada, el marco utiliza el mecanismo de intercambio masivo de campos de registros (RFX masivo) para transferir los datos. Para obtener más información, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

RFX es similar al intercambio de datos de cuadros de diálogo (DDX). Mover datos entre un origen de datos y los miembros de datos de campo de un conjunto de registros requiere varias llamadas a la función [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) del conjunto de registros y una interacción considerable entre el marco de trabajo y [ODBC](../../data/odbc/odbc-basics.md). El mecanismo de RFX tiene seguridad de tipos y le permite hacer llamadas a funciones ODBC como `::SQLBindCol`. Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

RFX es principalmente transparente para usted. Si declara las clases de conjunto de registros con el Asistente para aplicaciones MFC o la **clase Add** (como se describe en [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)), RFX se integra en ellos automáticamente. La clase de conjunto de registros se debe derivar de la clase base `CRecordset` proporciona el marco de trabajo. El Asistente para aplicaciones MFC le permite crear una clase de conjunto de registros inicial. **Agregar clase** le permite agregar otras clases de conjunto de registros a medida que las necesite. Para obtener más información y ejemplos, vea [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Debe agregar manualmente una pequeña cantidad de código RFX en tres casos, cuando quiera:

- Usar consultas con parámetros. Para obtener más información, vea [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

- Realizar combinaciones (utilizando un conjunto de registros para las columnas de dos o más tablas). Para obtener más información, vea [conjunto de registros: realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Enlazar columnas de datos dinámicamente. Esto es menos común que la parametrización. Para obtener más información, vea [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Si necesita una comprensión más avanzada de RFX, consulte [intercambio de campos de registros:](../../data/odbc/record-field-exchange-how-rfx-works.md)funcionamiento de RFX.

En los temas siguientes se explican los detalles del uso de objetos de conjunto de registros:

- [Intercambio de campos de registros: Usar RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [Intercambio de campos de registros: Usar las funciones de RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>Consulte también

[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Consumidor ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Compatibilidad con bases de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)
