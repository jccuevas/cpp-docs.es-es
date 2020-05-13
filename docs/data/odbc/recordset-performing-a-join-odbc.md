---
title: 'Conjunto de registros: Realizar una combinación (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
ms.openlocfilehash: 7e8d42f2b96911cd57aca7c132b53ed7c10162be
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212802"
---
# <a name="recordset-performing-a-join-odbc"></a>Conjunto de registros: Realizar una combinación (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

## <a name="what-a-join-is"></a>Qué es una combinación

La operación de combinación, una tarea común de acceso a datos, permite trabajar con datos de más de una tabla mediante un solo objeto de conjunto de registros. La combinación de dos o más tablas produce un conjunto de registros que puede contener columnas de cada tabla, pero aparece como una sola tabla para la aplicación. A veces, la combinación utiliza todas las columnas de todas las tablas, pero a veces la cláusula **Select** de SQL de una combinación solo usa algunas de las columnas de cada tabla. Las clases de base de datos admiten combinaciones de solo lectura pero no combinaciones actualizables.

Para seleccionar los registros que contienen las columnas de las tablas combinadas, necesita los siguientes elementos:

- Una lista de tablas que contiene los nombres de todas las tablas que se van a combinar.

- Una lista de columnas que contiene los nombres de todas las columnas que participan. Las columnas con el mismo nombre, pero de tablas diferentes, se califican con el nombre de la tabla.

- Un filtro (cláusula **Where** de SQL) que especifica las columnas en las que se unen las tablas. Este filtro toma la forma "Table1. KeyCol = Tabla2. KeyCol" y, en realidad, realiza la combinación.

Puede combinar más de dos tablas de la misma manera si equipara varios pares de columnas, cada par combinado por la palabra clave SQL **y**.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Declarar una clase para una consulta predefinida (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[Conjunto de registros: Declarar una clase para una tabla (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Conjunto de registros: Volver a consultar un conjunto de registros (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)
