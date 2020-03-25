---
title: Acceso a ODBC y SQL
ms.date: 11/04/2016
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
ms.openlocfilehash: 0b590ce9309cbbe95285001cc5befe70a1d1961f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213335"
---
# <a name="access-to-odbc-and-sql"></a>Acceso a ODBC y SQL

El biblioteca MFC encapsula muchas llamadas a la API de Windows y le permite llamar a cualquier función de la API de Windows directamente. Las clases de base de datos proporcionan la misma flexibilidad con respecto a la API de ODBC. Mientras que las clases de base de datos se protegen de gran parte de la complejidad de ODBC, puede llamar a funciones de la API de ODBC directamente desde cualquier lugar del programa.

Del mismo modo, las clases de base de datos evitan tener que trabajar mucho con [SQL](../../data/odbc/sql.md), pero puede usar SQL directamente si lo desea. Puede personalizar los objetos de conjunto de registros pasando una instrucción SQL personalizada (o estableciendo partes de la instrucción predeterminada) al abrir el conjunto de registros. También puede realizar llamadas a SQL directamente mediante la función miembro [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) de la clase [CDatabase](../../mfc/reference/cdatabase-class.md).

Para obtener más información, vea [ODBC: llamar directamente a funciones](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) de la API de ODBC y [SQL: realizar llamadas directas a SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md).

## <a name="see-also"></a>Consulte también

[ODBC y MFC](../../data/odbc/odbc-and-mfc.md)
