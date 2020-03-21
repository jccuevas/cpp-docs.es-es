---
title: 'Conjunto de registros: Obtener registros de forma masiva (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- bulk row fetching, implementing
- ODBC recordsets, bulk row fetching
- bulk record field exchange
- bulk row fetching
- bulk RFX functions
- recordsets, bulk row fetching
- DoBulkFieldExchange method
- fetching ODBC records in bulk
- RFX (ODBC), bulk
- rowsets, bulk row fetching
- RFX (ODBC), bulk row fetching
ms.assetid: 20d10fe9-c58a-414a-b675-cdf9aa283e4f
ms.openlocfilehash: cd9597da7ab4c405f90a145182d63945cef48c53
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079822"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Conjunto de registros: Obtener registros de forma masiva (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

La clase `CRecordset` proporciona compatibilidad con la obtención masiva de filas, lo que significa que se pueden recuperar varios registros a la vez durante una captura única, en lugar de recuperar un registro a la vez desde el origen de datos. Solo puede implementar la obtención masiva de filas en una clase `CRecordset` derivada. El proceso de transferir datos desde el origen de datos al objeto de conjunto de registros se denomina intercambio masivo de campos de registro (RFX masivo). Tenga en cuenta que si no usa la obtención masiva de filas en una clase derivada de `CRecordset`, los datos se transfieren a través de intercambio de campos de registros (RFX). Para obtener más información, vea [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).

En este tema se explica:

- [Cómo admite CRecordset la obtención masiva de filas](#_core_how_crecordset_supports_bulk_row_fetching).

- [Algunas consideraciones especiales al usar la obtención masiva de filas](#_core_special_considerations).

- [Cómo implementar el intercambio masivo de campos de registros](#_core_how_to_implement_bulk_record_field_exchange).

##  <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>Cómo admite CRecordset la obtención masiva de filas

Antes de abrir el objeto de conjunto de registros, puede definir un tamaño de conjunto de filas con la función miembro `SetRowsetSize`. El tamaño del conjunto de filas especifica el número de registros que se deben recuperar durante una sola captura. Cuando se implementa la obtención masiva de filas, el tamaño del conjunto de filas predeterminado es 25. Si no se implementa la obtención masiva de filas, el tamaño del conjunto de filas permanece fijo en 1.

Una vez inicializado el tamaño del conjunto de filas, llame a la función miembro [Open](../../mfc/reference/crecordset-class.md#open) . Aquí debe especificar la opción `CRecordset::useMultiRowFetch` del parámetro *dwOptions* para implementar la obtención masiva de filas. Además, puede establecer la opción `CRecordset::userAllocMultiRowBuffers`. El mecanismo de intercambio masivo de campos de registro utiliza matrices para almacenar las múltiples filas de datos recuperadas durante una captura. Estos búferes de almacenamiento pueden ser asignados automáticamente por el marco de trabajo o puede asignarlos manualmente. Si se especifica la opción `CRecordset::userAllocMultiRowBuffers`, se realizará la asignación.

En la tabla siguiente se enumeran las funciones miembro proporcionadas por `CRecordset` para admitir la obtención masiva de filas.

|Función de miembro|Descripción|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Función virtual que controla los errores que se producen durante la captura.|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implementa el intercambio masivo de campos de registros. Se llama automáticamente a para transferir varias filas de datos del origen de datos al objeto de conjunto de registros.|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Recupera el valor actual para el tamaño del conjunto de filas.|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Indica el número de filas que se recuperaron realmente después de una captura determinada. En la mayoría de los casos, este es el tamaño del conjunto de filas, a menos que se haya capturado un conjunto de filas incompleto.|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Devuelve un estado de captura para una fila determinada dentro de un conjunto de filas.|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Actualiza los datos y el estado de una fila determinada dentro de un conjunto de filas.|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Mueve el cursor a una fila determinada dentro de un conjunto de filas.|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Función virtual que cambia la configuración del tamaño del conjunto de filas al valor especificado.|

##  <a name="special-considerations"></a><a name="_core_special_considerations"></a>Consideraciones especiales

Aunque la obtención masiva de filas es una mejora del rendimiento, ciertas características funcionan de manera diferente. Antes de decidir implementar la obtención masiva de filas, tenga en cuenta lo siguiente:

- El marco de trabajo llama automáticamente a la función miembro `DoBulkFieldExchange` para transferir datos desde el origen de datos al objeto de conjunto de registros. Sin embargo, los datos no se transfieren desde el conjunto de registros hasta el origen de datos. Llamar a las funciones miembro `AddNew`, `Edit`, `Delete`o `Update` produce un error en una aserción. Aunque actualmente `CRecordset` no proporciona un mecanismo para actualizar filas de datos masivas, puede escribir sus propias funciones mediante la función de la API de ODBC `SQLSetPos`. Para obtener más información acerca de `SQLSetPos`, vea la *Referencia del programador del SDK de ODBC* en la documentación de MSDN.

- Las funciones miembro `IsDeleted`, `IsFieldDirty`, `IsFieldNull`, `IsFieldNullable`, `SetFieldDirty`y `SetFieldNull` no se pueden utilizar en conjuntos de registros que implementan la obtención masiva de filas. Sin embargo, puede llamar a `GetRowStatus` en lugar de `IsDeleted`y `GetODBCFieldInfo` en lugar de `IsFieldNullable`.

- El `Move` operaciones cambia la posición del conjunto de registros por conjunto de filas. Por ejemplo, supongamos que abre un conjunto de registros que tiene 100 registros con un tamaño de conjunto de filas inicial de 10. `Open` captura las filas del 1 al 10, con el registro actual colocado en la fila 1. Una llamada a `MoveNext` captura el siguiente conjunto de filas, no la fila siguiente. Este conjunto de filas consta de las filas 11 a 20, con el registro actual colocado en la fila 11. Tenga en cuenta que `MoveNext` y `Move( 1 )` no son equivalentes cuando se implementa la obtención masiva de filas. `Move( 1 )` captura el conjunto de filas que comienza 1 fila del registro actual. En este ejemplo, la llamada a `Move( 1 )` después de llamar a `Open` captura el conjunto de filas que consta de las filas 2 a 11, con el registro actual colocado en la fila 2. Para obtener más información, vea la función miembro [Move](../../mfc/reference/crecordset-class.md#move) .

- A diferencia del intercambio de campos de registros, los asistentes no admiten el intercambio masivo de campos de registros. Esto significa que debe declarar manualmente los miembros de datos de campo y reemplazar manualmente `DoBulkFieldExchange` escribiendo llamadas a las funciones de RFX masivo. Para obtener más información, vea [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md) en la referencia de la biblioteca de *clases*.

##  <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>Cómo implementar el intercambio masivo de campos de registros

Intercambio masivo de campos de registros transfiere un conjunto de filas de datos del origen de datos al objeto de conjunto de registros. Las funciones de RFX masivo usan matrices para almacenar estos datos, así como matrices para almacenar la longitud de cada elemento de datos en el conjunto de filas. En la definición de clase, debe definir los miembros de datos de campo como punteros para tener acceso a las matrices de datos. Además, debe definir un conjunto de punteros para tener acceso a las matrices de longitudes. Los miembros de datos de parámetros no se deben declarar como punteros; la declaración de miembros de datos de parámetro cuando se usa el intercambio masivo de campos de registros es igual que la declaración cuando se usa el intercambio de campos de registros. En el código siguiente se muestra un ejemplo sencillo:

```cpp
class MultiRowSet : public CRecordset
{
public:
   // Field/Param Data
      // field data members
      long* m_rgID;
      LPSTR m_rgName;

      // pointers for the lengths
      // of the field data
      long* m_rgIDLengths;
      long* m_rgNameLengths;

      // input parameter data member
      CString m_strNameParam;

   .
   .
   .
}
```

Puede asignar estos búferes de almacenamiento manualmente o hacer que el marco realice la asignación. Para asignar los búferes usted mismo, debe especificar la opción `CRecordset::userAllocMultiRowBuffers` del parámetro *dwOptions* en la función miembro `Open`. Asegúrese de establecer los tamaños de las matrices al menos igual que el tamaño del conjunto de filas. Si desea que el marco realice la asignación, debe inicializar los punteros en NULL. Esto se hace normalmente en el constructor del objeto de conjunto de registros:

```cpp
MultiRowSet::MultiRowSet( CDatabase* pDB )
   : CRecordset( pDB )
{
   m_rgID = NULL;
   m_rgName = NULL;
   m_rgIDLengths = NULL;
   m_rgNameLengths = NULL;
   m_strNameParam = "";

   m_nFields = 2;
   m_nParams = 1;

   .
   .
   .
}
```

Por último, debe invalidar la función miembro `DoBulkFieldExchange`. Para los miembros de datos de campo, llame a las funciones de RFX masivo; para cualquier miembro de datos de parámetro, llame a las funciones de RFX. Si ha abierto el conjunto de registros pasando una instrucción SQL o un procedimiento almacenado a `Open`, el orden en el que realiza las llamadas a RFX masivo debe corresponder al orden de las columnas del conjunto de registros; del mismo modo, el orden de las llamadas RFX para los parámetros debe corresponderse con el orden de los parámetros en la instrucción SQL o el procedimiento almacenado.

```cpp
void MultiRowSet::DoBulkFieldExchange( CFieldExchange* pFX )
{
   // call the Bulk RFX functions
   // for field data members
   pFX->SetFieldType( CFieldExchange::outputColumn );
   RFX_Long_Bulk( pFX, _T( "[colRecID]" ),
                  &m_rgID, &m_rgIDLengths );
   RFX_Text_Bulk( pFX, _T( "[colName]" ),
                  &m_rgName, &m_rgNameLengths, 30 );

   // call the RFX functions for
   // for parameter data members
   pFX->SetFieldType( CFieldExchange::inputParam );
   RFX_Text( pFX, "NameParam", m_strNameParam );
}
```

> [!NOTE]
>  Debe llamar a la función miembro `Close` antes de que la clase derivada `CRecordset` quede fuera del ámbito. Esto garantiza que se libere cualquier memoria asignada por el marco. Se recomienda llamar siempre a `Close`explícitamente, independientemente de si se ha implementado la obtención masiva de filas.

Para obtener más información sobre el intercambio de campos de registros (RFX), vea [intercambio de campos de registros:](../../data/odbc/record-field-exchange-how-rfx-works.md)funcionamiento de RFX. Para obtener más información sobre el uso de parámetros, vea [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) y [Recordset: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset:: m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset:: m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
