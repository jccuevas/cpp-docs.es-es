---
title: 'ODBC: Llamar directamente a funciones de la API de ODBC'
ms.date: 11/04/2016
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
ms.openlocfilehash: 208749438f40eef746a638dd12373397c426d454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368664"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC: Llamar directamente a funciones de la API de ODBC

Las clases de base de datos proporcionan una interfaz más sencilla a un origen de [datos](../../data/odbc/data-source-odbc.md) que ODBC. Como resultado, las clases no encapsulan toda la API ODBC. Para cualquier funcionalidad que quede fuera de las capacidades de las clases, debe llamar directamente a las funciones de la API ODBC. Por ejemplo, debe llamar directamente`::SQLColumns` `::SQLProcedures`a `::SQLTables`las funciones de catálogo ODBC ( , , , y otras).

> [!NOTE]
> Mediante las clases ODBC de MFC, como se describe en este tema, o las clases DAO de MFC se puede tener acceso a los orígenes de datos ODBC.

Para llamar a una función de API ODBC directamente, debe realizar los mismos pasos que seguiría si estuviera realizando las llamadas sin el marco de trabajo. Estos pasos son:

- Asigne almacenamiento para los resultados que devuelve la llamada.

- Pase un `HDBC` `HSTMT` ODBC o un identificador, dependiendo de la firma de parámetro de la función. Utilice la macro [AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv) para recuperar el identificador ODBC.

   Variables `CDatabase::m_hdbc` miembro `CRecordset::m_hstmt` y están disponibles para que no sea necesario asignarlas e inicializarlas usted mismo.

- Tal vez llame a funciones ODBC adicionales para preparar o realizar un seguimiento de la llamada principal.

- Desasignar almacenamiento cuando termine.

Para obtener más información acerca de estos pasos, consulte el SDK de conectividad abierta de base de [datos (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) en la documentación de MSDN.

Además de estos pasos, debe realizar pasos adicionales para comprobar los valores devueltos por la función, asegurarse de que el programa no está esperando a que finalice una llamada asincrónica, etc. Puede simplificar estos últimos pasos mediante las macros AFX_SQL_ASYNC y AFX_SQL_SYNC. Para obtener más información, vea [Macros y globales](../../mfc/reference/mfc-macros-and-globals.md) en la *referencia de MFC*.

## <a name="see-also"></a>Consulte también

[Fundamentos de ODBC](../../data/odbc/odbc-basics.md)
