---
title: Acceso a datos en Visual C++ | Documentos de Microsoft
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, data access applications
- databases [C++]
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 95da6237-bbe2-480a-ae50-3a520051ceff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bb74d27af485f765e1330bc83ab196e1d9ba6b5c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="data-access-in-visual-c"></a>Acceso a datos en Visual C++

Prácticamente todos los productos de base de datos, SQL y NoSQL, proporcionan una interfaz para aplicaciones nativas de C++. La interfaz estándar de la industria es ODBC, que se admite en los principales productos de base de datos SQL y en muchos productos NoSQL. Para productos que no son de Microsoft, consulte al proveedor para obtener más información. También existen bibliotecas de terceros con diferentes términos de licencia.

Desde 2011, Microsoft cuenta con ODBC como el estándar de conexión para las aplicaciones nativas a bases de datos de Microsoft SQL Server, tanto locales como en la nube. Para más información, vea [Programación del acceso a datos \(MFC/ATL\)](data-access-programming-mfc-atl.md). Las bibliotecas de C++/CLI pueden usar los controladores nativos de ODBC o ADO.NET. Para más información, vea [Acceso a datos en ADO.NET(C++/CLI)](/dotnet/data-access-using-adonet-cpp-cli.md) y [Obtener acceso a los datos en Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

## <a name="in-this-section"></a>En esta sección
[Programación del acceso a datos (MFC/ATL)](data-access-programming-mfc-atl.md) programación con Visual C++, donde la forma preferida es utilizar una de las bibliotecas de clases como la Active Template Library (ATL) o la biblioteca MFC (Microsoft Foundation Classes), de acceso a datos heredados describe que simplifican el trabajo con la API de base de datos.

[Abra Database Connectivity (ODBC)](odbc/open-database-connectivity-odbc.md) biblioteca Microsoft Foundation Classes (MFC) proporciona clases para la programación con Open Database Connectivity (ODBC).

[Programación de OLE DB](oledb/ole-db-programming.md) una interfaz heredada principalmente que todavía es necesaria en algunos escenarios, en concreto cuando se programa en servidores vinculados.

## <a name="related-topics"></a>Temas relacionados
[Conectar con base de datos de SQL con C y C++](/azure/sql-database/sql-database-develop-cplusplus-simple) conectar con base de datos de SQL Azure desde las aplicaciones de C o C++.

[Biblioteca de cliente de almacenamiento de Azure de Microsoft para C++](https://github.com/Azure/azure-storage-cpp)
[el almacenamiento de Azure](/azure/storage/storage-introduction) es una solución de almacenamiento en la nube para aplicaciones modernas que se basan en durabilidad, disponibilidad y escalabilidad para satisfacer las necesidades de su clientes. Conectarse a Azure Storage desde C++ mediante la biblioteca de cliente de Azure Storage para C++.

[ODBC Driver 13.1 for SQL Server: publicó Windows](https://blogs.msdn.microsoft.com/sqlnativeclient/2016/08/01/announcing-the-odbc-driver-13-1-for-sql-server) el último controlador ODBC proporciona acceso a datos sólido para Microsoft SQL Server 2016 Microsoft Azure SQL Database para las aplicaciones basadas en C o C++. Proporciona compatibilidad para las características incluidas que siempre se cifran, Azure Active Directory y grupos de disponibilidad AlwaysOn. También está disponible para MacOS y Linux.     
 
[SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client-programming) SQL Server Native Client es una datos independiente acceso aplicación interfaz de programación (API) utilizada para OLE DB y ODBC, que es compatible con SQL Server 2005 mediante SQL Server 2014. Las aplicaciones nuevas deben usar el controlador ODBC 13.1 para SQL Server.

[Centro de desarrolladores de C++ y Microsoft Azure C](https://azure.microsoft.com/develop/cpp/) Azure facilita el proceso crear aplicaciones de C++ con una mayor flexibilidad, escalabilidad y confiabilidad mediante herramientas que le encanta.    

[Introducción al almacenamiento de Blob desde C++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs) almacenamiento de blobs de Azure es un servicio que almacena los datos no estructurados en la nube como objetos/blobs. El almacenamiento de blobs puede almacenar cualquier tipo de texto o datos binarios, como un documento, un archivo multimedia o un instalador de aplicación. El Almacenamiento de blobs también se conoce como "almacenamiento de objetos".

[ Referencia del programador de ODBC](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference) ODBC la interfaz está diseñada para su uso con el lenguaje de programación de C. El uso de la interfaz ODBC abarca tres áreas: instrucciones SQL, llamadas a funciones de ODBC y programación de C.

## <a name="see-also"></a>Vea también
[Visual C++](../visual-cpp-in-visual-studio.md)
