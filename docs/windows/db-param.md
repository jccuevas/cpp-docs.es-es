---
title: db_param | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.db_param
dev_langs: C++
helpviewer_keywords: db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5224c406f6e10cd4ef9f0ed64fbdbd7c5cc8e62
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dbparam"></a>db_param
La variable de miembro especificado se asocia con un parámetro de entrada o de salida y delimita la variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ db_param(   
   ordinal,   
   paramtype="DBPARAMIO_INPUT",   
   dbtype,   
   precision,   
   scale,   
   status,   
   length  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ordinal`  
 El número de columna (**DBCOLUMNINFO** ordinal) correspondiente a un campo del conjunto de filas que se va a enlazar los datos.  
  
 *ParamType* (opcional)  
 El tipo de conjunto para el parámetro. Proveedores admiten solo tipos de E/S de parámetros que son compatibles con el origen de datos subyacente. El tipo es una combinación de uno o varios **DBPARAMIOENUM** valores:  
  
-   **DBPARAMIO_INPUT** Un parámetro de entrada.  
  
-   **DBPARAMIO_OUTPUT** Un parámetro de salida.  
  
-   **DBPARAMIO_NOTPARAM** El descriptor de acceso no tiene ningún parámetro. Establecer **eParamIO** en este valor en la fila descriptores de acceso recuerda al usuario que se omiten los parámetros.  
  
 *DbType* (opcional)  
 OLE DB [indicador de tipo](https://msdn.microsoft.com/en-us/library/ms711251.aspx) para la entrada de la columna.  
  
 *precisión* (opcional)  
 La precisión que se usará para la entrada de columna. Para obtener más información, vea la descripción de **bPrecision** elemento de la [estructura DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *escala* (opcional)  
 La escala que se usará para la entrada de columna. Para obtener más información, vea la descripción de **bScale** elemento de la [estructura DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *estado* (opcional)  
 Una variable de miembro que se utiliza para almacenar el estado de esta columna. El estado indica si el valor de la columna es un valor de datos o algún otro valor, como **NULL**. Para los valores posibles, vea [estado](https://msdn.microsoft.com/en-us/library/ms722617.aspx) en el *referencia del programador de OLE DB*.  
  
 *longitud* (opcional)  
 Una variable de miembro que se usa para contener el tamaño de la columna en bytes.  
  
## <a name="remarks"></a>Comentarios  
 **db_param** define los parámetros que utilizar en los comandos; por consiguiente Utilícela con **db_command**. Por ejemplo, puede usar **db_param** para enlazar parámetros en consultas SQL o procedimientos almacenados. Parámetros de un procedimiento almacenado se denotan mediante signos de interrogación (?) y debe enlazar a los miembros de datos en el orden en que aparecen los parámetros.  
  
 **db_param** delimita los datos de miembros que pueden participar en OLE DB `ICommandWithParameters`-basados en el enlace. Establece el tipo de parámetro (entrada o salida), tipo de OLE DB, precisión, escala, estado y longitud para el parámetro especificado. Este atributo inserta las macros de consumidor OLE DB BEGIN_PARAM_MAP... END_PARAM_MAP. Cada miembro se marca con la **db_param** atributo ocupan una entrada en el mapa en la forma de un COLUMN_ENTRY.  
  
 **db_param** se usa junto con cualquiera el [db_table](../windows/db-table.md) o [db_command](../windows/db-command.md) atributos.  
  
 Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_ *YourClassName*descriptor de acceso, donde *YourClassName* es el nombre que asignó el clase y el compilador también creará una clase denominada *YourClassName*, que deriva de \_ *YourClassName*descriptor de acceso.  En Vista de clases verá ambas clases.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea una clase de comando que se basa en el procedimiento SalesbyYear almacenado en la base de datos Northwind. Asocie el primer parámetro del procedimiento almacenado con el `m_RETURN_VALUE` variable y se define como un parámetro de salida. Asocia los dos últimos parámetros (entrados) con `m_Beginning_Date` y `m_Ending_Date`.  
  
 En el ejemplo siguiente se asocia el `nOutput` variable con un parámetro de salida.  
  
```  
// db_param.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_source(L"my_connection_string"),   
  db_command(L"{ ? = CALL dbo.\"Sales by Year\"(?,?) }")   
]  
struct CSalesbyYear {  
   DBSTATUS m_dwShippedDateStatus;  
   DBSTATUS m_dwOrderIDStatus;  
   DBSTATUS m_dwSubtotalStatus;  
   DBSTATUS m_dwYearStatus;  
  
   DBLENGTH m_dwShippedDateLength;  
   DBLENGTH m_dwOrderIDLength;  
   DBLENGTH m_dwSubtotalLength;  
   DBLENGTH m_dwYearLength;  
  
   // Bind columns  
   [ db_column("1", status="m_dwShippedDateStatus", length="m_dwShippedDateLength") ] DBTIMESTAMP m_ShippedDate;  
   [ db_column("2", status="m_dwOrderIDStatus", length="m_dwOrderIDLength") ] LONG m_OrderID;  
   [ db_column("3", status="m_dwSubtotalStatus", length="m_dwSubtotalLength") ] CURRENCY m_Subtotal;  
   [ db_column("4", status="m_dwYearStatus", length="m_dwYearLength") ] TCHAR m_Year[31];  
  
   // Bind parameters  
   [ db_param("1", paramtype="DBPARAMIO_OUTPUT") ] LONG m_RETURN_VALUE;  
   [ db_param("2", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Beginning_Date;  
   [ db_param("3", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Ending_Date;  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`, miembro, método, local|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos de consumidor OLE DB](../windows/ole-db-consumer-attributes.md)   
