---
title: "db_source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_source attribute"
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# db_source
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

crea una conexión a un origen de datos.  
  
## Sintaxis  
  
```  
  
      [ db_source(   
   db_source,   
   name,   
   hresult   
) ]  
```  
  
#### Parámetros  
 *db\_source*  
 La cadena de conexión utilizada para conectarse al origen de datos.  Para el formato de la cadena de conexión, vea [cadenas de conexión y vínculos de datos](https://msdn.microsoft.com/en-us/library/ms718376.aspx) de Microsoft Data Access Components \(MDAC\) SDK.  
  
 \(opcional\)*nombre*  
 Cuando se utiliza `db_source` en una clase, *el nombre* es una instancia de un objeto de origen de datos que tiene el atributo de `db_source` aplicadas \(vea el ejemplo 1\).  Cuando se utiliza `db_source` especificado en una implementación del método, *el nombre* es una variable \(local al método\) que se puede utilizar para tener acceso al origen de datos \(vea el ejemplo 2\).  Pasa este *nombre* al parámetro de `source_name` de **db\_command** para asociar el origen de datos a un comando.  
  
 `hresult` \(opcional\)  
 identifica la variable que recibirá `HRESULT` de este comando de base de datos.  Si no existe la variable, automáticamente se insertada por el atributo.  
  
## Comentarios  
 `db_source` crea [CDataSource](../data/oledb/cdatasource-class.md) y un objeto de [CSession](../data/oledb/csession-class.md) , que conjuntamente representan una conexión con un origen de datos de consumidor OLE DB.  
  
 Cuando se utiliza `db_source` en una clase, el objeto de `CSession` se convierte en un miembro de clase.  
  
 Cuando se utiliza `db_source` en un método, el código insertado se ejecutará en el ámbito del método, y el objeto de `CSession` se crea como una variable local.  
  
 `db_source` agrega propiedades de origen de datos a una clase o dentro de un método.  Se utiliza junto con **db\_command** \(que toma el parámetro de*nombre de*`db_source`como parámetro de `source_name` \).  
  
 Cuando el proveedor de atributos de consumidor aplicar este atributo a una clase, el compilador cambiará la clase al \_TheClassNameAccessor, donde es el nombre *TheClassName que* asignó la clase, y el compilador también creará una clase denominada *TheClassName,* que deriva de \_TheClassNameAccessor.  En la vista de clases, verá ambas clases.  
  
 Para obtener un ejemplo de este atributo se utiliza en una aplicación, vea los ejemplos [AtlAgent](http://msdn.microsoft.com/es-es/52bef5da-c1a0-4223-b4e6-9e464b6db409) y [MultiRead](http://msdn.microsoft.com/es-es/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## Ejemplo  
 Este ejemplo llama a `db_source` en una clase para crear una conexión al origen de datos `ds` mediante la base de datos Northwind.  `ds` es un identificador para el origen de datos, que se puede utilizar internamente en la clase de `CMyCommand` .  
  
```  
// db_source_1.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[  
  db_source(L"my_connection_string", name="ds"),  
  db_command(L"select * from Products")  
]  
class CMyCommand {};  
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