---
title: "Intercambio de campos de registros (RFX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "datos [MFC]"
  - "datos [MFC], mover entre orígenes y conjuntos de registros"
  - "clases de base de datos [C++], RFX"
  - "ODBC [C++], RFX"
  - "RFX (ODBC) [C++]"
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Intercambio de campos de registros (RFX)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las clases de base de datos ODBC de MFC automatizan la transferencia de datos entre el origen de datos y un objeto de [conjunto de registros](../../data/odbc/recordset-odbc.md).  Al derivar una clase de [CRecordset](../../mfc/reference/crecordset-class.md) y no utilizar la obtención de filas masiva, los datos se transfieren mediante el mecanismo de intercambio de campos de registros \(RFX\).  
  
> [!NOTE]
>  Si está implementada la obtención de filas masiva en una clase derivada de `CRecordset`, el marco de trabajo usa el intercambio masivo de campos de registros \(RFX masivo\) para transferir datos.  Para obtener más información, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 RFX es similar al intercambio de datos de cuadros de diálogo \(DDX\).  Mover datos entre un origen de datos y los miembros de datos de campo de un conjunto de registros requiere múltiples llamadas a la función [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) del conjunto de registros y considerable interacción entre el marco de trabajo y [ODBC](../../data/odbc/odbc-basics.md).  El mecanismo de RFX incluye seguridad de tipos y ahorra el trabajo de llamar a funciones ODBC como **::SQLBindCol**.  Para obtener más información sobre DDX, vea [Intercambio y validación de datos de cuadros de diálogo](../../mfc/dialog-data-exchange-and-validation.md).  
  
 RFX es, en su mayoría, transparente para el programador.  Si se declaran las clases de conjunto de registros mediante el Asistente para aplicaciones MFC o el comando **Agregar clase** \(como se describe en [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)\), incorporan RFX de forma automática.  La clase de conjunto de registros debe derivarse de la clase base `CRecordset` proporcionada por el marco de trabajo.  El Asistente para aplicaciones MFC permite crear una clase de conjunto de registros inicial.  El comando **Agregar clase permite agregar otras clases de conjunto de registros a medida que se necesita.** Para obtener más información y ejemplos, vea [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Es necesario agregar manualmente una pequeña cantidad de código RFX en tres casos, en concreto, cuando se desea:  
  
-   Utilizar consultas parametrizadas.  Para obtener más información, vea [Conjunto de registros: Parametrizar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
-   Realizar combinaciones \(usando un conjunto de registros para las columnas de dos o más tablas\).  Para obtener más información, vea [Conjunto de registros: Realizar una combinación \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
-   Enlazar columnas de datos dinámicamente.  Esto es menos común que la parametrización.  Para obtener más información, vea [Conjunto de registros: Enlazar dinámicamente columnas de datos \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Si necesita comprender mejor el funcionamiento de RFX, vea [Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 Los temas mostrados a continuación explican los detalles acerca del uso de objetos de conjunto de registros.  
  
-   [Intercambio de campos de registros: Utilizar RFX](../../data/odbc/record-field-exchange-using-rfx.md)  
  
-   [Intercambio de campos de registros: Utilizar las funciones de RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)  
  
-   [Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)  
  
## Vea también  
 [Conectividad abierta de bases de datos \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Compatibilidad con bases de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)