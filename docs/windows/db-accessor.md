---
title: db_accessor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_accessor
dev_langs:
- C++
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 68c7d70c6d1192e1b80253cf1fb3cfc3040d8fce
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570663"
---
# <a name="dbaccessor"></a>db_accessor
Grupos `db_column` atributos que participan en `IAccessor`-enlace basado en.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[ db_accessor(   
   num,   
   auto   
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *num*  
 Especifica el número de descriptor de acceso (un índice entero basado en cero). Debe especificar números de descriptor de acceso en aumentar orden, utilizando enteros o valores definen.  
  
 *auto*  
 Un valor booleano que especifica si el descriptor de acceso se recuperan automáticamente (TRUE) o no (FALSE) recuperado.  
  
## <a name="remarks"></a>Comentarios  
 **db_accessor** define el descriptor de acceso de OLE DB subyacente para posteriores `db_column` y `db_param` atributos dentro de la misma clase o función. **db_accessor** se puede usar en el nivel de miembro y se usa al grupo `db_column` atributos que participan en OLE DB `IAccessor`-enlace basado en. Se usa junto con el `db_table` o `db_command` atributos. Llamar a este atributo es similar a llamar a la [BEGIN_ACCESSOR](../data/oledb/begin-accessor.md) y [END_ACCESSOR](../data/oledb/end-accessor.md) macros.  
  
 **db_accessor** genera un conjunto de filas y lo enlaza a las asignaciones de descriptor de acceso correspondiente. Si no se llama **db_accessor**0 del descriptor de acceso se genera automáticamente y todos los enlaces de columna se asignarán a este bloque descriptor de acceso.  
  
 **db_accessor** enlaces de columna en los descriptores de acceso de uno o varios grupos de la base de datos. Para obtener una explicación de los escenarios en los que es necesario utilizar varios descriptores de acceso, consulte [utilizar varios descriptores de acceso en un conjunto de filas](../data/oledb/using-multiple-accessors-on-a-rowset.md). Vea también "Usuario registro soporte para varios descriptores de acceso" en [registros de usuario](../data/oledb/user-records.md).  
  
 Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_ *NombreClase*descriptor de acceso, donde *NombreClase* es el nombre que asignó el clase y el compilador también creará una clase denominada *NombreClase*, que se deriva de \_ *NombreClase*descriptor de acceso.  En Vista de clases verá ambas clases.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa **db_accessor** para agrupar las columnas en la tabla Orders de la base de datos Northwind en dos descriptores de acceso. 0 de descriptor de acceso es automática y no es el descriptor de acceso 1.  
  
```cpp  
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