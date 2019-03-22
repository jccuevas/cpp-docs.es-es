---
title: db_param (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_param
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
ms.openlocfilehash: 2de051b099da5f179a7634cddfb359d85f4b1f83
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328797"
---
# <a name="dbparam"></a>db_param

La variable de miembro especificado se asocia con un parámetro de entrada o salido y delimita la variable.

## <a name="syntax"></a>Sintaxis

```cpp
[ db_param(ordinal, paramtype="DBPARAMIO_INPUT", dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>Parámetros

*ordinal*<br/>
El número de columna (ordinal DBCOLUMNINFO) correspondiente a un campo del conjunto de filas que se va a enlazar datos.

*paramtype*<br/>
(Opcional) El tipo de conjunto para el parámetro. Los proveedores admiten solo tipos de E/S de parámetros que son compatibles con el origen de datos subyacente. El tipo es una combinación de uno o más valores DBPARAMIOENUM:

- DBPARAMIO_INPUT un parámetro de entrada.

- DBPARAMIO_OUTPUT un parámetro de salida.

- DBPARAMIO_NOTPARAM el descriptor de acceso no tiene parámetros. Establecer `eParamIO` en este valor en la fila de los descriptores de acceso recuerda al usuario que se omiten los parámetros.

*dbtype*<br/>
(Opcional) OLE DB [indicador de tipo](/previous-versions/windows/desktop/ms711251(v=vs.85)) para la entrada de columna.

*precision*<br/>
(Opcional) La precisión que se usará para la entrada de columna. Para obtener más información, vea la descripción de `bPrecision` elemento de la [estructura DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))

*scale*<br/>
(Opcional) La escala que se usará para la entrada de columna. Para obtener más información, vea la descripción de `bScale` elemento de la [estructura DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))

*status*<br/>
(Opcional) Una variable de miembro que se usa para mantener el estado de esta columna. El estado indica si el valor de columna es un valor de datos o algún otro valor, como valores NULL. Para los valores posibles, vea [estado](/previous-versions/windows/desktop/ms722617(v=vs.85)) en el *referencia del programador de OLE DB*.

*length*<br/>
(Opcional) Una variable de miembro que se usa para mantener el tamaño de la columna en bytes.

## <a name="remarks"></a>Comentarios

**db_param** define los parámetros que utiliza en los comandos; por lo tanto, se usa con `db_command`. Por ejemplo, puede usar **db_param** para enlazar parámetros en consultas SQL o procedimientos almacenados. Los parámetros de un procedimiento almacenado se indican por signos de interrogación (?) y se deben enlazar a los miembros de datos en el orden en que aparecen los parámetros.

**db_param** delimita los datos de miembros que pueden participar en OLE DB `ICommandWithParameters`-enlace basado en. Establece el tipo de parámetro (entrada o salida), tipo de OLE DB, precisión, escala, estado y longitud para el parámetro especificado. Este atributo inserta las macros de consumidor OLE DB BEGIN_PARAM_MAP... END_PARAM_MAP. Cada miembro se marca con el **db_param** atributo ocupa una entrada en el mapa en forma de un COLUMN_ENTRY.

**db_param** se usa junto con el [db_table](db-table.md) o [db_command](db-command.md) atributos.

Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_ *NombreClase*descriptor de acceso, donde *NombreClase* es el nombre que asignó el clase y el compilador también creará una clase denominada *NombreClase*, que se deriva de \_ *NombreClase*descriptor de acceso.  En Vista de clases verá ambas clases.

## <a name="example"></a>Ejemplo

El ejemplo siguiente crea una clase de comando basada en el procedimiento SalesbyYear almacenado en la base de datos Northwind. Asocie el primer parámetro del procedimiento almacenado con el `m_RETURN_VALUE` variable y lo define como un parámetro de salida. Asocia los dos últimos parámetros (entrados) con `m_Beginning_Date` y `m_Ending_Date`.

En el ejemplo siguiente se asocia el `nOutput` variable con un parámetro de salida.

```cpp
// db_param.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_source(L"my_connection_string"),
  db_command(L"{ ? = CALL dbo.\"Sales by Year\"(?,?) }")
]
struct CSalesbyYear {
   DBSTATUS m_dwShippedDateStatus;
   DBSTATUS m_dwOrderIDStatus;
   DBSTATUS m_dwSubtotalStatus;
   DBSTATUS m_dwYearStatus;

   DBLENGTH m_dwShippedDateLength;
   DBLENGTH m_dwOrderIDLength;
   DBLENGTH m_dwSubtotalLength;
   DBLENGTH m_dwYearLength;

   // Bind columns
   [ db_column("1", status="m_dwShippedDateStatus", length="m_dwShippedDateLength") ] DBTIMESTAMP m_ShippedDate;
   [ db_column("2", status="m_dwOrderIDStatus", length="m_dwOrderIDLength") ] LONG m_OrderID;
   [ db_column("3", status="m_dwSubtotalStatus", length="m_dwSubtotalLength") ] CURRENCY m_Subtotal;
   [ db_column("4", status="m_dwYearStatus", length="m_dwYearLength") ] TCHAR m_Year[31];

   // Bind parameters
   [ db_param("1", paramtype="DBPARAMIO_OUTPUT") ] LONG m_RETURN_VALUE;
   [ db_param("2", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Beginning_Date;
   [ db_param("3", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Ending_Date;
};
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
