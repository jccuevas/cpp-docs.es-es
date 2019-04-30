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
ms.openlocfilehash: 142d067b6fbc9e2357ff8fc23fd931a1194477e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398074"
---
# <a name="data-access-in-visual-c"></a>Acceso a datos en Visual C++

Prácticamente todos los productos de base de datos, SQL y NoSQL, proporcionan una interfaz para aplicaciones nativas de C++. La interfaz estándar de la industria es ODBC, que se admite en los principales productos de base de datos SQL y en muchos productos NoSQL. Para productos que no son de Microsoft, consulte al proveedor para obtener más información. También existen bibliotecas de terceros con diferentes términos de licencia.

Desde 2011, Microsoft cuenta con ODBC como el estándar de conexión para las aplicaciones nativas a bases de datos de Microsoft SQL Server, tanto locales como en la nube. Para más información, vea [Programación del acceso a datos \(MFC/ATL\)](data-access-programming-mfc-atl.md). Las bibliotecas de C++/CLI pueden usar los controladores nativos de ODBC o ADO.NET. Para más información, vea [Acceso a datos en ADO.NET(C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) y [Obtener acceso a los datos en Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

## <a name="in-this-section"></a>En esta sección

[Acceso a los datos de programación (MFC/ATL)](data-access-programming-mfc-atl.md)<br/>
Describe la programación de acceso a datos heredados con Visual C++, donde se suele utilizar una de las bibliotecas de clases, como Active Template Library (ATL) o Microsoft Foundation Class (MFC), que simplifican el trabajo con las API de bases de datos.

[Conectividad abierta de bases de datos (ODBC)](odbc/open-database-connectivity-odbc.md)<br/>
La biblioteca Microsoft Foundation Classes (MFC) proporciona clases para la programación con ODBC (Open Database Connectivity, Conectividad abierta de bases de datos).

[Programación de OLE DB](oledb/ole-db-programming.md)<br/>
Una interfaz heredada principalmente que es necesario en algunos escenarios, concretamente cuando se está programando en servidores vinculados.

## <a name="related-topics"></a>Temas relacionados

[Conectarse a SQL Database mediante C y C++](/azure/sql-database/sql-database-develop-cplusplus-simple)<br/>
Conectarse a Azure SQL Database desde aplicaciones de C o C++.

[Biblioteca de cliente de Microsoft Azure Storage para C++](https://github.com/Azure/azure-storage-cpp)<br/>
[Azure Storage](/azure/storage/storage-introduction) es una solución de almacenamiento en la nube para aquellas aplicaciones modernas que necesitan durabilidad, disponibilidad y escalabilidad para satisfacer las necesidades de sus clientes. Conectarse a Azure Storage desde C++ mediante la biblioteca de cliente de Azure Storage para C++.

[Controlador ODBC 13.1 para SQL Server - Windows publicado](https://blogs.msdn.microsoft.com/sqlnativeclient/2016/08/01/announcing-the-odbc-driver-13-1-for-sql-server)<br/>
El controlador ODBC más reciente proporciona un acceso a datos sólido a aplicaciones basadas en Microsoft Azure SQL Database para C/C++ de Microsoft SQL Server 2016. Proporciona compatibilidad con las características incluidas always encrypted, Azure Active Directory y grupos de disponibilidad AlwaysOn. También está disponible para MacOS y Linux.

[SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client-programming)<br/>
SQL Server Native Client es una interfaz de programación de aplicaciones (API) independiente de acceso a datos que se usa para OLE DB y ODBC, y que es compatible con SQL Server 2005-2014. Las aplicaciones nuevas deben usar el controlador ODBC 13.1 para SQL Server.

[Centro para desarrolladores de C++ y de C de Microsoft Azure](https://azure.microsoft.com/develop/cpp/)<br/>
Azure facilita la compilación de aplicaciones en C++ con más flexibilidad, escalabilidad y confiabilidad, usando las herramientas que prefiera.

[Cómo usar Blob Storage en C++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs)<br/>
Azure Blob Storage es un servicio que almacena datos no estructurados en la nube como objetos o blobs. El almacenamiento de blobs puede almacenar cualquier tipo de texto o datos binarios, como un documento, un archivo multimedia o un instalador de aplicación. El Almacenamiento de blobs también se conoce como "almacenamiento de objetos".

[ Referencia del programador de ODBC](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference)<br/>
La interfaz ODBC está diseñada para su uso con el lenguaje de programación C. Uso de la interfaz ODBC abarca tres áreas: Las instrucciones SQL, llamadas a funciones ODBC y programación de C.

## <a name="see-also"></a>Vea también

[Visual C++](../overview/visual-cpp-in-visual-studio.md)
