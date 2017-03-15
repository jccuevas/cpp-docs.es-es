---
title: "Conjunto de registros: Agregar registros de forma masiva (ODBC) | Microsoft Docs"
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
  - "agregar registros de forma masiva a conjuntos de registros"
  - "conjuntos de registros ODBC, agregar registros"
  - "conjuntos de registros, agregar registros"
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Conjunto de registros: Agregar registros de forma masiva (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 La clase [CRecordset](../../mfc/reference/crecordset-class.md) de MFC tiene una nueva optimización que mejora la eficacia cuando se agregan nuevos registros a una tabla de forma masiva.  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas.  Si utiliza la obtención masiva de filas, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Una nueva opción para el parámetro **dwOptions** de la función miembro [CRecordset::Open](../Topic/CRecordset::Open.md), **optimizeBulkAdd**, mejora el rendimiento al agregar varios registros de forma consecutiva sin llamar a **Requery** o **Close**.  Sólo aquellos campos modificados antes de la primera llamada a **Update** se marcan como tales en posteriores llamadas a `AddNew`\/**Update**.  
  
 Si se utilizan las clases de base de datos para aprovechar la función **::SQLSetPos** de la API ODBC al agregar, editar y eliminar registros, esta optimización no es necesaria.  
  
 Si está cargada la biblioteca de cursores ODBC o el controlador ODBC no admite agregar, editar o eliminar registros mediante **::SQLSetPos**, esta optimización debe mejorar el rendimiento al agregar registros de forma masiva.  Para activarla, establezca de la forma siguiente el parámetro **dwOptions** de la llamada a **Open** en el conjunto de registros:  
  
```  
appendOnly | optimizeBulkAdd  
```  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Agregar, actualizar y eliminar registros \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [Conjunto de registros: Bloquear registros \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)