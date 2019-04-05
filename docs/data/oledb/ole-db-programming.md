---
title: Programación de OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB [C++]
- data access [C++], OLE DB programming
- OLE DB [C++], about OLE DB
ms.assetid: 52a80d66-17a9-43a1-9b90-392ae43cea2b
ms.openlocfilehash: ac74f94b4cdc738237c2994646f7602f7f5118ca
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031652"
---
# <a name="ole-db-programming"></a>Programación de OLE DB

OLE DB de Microsoft es una tecnología heredada; es la API de acceso de datos necesarios para los servidores vinculados de SQL para las aplicaciones nuevas. Todas las demás aplicaciones nuevas deben utilizar ODBC. El proveedor OLE DB actual para SQL Server es SQLNCLI11. ARCHIVO DLL. El proveedor aún se envía a SQL Server 2016. Esta documentación está dirigida a los desarrolladores que son mantener las aplicaciones existentes que ya usan OLE DB.

Las plantillas OLE DB son plantillas de C++ que facilitan el uso de la tecnología de base de datos de OLE DB de alto rendimiento, al proporcionar clases que implementan muchas interfaces OLE DB comúnmente usadas. Esta biblioteca de plantillas se divide en plantillas de consumidor y de proveedor.

Visual C++ también admite el asistente para la creación de aplicaciones de inicio de OLE DB.

Además, puede usar atributos para implementar las plantillas de consumidor OLE DB.

|Para obtener información adicional acerca de|Vea|
|-------------------------|---------|
|Utilizar las plantillas de consumidor OLE DB (temas conceptuales)|[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)|
|Utilizar las plantillas de proveedor OLE DB (temas conceptuales)|[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)|
|Clases y macros de plantillas OLE DB|[Referencia de plantillas OLE DB](../../data/oledb/ole-db-templates.md) (Visual C++)|
|Atributos de consumidor OLE DB|[Atributos del consumidor OLE DB](../../windows/ole-db-consumer-attributes.md)|
|Interfaces OLE DB|[Referencia del programador de OLE DB](/sql/connect/oledb/oledb-driver-for-sql-server) (en el SDK de Windows)|
|Ejemplos de plantillas OLE DB|[Ejemplos de plantillas OLE DB](https://github.com/Microsoft/VCSamples)|
|Información general sobre la programación de acceso a datos (Visual C++)|[Programación con Data Access](../../data/data-access-programming-mfc-atl.md)|
|Temas conceptuales de ODBC|[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)|

## <a name="see-also"></a>Vea también

[Acceso a datos en ASP.NET (Visual Studio)](../data-access-in-cpp.md)