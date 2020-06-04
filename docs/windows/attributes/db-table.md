---
title: db_table (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_table
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
ms.openlocfilehash: 2b3be55a4ea118ef3441d3ea93f63e19ebdb3d79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167256"
---
# <a name="db_table"></a>db_table

Abre una tabla de OLE DB.

## <a name="syntax"></a>Sintaxis

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

### <a name="parameters"></a>Parámetros

*db_table*<br/>
Cadena que especifica el nombre de una tabla de base de datos (por ejemplo, "Products").

*name*<br/>
Opta Nombre del identificador que se utiliza para trabajar con la tabla. Debe especificar este parámetro si desea devolver más de una fila de resultados. **db_table** genera una variable con el *nombre* especificado que se puede utilizar para recorrer el conjunto de filas o para ejecutar varias consultas de acción.

*source_name*<br/>
Opta `CSession` variable o instancia de una clase que tiene el atributo `db_source` aplicado en el que se ejecuta el comando. Consulte [db_source](db-source.md).

*valor*<br/>
Opta Identifica la variable que recibirá el HRESULT de este comando de base de datos. Si la variable no existe, el atributo la insertará automáticamente.

## <a name="remarks"></a>Observaciones

**db_table** crea un objeto [CTable](../../data/oledb/ctable-class.md) , que utiliza un consumidor OLE DB para abrir una tabla. Este atributo solo se puede utilizar en el nivel de clase. no se puede usar en línea. Utilice `db_column` para enlazar columnas de tabla a variables. Use `db_param` para delimitar (establecer el tipo de parámetro, etc.) de los parámetros.

Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_descriptor de acceso *NombreClase descriptoracceso*, donde *NombreClase descriptoracceso* es el nombre que asignó a la clase, y el compilador también creará una clase denominada *NombreClase descriptoracceso*, que se deriva de \_descriptor de acceso *NombreClase descriptoracceso*.  En Vista de clases verá ambas clases.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se abre la tabla Products para su uso por `CProducts`.

```cpp
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

Para obtener un ejemplo de este atributo utilizado en una aplicación, vea [MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos de consumidor OLE DB](ole-db-consumer-attributes.md)
