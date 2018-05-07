---
title: Conectarse a un origen de datos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b6a33f1e2421c56f89184d26185903b4ec7859e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="connecting-to-a-data-source"></a>Conectarse a un origen de datos
Un origen de datos ODBC es un conjunto de datos, la información necesaria para tener acceso a esos datos y la ubicación del origen de datos, que se puede describir mediante un nombre de origen de datos específico. Desde el punto de vista de su programa, el origen de datos incluye los datos, el DBMS, la red (si existe) y ODBC.  
  
 Para obtener acceso a datos proporcionados por un origen de datos, el programa en primer lugar debe establecer una conexión al origen de datos. Todo acceso a datos se administra a través de esa conexión.  
  
 Las conexiones de origen de datos están encapsuladas por clase [CDatabase](../../mfc/reference/cdatabase-class.md). Cuando un `CDatabase` objeto está conectado a un origen de datos, puede:  
  
-   Construir [conjuntos de registros](../../mfc/reference/crecordset-class.md), que seleccionar los registros de las tablas o las consultas.  
  
-   Administrar [transacciones](../../data/odbc/transaction-odbc.md), las actualizaciones por lotes por lo que todo se confirmen en el origen de datos a la vez (o se revierte la transacción completa para que el origen de datos permanezca sin cambios), si el origen de datos admite el nivel requerido de transacciones.  
  
-   Ejecutar directamente [SQL](../../data/odbc/sql.md) instrucciones.  
  
 Cuando termine de trabajar con una conexión de origen de datos, cierre la `CDatabase` objeto y destruirlo o reutilizarlo para una nueva conexión. Para obtener más información acerca de las conexiones de origen de datos, vea [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md).  
  
## <a name="see-also"></a>Vea también  
 [ODBC y MFC](../../data/odbc/odbc-and-mfc.md)