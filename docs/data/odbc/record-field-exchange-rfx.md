---
title: Registre el intercambio de campos (RFX) | Documentos de Microsoft
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
ms.openlocfilehash: 8b214cf05115056efc96c4a078dedd4b7f9a3a1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="record-field-exchange-rfx"></a>Intercambio de campos de registros (RFX)
Las clases de base de datos ODBC de MFC automatizan la transferencia de datos entre el origen de datos y un [recordset](../../data/odbc/recordset-odbc.md) objeto. Al derivar una clase de [CRecordset](../../mfc/reference/crecordset-class.md) y no utiliza la obtención masiva de filas, datos se transfieren mediante el mecanismo de campos de registros (RFX) de exchange.  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas de una derivada `CRecordset` (clase), el marco de trabajo utiliza el mecanismo de intercambio (RFX masivo) de campos de registros de forma masiva para transferir datos. Para obtener más información, consulte [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 RFX es similar al intercambio de datos de cuadros de diálogo (DDX). Mover datos entre un origen de datos y los miembros de datos de campo de un conjunto de registros requiere varias llamadas para el conjunto de registros [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) función y considerable interacción entre el marco de trabajo y [ODBC](../../data/odbc/odbc-basics.md). El mecanismo RFX tiene seguridad de tipos y ahorra el trabajo de llamar a funciones ODBC como **:: SQLBindCol**. Para obtener más información sobre DDX, consulte [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md).  
  
 RFX principalmente es transparente para el programador. Si declara las clases de conjunto de registros con el Asistente para aplicaciones MFC o **Agregar clase** (como se describe en [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)), RFX se integran automáticamente. La clase de conjunto de registros debe derivarse de la clase base `CRecordset` proporcionado por el marco de trabajo. El Asistente para aplicaciones MFC permite crear una clase de conjunto de registros inicial. **Agregar clase** le permite agregar otras clases de conjunto de registros según sea necesario. Para obtener más información y ejemplos, vea [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Debe agregar manualmente una pequeña cantidad de código RFX en tres casos, cuando desea:  
  
-   Utilizar consultas parametrizadas. Para obtener más información, consulte [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
-   Realizar combinaciones (con un conjunto de registros para las columnas de dos o más tablas). Para obtener más información, consulte [conjunto de registros: realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
-   Enlazar dinámicamente columnas de datos. Esto es menos común que la parametrización. Para obtener más información, consulte [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Si necesita comprender mejor el funcionamiento de RFX, consulte [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 Los siguientes temas explican los detalles del uso de objetos de conjunto de registros:  
  
-   [Intercambio de campos de registros: Usar RFX](../../data/odbc/record-field-exchange-using-rfx.md)  
  
-   [Intercambio de campos de registros: Usar las funciones de RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)  
  
-   [Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)  
  
## <a name="see-also"></a>Vea también  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Compatibilidad de base de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)