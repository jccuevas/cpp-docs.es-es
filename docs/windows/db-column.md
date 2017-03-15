---
title: "db_column | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_column"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_column attribute"
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# db_column
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

enlaza una columna especificada a una variable en el conjunto de filas.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `ordinal`  
 El número de columnas ordinal \(ordinal de**DBCOLUMNINFO** \) o nombre de columna \(ANSI o cadena Unicode\) correspondiente a un campo del conjunto de filas al enlazar datos.  Si utiliza números, puede omitir ordinales consecutivos \(por ejemplo: 1, 2, 3, 5\).  El nombre puede contener espacios si el proveedor OLE DB que utiliza lo admite.  Por ejemplo, puede utilizar cualquiera de los formatos siguientes:  
  
```  
[db_column("2")] TCHAR szCity[30];  
[db_column(L"city_name")] TCHAR szCity[30];  
```  
  
 *dbtype* \(opcional\)  
 OLE DB [Indicador de tipo](https://msdn.microsoft.com/en-us/library/ms711251.aspx) para la entrada de la columna.  
  
 *precisión* \(opcional\)  
 la precisión que se utilizará para la entrada de la columna.  Para obtener información detallada, vea la descripción del elemento de `bPrecision` de [estructura de DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *escala* \(opcional\)  
 la escala que se utilizará para la entrada de la columna.  Para obtener información detallada, vea la descripción del elemento de `bScale` de [estructura de DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *estado* \(opcional\)  
 Una variable miembro utilizada para contener el estado de esta columna.  El estado indica si el valor de la columna es un valor de datos o algún otro valor, como **NULL**.  Por valores posibles, vea [Estado](https://msdn.microsoft.com/en-us/library/ms722617.aspx) en *la referencia del*programador.  
  
 *length* \(opcional\)  
 Una variable miembro utilizada para contener el tamaño de la columna en bytes.  
  
## Comentarios  
 **db\_column** enlaza la columna de la tabla especificada a una variable en el conjunto de filas.  Delimitan los datos de miembro que pueden participar en OLE DB `IAccessor`\- enlace basado.  Este atributo coloque el normalmente definido asignado columna utilizando las macros [BEGIN\_COLUMN\_MAP](../data/oledb/begin-column-map.md), [END\_COLUMN\_MAP](../data/oledb/end-column-map.md), y [COLUMN\_ENTRY](../data/oledb/column-entry.md)de consumidor OLE DB.  éstos manipulan OLE DB [estructura de DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) para enlazar la columna especificada.  Cada miembro que se marca con el atributo de **db\_column** ocupará una entrada en la columna asignada en forma de entrada de la columna.  Por consiguiente, se llama a este atributo donde se pone el mapa de columnas, es decir, en la clase de comando o tabla.  
  
 Utilice **db\_column** junto con los atributos de [db\_table](../windows/db-table.md) o de [db\_command](../windows/db-command.md) .  
  
 Cuando el proveedor de atributos de consumidor aplicar este atributo a una clase, el compilador cambiará la clase al \_TheClassNameAccessor, donde es el nombre *TheClassName que* asignó la clase, y el compilador también creará una clase denominada *TheClassName,* que deriva de \_TheClassNameAccessor.  En la vista de clases, verá ambas clases.  
  
 Para obtener ejemplos de este atributo se utiliza en una aplicación, vea los ejemplos [AtlAgent](http://msdn.microsoft.com/es-es/52bef5da-c1a0-4223-b4e6-9e464b6db409), y [MultiRead](http://msdn.microsoft.com/es-es/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## Ejemplo  
 Este ejemplo enlaza una columna de una tabla a un miembro de datos de **Más** y especificar los campos de estado y longitud.  
  
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
  
## Ejemplo  
 Este ejemplo enlaza cuatro columnas a **Más**, una cadena de caracteres, una marca de tiempo, y un entero de **DB\_NUMERIC** , en ese orden.  
  
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
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`, miembro, método|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [OLE DB Consumer Attributes](../windows/ole-db-consumer-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)