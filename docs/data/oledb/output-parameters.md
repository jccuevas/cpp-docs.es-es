---
title: "Parámetros de salida | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3d1f1a4c84c4567b325bb19e3696170f7960b46b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="output-parameters"></a>Parámetros de salida
Llamar a un procedimiento almacenado es similar a invocar un comando SQL. La principal diferencia es que los procedimientos almacenados usan parámetros de salida (o "parámetros de salida") y valores devuelven.  
  
 En el siguiente procedimiento almacenado, la primera '? 'es el valor devuelto (phone) y la segunda'?' es el parámetro de entrada (name):  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }")  
```  
  
 Especifique los parámetros in y out en la asignación de parámetros:  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)  
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter  
END_PARAM_MAP()  
```  
  
 La aplicación debe administrar los resultados devueltos por procedimientos almacenados. Diferentes proveedores OLE DB devuelven parámetros de salida y valores devuelven en diferentes momentos durante el procesamiento de los resultados. Por ejemplo, el proveedor Microsoft OLE DB para SQL Server (SQLOLEDB) no proporciona parámetros de salida y códigos devueltos hasta que el consumidor haya recuperado o cancelado los conjuntos de resultados devueltos por el procedimiento almacenado. El resultado se devuelve en el último paquete TDS del servidor.  
  
## <a name="row-count"></a>Recuento de filas  
 Si usa las plantillas de consumidor OLE DB para ejecutar un procedimiento almacenado con parámetros de salida, el recuento de filas no se establece hasta que se cierra el conjunto de filas.  
  
 Por ejemplo, considere la posibilidad de un procedimiento almacenado con un conjunto de filas y un parámetro de salida:  
  
```  
create procedure sp_test  
   @_rowcount integer output  
as  
   select top 50 * from test  
   @_rowcount = @@rowcount  
return 0  
```  
  
 El @_rowcount parámetro de salida informa de cuántas filas se han devuelto realmente de la tabla de prueba. Sin embargo, este procedimiento almacenado limita el número de filas a un máximo de 50. Por ejemplo, si hay 100 filas en la prueba, el recuento de filas sería 50 (porque este código recupera solo las 50 primeras filas). Si sólo hay 30 filas en la tabla, el recuento de filas sería 30. Debe llamar a **cerrar** o **CloseAll** para rellenar el parámetro de salida antes de recuperar su valor.  
  
## <a name="see-also"></a>Vea también  
 [Usar procedimientos almacenados](../../data/oledb/using-stored-procedures.md)