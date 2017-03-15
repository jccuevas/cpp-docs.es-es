---
title: "ODBC: Llamar directamente a funciones de la API de ODBC | Microsoft Docs"
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
  - "API [C++], llamar"
  - "funciones de catálogo (ODBC)"
  - "funciones de catálogo (ODBC), llamar"
  - "llamadas API directas de ODBC"
  - "ODBC [C++], funciones API"
  - "ODBC [C++], funciones de catálogo"
  - "funciones de la API de ODBC [C++]"
  - "funciones de la API de ODBC [C++], llamar"
  - "clases ODBC [C++], API de ODBC"
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ODBC: Llamar directamente a funciones de la API de ODBC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las clases de base de datos proporcionan una interfaz más simple con un [origen de datos](../../data/odbc/data-source-odbc.md) que la proporcionada por ODBC.  Como resultado, las clases no encapsulan toda la API de ODBC.  Para cualquier funcionalidad que no esté incluida en las posibilidades de las clases MFC, se debe llamar a las funciones de la API de ODBC directamente.  Por ejemplo, se debe llamar a las funciones de catálogo de ODBC \(**::SQLColumns**, **::SQLProcedures**, **::SQLTables** y otras\) directamente.  
  
> [!NOTE]
>  Mediante las clases ODBC de MFC, como se describe en este tema, o las clases DAO de MFC se puede tener acceso a los orígenes de datos ODBC.  
  
 Para llamar a una función de la API de ODBC directamente, se deben seguir los mismos pasos que se seguirían en el caso de realizar llamadas sin el marco de trabajo.  Estos pasos son los siguientes:  
  
-   Asignar almacenamiento para los resultados devueltos por la llamada.  
  
-   Pasar un identificador ODBC **HDBC** o **HSTMT**, dependiendo de la firma de parámetro de la función.  Utilizar la macro [AFXGetHENV](../Topic/AfxGetHENV.md) para recuperar el identificador de ODBC.  
  
     Las variables miembro **CDatabase::m\_hdbc** y **CRecordset::m\_hstmt** están disponibles, por lo que no es necesario que las asigne e inicialice el usuario.  
  
-   Se puede llamar a otras funciones ODBC para preparar o hacer un seguimiento de la llamada principal.  
  
-   Desasignar cualquier espacio de almacenamiento asignado al terminar.  
  
 Para obtener más información sobre estos pasos, vea el SDK de [Conectividad abierta de bases de datos \(ODBC\)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) en la documentación de MSDN.  
  
 Además de estos pasos, es necesario seguir otros pasos para comprobar los valores devueltos por la función, asegurarse de que el programa no está esperando una llamada asincrónica para terminar, etc.  Estos últimos pasos se pueden simplificar utilizando las macros `AFX_SQL_ASYNC` y `AFX_SQL_SYNC`.  Para obtener más información, vea [Macros y funciones globales](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md) en la *Referencia de MFC*.  
  
## Vea también  
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)