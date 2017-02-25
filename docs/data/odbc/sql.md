---
title: "SQL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de base de datos [C++], instrucciones SQL"
  - "ODBC [C++], implementación de SQL"
  - "SQL [C++]"
  - "SQL [C++], ODBC"
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# SQL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

SQL \(lenguaje de consulta estructurado\) es una forma de comunicarse con una base de datos relacional que permite definir, de ver, de modificar, y de controlar los datos.  Mediante la sintaxis SQL se puede crear una instrucción que extraiga los registros según determinados criterios.  
  
> [!NOTE]
>  Esta información es aplicable a las clases ODBC de MFC.  Si trabaja con las clases DAO de MFC, vea el tema Comparación entre SQL del motor de bases de datos Microsoft Jet y SQL ANSI en la Ayuda de DAO.  
  
 Las instrucciones SQL comienzan con un verbo de palabra clave como **CREATE** o **SELECT**.  SQL es un lenguaje muy eficaz; una sola instrucción puede afectar a toda una tabla.  
  
 Existen muchas versiones de SQL, cada una de ellas desarrollada con un particular sistema de administración de bases de datos \(DBMS\) en mente.  Las clases de base de datos de MFC reconocen un conjunto de instrucciones SQL que se corresponde con el borrador de especificación de SQL *X\/Open and SQL Access Group Common Applications Environment \(CAE\)* de 1991.  Para obtener información sobre la sintaxis de estas instrucciones, vea el Apéndice C de la *Referencia del programador del* *SDK de ODBC* en el CD de MSDN Library.  
  
 En este tema se explica:  
  
-   [La relación entre ODBC y SQL](#_core_open_database_connectivity_.28.odbc.29).  
  
-   [Las palabras clave más comunes de SQL utilizadas en las clases de base de datos](#_core_the_database_classes).  
  
-   [Cómo utilizan SQL las clases de base de datos](#_core_how_the_database_classes_use_sql).  
  
##  <a name="_core_open_database_connectivity_.28.odbc.29"></a> Conectividad abierta de bases de datos \(ODBC\)  
 Las clases de base de datos se implementan mediante ODBC, que utiliza SQL en la interfaz de nivel de llamada en lugar de incrustar comandos SQL en el código.  ODBC usa SQL para comunicarse con un [origen de datos](../../data/odbc/data-source-odbc.md) mediante controladores ODBC.  Estos controladores interpretan el código SQL y lo convierten, si es necesario, para su uso con un formato específico de base de datos, como Microsoft Access.  Para obtener más información sobre cómo utiliza ODBC el lenguaje SQL, vea [ODBC](../../data/odbc/odbc-basics.md) y la *Referencia del programador del SDK de ODBC* en el CD de MSDN Library.  
  
##  <a name="_core_the_database_classes"></a> Clases de base de datos  
 Las clases de base de datos están diseñadas para la manipulación y actualización de datos en un [origen de datos](../../data/odbc/data-source-odbc.md) existente.  El [Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md), el [Asistente para consumidores ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) \(al que se tiene acceso a través del comando **Agregar clase**\) y las clases de base de datos crean la mayoría de las instrucciones SQL para el programador.  
  
 Las clases de base de datos usan una parte de SQL conocida como Lenguaje de manipulación de datos \(*Data Manipulation Language*, DML\).  Estos comandos permiten trabajar con la totalidad o una parte del origen de datos, agregar nuevos registros, editar y eliminar registros.  La siguiente tabla muestra las palabras clave de SQL más comunes y las maneras en que son utilizadas por las clases de base de datos.  
  
### Algunas palabras clave comunes de SQL  
  
|Palabra clave de SQL|Los asistentes y las clases de base de datos las utilizan para|  
|--------------------------|--------------------------------------------------------------------|  
|**SELECT**|Identificar qué tablas y columnas del origen de datos se deben usar.|  
|**WHERE**|Aplicar un filtro que reduce la selección.|  
|**ORDER BY**|Aplicar un criterio de ordenación al conjunto de registros.|  
|**Insertar**|Agregar nuevos registros a un conjunto de registros.|  
|**SUPR**|Eliminar registros de un conjunto de registros.|  
|**UPDATE**|Modificar los campos de un registro.|  
  
 Además, las clases de base de datos reconocen las instrucciones **CALL** de ODBC, que se pueden utilizar para llamar a una consulta predefinida \(también conocida como procedimiento almacenado\) en algunos orígenes de datos.  El controlador de base de datos ODBC interpreta estas instrucciones y utiliza el campo apropiado para cada DBMS.  
  
> [!NOTE]
>  No todos los DBMS admiten instrucciones **CALL**.  
  
 Si las clases no reconocen una instrucción proporcionada por el usuario en `CRecordset::Open`, se interpreta como un nombre de tabla.  
  
 Para obtener una explicación de cómo crea el marco de trabajo las instrucciones SQL, vea [Conjunto de registros: Cómo se seleccionan los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) y [SQL: Personalizar la instrucción SQL del conjunto de registros \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md).  
  
 Las bases de datos SQL usan tipos de datos similares a los empleados en C y C\+\+.  Para consultar estas semejanzas, vea [SQL: tipos de datos de SQL y C\+\+ \(ODBC\)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).  
  
 Encontrará más información sobre SQL, incluida una lista de instrucciones SQL compatibles, tipos de datos, gramática básica de SQL y una lista de lecturas recomendadas sobre SQL en la *Referencia del programador del* *SDK de ODBC*, en el CD de MSDN Library.  
  
##  <a name="_core_how_the_database_classes_use_sql"></a> Cómo utilizan SQL las clases de base de datos  
 Los conjuntos de registros derivados de las clases de base de datos utilizan ODBC para comunicarse con un origen de datos, y ODBC recupera los registros de éste enviando instrucciones SQL.  Este tema explica la relación entre las clases de base de datos y SQL.  
  
 Un conjunto de registros crea una instrucción SQL agregando las piezas de una instrucción SQL a un objeto `CString`.  La cadena se genera como instrucción **SELECT**, la cual devuelve un conjunto de registros.  
  
 Cuando el conjunto de registros llama a ODBC para enviar una instrucción SQL al origen de datos, el Administrador de controladores ODBC pasa la instrucción al controlador ODBC, y éste la envía al DBMS subyacente.  El DBMS devuelve un conjunto de resultados de registros, y el controlador ODBC devuelve los registros a la aplicación.  Las clases de base de datos permiten a los programas el acceso al conjunto de resultados en una clase de C\+\+ con seguridad de tipos, derivada de `CRecordset`.  
  
 Los temas siguientes proporcionan más información sobre cómo utilizan SQL las clases de base de datos:  
  
-   [SQL: personalizar la instrucción SQL del conjunto de registros \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)  
  
-   [SQL: tipos de datos de SQL y C\+\+ \(ODBC\)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)  
  
-   [SQL: Realizar llamadas directas a SQL \(ODBC\)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)  
  
## Vea también  
 [Conectividad abierta de bases de datos \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)