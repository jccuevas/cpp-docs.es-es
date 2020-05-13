---
title: db_accessor (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_accessor
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
ms.openlocfilehash: 1e9725dad39974b828d87bd8b4cdeac623f4e12f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214869"
---
# <a name="db_accessor"></a>db_accessor

Agrupa `db_column` atributos que participan en el enlace basado en `IAccessor`.

## <a name="syntax"></a>Sintaxis

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>Parámetros

*num*<br/>
Especifica el número de descriptor de acceso (un índice de entero de base cero). Debe especificar los números de descriptor de acceso en orden ascendente, utilizando enteros o valores definidos.

*auto*<br/>
Valor booleano que especifica si el descriptor de acceso se recupera automáticamente (TRUE) o no (FALSE).

## <a name="remarks"></a>Observaciones

**db_accessor** define el descriptor de acceso de OLE DB subyacente para los atributos `db_column` y `db_param` subsiguientes dentro de la misma clase o función. **db_accessor** se puede usar en el nivel de miembro y se utiliza para agrupar los atributos de `db_column` que participan en OLE DB enlace basado en `IAccessor`. Se usa junto con los atributos `db_table` o `db_command`. Llamar a este atributo es similar a llamar a las macros [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR](../../data/oledb/end-accessor.md) .

**db_accessor** genera un conjunto de filas y lo enlaza a las asignaciones de descriptores de acceso correspondientes. Si no llama a **db_accessor**, el descriptor de acceso 0 se generará automáticamente y todos los enlaces de columna se asignarán a este bloque de descriptores de acceso.

**db_accessor** agrupa los enlaces de columnas de base de datos en uno o más descriptores de acceso. Para obtener una explicación de los escenarios en los que es necesario utilizar varios descriptores de acceso, vea [utilizar varios descriptores de acceso en un conjunto de filas](../../data/oledb/using-multiple-accessors-on-a-rowset.md). Vea también "compatibilidad con registros de usuario para varios descriptores de acceso" en [registros de usuario](../../data/oledb/user-records.md).

Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_descriptor de acceso *NombreClase descriptoracceso*, donde *NombreClase descriptoracceso* es el nombre que asignó a la clase, y el compilador también creará una clase denominada *NombreClase descriptoracceso*, que se deriva de \_descriptor de acceso *NombreClase descriptoracceso*.  En Vista de clases verá ambas clases.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa **db_accessor** para agrupar las columnas de la tabla Orders de la base de datos Northwind en dos descriptores de acceso. Descriptor de acceso 0 es un descriptor de acceso automático y el descriptor de acceso 1 no.

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
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos de consumidor OLE DB](ole-db-consumer-attributes.md)
