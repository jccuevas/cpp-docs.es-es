---
title: SQL
ms.date: 05/09/2019
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
ms.openlocfilehash: e5ab824f850b6050e11c10734dd709330af416b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376439"
---
# <a name="sql"></a>SQL

SQL (Lenguaje de consulta estructurado) es una manera de comunicarse con una base de datos relacional que permite definir, consultar, modificar y controlar los datos. Mediante la sintaxis SQL, puede construir una instrucción que extraiga los registros según los criterios que especifique.

> [!NOTE]
> Esta información es aplicable a las clases ODBC de MFC. Si trabaja con las clases DAO de MFC, vea el tema Comparación del código SQL del motor de base de datos de Microsoft Jet y del código SQL ANSI en la Ayuda de DAO.

Las instrucciones SQL comienzan con un verbo que es una palabra clave, como **CREATE** o **SELECT**. SQL es un lenguaje muy eficaz, ya que una sola instrucción puede afectar a toda una tabla.

Existen muchas versiones de SQL, cada una de ellas desarrollada pensando en un sistema de administración de bases de datos (DBMS) en concreto. Las clases de base de datos MFC reconocen un conjunto de instrucciones SQL que se corresponden con el borrador de especificación de SQL de 1991 relativo al Entorno de aplicaciones comunes (CAE) del grupo de acceso SQL y X/Open. Para obtener información acerca de la sintaxis de estas instrucciones, vea Apéndice C en la *referencia del programador del* SDK de *ODBC* en el CD de MSDN Library.

En este tema se explica:

- [La relación entre ODBC y SQL](#_core_open_database_connectivity_.28.odbc.29).

- [Las palabras clave más comunes de SQL usadas por las clases de base de datos](#_core_the_database_classes).

- [Cómo las clases](#_core_how_the_database_classes_use_sql)de base de datos utilizan SQL .

## <a name="open-database-connectivity-odbc"></a><a name="_core_open_database_connectivity_.28.odbc.29"></a>Conectividad de base de datos abierta (ODBC)

Las clases de base de datos se implementan con ODBC, que usa SQL en una interfaz de nivel de llamada en lugar de insertar comandos SQL en el código. ODBC usa SQL para comunicarse con un [origen de datos](../../data/odbc/data-source-odbc.md) mediante controladores ODBC. Estos controladores interpretan el código SQL y lo convierten, si es necesario, para su uso con un formato de base de datos concreto, como Microsoft Access. Para obtener más información sobre la forma en que ODBC usa SQL, vea [ODBC](../../data/odbc/odbc-basics.md) y la *referencia del programador* del SDK de ODBC en el CD de MSDN Library.

## <a name="database-classes"></a><a name="_core_the_database_classes"></a> Clases de base de datos

> [!NOTE]
> El Asistente para consumidores ODBC MFC no está disponible en Visual Studio 2019 ni en versiones posteriores. Aun así, puede crear un consumidor manualmente.

Las clases de base de datos están diseñadas de modo que se pueda manipular y actualizar datos en un [origen de datos](../../data/odbc/data-source-odbc.md) existente. El [Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md), el [Asistente para consumidores ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (acceso a través de **Agregar clase**) y las clases de base de datos construyen automáticamente la mayoría de las instrucciones SQL.

Las clases de base de datos usan una parte de SQL conocida como Lenguaje de manipulación de datos (DML). Estos comandos permiten trabajar con todo el origen de datos o con parte de este, agregar nuevos registros y modificar y eliminar registros. En la tabla siguiente se muestran las palabras clave más comunes de SQL y las formas en que las usan las clases de base de datos.

### <a name="some-common-sql-keywords"></a>Algunas palabras clave comunes de SQL

|Palabra clave de SQL|Los asistentes y las clases de base de datos la usan|
|-----------------|---------------------------------------------|
|**Seleccione**|Para identificar qué tablas y columnas del origen de datos se van a usar.|
|**Dónde**|Para aplicar un filtro que limite la selección.|
|**ORDER BY**|Para aplicar un criterio de ordenación al conjunto de registros.|
|**insertar**|Para agregar nuevos registros a un conjunto de registros.|
|**Eliminar**|Para eliminar registros de un conjunto de registros.|
|**actualizar**|Para modificar los campos de un registro.|

Además, las clases de base de datos reconocen las instrucciones **CALL** de ODBC, que se pueden usar para llamar a una consulta predefinida (o un procedimiento almacenado) en algunos orígenes de datos. El controlador de base de datos ODBC interpreta estas instrucciones y sustituye el comando apropiado para cada DBMS.

> [!NOTE]
> No todos los DBMS admiten las instrucciones **CALL**.

Si las clases no reconocen una instrucción proporcionada por el usuario en `CRecordset::Open`, se interpreta como un nombre de tabla.

Para obtener una explicación de cómo el marco de trabajo construye instrucciones SQL, vea Conjunto de registros: cómo los conjuntos de [registros seleccionan registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) y SQL: personalizar la instrucción SQL del conjunto de [registros (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

Las bases de datos SQL usan tipos de datos similares a los que se emplean en C y C++. Para obtener una explicación de estas similitudes, vea [SQL: SQL y C+ tipos de datos (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

Puede encontrar más información acerca de SQL, incluida una lista de instrucciones SQL admitidas, tipos de datos, gramática de núcleo de SQL y una lista de lectura de publicaciones recomendadas sobre SQL, en la *referencia del programador del* SDK de *ODBC* en el CD de MSDN Library.

## <a name="how-the-database-classes-use-sql"></a><a name="_core_how_the_database_classes_use_sql"></a> Cómo usan SQL las clases de base de datos

Los conjuntos de registros que se derivan de las clases de base de datos usan ODBC para comunicarse con un origen de datos, mientras que ODBC recupera los registros del origen de datos mediante el envío de instrucciones SQL. En este tema se explica la relación que existe entre las clases de base de datos y SQL.

Un conjunto de registros construye una instrucción SQL mediante la integración de las partes de una instrucción SQL en un elemento `CString`. La cadena se construye como una instrucción **SELECT**, que devuelve un conjunto de registros.

Cuando el conjunto de registros llama a ODBC para enviar una instrucción SQL al origen de datos, el Administrador de controladores ODBC pasa la instrucción al controlador ODBC y este lo envía al DBMS subyacente. El DBMS devuelve un conjunto de resultados de registros y el controlador ODBC devuelve los registros a la aplicación. Las clases de base de datos permiten al programa acceder al conjunto de resultados en una clase de C++ con seguridad de tipos derivada de `CRecordset`.

En los temas siguientes se proporciona más información sobre la manera en que las clases de base de datos usan SQL:

- [SQL: personalización de la instrucción SQL del conjunto de registros (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL: Tipos de datos de SQL y C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL: Realizar llamadas directas a SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>Consulte también

[Conectividad de base de datos abierta (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Fundamentos de ODBC](../../data/odbc/odbc-basics.md)
