---
title: Crear una tabla en un origen de datos ODBC mediante programación
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 25c975560d6a73ce67294d97830b2f5bec9cd635
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213283"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Origen de datos: Crear una tabla en un origen de datos ODBC mediante programación

En este tema se explica cómo crear una tabla para el origen de datos, utilizando la función miembro `ExecuteSQL` de la clase `CDatabase`, pasando la función a una cadena que contiene una instrucción **CREATE TABLE** SQL.

Para obtener información general sobre los orígenes de datos ODBC en MFC, vea [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md). Origen de [datos del tema: configurar un origen de datos ODBC mediante programación](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) describe la creación de orígenes de datos.

Una vez establecido el origen de datos, puede crear fácilmente tablas mediante la función miembro `ExecuteSQL` y la instrucción SQL **CREATE TABLE** . Por ejemplo, si tuviera un objeto `CDatabase` denominado `myDB`, podría usar el siguiente código MFC para crear una tabla:

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

En este ejemplo de código se crea una tabla denominada "oficinas" en la conexión de origen de datos de Microsoft Access mantenida por `myDB`; la tabla contiene dos campos "OfficeID" y "OfficeName".

> [!NOTE]
>  Los tipos de campo especificados en la instrucción SQL **CREATE TABLE** pueden variar según el controlador ODBC que esté usando. El programa Microsoft Query (distribuido con C++ visual 1,5) es una manera de detectar los tipos de campo que están disponibles para un origen de datos. En Microsoft Query, haga clic en **archivo**, en **Table_Definition**, seleccione una tabla de un origen de datos y mire el tipo que se muestra en el cuadro combinado **tipo** . También existe la sintaxis SQL para crear índices.

## <a name="see-also"></a>Consulte también

[Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)
