---
title: "db_table | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_table"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_table attribute"
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# db_table
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Abra una tabla de OLE DB.  
  
## Sintaxis  
  
```  
  
      [ db_table(   
   db_table,   
   name,   
   source_name,   
   hresult   
) ]  
```  
  
#### Parámetros  
 *db\_table*  
 Una cadena que especifica el nombre de una tabla de base de datos \(como “Products”\).  
  
 \(opcional\)*nombre*  
 El nombre del identificador que se utiliza para trabajar con la tabla.  Debe especificar este parámetro si desea devolver más de una fila de resultados.  **db\_table** genera una variable con *el nombre* especificado que se puede utilizar para recorrer el conjunto de filas o para ejecutar consultas de varias acciones.  
  
 *source\_name* \(opcional\)  
 La variable de `CSession` o la instancia de una clase que tiene el atributo de `db_source` aplicado en la que se ejecuta el comando.  Vea [db\_source](../windows/db-source.md).  
  
 `hresult` \(opcional\)  
 identifica la variable que recibirá `HRESULT` de este comando de base de datos.  Si no existe la variable, automáticamente se insertada por el atributo.  
  
## Comentarios  
 **db\_table** crea un objeto de [CTable](../data/oledb/ctable-class.md) , que utiliza un consumidor OLE DB para abrir una tabla.  Puede utilizar este atributo sólo en el nivel de clase; no puede utilizarlo en línea.  Uso **db\_column** de enlazar columnas de la tabla a variables; utilice **db\_param** para delimitar \(establecido el tipo de parámetro etc.\) de parámetros.  
  
 Cuando el proveedor de atributos de consumidor aplicar este atributo a una clase, el compilador cambiará la clase al \_TheClassNameAccessor, donde es el nombre *TheClassName que* asignó la clase, y el compilador también creará una clase denominada *TheClassName,* que deriva de \_TheClassNameAccessor.  En la vista de clases, verá ambas clases.  
  
## Ejemplo  
 El ejemplo siguiente se abre la tabla products para uso de `CProducts`.  
  
```  
// db_table.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_table(L"dbo.Products") ]  
class CProducts {  
   [ db_column("1") ] LONG m_ProductID;  
};  
```  
  
 Para obtener un ejemplo de este atributo se utiliza en una aplicación, vea los ejemplos [AtlAgent](http://msdn.microsoft.com/es-es/52bef5da-c1a0-4223-b4e6-9e464b6db409) y [MultiRead](http://msdn.microsoft.com/es-es/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [OLE DB Consumer Attributes](../windows/ole-db-consumer-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)