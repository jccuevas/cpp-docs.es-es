---
title: "Seleccionar y manipular registros | Microsoft Docs"
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
  - "conjuntos de registros ODBC, seleccionar registros"
  - "selección de registros, clases ODBC de MFC"
  - "registros, seleccionar"
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Seleccionar y manipular registros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Normalmente, cuando se seleccionan registros desde un origen de datos utilizando una instrucción SQL **SELECT**, se obtiene un conjunto de resultados, es decir, un conjunto de registros de una tabla o consulta.  Con las clases de base de datos se utiliza un objeto conjunto de registros para seleccionar y tener acceso al conjunto de resultados.  Se trata de un objeto de una clase específica de la aplicación que hay que derivar de la clase [CRecordset](../../mfc/reference/crecordset-class.md).  Cuando se define una clase de conjunto de registros, hay que especificar el origen de datos al que se ha de asociar la clase, la tabla que se va a utilizar y las columnas de la tabla.  El Asistente para aplicaciones MFC o el comando **Agregar clase** \(como se describe en [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)\) crea una clase con una conexión a un origen de datos específico.  Los asistentes crean la función miembro [GetDefaultSQL](../Topic/CRecordset::GetDefaultSQL.md) de clase `CRecordset` que devuelve el nombre de tabla.  Para obtener más información sobre cómo se utilizan los asistentes para crear clases de conjunto de registros, vea [Compatibilidad con bases de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md) y [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Cuando se utiliza un objeto [CRecordset](../../mfc/reference/crecordset-class.md) en tiempo de ejecución, se puede:  
  
-   Examinar los campos de datos del registro actual.  
  
-   Filtrar u ordenar el conjunto de registros.  
  
-   Personalizar la instrucción SQL **SELECT** predeterminada.  
  
-   Desplazarse por los registros seleccionados.  
  
-   Agregar, actualizar o eliminar registros \(si el origen de datos y el conjunto de registros son actualizables\).  
  
-   Probar si el conjunto de registros permite realizar consultas y actualizar el contenido del conjunto de registros.  
  
 Una vez terminada la utilización del objeto de conjunto de registros, se ha de cerrar y destruir.  Para obtener más información sobre conjuntos de registros, vea [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md).  
  
## Vea también  
 [ODBC y MFC](../../data/odbc/odbc-and-mfc.md)