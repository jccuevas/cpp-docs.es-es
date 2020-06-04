---
title: db_source (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_source
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
ms.openlocfilehash: 6346a8d6f60313dc17bbcbad062aa888857f0b67
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167282"
---
# <a name="db_source"></a>db_source

Crea una conexión a un origen de datos.

## <a name="syntax"></a>Sintaxis

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>Parámetros

*db_source*<br/>
Cadena de conexión utilizada para conectarse al origen de datos. Para obtener el formato de la cadena de conexión, consulte [cadenas de conexión y vínculos de datos](/previous-versions/windows/desktop/ms718376(v=vs.85)) en el SDK de Microsoft Data Access Components (MDAC).

*name*<br/>
Opta Cuando se utiliza **db_source** en una clase, *Name* es una instancia de un objeto de origen de datos que tiene aplicado el atributo **db_source** (vea el ejemplo 1). Cuando se usa **db_source** insertado en una implementación de método, *Name* es una variable (local del método) que se puede utilizar para tener acceso al origen de datos (vea el ejemplo 2). Este *nombre* se pasa al parámetro *source_name* de `db_command` para asociar el origen de datos a un comando.

*valor*<br/>
Opta Identifica la variable que recibirá el HRESULT de este comando de base de datos. Si la variable no existe, el atributo la insertará automáticamente.

## <a name="remarks"></a>Observaciones

**db_source** crea un objeto [CDataSource](../../data/oledb/cdatasource-class.md) y un objeto [CSession](../../data/oledb/csession-class.md) , que juntos representan una conexión con un origen de datos de consumidor OLE DB.

Cuando se utiliza **db_source** en una clase, el objeto `CSession` se convierte en un miembro de la clase.

Cuando se utiliza **db_source** en un método, el código insertado se ejecutará dentro del ámbito del método y el objeto `CSession` se creará como una variable local.

**db_source** agrega propiedades de origen de datos a una clase o dentro de un método. Se usa junto con `db_command` (que toma el parámetro de *db_source* *nombre* db_source como su parámetro *source_name* ).

Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_descriptor de acceso *NombreClase descriptoracceso*, donde *NombreClase descriptoracceso* es el nombre que asignó a la clase, y el compilador también creará una clase denominada *NombreClase descriptoracceso*, que se deriva de \_descriptor de acceso *NombreClase descriptoracceso*.  En Vista de clases verá ambas clases.

Para obtener un ejemplo de este atributo utilizado en una aplicación, vea [MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="example"></a>Ejemplo

En este ejemplo se llama a **db_source** en una clase para crear una conexión con el origen de datos `ds` mediante la base de datos Northwind. `ds` es un identificador del origen de datos, que se puede usar internamente en la clase `CMyCommand`.

```cpp
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
|**Se aplica a**|**clase**, **struct**, miembro, método, local|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos de consumidor OLE DB](ole-db-consumer-attributes.md)
