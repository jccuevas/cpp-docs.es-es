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
ms.openlocfilehash: 38a625c73a17ecae4d8adc61e8c56bc4bdda67f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320082"
---
# <a name="odbc-and-mfc"></a>ODBC y MFC

> [!NOTE]
> Para usar las clases de base de datos MFC, debe tener el controlador ODBC adecuado para el origen de datos. El último controlador ODBC de Microsoft para SQL Server es [Microsoft ODBC Driver 13 para SQL Server](https://www.microsoft.com/download/details.aspx?id=50420). La mayoría de los proveedores de bases de datos proporcionan un controlador ODBC para Windows.

En este tema se presentan los conceptos principales de las clases de base de datos basadas en ODBC de la biblioteca Microsoft Foundation Classes (MFC) y se proporciona información general sobre cómo funcionan juntas las clases. Para obtener más información acerca de ODBC y MFC, vea los temas siguientes:

- [Conectarse a un origen de datos](connecting-to-a-data-source.md)

- [Selección y manipulación de registros](selecting-and-manipulating-records.md)

- [Visualización y manipulación de datos en un formulario](displaying-and-manipulating-data-in-a-form.md)

- [Trabajar con documentos y vistas](working-with-documents-and-views.md)

- [Acceso a ODBC y SQL](access-to-odbc-and-sql.md)

- [Información adicional sobre las clases ODBC de MFC](further-reading-about-the-mfc-odbc-classes.md)

Las clases de base de datos MFC basadas en ODBC están diseñadas para proporcionar acceso a cualquier base de datos para la que está disponible un controlador ODBC. Dado que las clases usan ODBC, la aplicación puede tener acceso a datos en muchos formatos de datos diferentes y configuraciones locales/remotas diferentes. No es necesario escribir código de caso especial para gestionar diferentes sistemas de administración de bases de datos (DBMS). Siempre que los usuarios tengan un controlador ODBC adecuado para los datos a los que desean acceder, pueden usar el programa para manipular los datos de las tablas almacenadas allí.

## <a name="see-also"></a>Consulte también

[Conectividad de base de datos abierta (ODBC)](open-database-connectivity-odbc.md)
