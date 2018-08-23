---
title: db_table | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_table
dev_langs:
- C++
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07c126e2cc6efe0193f6cfd55b84d8dfa7021ffc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605624"
---
# <a name="dbtable"></a>db_table

Se abre una tabla de OLE DB.

## <a name="syntax"></a>Sintaxis

```cpp
[ db_table(
   db_table,
   name,
   source_name,
   hresult
) ]
```

#### <a name="parameters"></a>Parámetros

*db_table*  
Cadena que especifica el nombre de una tabla de base de datos (por ejemplo, "productos").

*name* (opcional)  
El nombre del identificador que se utiliza para trabajar con la tabla. Debe especificar este parámetro si desea devolver más de una fila de resultados. **db_table** genera una variable con los valores especificados *nombre* que puede utilizarse para recorrer el conjunto de filas o ejecutar varias consultas de acción.

*source_name* (opcional)  
Variable o instancia `CSession` de una clase que tiene aplicado el atributo `db_source` , en el que se ejecuta el comando. Consulte [db_source](../windows/db-source.md).

*HRESULT* (opcional)  
Identifica la variable que recibirá el valor HRESULT de este comando de base de datos. Si la variable no existe, el atributo la insertará automáticamente.

## <a name="remarks"></a>Comentarios

**db_table** crea un [CTable](../data/oledb/ctable-class.md) objeto, que es utilizado por un consumidor OLE DB para abrir una tabla. Puede usar este atributo solo en el nivel de clase; no se puede usar en línea. Usar `db_column` para enlazar las columnas de tabla a las variables; use `db_param` delimitar (establece el tipo de parámetro de modo que en) de parámetros.

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

Para obtener un ejemplo de este atributo se usa en una aplicación, vea los ejemplos [AtlAgent](http://msdn.microsoft.com/52bef5da-c1a0-4223-b4e6-9e464b6db409) y [MultiRead](http://msdn.microsoft.com/5a2a915a-77dc-492f-94b2-1b809995dd5e).

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos de consumidor OLE DB](../windows/ole-db-consumer-attributes.md)  
