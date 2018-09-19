---
title: SQL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5e92b0d57ca47c4be7029b7713eeb84e7b3dd2ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106173"
---
# <a name="sql"></a>SQL

SQL (lenguaje de consulta estructurado) es una manera de comunicarse con una base de datos relacional que permite definir, consultar, modificar y controlar los datos. Mediante la sintaxis SQL, puede construir una instrucción que extraiga los registros según los criterios que especifique.  
  
> [!NOTE]
>  Esta información se aplica a las clases ODBC de MFC. Si está trabajando con las clases DAO de MFC, vea el tema comparación de Microsoft Jet Database Engine SQL y SQL ANSI en la Ayuda de DAO.  
  
Las instrucciones SQL comienzan con un verbo de palabra clave como **crear** o **seleccione**. SQL es un lenguaje muy eficaz; una sola instrucción puede afectar a toda la tabla.  
  
Existen muchas versiones de SQL, cada uno de ellos desarrollado con un DBMS concreto en mente. Las clases de base de datos MFC reconocen un conjunto de instrucciones SQL que corresponde a la X / Open y especificación de borrador del entorno de aplicaciones comunes (CAE) de SQL acceso grupo SQL (1991). Para obtener información sobre la sintaxis de estas instrucciones, consulte el apéndice C en el *ODBC SDK* *referencia del programador* en el CD de MSDN Library.  
  
En este tema se explica:  
  
- [La relación entre ODBC y SQL](#_core_open_database_connectivity_.28.odbc.29).  
  
- [Las palabras clave SQL más comunes utilizadas por las clases de base de datos](#_core_the_database_classes).  
  
- [Usan de las clases de base de datos SQL](#_core_how_the_database_classes_use_sql).  
  
##  <a name="_core_open_database_connectivity_.28.odbc.29"></a> Conectividad abierta de base de datos (ODBC)  

Las clases de base de datos se implementan con ODBC, que utiliza SQL en una interfaz de nivel de llamada en lugar de incrustar comandos SQL en el código. ODBC utiliza SQL para comunicarse con un [origen de datos](../../data/odbc/data-source-odbc.md) mediante controladores ODBC. Estos controladores interpretan el código SQL y convierten, si es necesario, para su uso con un formato de base de datos concreta, como Microsoft Access. Para obtener más información sobre cómo utiliza ODBC SQL, consulte [ODBC](../../data/odbc/odbc-basics.md) y el SDK de ODBC *referencia del programador* en el CD de MSDN Library.  
  
##  <a name="_core_the_database_classes"></a> Clases de base de datos  

Las clases de base de datos se ha diseñado para permitirle manipular y actualizar datos en una existente [origen de datos](../../data/odbc/data-source-odbc.md). El [MFC Application Wizard](../../mfc/reference/database-support-mfc-application-wizard.md), el [Asistente para consumidores ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (acceso a través **Agregar clase**), y las clases de base de datos crean la mayoría de las instrucciones SQL automáticamente.  
  
Las clases de base de datos usan una parte de SQL que se conoce como lenguaje de manipulación de datos (DML). Estos comandos permiten trabajar con todo o parte del origen de datos, agregar nuevos registros, modificar registros y eliminar registros. En la tabla siguiente se enumera las palabras clave SQL más comunes y las formas en las clases de base de datos usan.  
  
### <a name="some-common-sql-keywords"></a>Algunas palabras clave SQL comunes  
  
|Palabra clave SQL|Utilizan los asistentes y las clases de base de datos|  
|-----------------|---------------------------------------------|  
|**SELECT**|Para identificar qué tablas y columnas del origen de datos que se van a utilizar.|  
|**WHERE**|Para aplicar un filtro que limita la selección.|  
|**ORDER BY**|Para aplicar un criterio de ordenación para el conjunto de registros.|  
|**INSERTAR**|Para agregar nuevos registros a un conjunto de registros.|  
|**ELIMINAR**|Para eliminar registros de un conjunto de registros.|  
|**ACTUALIZACIÓN DE**|Para modificar los campos de un registro.|  
  
Además, las clases de base de datos reconocen ODBC **llamar** instrucciones, que puede usar para llamar a una consulta predefinida (o un procedimiento almacenado) en algunos orígenes de datos. El controlador de base de datos ODBC interpreta estas instrucciones y sustituye el comando apropiado para cada DBMS.  
  
> [!NOTE]
>  No todo el soporte técnico de los DBMS **llamar** instrucciones.  
  
Si las clases no reconocen una instrucción proporcionada por el usuario en `CRecordset::Open`, se interpreta como un nombre de tabla.  
  
Para obtener una explicación de cómo el marco de trabajo crea instrucciones SQL, consulte [conjunto de registros: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) y [SQL: SQL instrucción (ODBC de personalizar un conjunto de registros)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
Las bases de datos SQL usan tipos de datos similares a aquellos utilizados en C y C++. Para obtener una explicación de estas similitudes, consulte [SQL: SQL y tipos de datos de C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).  
  
Puede encontrar más información sobre SQL, incluida una lista de instrucciones SQL compatibles, tipos de datos, gramática básica de SQL y una lista de lectura recomendada publicaciones sobre SQL, en el *ODBC SDK* *referencia del programador*  en el CD de MSDN Library.  
  
##  <a name="_core_how_the_database_classes_use_sql"></a> Usan de las clases de base de datos SQL  

Los conjuntos de registros que se derivan las clases de base de datos usan ODBC para comunicarse con un origen de datos y ODBC recupera los registros del origen de datos mediante el envío de instrucciones SQL. En este tema se explica la relación entre las clases de base de datos y SQL.  
  
Un conjunto de registros crea una instrucción SQL mediante la creación de las partes de una instrucción SQL a un `CString`. La cadena se genera como un **seleccione** instrucción, que devuelve un conjunto de registros.  
  
Cuando el conjunto de registros llama a ODBC para enviar una instrucción SQL al origen de datos, el Administrador de controladores ODBC pasa la instrucción para el controlador ODBC y el controlador lo envía del DBMS subyacente. El DBMS devuelve un conjunto de resultados de registros y el controlador ODBC devuelve los registros a la aplicación. Las clases de base de datos permiten el acceso del programa el conjunto de resultados en una clase de C++ con seguridad de tipos derivados de `CRecordset`.  
  
Los temas siguientes proporcionan más información acerca del usan de las clases de base de datos SQL:  
  
- [SQL: Personalizar la instrucción de SQL del conjunto de registros (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)  
  
- [SQL: Tipos de datos de SQL y C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)  
  
- [SQL: Realizar llamadas directas a SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)  
  
## <a name="see-also"></a>Vea también  

[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)