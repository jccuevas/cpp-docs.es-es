---
title: 'Conjunto de registros: Realizar una combinación (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0be740a57f5c455b971dd23575401c666bf0723c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093316"
---
# <a name="recordset-performing-a-join-odbc"></a>Conjunto de registros: Realizar una combinación (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
## <a name="what-a-join-is"></a>¿Qué es una combinación  
 La operación de combinación, una tarea común de acceso a datos, le permite trabajar con datos de más de una tabla mediante un objeto único de conjunto de registros. Combinar dos o más tablas genera un conjunto de registros que puede contener columnas de cada tabla, pero aparece como una tabla única para la aplicación. A veces, la combinación usa todas las columnas de todas las tablas, pero a veces el código SQL **seleccione** cláusula en una combinación utiliza sólo algunas de las columnas de cada tabla. Las clases de base de datos admiten combinaciones de solo lectura pero no combinaciones actualizables.  
  
 Para seleccionar los registros que contienen columnas de tablas combinadas, necesita los siguientes elementos:  
  
-   Una lista de tablas que contienen los nombres de todas las tablas que se está combinando.  
  
-   Una lista de columnas que contiene los nombres de todas las columnas que participan. Las columnas con el mismo nombre pero de tablas diferentes se califican con el nombre de tabla.  
  
-   Un filtro (SQL **donde** cláusula) que especifica las columnas en el que se combinan las tablas. Este filtro toma la forma "Table1.KeyCol = Table2.KeyCol" y realiza efectivamente la combinación.  
  
 Se pueden combinar más de dos tablas de la misma forma haciendo coincidir múltiples pares de columnas, cada par combinadas mediante la palabra clave SQL **AND**.  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Declarar una clase para una consulta predefinida (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)   
 [Conjunto de registros: Declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Conjunto de registros: Volver a consultar un conjunto de registros (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)