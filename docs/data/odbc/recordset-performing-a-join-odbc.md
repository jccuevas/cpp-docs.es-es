---
title: "Conjunto de registros: Realizar una combinaci&#243;n (ODBC) | Microsoft Docs"
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
  - "enlace de datos [C++], columnas en conjuntos de registros"
  - "enlace de datos [C++], columnas de conjuntos de registros"
  - "filtros [C++], condiciones de combinación para conjuntos de registros"
  - "combinaciones [C++], en conjuntos de registros"
  - "conjuntos de registros ODBC [C++], combinaciones"
  - "conjuntos de registros [C++], enlazar datos"
  - "conjuntos de registros [C++], combinar tablas"
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Conjunto de registros: Realizar una combinaci&#243;n (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
## Qué es una combinación  
 La operación de combinación \(JOIN\), una tarea común en bases de datos, permite trabajar con datos de más de una tabla usando un solo objeto de conjunto de registros.  Combinar dos o más tablas da como resultado un conjunto de registros capaz de contener columnas de cada tabla, pero aparece como una sola tabla para la aplicación.  A veces, la combinación usa todas las columnas de todas las tablas, pero en otras ocasiones la cláusula SQL **SELECT** utiliza sólo algunas de las columnas de cada tabla.  Las clases de base de datos admiten combinaciones de sólo lectura pero no combinaciones actualizables.  
  
 Para seleccionar registros que contengan columnas de tablas combinadas, se necesitan los siguientes elementos:  
  
-   Una lista de tablas que contiene los nombres de todas las tablas combinadas.  
  
-   Una lista de columnas que contenga los nombres de todas las columnas participantes.  Las columnas con el mismo nombre pero pertenecientes a diferentes tablas se diferencian por el nombre de tabla.  
  
-   Un filtro \(cláusula SQL **WHERE**\) que especifica las columnas en las que se combinan las tablas.  Este filtro toma la forma "Table1.KeyCol \= Table2.KeyCol" y realiza efectivamente la combinación.  
  
 Se pueden combinar más de dos tablas de la misma forma haciendo coincidir múltiples pares de columnas, combinando cada uno de ellos mediante la instrucción SQL **AND**.  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Declarar una clase para una consulta predefinida \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)   
 [Conjunto de registros: Declarar una clase para una tabla \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Conjunto de registros: Volver a consultar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)