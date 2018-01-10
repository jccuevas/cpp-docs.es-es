---
title: 'ODBC: Llamar a la API de ODBC directamente a las funciones | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC API functions [C++], calling
- ODBC [C++], catalog functions
- ODBC API functions [C++]
- APIs [C++], calling
- ODBC classes [C++], vs. ODBC API
- direct ODBC API calls
- catalog functions (ODBC)
- catalog functions (ODBC), calling
- ODBC [C++], API functions
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51fde2bb7ea73a2655c0b771dabfe14d2c833fb5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC: Llamar directamente a funciones de la API de ODBC
Las clases de base de datos proporcionan una interfaz más sencilla para un [origen de datos](../../data/odbc/data-source-odbc.md) de ODBC. Como resultado, las clases no encapsulan la API de ODBC. Para cualquier función que se encuentra fuera de las capacidades de las clases, debe llamar a funciones de la API de ODBC directamente. Por ejemplo, debe llamar a las funciones de catálogo ODBC (**:: SQLColumns**, **:: SQLProcedures**, **:: SQLTables**etc.) directamente.  
  
> [!NOTE]
>  Mediante las clases ODBC de MFC, como se describe en este tema, o las clases DAO de MFC se puede tener acceso a los orígenes de datos ODBC.  
  
 Para llamar a una función de la API de ODBC directamente, debe realizar los mismos pasos que debe seguir si se realiza las llamadas sin el marco de trabajo. Estos pasos son:  
  
-   Asignar el almacenamiento para los resultados de que la llamada se devuelve.  
  
-   Pasar un ODBC **HDBC** o **HSTMT** controlar, dependiendo de la firma de parámetro de la función. Use la [AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv) macro para recuperar el identificador ODBC.  
  
     Variables de miembro **CDatabase:: M_hdbc** y **CRecordset:: M_hstmt** están disponibles para que no necesite asignar e inicialice el usuario.  
  
-   Se puede llamar a funciones ODBC adicionales para preparar o realizar un seguimiento de la llamada principal.  
  
-   Cancela la asignación de almacenamiento cuando haya terminado.  
  
 Para obtener más información acerca de estos pasos, consulte la [Open Database Connectivity (ODBC)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) SDK en la documentación de MSDN.  
  
 Además de estos pasos, debe tomar pasos adicionales para comprobar los valores devueltos de función, asegúrese de que el programa no está esperando una llamada asincrónica al finalizar y así sucesivamente. Estos últimos pasos se pueden simplificar mediante el uso de la `AFX_SQL_ASYNC` y `AFX_SQL_SYNC` macros. Para obtener más información, consulte [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md) en el *referencia de MFC*.  

  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)
