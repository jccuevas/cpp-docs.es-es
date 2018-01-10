---
title: SQL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0c4283e73b800ac0fd4d448d5137372807f893d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sql"></a>SQL
SQL (lenguaje de consulta estructurado) es una manera para comunicarse con una base de datos relacional que permite definir, consultar, modificar y controlar los datos. Mediante la sintaxis SQL, puede construir una instrucción que extraiga los registros según los criterios que especifique.  
  
> [!NOTE]
>  Esta información se aplica a las clases ODBC de MFC. Si está trabajando con las clases DAO de MFC, vea el tema comparación de base de datos de motor de SQL de Microsoft Jet y SQL ANSI en la Ayuda de DAO.  
  
 Las instrucciones SQL comienzan con un verbo de palabra clave como **crear** o **seleccione**. SQL es un lenguaje muy eficaz; una sola instrucción puede afectar a toda una tabla.  
  
 Existen muchas versiones de SQL, cada uno de ellos desarrollado con un DBMS concreto en mente. Las clases de base de datos MFC reconocen un conjunto de instrucciones SQL que corresponde a X / Open y especificación de borrador SQL de SQL acceso grupo Common Applications Environment (CAE) (1991). Para obtener información acerca de la sintaxis de estas instrucciones, consulte el apéndice C en el *el SDK de ODBC* *referencia del programador* en el CD de MSDN Library.  
  
 En este tema se explica:  
  
-   [La relación entre ODBC y SQL](#_core_open_database_connectivity_.28.odbc.29).  
  
-   [Las palabras clave SQL más comunes utilizadas por las clases de base de datos](#_core_the_database_classes).  
  
-   [Cómo utilizan las clases de base de datos SQL](#_core_how_the_database_classes_use_sql).  
  
##  <a name="_core_open_database_connectivity_.28.odbc.29"></a>Open Database Connectivity (ODBC)  
 Las clases de base de datos se implementan con ODBC, que utiliza SQL en una interfaz de nivel de llamada en lugar de incrustar comandos SQL en el código. ODBC utiliza SQL para comunicarse con un [origen de datos](../../data/odbc/data-source-odbc.md) mediante controladores ODBC. Estos controladores interpretan el código SQL y traducen, si es necesario, para su uso con un formato de base de datos concreta, como Microsoft Access. Para obtener más información sobre cómo utiliza ODBC SQL, consulte [ODBC](../../data/odbc/odbc-basics.md) y el SDK de ODBC *referencia del programador* en el CD de MSDN Library.  
  
##  <a name="_core_the_database_classes"></a>Clases de base de datos  
 Las clases de base de datos están diseñadas para permitirle manipular y actualizar datos en una existente [origen de datos](../../data/odbc/data-source-odbc.md). El [Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md), el [Asistente para consumidores ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (acceso a través de **Agregar clase**), y las clases de base de datos crean la mayoría de las instrucciones SQL para el programador.  
  
 Las clases de base de datos utilizan una parte de SQL conocida como lenguaje de manipulación de datos (DML). Estos comandos permiten trabajar con la totalidad o parte del origen de datos, agregar nuevos registros, modificar registros y eliminar registros. En la tabla siguiente se enumera las palabras clave SQL más comunes y las formas de las clases de base de datos usan.  
  
### <a name="some-common-sql-keywords"></a>Algunas palabras clave SQL comunes  
  
|La palabra clave SQL|Los asistentes y las clases de base de datos usarlo|  
|-----------------|---------------------------------------------|  
|**SELECT**|Para identificar qué tablas y columnas del origen de datos que se van a utilizar.|  
|**WHERE**|Para aplicar un filtro que limita la selección.|  
|**ORDER BY**|Para aplicar un criterio de ordenación para el conjunto de registros.|  
|**INSERTAR**|Para agregar nuevos registros a un conjunto de registros.|  
|**ELIMINAR**|Para eliminar registros de un conjunto de registros.|  
|**ACTUALIZACIÓN**|Para modificar los campos de un registro.|  
  
 Además, las clases de base de datos reconocen ODBC **llamar** instrucciones, que puede usar para llamar a una consulta predefinida (o procedimiento almacenado) en algunos orígenes de datos. El controlador de base de datos ODBC interpreta estas instrucciones y sustituye el comando apropiado para cada DBMS.  
  
> [!NOTE]
>  No todo el soporte de DBMS **llamar** instrucciones.  
  
 Si las clases no reconocen una instrucción proporcionada por el usuario en `CRecordset::Open`, se interpretará como un nombre de tabla.  
  
 Para obtener una explicación de cómo el marco de trabajo crea instrucciones SQL, consulte [conjunto de registros: cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) y [SQL: SQL instrucción (ODBC de personalizar un conjunto de registros)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
 Bases de datos SQL usan tipos de datos similares a aquellos utilizados en C y C++. Para obtener una descripción de estas similitudes, consulte [SQL: SQL y tipos de datos de C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).  
  
 También puede encontrar más información acerca de SQL, incluida una lista de instrucciones SQL compatibles, tipos de datos, gramática básica de SQL y una lista de lectura de publicaciones recomendadas acerca de SQL, en la *el SDK de ODBC* *referencia del programador*  en el CD de MSDN Library.  
  
##  <a name="_core_how_the_database_classes_use_sql"></a>Cómo utilizan las clases de base de datos SQL  
 Los conjuntos de registros que se derivan de las clases de base de datos utilizan ODBC para comunicarse con un origen de datos, y ODBC recupera los registros del origen de datos mediante el envío de instrucciones SQL. Este tema explica la relación entre las clases de base de datos y SQL.  
  
 Un conjunto de registros crea una instrucción SQL con la construcción de las partes de una instrucción SQL en un `CString`. La cadena se construye como una **seleccione** instrucción, que devuelve un conjunto de registros.  
  
 Cuando el conjunto de registros llama a ODBC para enviar una instrucción SQL al origen de datos, el Administrador de controladores ODBC pasa la instrucción en el controlador ODBC y el controlador lo envía del DBMS subyacente. El DBMS devuelve un conjunto de resultados de registros, y el controlador ODBC devuelve los registros a la aplicación. Las clases de base de datos permiten el acceso del programa el conjunto de resultados en una clase de C++ con seguridad de tipos se derivan `CRecordset`.  
  
 Los temas siguientes proporcionan más información acerca del usan de las clases de base de datos SQL:  
  
-   [SQL: Personalizar la instrucción de SQL del conjunto de registros (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)  
  
-   [SQL: Tipos de datos de SQL y C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)  
  
-   [SQL: Realizar llamadas directas a SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)  
  
## <a name="see-also"></a>Vea también  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)