---
title: Acceso a ODBC y SQL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 40b88cd7db95a05edd6174701c04724a6f245223
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018722"
---
# <a name="access-to-odbc-and-sql"></a>Acceso a ODBC y SQL

La biblioteca Microsoft Foundation Class encapsula muchas llamadas de API de Windows y todavía le permite llamar directamente a cualquier función de la API de Windows. Las clases de base de datos proporcionan la misma flexibilidad con respecto a la API de ODBC. Mientras que las clases de base de datos de gran parte de la complejidad de ODBC blindar, puede llamar a funciones API de ODBC directamente desde cualquier lugar en el programa.  
  
De forma similar, las clases de base de datos evitan tener que trabajar mucho con [SQL](../../data/odbc/sql.md), pero se puede usar SQL directamente si desea. Puede personalizar los objetos de conjunto de registros pasando una instrucción SQL personalizada (o partes de la configuración de la instrucción predeterminada) al abrir el conjunto de registros. También puede realizar llamadas a SQL directamente mediante el [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) función miembro de clase [CDatabase](../../mfc/reference/cdatabase-class.md).  
  
Para obtener más información, consulte [ODBC: llamar a ODBC API directamente a funciones](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) y [SQL: realizar directo SQL llamadas (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md).  
  
## <a name="see-also"></a>Vea también  

[ODBC y MFC](../../data/odbc/odbc-and-mfc.md)