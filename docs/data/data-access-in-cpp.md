---
title: Acceso a datos en Visual C++
ms.date: 03/28/2017
helpviewer_keywords:
- Visual C++, data access applications
- databases [C++]
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 95da6237-bbe2-480a-ae50-3a520051ceff
ms.openlocfilehash: 42c36259b14a7f0341e383bb3a7f2760bab165aa
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538597"
---
# <a name="data-access-in-visual-c"></a>Acceso a datos en Visual C++

Prácticamente todos los productos de base de datos, SQL y NoSQL, proporcionan una interfaz para aplicaciones nativas de C++. La interfaz estándar de la industria es ODBC, que se admite en los principales productos de base de datos SQL y en muchos productos NoSQL. Para productos que no son de Microsoft, consulte al proveedor para obtener más información. También existen bibliotecas de terceros con diferentes términos de licencia.

Desde 2011, Microsoft cuenta con ODBC como el estándar de conexión para las aplicaciones nativas a bases de datos de Microsoft SQL Server, tanto locales como en la nube. Para más información, vea [Programación del acceso a datos \(MFC/ATL\)](data-access-programming-mfc-atl.md). Las bibliotecas de C++/CLI pueden usar los controladores nativos de ODBC o ADO.NET. Para obtener más información, vea [acceso a datos con ADO.net (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) y [obtener acceso a datos en Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

## <a name="in-this-section"></a>En esta sección

[Programación de acceso a datos (MFC/ATL)](data-access-programming-mfc-atl.md)<br/>
Describe la programación de acceso a datos heredados con Visual C++, donde se suele utilizar una de las bibliotecas de clases, como Active Template Library (ATL) o Microsoft Foundation Class (MFC), que simplifican el trabajo con las API de bases de datos.

[Conectividad abierta de bases de datos (ODBC)](odbc/open-database-connectivity-odbc.md)<br/>
La biblioteca Microsoft Foundation Classes (MFC) proporciona clases para la programación con ODBC (Open Database Connectivity, Conectividad abierta de bases de datos).

[Programación de OLE DB](oledb/ole-db-programming.md)<br/>
Interfaz principalmente heredada que todavía es necesaria en algunos escenarios, en concreto al programar con servidores vinculados.

## <a name="related-topics"></a>Temas relacionados

[Conexión a SQL Database mediante C y C++](/azure/sql-database/sql-database-develop-cplusplus-simple)<br/>
Conexión a Azure SQL Database desde aplicaciones de C o C++.

[Biblioteca de cliente de Microsoft Azure Storage para C++](https://github.com/Azure/azure-storage-cpp)<br/>
[Azure Storage](/azure/storage/common/storage-introduction) es una solución de almacenamiento en la nube para aquellas aplicaciones modernas que necesitan durabilidad, disponibilidad y escalabilidad para satisfacer las necesidades de sus clientes. Conectarse a Azure Storage desde C++ mediante la biblioteca de cliente de Azure Storage para C++.

[Controlador ODBC de SQL Server](/sql/connect/odbc/microsoft-odbc-driver-for-sql-server)<br/>
El controlador ODBC más reciente proporciona un acceso a datos sólido a aplicaciones basadas en Microsoft SQL Server y Microsoft Azure SQL Database para C/C++. Proporciona compatibilidad con características, incluidas Always Encrypted, Azure Active Directory y Grupos de disponibilidad Always On. También está disponible para MacOS y Linux.

[Controlador OLE DB para SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)<br/>
El controlador de OLE DB más reciente es una interfaz de programación de aplicaciones (API) independiente de acceso a datos que admite Microsoft SQL Server y Microsoft Azure SQL Database.

[Centro para desarrolladores de C y C++ de Microsoft Azure](https://azure.microsoft.com/develop/cpp/)<br/>
Azure facilita la compilación de aplicaciones en C++ con más flexibilidad, escalabilidad y confiabilidad, usando las herramientas que prefiera.

[Cómo usar Blob Storage de C++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs)<br/>
Almacenamiento de blobs de Azure es un servicio que almacena datos no estructurados en la nube como objetos o blobs. El Almacenamiento de blobs puede almacenar cualquier tipo de datos binarios o texto, como un documento, un archivo multimedia o un instalador de aplicación. El Almacenamiento de blobs a veces se conoce como "almacenamiento de objetos".

[Referencia del programador de ODBC](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference)<br/>
La interfaz ODBC está diseñada para su uso con el lenguaje de programación C. El uso de la interfaz ODBC abarca tres áreas: instrucciones SQL, llamadas a funciones de ODBC y programación de C.

## <a name="see-also"></a>Consulte también

[C++ en Visual Studio](../overview/visual-cpp-in-visual-studio.md)
