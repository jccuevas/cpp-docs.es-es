---
title: db_table (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_table
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
ms.openlocfilehash: d0b67bae643698b6d4f09a75dd2e4ec6a23a5d28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607277"
---
# <a name="dbtable"></a>db_table

Se abre una tabla de OLE DB.

## <a name="syntax"></a>Sintaxis

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

#### <a name="parameters"></a>Parámetros

*db_table*<br/>
Cadena que especifica el nombre de una tabla de base de datos (por ejemplo, "productos").

*name*<br/>
(Opcional) El nombre del identificador que se utiliza para trabajar con la tabla. Debe especificar este parámetro si desea devolver más de una fila de resultados. **db_table** genera una variable con los valores especificados *nombre* que puede utilizarse para recorrer el conjunto de filas o ejecutar varias consultas de acción.

*source_name*<br/>
(Opcional) El `CSession` variable o instancia de una clase que tiene el `db_source` atributo aplicado a él en el que se ejecuta el comando. Consulte [db_source](db-source.md).

*HRESULT*<br/>
(Opcional) Identifica la variable que recibirá el valor HRESULT de este comando de base de datos. Si la variable no existe, el atributo la insertará automáticamente.

## <a name="remarks"></a>Comentarios

**db_table** crea un [CTable](../../data/oledb/ctable-class.md) objeto, que es utilizado por un consumidor OLE DB para abrir una tabla. Puede usar este atributo solo en el nivel de clase; no se puede usar en línea. Usar `db_column` para enlazar las columnas de tabla a las variables; use `db_param` delimitar (establece el tipo de parámetro de modo que en) de parámetros.

Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_ *NombreClase*descriptor de acceso, donde *NombreClase* es el nombre que asignó el clase y el compilador también creará una clase denominada *NombreClase*, que se deriva de \_ *NombreClase*descriptor de acceso.  En Vista de clases verá ambas clases.

## <a name="example"></a>Ejemplo

El ejemplo siguiente abre la tabla de productos para su uso por `CProducts`.

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

Para obtener un ejemplo de este atributo se usa en una aplicación, vea los ejemplos [AtlAgent](https://github.com/Microsoft/VCSamples) y [MultiRead](https://github.com/Microsoft/VCSamples).

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de consumidor OLE DB](ole-db-consumer-attributes.md)
