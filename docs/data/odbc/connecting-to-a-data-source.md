---
title: Conectar con un origen de datos
ms.date: 11/04/2016
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
ms.openlocfilehash: 712910aca2622f2678b8b9d06b18a2fdbf9157e4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213348"
---
# <a name="connecting-to-a-data-source"></a>Conectar con un origen de datos

Un origen de datos ODBC es un conjunto específico de datos, la información necesaria para obtener acceso a esos datos y la ubicación del origen de datos, que se puede describir mediante un nombre de origen de datos. Desde el punto de vista del programa, el origen de datos incluye los datos, el DBMS, la red (si existe) y ODBC.

Para obtener acceso a los datos proporcionados por un origen de datos, el programa primero debe establecer una conexión con el origen de datos. Todos los accesos a datos se administran a través de esa conexión.

La clase [CDatabase](../../mfc/reference/cdatabase-class.md)encapsula las conexiones de origen de datos. Cuando un objeto de `CDatabase` se conecta a un origen de datos, puede:

- Construya [conjuntos de registros](../../mfc/reference/crecordset-class.md), que seleccionan registros de tablas o consultas.

- Administrar [transacciones](../../data/odbc/transaction-odbc.md)y procesar por lotes las actualizaciones para que todas se confirmen en el origen de datos de una vez (o se revierta toda la transacción para que el origen de datos no se modifique), si el origen de datos admite el nivel requerido de transacciones.

- Ejecutar directamente instrucciones [SQL](../../data/odbc/sql.md) .

Cuando termina de trabajar con una conexión a un origen de datos, cierra el objeto `CDatabase` y lo destruye o lo reutiliza para una nueva conexión. Para obtener más información sobre las conexiones de origen de datos, vea [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md).

## <a name="see-also"></a>Consulte también

[ODBC y MFC](../../data/odbc/odbc-and-mfc.md)
