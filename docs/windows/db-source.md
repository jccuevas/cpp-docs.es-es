---
title: db_source | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b826e5d630b52062892001c26efda01b5c7293f4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873724"
---
# <a name="dbsource"></a>db_source
Crea una conexión a un origen de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ db_source(   
   db_source,   
   name,   
   hresult   
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *db_source*  
 La cadena de conexión utilizada para conectarse al origen de datos. Para el formato de la cadena de conexión, vea [cadenas de conexión y vínculos de datos](https://msdn.microsoft.com/en-us/library/ms718376.aspx) en Microsoft Data Access Components (MDAC) SDK.  
  
 *name* (opcional)  
 Cuando usas `db_source` en una clase, *nombre* es una instancia de un objeto de origen de datos que tiene el `db_source` atributo aplicado a él (vea el ejemplo 1). Cuando se usa `db_source` en línea en una implementación de método *nombre* es una variable (local para el método) que puede utilizarse para tener acceso a los datos de origen (vea el ejemplo 2). Pase este *nombre* a la `source_name` parámetro de **db_command** para asociar un comando en el origen de datos.  
  
 `hresult` (opcional)  
 Identifica la variable que recibirá el `HRESULT` de este comando de base de datos. Si la variable no existe, el atributo la insertará automáticamente.  
  
## <a name="remarks"></a>Comentarios  
 `db_source` crea un [CDataSource](../data/oledb/cdatasource-class.md) y un [CSession](../data/oledb/csession-class.md) objeto, que juntas representan una conexión con un origen de datos del consumidor de OLE DB.  
  
 Cuando usas `db_source` en una clase, el `CSession` objeto pasa a ser un miembro de la clase.  
  
 Cuando usas `db_source` en un método, se ejecutará el código insertado en el ámbito del método y el `CSession` objeto se crea como una variable local.  
  
 `db_source` Agrega propiedades del origen de datos a una clase o dentro de un método. Se utiliza junto con **db_command** (que adopta el `db_source` *nombre* parámetro como su `source_name` parámetro).  
  
 Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_ *YourClassName*descriptor de acceso, donde *YourClassName* es el nombre que asignó el clase y el compilador también creará una clase denominada *YourClassName*, que deriva de \_ *YourClassName*descriptor de acceso.  En Vista de clases verá ambas clases.  
  
 Para obtener un ejemplo de este atributo se usa en una aplicación, vea los ejemplos [AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409) y [MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo se llama `db_source` en una clase para crear una conexión al origen de datos `ds` con la base de datos Northwind. `ds` es un identificador para el origen de datos, que puede utilizarse internamente en la `CMyCommand` clase.  
  
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
