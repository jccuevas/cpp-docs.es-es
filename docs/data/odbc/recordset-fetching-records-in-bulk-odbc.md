---
title: 'Conjunto de registros: Obtener registros de forma masiva (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ef8803459edeba98e472a0e7fd07e7f5daf2c4e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097899"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Conjunto de registros: Obtener registros de forma masiva (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 Clase `CRecordset` proporciona compatibilidad para la obtención masiva de filas, lo que significa que varios registros se pueden recuperar a la vez durante una sola operación de obtención, en lugar de recuperar un registro a la vez desde el origen de datos. Puede implementar la obtención masiva de filas únicamente en un derivada `CRecordset` clase. El proceso de transferencia de datos desde el origen de datos para el objeto de conjunto de registros se denomina intercambio masivo de campos de registros (RFX masivo). Tenga en cuenta que si no utiliza la obtención masiva de filas en un `CRecordset`-clase derivada, los datos se transfiere a través de intercambio de campos de registros (RFX). Para obtener más información, consulte [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
 En este tema se explica:  
  
-   [¿Cómo admite CRecordset la obtención masiva de filas](#_core_how_crecordset_supports_bulk_row_fetching).  
  
-   [Algunas consideraciones especiales al utilizar la obtención de filas masiva](#_core_special_considerations).  
  
-   [Cómo implementar el intercambio masivo de campos de registros](#_core_how_to_implement_bulk_record_field_exchange).  
  
##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a> ¿Cómo admite CRecordset la obtención masiva de filas  
 Antes de abrir el objeto de conjunto de registros, puede definir un tamaño de conjunto de filas con el `SetRowsetSize` función miembro. El tamaño del conjunto de filas especifica cuántos registros se deben recuperar durante una sola operación de obtención. Cuando se implementa la obtención masiva de filas, el tamaño del conjunto de filas predeterminado es 25. Si no se implementa la obtención masiva de filas, el tamaño del conjunto de filas permanece fijo en 1.  
  
 Después de haber inicializado el tamaño del conjunto de filas, llame a la [abiertos](../../mfc/reference/crecordset-class.md#open) función miembro. Debe especificar el `CRecordset::useMultiRowFetch` opción de la **dwOptions** parámetro para implementar la obtención masiva de filas. Adicionalmente, puede establecer la **CRecordset:: userAllocMultiRowBuffers** opción. El mecanismo de intercambio de campos de registros de forma masiva usa matrices para almacenar las múltiples filas de datos recuperados durante una búsqueda. Estos búferes de almacenamiento pueden asignarse automáticamente por el marco de trabajo o se puede asignar manualmente. Especificar el **CRecordset:: userAllocMultiRowBuffers** opción implica que se realizará la asignación.  
  
 En la tabla siguiente se enumera las funciones de miembro proporcionadas por `CRecordset` para admitir la obtención masiva de filas.  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Función virtual que controla los errores que se producen durante la captura.|  
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implementa el intercambio de campos de registros de forma masiva. Se llama automáticamente para las transferencias de varias filas de datos desde el origen de datos para el objeto de conjunto de registros.|  
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Recupera el valor actual para el tamaño del conjunto de filas.|  
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Indica cuántas filas se recuperaron realmente después de una operación de obtención determinada. En la mayoría de los casos, esto es el tamaño del conjunto de filas, a menos que se capturó un conjunto de filas incompleto.|  
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Devuelve un estado de captura para una fila determinada en un conjunto de filas.|  
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Actualiza los datos y el estado de una fila concreta dentro de un conjunto de filas.|  
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Mueve el cursor una fila determinada en un conjunto de filas.|  
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Función virtual que cambia el valor para el tamaño del conjunto de filas en el valor especificado.|  
  
##  <a name="_core_special_considerations"></a> Consideraciones especiales  
 Aunque la obtención masiva de filas es un aumento del rendimiento, algunas características funcionan de manera diferente. Antes de decidirse a implementar la obtención masiva de filas, considere lo siguiente:  
  
-   El marco de trabajo llama automáticamente a la `DoBulkFieldExchange` función de miembro para transferir datos desde el origen de datos para el objeto de conjunto de registros. Sin embargo, no se transfieren datos desde el conjunto de registros en el origen de datos. Llamar a la `AddNew`, **editar**, **eliminar**, o **actualización** resultados de las funciones de miembro en un error de aserción. Aunque `CRecordset` actualmente no proporciona un mecanismo para actualizar filas masivas de datos, puede escribir sus propias funciones mediante la función API de ODBC **SQLSetPos**. Para obtener más información acerca de **SQLSetPos**, consulte el *referencia del programador del SDK de ODBC* en la documentación de MSDN.  
  
-   Las funciones miembro `IsDeleted`, `IsFieldDirty`, `IsFieldNull`, `IsFieldNullable`, `SetFieldDirty`, y `SetFieldNull` no se puede utilizar en conjuntos de registros que implementan la obtención masiva de filas. Sin embargo, puede llamar a `GetRowStatus` en lugar de `IsDeleted`, y `GetODBCFieldInfo` en lugar de `IsFieldNullable`.  
  
-   El **mover** operaciones cambia de posición el conjunto de registros por conjunto de filas. Por ejemplo, supongamos que abre un conjunto de registros que tiene 100 registros con un tamaño inicial del conjunto de filas de 10. **Abra** recupera filas de 1 a 10, con el registro actual que se coloca en la fila 1. Una llamada a `MoveNext` captura el siguiente conjunto de filas, no la siguiente fila. Este conjunto de filas está formado por filas 11 a 20, con el registro actual situadas en la fila 11. Tenga en cuenta que `MoveNext` y **Move (1)** no son equivalentes cuando se implementa la obtención masiva de filas. **Mover (1)** captura el conjunto de filas que comienza en 1 fila desde el registro actual. En este ejemplo, una llamada a **Move (1)** después de llamar a **abiertos** captura el conjunto de filas que consta de las filas 2 a 11, con el registro actual en la fila 2. Para obtener más información, consulte el [mover](../../mfc/reference/crecordset-class.md#move) función miembro.  
  
-   A diferencia de intercambio de campos de registros, los asistentes no admiten el intercambio masivo de campos de registros. Esto significa que debe declarar manualmente los miembros de datos de campo y reemplazar manualmente `DoBulkFieldExchange` escribiendo llamadas a las funciones de RFX masivo. Para obtener más información, consulte [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md) en el *Class Library Reference*.  
  
##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a> Cómo implementar el intercambio masivo de campos de registro  
 Intercambio masivo de campos de registros, transfiere un conjunto de filas de datos del origen de datos para el objeto de conjunto de registros. Las funciones de RFX masivo usan matrices para almacenar estos datos, así como matrices para almacenar la longitud de cada elemento de datos en el conjunto de filas. En la definición de clase, debe definir a los miembros de datos de campo como punteros para tener acceso a las matrices de datos. Además, debe definir un conjunto de punteros para tener acceso a las matrices de longitudes. Los miembros de datos de parámetro no deben declararse como punteros; declarar miembros de datos de parámetro cuando se usa el intercambio masivo de campos de registros es igual que declararlos cuando mediante el intercambio de campos de registros. El código siguiente muestra un ejemplo sencillo:  
  
```  
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
  
 Puede asignar estos archivos de almacenamiento manualmente o que el marco de trabajo realice la asignación. Para asignar los búferes, debe especificar el **CRecordset:: userAllocMultiRowBuffers** opción de la **dwOptions** parámetro en el **abiertos** función miembro. Asegúrese de establecer los tamaños de las matrices de al menos igual que el tamaño del conjunto de filas. Si desea que el marco de trabajo realice la asignación, debe inicializar los punteros a **NULL.** Esto suele hacerse en el constructor del objeto de conjunto de registros:  
  
```  
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
  
 Por último, debe invalidar el `DoBulkFieldExchange` función miembro. Para los miembros de datos de campo, llame a las funciones de RFX masivo; los miembros de datos de parámetro, llame a las funciones de RFX. Si abre el conjunto de registros pasando una instrucción SQL o un procedimiento almacenado que **abiertos**, el orden en el que se realicen las llamadas a RFX masivo debe corresponder al orden de las columnas del conjunto de registros; de igual forma, el orden de lo RFX llama para parámetros deben corresponder al orden de los parámetros de la instrucción SQL o procedimiento almacenan.  
  
```  
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
>  Debe llamar a la **cerrar** función miembro antes de su derivada `CRecordset` clase sale del ámbito. Esto garantiza que se liberan cualquier memoria asignada por el marco de trabajo. Es conveniente llamar siempre explícitamente una práctica de programación **cerrar**, independientemente de si ha implementado la obtención masiva de filas.  
  
 Para obtener más información acerca del intercambio de campos de registros (RFX), vea [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Para obtener más información sobre el uso de parámetros, vea [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) y [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)   
 [CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)

