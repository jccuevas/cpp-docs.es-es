---
title: db_column (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_column
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
ms.openlocfilehash: 4ce57443480e35e7a4c7b9e872e41777662ddc20
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167295"
---
# <a name="db_column"></a>db_column

Enlaza una columna especificada a una variable del conjunto de filas.

## <a name="syntax"></a>Sintaxis

```cpp
[ db_column(ordinal, dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>Parámetros

*ordinal*<br/>
El número de columna ordinal (`DBCOLUMNINFO` ordinal) o el nombre de columna (cadena ANSI o Unicode) correspondiente a un campo del conjunto de filas al que se van a enlazar los datos. Si usa números, puede omitir los ordinales consecutivos (por ejemplo: 1, 2, 3, 5). El nombre puede contener espacios si el proveedor de OLE DB que usa lo admite. Por ejemplo, puede usar cualquiera de los siguientes formatos:

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

*DbType*<br/>
Opta Indicador de [tipo](/previous-versions/windows/desktop/ms711251(v=vs.85)) de OLE DB para la entrada de columna.

*precisión*<br/>
Opta Precisión que se va a utilizar para la entrada de la columna. Para obtener más información, vea la descripción del elemento `bPrecision` de la [estructura DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) .

*scale*<br/>
Opta Escala que se va a utilizar para la entrada de la columna. Para obtener más información, vea la descripción de `bScale` elemento de la [estructura DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) .

*status*<br/>
Opta Una variable miembro que se usa para contener el estado de esta columna. El estado indica si el valor de la columna es un valor de datos o algún otro valor, como, por ejemplo, NULL. Para obtener los valores posibles, vea [status](/previous-versions/windows/desktop/ms722617(v=vs.85)) en la *Referencia del programador de OLE DB*.

*length*<br/>
Opta Variable miembro que se usa para almacenar el tamaño de la columna en bytes.

## <a name="remarks"></a>Observaciones

**db_column** enlaza la columna de la tabla especificada a una variable del conjunto de filas. Delimita los datos de miembro que pueden participar en OLE DB enlace basado en `IAccessor`. Este atributo configura el mapa de columnas que se define normalmente mediante las macros OLE DB consumidor [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../../data/oledb/end-column-map.md)y [COLUMN_ENTRY](../../data/oledb/column-entry.md). Estos manipulan el OLE DB [estructura DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) para enlazar la columna especificada. Cada miembro marcado con el atributo **db_column** ocupará una entrada en el mapa de columnas en forma de entrada de columna. Por lo tanto, se llama a este atributo en el que se colocaría el mapa de columnas, es decir, en la clase de comando o de tabla.

Use **db_column** junto con los atributos [db_table](db-table.md) o [db_command](db-command.md) .

Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_descriptor de acceso *NombreClase descriptoracceso*, donde *NombreClase descriptoracceso* es el nombre que asignó a la clase, y el compilador también creará una clase denominada *NombreClase descriptoracceso*, que se deriva de \_descriptor de acceso *NombreClase descriptoracceso*.  En Vista de clases verá ambas clases.

Para obtener un ejemplo de este atributo utilizado en una aplicación, vea [MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="example"></a>Ejemplo

Este ejemplo enlaza una columna de una tabla a un miembro de datos **largo** y especifica los campos de estado y longitud.

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

Este ejemplo enlaza cuatro columnas a una larga, una cadena de caracteres, una marca de **tiempo**y un `DB_NUMERIC` entero, en ese orden.

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
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos de consumidor OLE DB](ole-db-consumer-attributes.md)<br/>
[Atributos de clase](class-attributes.md)
