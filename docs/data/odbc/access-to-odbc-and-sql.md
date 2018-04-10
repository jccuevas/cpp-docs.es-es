---
title: Acceso a ODBC y SQL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 25e9533752e47e5cf3ea50e594a23b99e19355ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="access-to-odbc-and-sql"></a>Acceso a ODBC y SQL
La biblioteca Microsoft Foundation Class encapsula muchas llamadas de API de Windows y aún le permite llamar directamente a cualquier función de la API de Windows. Las clases de base de datos proporcionan la misma flexibilidad con respecto a la API de ODBC. Mientras que protegen a las clases de base de datos de gran parte de la complejidad de ODBC, puede llamar a funciones de la API de ODBC directamente desde cualquier lugar en el programa.  
  
 De forma similar, las clases de base de datos evitan tener que trabajar mucho con [SQL](../../data/odbc/sql.md), pero se puede usar SQL directamente si desea. Puede personalizar objetos de conjunto de registros pasando una instrucción SQL personalizada (o partes de la configuración de la instrucción predeterminada) cuando se abre el conjunto de registros. También puede hacer llamadas a SQL utilizando directamente la [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) función miembro de clase [CDatabase](../../mfc/reference/cdatabase-class.md).  
  
 Para obtener más información, consulte [ODBC: llamar a ODBC API directamente a funciones de](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) y [SQL: realizar directo SQL llamadas (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md).  
  
## <a name="see-also"></a>Vea también  
 [ODBC y MFC](../../data/odbc/odbc-and-mfc.md)