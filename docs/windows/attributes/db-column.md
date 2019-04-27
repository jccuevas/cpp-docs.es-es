---
title: db_column (C++ atributo COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_column
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
ms.openlocfilehash: e0e2c873452884275e97663ae2d9d6df2f790ffd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148190"
---
# <a name="dbcolumn"></a>db_column

Enlaza una columna especificada a una variable en el conjunto de filas.

## <a name="syntax"></a>Sintaxis

```cpp
[ db_column(ordinal, dbtype, precision, scale, status, length) ]
```

#### <a name="parameters"></a>Parámetros

*ordinal*<br/>
El número de columna ordinal (`DBCOLUMNINFO` ordinal) o nombre de columna (cadena ANSI o Unicode) correspondiente a un campo del conjunto de filas que se va a enlazar datos. Si utiliza números, puede omitir los ordinales consecutivos (por ejemplo: 1, 2, 3, 5). El nombre puede contener espacios, si lo admite el proveedor OLE DB que utiliza. Por ejemplo, puede usar cualquiera de los siguientes formatos:

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

*dbtype*<br/>
(Opcional) OLE DB [indicador de tipo](/previous-versions/windows/desktop/ms711251(v=vs.85)) para la entrada de columna.

*precision*<br/>
(Opcional) La precisión que se usará para la entrada de columna. Para obtener más información, vea la descripción de la `bPrecision` elemento de la [estructura DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))

*scale*<br/>
(Opcional) La escala que se usará para la entrada de columna. Para obtener más información, vea la descripción de `bScale` elemento de la [estructura DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))

*status*<br/>
(Opcional) Una variable de miembro que se usa para mantener el estado de esta columna. El estado indica si el valor de columna es un valor de datos o algún otro valor, como valores NULL. Para los valores posibles, vea [estado](/previous-versions/windows/desktop/ms722617(v=vs.85)) en el *referencia del programador de OLE DB*.

*length*<br/>
(Opcional) Una variable de miembro que se usa para mantener el tamaño de la columna en bytes.

## <a name="remarks"></a>Comentarios

**db_column** enlaza la columna de tabla especificada a una variable en el conjunto de filas. Delimita los datos de los miembros que pueden participar en OLE DB `IAccessor`-enlace basado en. Este atributo se configura la asignación de columna que normalmente se definen mediante las macros de consumidor OLE DB [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../../data/oledb/end-column-map.md), y [COLUMN_ENTRY](../../data/oledb/column-entry.md). Estos manipulan OLE DB [estructura DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) para enlazar la columna especificada. Cada miembro se marca con el **db_column** atributo ocupa una entrada en el mapa de columnas en forma de una entrada de columna. Por lo tanto, llamar a este atributo donde tendría que poner el mapa de columnas, es decir, en la clase de comando o una tabla.

Use **db_column** junto con el [db_table](db-table.md) o [db_command](db-command.md) atributos.

Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_ *NombreClase*descriptor de acceso, donde *NombreClase* es el nombre que asignó el clase y el compilador también creará una clase denominada *NombreClase*, que se deriva de \_ *NombreClase*descriptor de acceso.  En Vista de clases verá ambas clases.

Para obtener ejemplos de este atributo se usa en una aplicación, vea los ejemplos [AtlAgent](https://github.com/Microsoft/VCSamples), y [MultiRead](https://github.com/Microsoft/VCSamples).

## <a name="example"></a>Ejemplo

En este ejemplo se enlaza a una columna de una tabla para un **largo** miembro de datos y especifica los campos Estado y longitud.

```cpp
// db_column_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   DBSTATUS m_dwProductIDStatus;
   DBLENGTH m_dwProductIDLength;

   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;
};
```

## <a name="example"></a>Ejemplo

Este ejemplo enlaza cuatro columnas a un **largo**, una cadena de caracteres, una marca de tiempo y un `DB_NUMERIC` entero, en ese orden.

```cpp
// db_column_2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   [db_column("1")] LONG m_OrderID;
   [db_column("2")] TCHAR m_CustomerID[6];
   [db_column("4")] DB_NUMERIC m_OrderDate;
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**, miembro, método|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de consumidor OLE DB](ole-db-consumer-attributes.md)<br/>
[Atributos de clase](class-attributes.md)
