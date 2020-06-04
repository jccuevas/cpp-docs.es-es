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
ms.openlocfilehash: ec4d83481f6335d4c40ffb8f004b617f2ee09c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367025"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Conjunto de registros: Obtener registros de forma masiva (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

La `CRecordset` clase proporciona compatibilidad para la obtención masiva de filas, lo que significa que se pueden recuperar varios registros a la vez durante una sola captura, en lugar de recuperar un registro a la vez desde el origen de datos. Puede implementar la obtención masiva de `CRecordset` filas solo en una clase derivada. El proceso de transferencia de datos desde el origen de datos al objeto de conjunto de registros se denomina intercambio de campos de registros masivos (RFX masivo). Tenga en cuenta que si no utiliza `CRecordset`la obtención masiva de filas en una clase derivada, los datos se transfieren mediante el intercambio de campos de registros (RFX). Para obtener más información, vea Intercambio de campos de [registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).

En este tema se explica:

- [Cómo CRecordset admite la obtención](#_core_how_crecordset_supports_bulk_row_fetching)masiva de filas .

- [Algunas consideraciones especiales al usar](#_core_special_considerations)la obtención masiva de filas .

- Cómo implementar el intercambio de campos de [registros masivos](#_core_how_to_implement_bulk_record_field_exchange).

## <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>Cómo CRecordset admite la obtención masiva de filas

Antes de abrir el objeto de conjunto `SetRowsetSize` de registros, puede definir un tamaño de conjunto de filas con la función miembro. El tamaño del conjunto de filas especifica cuántos registros se deben recuperar durante una sola captura. Cuando se implementa la obtención masiva de filas, el tamaño predeterminado del conjunto de filas es 25. Si no se implementa la obtención masiva de filas, el tamaño del conjunto de filas permanece fijo en 1.

Después de inicializar el tamaño del conjunto de filas, llame a la [Open](../../mfc/reference/crecordset-class.md#open) función miembro. Aquí debe especificar `CRecordset::useMultiRowFetch` la opción del parámetro *dwOptions* para implementar la obtención masiva de filas. Además, puede `CRecordset::userAllocMultiRowBuffers` establecer la opción. El mecanismo de intercambio de campos de registros masivos utiliza matrices para almacenar las varias filas de datos recuperados durante una captura. El marco de trabajo puede asignar automáticamente estos búferes de almacenamiento o puede asignarlos manualmente. Especificar la `CRecordset::userAllocMultiRowBuffers` opción significa que realizará la asignación.

En la tabla siguiente se `CRecordset` enumeran las funciones miembro proporcionadas por para admitir la obtención masiva de filas.

|Función de miembro|Descripción|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Función virtual que controla los errores que se producen durante la obtención.|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implementa el intercambio de campos de registros masivos. Se llama automáticamente para transfiere varias filas de datos del origen de datos al objeto de conjunto de registros.|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Recupera la configuración actual para el tamaño del conjunto de filas.|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Indica cuántas filas se recuperaron realmente después de una captura determinada. En la mayoría de los casos, se trata del tamaño del conjunto de filas, a menos que se haya capturado un conjunto de filas incompleto.|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Devuelve un estado de captura para una fila determinada dentro de un conjunto de filas.|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Actualiza los datos y el estado de una fila determinada dentro de un conjunto de filas.|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Mueve el cursor a una fila determinada dentro de un conjunto de filas.|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Función virtual que cambia la configuración del tamaño del conjunto de filas al valor especificado.|

## <a name="special-considerations"></a><a name="_core_special_considerations"></a>Consideraciones especiales

Aunque la obtención masiva de filas es una ganancia de rendimiento, ciertas características funcionan de manera diferente. Antes de decidir implementar la obtención masiva de filas, tenga en cuenta lo siguiente:

- El marco de `DoBulkFieldExchange` trabajo llama automáticamente a la función miembro para transferir datos desde el origen de datos al objeto de conjunto de registros. Sin embargo, los datos no se transfieren desde el conjunto de registros al origen de datos. Al `AddNew`llamar `Edit` `Delete`a `Update` las funciones miembro , , o se produce un error en la aserción. Aunque `CRecordset` actualmente no proporciona un mecanismo para actualizar filas masivas de datos, `SQLSetPos`puede escribir sus propias funciones mediante la función de API ODBC . Para obtener `SQLSetPos`más información acerca de , consulte la *referencia del programador del SDK de ODBC* en la documentación de MSDN.

- `IsDeleted`Las funciones `IsFieldDirty` `IsFieldNull`miembro `IsFieldNullable` `SetFieldDirty`, `SetFieldNull` , , , , , y no se pueden usar en conjuntos de registros que implementan la obtención masiva de filas. Sin embargo, `GetRowStatus` puede `IsDeleted`llamar `GetODBCFieldInfo` en lugar `IsFieldNullable`de , y en lugar de .

- Las `Move` operaciones cambian la posición del conjunto de registros por conjunto de filas. Por ejemplo, supongamos que abre un conjunto de registros que tiene 100 registros con un tamaño de conjunto de filas inicial de 10. `Open`obtiene las filas 1 a 10, con el registro actual colocado en la fila 1. Una llamada `MoveNext` a recupera el siguiente conjunto de filas, no la fila siguiente. Este conjunto de filas consta de las filas 11 a 20, con el registro actual colocado en la fila 11. Tenga `MoveNext` en `Move( 1 )` cuenta que y no son equivalentes cuando se implementa la obtención masiva de filas. `Move( 1 )`recupera el conjunto de filas que comienza 1 fila del registro actual. En este ejemplo, al llamar `Move( 1 )` después de llamar `Open` se recupera el conjunto de filas que consta de las filas 2 a 11, con el registro actual situado en la fila 2. Para obtener más información, vea el [Move](../../mfc/reference/crecordset-class.md#move) función miembro.

- A diferencia del intercambio de campos de registros, los asistentes no admiten el intercambio masivo de campos de registros. Esto significa que debe declarar manualmente los miembros `DoBulkFieldExchange` de datos de campo y reemplazar manualmente escribiendo llamadas a las funciones RFX masivas. Para obtener más información, vea [Funciones](../../mfc/reference/record-field-exchange-functions.md) de intercambio de campos de registro en la Referencia de biblioteca de *clases*.

## <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>Cómo implementar el intercambio de campos de registros masivos

El intercambio masivo de campos de registros transfiere un conjunto de filas de datos del origen de datos al objeto de conjunto de registros. Las funciones RFX masivas usan matrices para almacenar estos datos, así como matrices para almacenar la longitud de cada elemento de datos en el conjunto de filas. En la definición de clase, debe definir los miembros de datos de campo como punteros para tener acceso a las matrices de datos. Además, debe definir un conjunto de punteros para tener acceso a las matrices de longitudes. Los miembros de datos de parámetro no deben declararse como punteros; declarar miembros de datos de parámetro cuando se utiliza el intercambio de campos de registros masivos es lo mismo que declararlos cuando se utiliza el intercambio de campos de registros. El código siguiente muestra un ejemplo sencillo:

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

Puede asignar estos búferes de almacenamiento manualmente o hacer que el marco de trabajo realice la asignación. Para asignar los búferes usted `CRecordset::userAllocMultiRowBuffers` mismo, debe especificar la `Open` opción del parámetro *dwOptions* en la función miembro. Asegúrese de establecer los tamaños de las matrices al menos igual al tamaño del conjunto de filas. Si desea que el marco de trabajo realice la asignación, debe inicializar los punteros a NULL. Esto se hace normalmente en el constructor del objeto de conjunto de registros:

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

Por último, debe `DoBulkFieldExchange` invalidar la función miembro. Para los miembros de datos de campo, llame a las funciones RFX masivas; para cualquier miembro de datos de parámetro, llame a las funciones RFX. Si abrió el conjunto de registros pasando `Open`una instrucción SQL o un procedimiento almacenado a , el orden en el que realiza las llamadas RFX masivas debe corresponder al orden de las columnas del conjunto de registros; De forma similar, el orden de las llamadas RFX para parámetros debe corresponder al orden de los parámetros en la instrucción SQL o procedimiento almacenado.

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
> Debe llamar `Close` a la función `CRecordset` miembro antes de que la clase derivada salga del ámbito. Esto garantiza que se libere cualquier memoria asignada por el marco de trabajo. Es una buena práctica de `Close`programación llamar siempre explícitamente , independientemente de si ha implementado la obtención masiva de filas.

Para obtener más información sobre el intercambio de campos de registros (RFX), vea Intercambio de campos de [registros: Cómo funciona RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Para obtener más información sobre el uso de parámetros, vea [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) y [Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
