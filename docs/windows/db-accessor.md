---
title: "db_accessor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_accessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_accessor attribute"
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# db_accessor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Atributos de **db\_column** de grupos que participan en `IAccessor`\- enlace basado.  
  
## Sintaxis  
  
```  
  
      [ db_accessor(   
   num,   
   auto   
) ]  
```  
  
#### Parámetros  
 *num*  
 Especifica el número de descriptor de acceso \(un índice entero único\).  Debe especificar números de descriptor de acceso en sentido petición, mediante enteros o valores definidos.  
  
 *Auto*  
 Un valor booleano que especifica si se recuperan \(**TRUE**\) o no se recupera el descriptor automáticamente \(**FALSO**\).  
  
## Comentarios  
 **db\_accessor** define el descriptor subyacente de OLE DB para **db\_column** subsiguiente y los atributos de **db\_param** dentro de la misma clase o de la función.  **db\_accessor** es utilizable en el nivel de miembro y se utiliza para agrupar los atributos de **db\_column** que participan en OLE DB `IAccessor`\- enlace basado.  Se utiliza junto con los atributos de **db\_table** o de **db\_command** .  Llamar a este atributo es similar a llamar a macros de [BEGIN\_ACCESSOR](../data/oledb/begin-accessor.md) y de [END\_ACCESSOR](../data/oledb/end-accessor.md) .  
  
 **db\_accessor** genera un conjunto de filas y enlazarlo a los mapas correspondientes de descriptor de acceso.  Si no llama **db\_accessor**, el descriptor de acceso 0 se generará automáticamente, y todos los enlaces de columna se asignan a este bloque de descriptor de acceso.  
  
 enlaces de columna de base de datos de los grupos de**db\_accessor** en uno o varios descriptores de acceso.  Para obtener una descripción de las situaciones en las que es necesario utilizar múltiples descriptores de acceso, vea [Utilizar varios descriptores de acceso en un conjunto de filas](../data/oledb/using-multiple-accessors-on-a-rowset.md).  Vea también “compatibilidad de registro para Múltiples Descriptores” en [registros de usuario](../data/oledb/user-records.md).  
  
 Cuando el proveedor de atributos de consumidor aplicar este atributo a una clase, el compilador cambiará la clase al \_TheClassNameAccessor, donde es el nombre *TheClassName que* asignó la clase, y el compilador también creará una clase denominada *TheClassName,* que deriva de \_TheClassNameAccessor.  En la vista de clases, verá ambas clases.  
  
## Ejemplo  
 El ejemplo siguiente utiliza **db\_accessor** para agrupar columnas de la tabla Orders de la base de datos Northwind en dos descriptores de acceso.  El descriptor de acceso 0 es un descriptor de acceso automático, y el descriptor de acceso 1 no.  
  
```  
// cpp_attr_ref_db_accessor.cpp  
// compile with: /LD /link /OPT:NOREF  
#define _ATL_ATTRIBUTES  
#include <atlbase.h>  
#include <atldbcli.h>  
  
[ db_command(L"SELECT LastName, FirstName FROM Orders") ]  
class CEmployees {  
public:  
   [ db_accessor(0, TRUE) ];  
   [ db_column("1") ] LONG m_OrderID;  
   [ db_column("2") ] TCHAR m_CustomerID[6];  
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;   
  
   [ db_accessor(1, FALSE) ];  
   [ db_column("8") ] CURRENCY m_Freight;  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Bloques de atributo|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [OLE DB Consumer Attributes](../windows/ole-db-consumer-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)