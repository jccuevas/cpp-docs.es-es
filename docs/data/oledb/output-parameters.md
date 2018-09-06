---
title: Parámetros de salida | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5f9e0e273df1221801a9b761cd7f45200e0b50c0
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895089"
---
# <a name="output-parameters"></a>Parámetros de salida

Llamar a un procedimiento almacenado es similar a invocar un comando SQL. La principal diferencia es que los procedimientos almacenados, utilizan parámetros de salida (o "parámetros de salida") y valores devuelven.

En el siguiente procedimiento almacenado, la primera '? 'es el valor devuelto (phone) y el segundo'?' es el parámetro de entrada (nombre):

```  
DEFINE_COMMAND(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }")  
```  

Especifique los parámetros dentro y fuera de la asignación de parámetros:

```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)  
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter
END_PARAM_MAP()  
```  

La aplicación debe controlar la salida devuelta desde procedimientos almacenados. Diferentes proveedores OLE DB devuelven parámetros de salida y valores devuelven en distintos momentos durante el procesamiento del resultado. Por ejemplo, el proveedor Microsoft OLE DB para SQL Server (SQLOLEDB) no proporciona parámetros de salida y códigos devueltos hasta que el consumidor haya recuperado o cancelado los conjuntos de resultados devueltos por el procedimiento almacenado. El resultado se devuelve en el último paquete TDS del servidor.

## <a name="row-count"></a>Recuento de filas

Si usa las plantillas de consumidor OLE DB para ejecutar un procedimiento almacenado con parámetros de salida, el recuento de filas no se establece hasta que se cierra el conjunto de filas.

Por ejemplo, considere la posibilidad de un procedimiento almacenado con un conjunto de filas y un parámetro de salida:

```sql
create procedure sp_test
   @_rowcount integer output
as
   select top 50 * from test
   @_rowcount = @@rowcount
return 0
```  

El \@parámetro de salida _rowcount informa de cuántas filas se han devuelto realmente desde la tabla de prueba. Sin embargo, este procedimiento almacenado limita el número de filas a un máximo de 50. Por ejemplo, si hay 100 filas en la prueba, el recuento de filas sería 50 (porque este código recupera solo las primeras 50 filas). Si sólo hay 30 filas en la tabla, el recuento de filas sería 30. Debe llamar a `Close` o `CloseAll` para rellenar el parámetro de salida antes de recuperar su valor.

## <a name="see-also"></a>Vea también

[Usar procedimientos almacenados](../../data/oledb/using-stored-procedures.md)