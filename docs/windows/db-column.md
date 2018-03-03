---
title: db_column | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.db_column
dev_langs:
- C++
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5fe2d3c5edb4b90676c3880ae422c1fb507cd164
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dbcolumn"></a>db_column
Enlaza una columna especificada a una variable en el conjunto de filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ db_column(   
   ordinal,   
   dbtype,   
   precision,   
   scale,   
   status,   
   length   
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ordinal`  
 El número ordinal de la columna (**DBCOLUMNINFO** ordinal) o nombre de columna (cadena ANSI o Unicode) correspondiente a un campo del conjunto de filas que se va a enlazar los datos. Si usa números, puede omitir los ordinales consecutivos (por ejemplo: 1, 2, 3, 5). El nombre puede contener espacios, si lo admite el proveedor OLE DB que utiliza. Por ejemplo, puede usar cualquiera de los siguientes formatos:  
  
```  
[db_column("2")] TCHAR szCity[30];  
[db_column(L"city_name")] TCHAR szCity[30];  
```  
  
 *DbType* (opcional)  
 OLE DB [indicador de tipo](https://msdn.microsoft.com/en-us/library/ms711251.aspx) para la entrada de la columna.  
  
 *precisión* (opcional)  
 La precisión que se usará para la entrada de columna. Para obtener más información, vea la descripción de la `bPrecision` elemento de la [estructura DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *escala* (opcional)  
 La escala que se usará para la entrada de columna. Para obtener más información, vea la descripción de `bScale` elemento de la [estructura DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *estado* (opcional)  
 Una variable de miembro que se utiliza para almacenar el estado de esta columna. El estado indica si el valor de la columna es un valor de datos o algún otro valor, como **NULL**. Para los valores posibles, vea [estado](https://msdn.microsoft.com/en-us/library/ms722617.aspx) en el *referencia del programador de OLE DB*.  
  
 *longitud* (opcional)  
 Una variable de miembro que se usa para contener el tamaño de la columna en bytes.  
  
## <a name="remarks"></a>Comentarios  
 **db_column** enlaza la columna de tabla especificada a una variable en el conjunto de filas. Delimita los datos de miembros que pueden participar en OLE DB `IAccessor`-basados en el enlace. Este atributo configura la asignación de columna normalmente se definen mediante las macros de consumidor OLE DB [BEGIN_COLUMN_MAP](../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../data/oledb/end-column-map.md), y [COLUMN_ENTRY](../data/oledb/column-entry.md). Estos manipulan OLE DB [estructura DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) para enlazar la columna especificada. Cada miembro se marca con la **db_column** atributo ocupan una entrada en el mapa de columnas en el formulario de una entrada de la columna. Por lo tanto, llamar a este atributo donde tendría que poner el mapa de columnas, es decir, en la clase de comando o tabla.  
  
 Use **db_column** junto con cualquiera el [db_table](../windows/db-table.md) o [db_command](../windows/db-command.md) atributos.  
  
 Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_ *YourClassName*descriptor de acceso, donde *YourClassName* es el nombre que asignó el clase y el compilador también creará una clase denominada *YourClassName*, que deriva de \_ *YourClassName*descriptor de acceso.  En Vista de clases verá ambas clases.  
  
 Para obtener ejemplos de este atributo se usa en una aplicación, vea los ejemplos [AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409), y [MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo enlaza una columna en una tabla para un **largo** miembro de datos y especifica los campos Estado y longitud.  
  
```  
// db_column_1.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_command(L"Select * from Products") ]  
class CProducts {  
   DBSTATUS m_dwProductIDStatus;  
   DBLENGTH m_dwProductIDLength;  
  
   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;  
};  
```  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo enlaza cuatro columnas a una **largo**, una cadena de caracteres, una marca de tiempo y un **DB_NUMERIC** entero, en ese orden.  
  
```  
// db_column_2.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_command(L"Select * from Products") ]  
class CProducts {  
   [db_column("1")] LONG m_OrderID;  
   [db_column("2")] TCHAR m_CustomerID[6];  
   [db_column("4")] DB_NUMERIC m_OrderDate;     
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`, miembro, método|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos de consumidor OLE DB](../windows/ole-db-consumer-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
