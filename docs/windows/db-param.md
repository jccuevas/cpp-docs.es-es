---
title: "db_param | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_param"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_param attribute"
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# db_param
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Asociado a la variable miembro especificada a una entrada o parámetro de salida y delimita la variable.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `ordinal`  
 El número de columnas \(ordinal de**DBCOLUMNINFO** \) correspondiente a un campo del conjunto de filas al enlazar datos.  
  
 *paramtype* \(opcional\)  
 El tipo el conjunto para el parámetro.  Los proveedores admiten los tipos de E\/S de parámetro admitidos por el origen de datos subyacente.  el tipo es una combinación de uno o más valores de **DBPARAMIOENUM** :  
  
-   **DBPARAMIO\_INPUT** un parámetro de entrada.  
  
-   **DBPARAMIO\_OUTPUT** un parámetro de salida.  
  
-   El descriptor de**DBPARAMIO\_NOTPARAM**no tiene ningún parámetro.  El valor **eParamIO** a este valor en descriptores de fila recuerda al usuario que los parámetros se omiten.  
  
 *dbtype* \(opcional\)  
 OLE DB [Indicador de tipo](https://msdn.microsoft.com/en-us/library/ms711251.aspx) para la entrada de la columna.  
  
 *precisión* \(opcional\)  
 la precisión que se utilizará para la entrada de la columna.  Para obtener información detallada, vea la descripción del elemento de **bPrecision** de [estructura de DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *escala* \(opcional\)  
 la escala que se utilizará para la entrada de la columna.  Para obtener información detallada, vea la descripción del elemento de **bScale** de [estructura de DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *estado* \(opcional\)  
 Una variable miembro utilizada para contener el estado de esta columna.  El estado indica si el valor de la columna es un valor de datos o algún otro valor, como **NULL**.  Por valores posibles, vea [Estado](https://msdn.microsoft.com/en-us/library/ms722617.aspx) en *la referencia del*programador.  
  
 *length* \(opcional\)  
 Una variable miembro utilizada para contener el tamaño de la columna en bytes.  
  
## Comentarios  
 **db\_param** define los parámetros que utiliza en comandos; por consiguiente se utiliza con **db\_command**.  Por ejemplo, puede utilizar **db\_param** a los parámetros de enlace en consultas SQL o procedimientos almacenados.  Los parámetros de un procedimiento almacenado son denotados mediante signos de interrogación \(?\), y debe enlazar miembros de datos en el orden en que los parámetros aparecen.  
  
 **db\_param** delimita los datos de miembro que pueden participar en OLE DB `ICommandWithParameters`\- enlace basado.  Establece el tipo de parámetro \(entrada o salida\), el tipo de OLE DB, la precisión, escala, el estado, y la longitud del parámetro especificado.  Este atributo inserta las macros BEGIN\_PARAM\_MAP de consumidor OLE DB…  END\_PARAM\_MAP.  Cada miembro que se marca con el atributo de **db\_param** ocupará una entrada en el mapa en forma COLUMN\_ENTRY.  
  
 **db\_param** se utiliza junto con los atributos de [db\_table](../windows/db-table.md) o de [db\_command](../windows/db-command.md) .  
  
 Cuando el proveedor de atributos de consumidor aplicar este atributo a una clase, el compilador cambiará la clase al \_TheClassNameAccessor, donde es el nombre *TheClassName que* asignó la clase, y el compilador también creará una clase denominada *TheClassName,* que deriva de \_TheClassNameAccessor.  En la vista de clases, verá ambas clases.  
  
## Ejemplo  
 El ejemplo siguiente crea una clase de comando basada en el procedimiento almacenado de SalesbyYear en la base de datos Northwind.  Asocia el primer parámetro del procedimiento almacenado en la variable de `m_RETURN_VALUE` , y se define como parámetro de salida.  Asocia los últimos dos parámetros \(de entrada\) a `m_Beginning_Date` y a `m_Ending_Date`.  
  
 el ejemplo siguiente asocia la variable de `nOutput` a un parámetro de salida.  
  
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
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`, miembro, método, local|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [OLE DB Consumer Attributes](../windows/ole-db-consumer-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)