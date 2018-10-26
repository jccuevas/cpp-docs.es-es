---
title: db_source (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: bd8facb38bc4d71445674eb64ad09ab14d0b636a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065894"
---
# <a name="dbsource"></a>db_source

Crea una conexión a un origen de datos.

## <a name="syntax"></a>Sintaxis

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>Parámetros

*db_source*<br/>
La cadena de conexión usada para conectarse al origen de datos. Para el formato de la cadena de conexión, consulte [cadenas de conexión y vínculos de datos](/previous-versions/windows/desktop/ms718376) en Microsoft Data Access Components (MDAC) SDK.

*name*<br/>
(Opcional) Cuando usas **db_source** en una clase, *nombre* es una instancia de un objeto de origen de datos que tiene el **db_source** atributo aplicado a él (vea el ejemplo 1). Cuando usas **db_source** en línea en una implementación de método *nombre* es una variable (local al método) que se puede usar para acceder a los datos de origen (vea el ejemplo 2). Pase este *nombre* a la *source_name* parámetro de `db_command` para asociar un comando en el origen de datos.

*HRESULT*<br/>
(Opcional) Identifica la variable que recibirá el valor HRESULT de este comando de base de datos. Si la variable no existe, el atributo la insertará automáticamente.

## <a name="remarks"></a>Comentarios

**db_source** crea un [CDataSource](../../data/oledb/cdatasource-class.md) y un [CSession](../../data/oledb/csession-class.md) objeto, que juntas representan una conexión con un origen de datos del consumidor de OLE DB.

Cuando usas **db_source** en una clase, el `CSession` objeto se convierte en un miembro de la clase.

Cuando usas **db_source** en un método, se ejecutará el código insertado en el ámbito del método y el `CSession` objeto se crea como una variable local.

**db_source** agrega propiedades del origen de datos a una clase o dentro de un método. Se usa junto con `db_command` (que toma el *db_source* *nombre* parámetro como su *source_name* parámetro).

Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_ *NombreClase*descriptor de acceso, donde *NombreClase* es el nombre que asignó el clase y el compilador también creará una clase denominada *NombreClase*, que se deriva de \_ *NombreClase*descriptor de acceso.  En Vista de clases verá ambas clases.

Para obtener un ejemplo de este atributo se usa en una aplicación, vea los ejemplos [AtlAgent](https://github.com/Microsoft/VCSamples) y [MultiRead](https://github.com/Microsoft/VCSamples).

## <a name="example"></a>Ejemplo

Este ejemplo llama a **db_source** en una clase para crear una conexión al origen de datos `ds` con la base de datos Northwind. `ds` es un identificador para el origen de datos, que puede utilizarse internamente en el `CMyCommand` clase.

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
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de consumidor OLE DB](ole-db-consumer-attributes.md)
