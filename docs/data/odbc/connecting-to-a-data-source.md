---
title: Conectarse a un origen de datos
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
ms.openlocfilehash: 1740a34036798dac69ffc8b486e03bf6439845a5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024567"
---
# <a name="connecting-to-a-data-source"></a>Conectarse a un origen de datos

Un origen de datos ODBC es un conjunto de datos, la información necesaria para tener acceso a esos datos y la ubicación del origen de datos, que se puede describir mediante un nombre de origen de datos específico. Desde el punto de vista de su programa, el origen de datos incluye los datos, el DBMS, la red (si existe) y ODBC.

Para obtener acceso a datos proporcionados por un origen de datos, el programa en primer lugar debe establecer una conexión al origen de datos. Acceso a todos los datos se administra a través de esa conexión.

Las conexiones de origen de datos están encapsuladas por clase [CDatabase](../../mfc/reference/cdatabase-class.md). Cuando un `CDatabase` objeto está conectado a un origen de datos, puede:

- Construir [conjuntos de registros](../../mfc/reference/crecordset-class.md), que seleccione los registros de tablas o consultas.

- Administrar [transacciones](../../data/odbc/transaction-odbc.md), procesamiento por lotes actualizaciones de modo que todos se confirma en el origen de datos al mismo tiempo (o se revierte la transacción completa para que el origen de datos permanezca sin cambios): si el origen de datos admite el nivel requerido de transacciones.

- Ejecutar directamente [SQL](../../data/odbc/sql.md) instrucciones.

Cuando termine de trabajar con una conexión de origen de datos, se cierra el `CDatabase` objeto y lo destruirá o volver a usarlo para una conexión nueva. Para obtener más información acerca de las conexiones de origen de datos, vea [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md).

## <a name="see-also"></a>Vea también

[ODBC y MFC](../../data/odbc/odbc-and-mfc.md)