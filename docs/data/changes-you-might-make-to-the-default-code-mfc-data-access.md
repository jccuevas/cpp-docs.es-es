---
title: "Posibles cambios en el c&#243;digo predeterminado (acceso a datos MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vistas de registros [C++], personalizar el código predeterminado"
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Posibles cambios en el c&#243;digo predeterminado (acceso a datos MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El [Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md) escribe una clase de conjunto de registros que selecciona todos los registros de una sola tabla.  Con frecuencia, deseará modificar este comportamiento de alguna de las siguientes maneras:  
  
-   Establecer un filtro o un criterio de ordenación para el conjunto de registros.  Hágalo en `OnInitialUpdate` después de que se haya construido el conjunto de registros, pero antes de que se llame a la función miembro **Abrir**.  Para obtener más información, consulte [Conjunto de registros: Filtrar registros \(ODBC\)](../data/odbc/recordset-filtering-records-odbc.md) y [Conjunto de registros: Ordenar registros \(ODBC\)](../data/odbc/recordset-sorting-records-odbc.md).  
  
-   Parametrice el conjunto de registros.  Especifique el valor de parámetro de tiempo de ejecución real después del filtro.  Para obtener más información, consulte [Conjunto de registros: Parametrizar un conjunto de registros \(ODBC\)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
-   Pase una cadena SQL personalizada a la función miembro [Abrir](../Topic/CRecordset::Open.md).  Para obtener una explicación de lo que se puede lograr con esta técnica, consulte [SQL: Personalizar la instrucción SQL del conjunto de registros \(ODBC\)](../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md).  
  
## Vea también  
 [Utilizar una vista de registros](../data/using-a-record-view-mfc-data-access.md)