---
title: Origen de datos (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
ms.openlocfilehash: b435c65bab565e109d37e1dd24e051993cbb30c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397918"
---
# <a name="data-source-odbc"></a>Origen de datos (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En términos de bases de datos, un origen de datos comprende un conjunto de datos específico, la información requerida para tener acceso a esos datos y la ubicación del origen de datos, que se puede describir por medio de un nombre de origen de datos. Para trabajar con la clase [CDatabase](../../mfc/reference/cdatabase-class.md), el origen de datos debe ser uno de los que ha configurado mediante el Administrador de Open Database Connectivity (ODBC). Algunos ejemplos de orígenes de datos son una base de datos remoto que se ejecutan en Microsoft SQL Server a través de una red o un archivo de Microsoft Access en un directorio local. Desde la aplicación se puede tener acceso a cualquier origen de datos para el que se tenga un controlador ODBC.

Se pueden tener uno o varios orígenes de datos activos en la aplicación al mismo tiempo, cada uno de ellos representado por un objeto `CDatabase`. También se pueden tener varias conexiones simultáneas a cualquier origen de datos. La conexión se puede establecer tanto con orígenes de datos remotos como locales, dependiendo de los controladores que estén instalados y de las capacidades de los controladores ODBC. Para obtener más información acerca de los orígenes de datos y el Administrador de ODBC, vea [ODBC](../../data/odbc/odbc-basics.md) y [Administrador ODBC](../../data/odbc/odbc-administrator.md).

Los siguientes temas explican con más detalle los orígenes de datos:

- [Origen de datos: administración de conexiones (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)

- [Origen de datos: determinar el esquema del origen de datos (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)

## <a name="see-also"></a>Vea también

[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)