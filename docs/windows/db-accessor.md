---
title: db_accessor | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.db_accessor
dev_langs: C++
helpviewer_keywords: db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d5293712990685ff63bcafa8e5c9d5a0e8592a25
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="dbaccessor"></a>db_accessor
Grupos de **db_column** atributos que participan en `IAccessor`-basados en el enlace.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ db_accessor(   
   num,   
   auto   
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *num*  
 Especifica el número de descriptor de acceso (un índice entero basado en cero). Debe especificar números de descriptor de acceso de forma ascendente, orden, utilizando enteros o valores definidos.  
  
 *auto*  
 Un valor booleano que especifica si el descriptor de acceso se recupera automáticamente (**TRUE**) o no recuperado (**FALSE**).  
  
## <a name="remarks"></a>Comentarios  
 **db_accessor** define el descriptor de acceso de OLE DB subyacente para posteriores **db_column** y **db_param** atributos dentro de la misma clase o función. **db_accessor** es utilizable en el nivel de miembro y se utiliza al grupo **db_column** atributos que participan en OLE DB `IAccessor`-basados en el enlace. Se utiliza junto con cualquiera el **db_table** o **db_command** atributos. Llamar a este atributo es similar a llamar a la [BEGIN_ACCESSOR](../data/oledb/begin-accessor.md) y [END_ACCESSOR](../data/oledb/end-accessor.md) macros.  
  
 **db_accessor** genera un conjunto de filas y la enlaza con las asignaciones de descriptor de acceso correspondiente. Si no se llama **db_accessor**, automáticamente se generará el descriptor de acceso 0, y todos los enlaces de columna se asignarán a este bloque de descriptor de acceso.  
  
 **db_accessor** enlaces de columna en los descriptores de acceso de uno o varios grupos de la base de datos. Para obtener una explicación de los escenarios en los que es necesario utilizar varios descriptores de acceso, consulte [utilizar varios descriptores de acceso en un conjunto de filas](../data/oledb/using-multiple-accessors-on-a-rowset.md). Vea también "Usuario registro compatibilidad para varios descriptores de acceso" en [registros de usuario](../data/oledb/user-records.md).  
  
 Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_ *YourClassName*descriptor de acceso, donde *YourClassName* es el nombre que asignó el clase y el compilador también creará una clase denominada *YourClassName*, que deriva de \_ *YourClassName*descriptor de acceso.  En Vista de clases verá ambas clases.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza **db_accessor** para agrupar columnas de la tabla Orders de la base de datos Northwind en dos descriptores de acceso. Descriptor de acceso 0 es automática y descriptor de acceso 1 no lo es.  
  
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
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Bloques de atributos|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos de consumidor OLE DB](../windows/ole-db-consumer-attributes.md)   
