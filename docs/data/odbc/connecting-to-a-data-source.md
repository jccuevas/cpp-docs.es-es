---
title: "Conectarse a un origen de datos | Microsoft Docs"
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
  - "conexiones [C++], origen de datos"
  - "orígenes de datos [C++], conectar"
  - "conexiones de bases de datos [C++], clases ODBC de MFC"
  - "conexiones de bases de datos [C++], ODBC"
  - "bases de datos [C++], conectar"
  - "conexiones ODBC [C++], utilizar"
  - "orígenes de datos ODBC [C++], conexiones"
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conectarse a un origen de datos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un origen de datos ODBC comprende un conjunto de datos específico, la información requerida para tener acceso a esos datos y la ubicación del origen de datos, que se puede describir por medio de un nombre de origen de datos.  Desde el punto de vista del programa, el origen de datos incluye los datos, el DBMS, la red \(si la hubiera\) y ODBC.  
  
 Para tener acceso a los datos proporcionados por un origen de datos, el programa debe establecer antes de nada una conexión al origen de datos.  Dicha conexión administra el acceso a todos los datos.  
  
 Las conexiones de origen de datos están encapsuladas por la clase [CDatabase](../../mfc/reference/cdatabase-class.md).  Una vez conectado el objeto `CDatabase` a un origen de datos, se puede:  
  
-   Crear [conjuntos de registros](../../mfc/reference/crecordset-class.md) que seleccionen registros a partir de tablas o consultas.  
  
-   Administrar [transacciones](../../data/odbc/transaction-odbc.md) agrupando actualizaciones para que todas se confirmen en el origen de datos de una vez \(o se revierta la transacción completa para que el origen de datos permanezca inalterado\), si el origen de datos admite el nivel requerido de transacciones.  
  
-   Ejecutar directamente instrucciones de [SQL](../../data/odbc/sql.md) .  
  
 Una vez finalizado el trabajo con una conexión a un origen de datos, se ha de cerrar el objeto `CDatabase` y destruirlo o reutilizarlo para una nueva conexión.  Para obtener más información sobre conexiones a orígenes de datos, vea [Origen de datos \(ODBC\)](../../data/odbc/data-source-odbc.md).  
  
## Vea también  
 [ODBC y MFC](../../data/odbc/odbc-and-mfc.md)