---
title: 'Conjunto de registros: Realizar una combinación (ODBC) | Microsoft Docs'
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
ms.openlocfilehash: e033a300a023b3460fb27ced7cd4bae99ebd0b92
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097916"
---
# <a name="recordset-performing-a-join-odbc"></a>Conjunto de registros: Realizar una combinación (ODBC)

Este tema es aplicable a las clases ODBC de MFC.  
  
## <a name="what-a-join-is"></a>¿Qué es una combinación  

La operación de combinación, una tarea común de acceso a datos, le permite trabajar con datos de más de una tabla mediante un objeto de conjunto de registros único. Combinar dos o más tablas genera un conjunto de registros que puede contener columnas de cada tabla, pero aparece como una sola tabla a la aplicación. A veces, la combinación usa todas las columnas de todas las tablas, pero a veces SQL **seleccione** cláusula en una combinación usa solo algunas de las columnas de cada tabla. Las clases de base de datos admiten combinaciones de solo lectura pero no combinaciones actualizables.  
  
Para seleccionar registros que contienen columnas de tablas combinadas, necesita los siguientes elementos:  
  
- Una lista de tablas que contiene los nombres de todas las tablas que se están combinando.  
  
- Una lista de columnas que contiene los nombres de todas las columnas que participan. Las columnas con el mismo nombre pero de diferentes tablas están calificadas por el nombre de tabla.  
  
- Un filtro (SQL **donde** cláusula) que especifica las columnas en el que se combinan las tablas. Este filtro toma la forma "Table1.KeyCol = Table2.KeyCol" y en realidad, realiza la combinación.  
  
Se pueden combinar más de dos tablas de la misma forma haciendo coincidir múltiples pares de columnas, cada par combinadas mediante la palabra clave SQL **AND**.  
  
## <a name="see-also"></a>Vea también  

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Declarar una clase para una consulta predefinida (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[Conjunto de registros: Declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Conjunto de registros: Volver a consultar un conjunto de registros (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)