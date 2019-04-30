---
title: Crear una tabla mediante programación en un origen de datos ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 61d3f3e39362db27d1e3abc00fa3cb9ea82b86e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395941"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Origen de datos: Crear una tabla en un origen de datos ODBC mediante programación

En este tema se explica cómo crear una tabla para los datos de origen, utilizando el `ExecuteSQL` función miembro de clase `CDatabase`, pase a la función de una cadena que contiene un **CREATE TABLE** instrucción SQL.

Para obtener información general sobre orígenes de datos ODBC de MFC, vea [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md). El tema [origen de datos: Configurar mediante programación un origen de datos ODBC](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) describe los orígenes de datos.

Cuando haya establecido el origen de datos, puede crear fácilmente tablas usando el `ExecuteSQL` función miembro y el **CREATE TABLE** instrucción SQL. Por ejemplo, si tuviera un `CDatabase` objeto llamado `myDB`, podría usar el siguiente código MFC para crear una tabla:

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

Este ejemplo de código crea una tabla denominada "OFFICES" en la conexión de origen de datos de Microsoft Access mantenida por `myDB`; la tabla contiene dos campos "OfficeID" y "OfficeName."

> [!NOTE]
>  Los tipos de campo especificados en la **CREATE TABLE** instrucción SQL puede variar según el controlador ODBC que está usando. El programa Microsoft Query (distribuido con Visual C++ 1.5) es una manera de detectar los tipos de campo están disponibles para un origen de datos. En Microsoft Query, haga clic en **archivo**, haga clic en **Table_Definition**, seleccione una tabla de un origen de datos y mire el tipo se muestra en el **tipo** cuadro combinado. También existe la sintaxis SQL para crear índices.

## <a name="see-also"></a>Vea también

[Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)