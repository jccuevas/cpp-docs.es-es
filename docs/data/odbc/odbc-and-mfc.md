---
title: ODBC y MFC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], MFC
- connections [C++], databases
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- MFC [C++], ODBC and
- database connections [C++], MFC ODBC classes
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
ms.openlocfilehash: 94a3455324a52b789bcfcf192b698a3c42b37c00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213204"
---
# <a name="odbc-and-mfc"></a>ODBC y MFC

> [!NOTE]
>  Para utilizar las clases de base de datos MFC, debe tener el controlador ODBC apropiado para el origen de datos. El controlador ODBC más reciente de Microsoft para SQL Server es [Microsoft ODBC driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=50420). La mayoría de los proveedores de bases de datos proporcionan un controlador ODBC para Windows.

En este tema se presentan los conceptos principales de las clases de base de datos basadas en ODBC de la biblioteca de Microsoft Foundation Classes (MFC) y se proporciona información general sobre el funcionamiento conjunto de las clases. Para obtener más información acerca de ODBC y MFC, vea los temas siguientes:

- [Conexión a un origen de datos](connecting-to-a-data-source.md)

- [Selección y manipulación de registros](selecting-and-manipulating-records.md)

- [Visualización y manipulación de datos en un formulario](displaying-and-manipulating-data-in-a-form.md)

- [Trabajar con documentos y vistas](working-with-documents-and-views.md)

- [Acceso a ODBC y SQL](access-to-odbc-and-sql.md)

- [Información adicional sobre las clases ODBC de MFC](further-reading-about-the-mfc-odbc-classes.md)

Las clases de base de datos MFC basadas en ODBC están diseñadas para proporcionar acceso a cualquier base de datos para la que esté disponible un controlador ODBC. Dado que las clases usan ODBC, la aplicación puede tener acceso a los datos en muchos formatos de datos diferentes y configuraciones locales o remotas diferentes. No es necesario escribir código de caso especial para administrar distintos sistemas de administración de bases de datos (DBMS). Siempre que los usuarios tengan un controlador ODBC adecuado para los datos a los que desean obtener acceso, pueden usar el programa para manipular los datos de las tablas almacenadas allí.

## <a name="see-also"></a>Consulte también

[Conectividad abierta de bases de datos (ODBC)](open-database-connectivity-odbc.md)
