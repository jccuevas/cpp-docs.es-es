---
title: Crear mediante programación una tabla en un origen de datos ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 6cf26cad7fe39f374daf371902525087b446658c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358838"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Origen de datos: Crear una tabla en un origen de datos ODBC mediante programación

En este tema se explica cómo crear una `ExecuteSQL` tabla para `CDatabase`el origen de datos, mediante la función miembro de la clase , pasando la función una cadena que contiene una instrucción SQL **CREATE TABLE.**

Para obtener información general acerca de los orígenes de datos ODBC en MFC, vea Origen de [datos (ODBC)](../../data/odbc/data-source-odbc.md). El tema Origen de [datos: Configuración mediante programación de un origen](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) de datos ODBC describe la creación de orígenes de datos.

Cuando haya establecido el origen de datos, `ExecuteSQL` puede crear fácilmente tablas mediante la función miembro y la instrucción SQL **CREATE TABLE.** Por ejemplo, si `CDatabase` tuviera `myDB`un objeto llamado , podría usar el siguiente código MFC para crear una tabla:

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

En este ejemplo de código se crea una tabla denominada `myDB`"OFFICES" en la conexión de origen de datos de Microsoft Access mantenida por ; la tabla contiene dos campos "OfficeID" y "OfficeName."

> [!NOTE]
> Los tipos de campo especificados en la instrucción SQL **CREATE TABLE** pueden variar según el controlador ODBC que esté utilizando. El programa Microsoft Query (distribuido con Visual C++ 1.5) es una forma de descubrir qué tipos de campo están disponibles para un origen de datos. En Microsoft Query, haga clic en **Archivo**, haga clic en **Table_Definition**, seleccione una tabla de un origen de datos y examine el tipo que se muestra en el cuadro combinado **Tipo.** La sintaxis SQL también existe para crear índices.

## <a name="see-also"></a>Consulte también

[Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)
