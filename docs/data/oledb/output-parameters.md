---
title: Parámetros de salida
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
ms.openlocfilehash: ece626eb7fbecae9b90321ccc2569607897cf520
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209864"
---
# <a name="output-parameters"></a>Parámetros de salida

Llamar a un procedimiento almacenado es similar a ejecutar un comando SQL. La principal diferencia es que los procedimientos almacenados usan parámetros de salida (o "Parameters") y valores devueltos.

En el siguiente procedimiento almacenado, el primer '? ' es el valor devuelto (Phone) y el segundo '? ' es el parámetro de entrada (Name):

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }"))
```

Especifique los parámetros in y out en la asignación de parámetros:

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter
END_PARAM_MAP()
```

La aplicación debe controlar el resultado devuelto de los procedimientos almacenados. Diferentes proveedores OLE DB devuelven parámetros de salida y valores devueltos en diferentes momentos durante el procesamiento de los resultados. Por ejemplo, el proveedor de OLE DB de Microsoft para SQL Server (SQLOLEDB) no proporciona parámetros de salida y códigos de retorno hasta que el consumidor haya recuperado o cancelado los conjuntos de resultados devueltos por el procedimiento almacenado. La salida se devuelve en el último paquete TDS del servidor.

## <a name="row-count"></a>Recuento de filas

Si usa las plantillas de consumidor de OLE DB para ejecutar un procedimiento almacenado que tiene Parameters, el recuento de filas no se establece hasta que se cierra el conjunto de filas.

Por ejemplo, considere un procedimiento almacenado con un conjunto de filas y un parámetro outparameter:

```sql
create procedure sp_test
   @_rowcount integer output
as
   select top 50 * from test
   @_rowcount = @@rowcount
return 0
```

El `@_rowcount` outparameter informa del número de filas devueltas de la tabla de prueba. Sin embargo, este procedimiento almacenado limita el número de filas a 50. Por ejemplo, si había 100 filas en la prueba, el recuento de filas sería 50 (porque este código solo recupera las primeras 50 filas). Si solo había 30 filas en la tabla, el recuento de filas sería 30. Asegúrese de llamar a `Close` o `CloseAll` para rellenar el parámetro outparameter antes de recuperar su valor.

## <a name="see-also"></a>Consulte también

[Usar procedimientos almacenados](../../data/oledb/using-stored-procedures.md)
