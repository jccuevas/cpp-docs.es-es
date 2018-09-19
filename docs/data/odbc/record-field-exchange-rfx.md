---
title: Registre el intercambio de campos (RFX) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03b827b9f6ec1b1a378b1ffd04aa2c1e1c6aa111
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087765"
---
# <a name="record-field-exchange-rfx"></a>Intercambio de campos de registros (RFX)

Las clases de base de datos ODBC de MFC automatizan el movimiento de datos entre el origen de datos y un [recordset](../../data/odbc/recordset-odbc.md) objeto. Al derivar una clase de [CRecordset](../../mfc/reference/crecordset-class.md) y no utiliza la obtención masiva de filas, se transfieren datos mediante el mecanismo de campos de registros (RFX) de exchange.  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas en una derivada `CRecordset` (clase), el marco de trabajo usa el mecanismo de forma masiva campos de registros (RFX masivo) para transferir datos. Para obtener más información, consulte [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
RFX es similar al intercambio de datos de cuadro de diálogo (DDX). Mover datos entre un origen de datos y los miembros de datos de campo de un conjunto de registros requiere varias llamadas para el conjunto de registros [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) y considerable interacción entre el marco de trabajo y [ODBC](../../data/odbc/odbc-basics.md). El mecanismo de RFX tiene seguridad de tipos y ahorra el trabajo de llamar a funciones ODBC como `::SQLBindCol`. Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
RFX resulta casi transparente para usted. Si declara las clases de conjunto de registros mediante el Asistente para aplicaciones MFC o **Agregar clase** (como se describe en [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)), RFX se genera automáticamente en ellos. La clase de conjunto de registros debe derivarse de la clase base `CRecordset` proporcionado por el marco de trabajo. El Asistente para aplicaciones MFC permite crear una clase de conjunto de registros inicial. **Agregar clase** le permite agregar otras clases de conjunto de registros según sea necesario. Para obtener más información y ejemplos, vea [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
Debe agregar manualmente una pequeña cantidad de código RFX en tres casos, cuando desea:  
  
- Use consultas parametrizadas. Para obtener más información, consulte [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
- Realizar combinaciones (con un conjunto de registros para las columnas de dos o más tablas). Para obtener más información, consulte [conjunto de registros: realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
- Enlazar dinámicamente columnas de datos. Esto es menos común que la parametrización. Para obtener más información, consulte [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
Si necesita una descripción más avanzada de RFX, consulte [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
Los siguientes temas explican los detalles del uso de objetos de conjunto de registros:  
  
- [Intercambio de campos de registros: Usar RFX](../../data/odbc/record-field-exchange-using-rfx.md)  
  
- [Intercambio de campos de registros: Usar las funciones de RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)  
  
- [Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)  
  
## <a name="see-also"></a>Vea también  

[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Compatibilidad con bases de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)