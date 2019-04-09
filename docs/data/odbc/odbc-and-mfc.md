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
ms.openlocfilehash: 9b7d04e2eb8bbb1adf96e05282861ef33e20434a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031185"
---
# <a name="odbc-and-mfc"></a>ODBC y MFC

> [!NOTE]
>  Para usar las clases de base de datos MFC, debe tener el controlador ODBC adecuado para el origen de datos. El controlador ODBC de Microsoft más reciente para SQL Server es [Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=50420). La mayoría de los proveedores de base de datos proporciona un controlador ODBC para Windows.

Este tema presenta los conceptos principales de las clases de base de datos basadas en ODBC de la biblioteca Microsoft Foundation Classes (MFC) y proporciona información general sobre cómo funcionan conjuntamente las clases. Para obtener más información sobre ODBC y MFC, vea los temas siguientes:

- [Conectarse a un origen de datos](connecting-to-a-data-source.md)

- [Seleccionar y manipular registros](selecting-and-manipulating-records.md)

- [Mostrar y manipular datos en un formulario](displaying-and-manipulating-data-in-a-form.md)

- [Trabajar con documentos y vistas](working-with-documents-and-views.md)

- [Acceso a ODBC y SQL](access-to-odbc-and-sql.md)

- [Información adicional sobre las clases ODBC de MFC](further-reading-about-the-mfc-odbc-classes.md)

Las clases de base de datos MFC basadas en ODBC están diseñadas para proporcionar acceso a cualquier base de datos para el que está disponible un controlador ODBC. Dado que las clases utilizan ODBC, la aplicación puede acceder a datos en muchos formatos de datos diferentes y distintas configuraciones locales y remotos. No es necesario escribir código de casos especiales para administrar sistemas de administración de otra base de datos (DBMS). Siempre y cuando los usuarios tienen un controlador ODBC adecuado para los datos que desean obtener acceso, puede usar el programa para manipular los datos en tablas que se almacenan allí.

## <a name="see-also"></a>Vea también

[Conectividad abierta de bases de datos (ODBC)](open-database-connectivity-odbc.md)