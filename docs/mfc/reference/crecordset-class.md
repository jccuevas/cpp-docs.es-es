---
title: "CRecordset Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRecordset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRecordset class"
  - "database records [C++]"
  - "conjuntos de registros ODBC [C++], CRecordset (objetos)"
  - "sets of records [C++]"
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRecordset Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un conjunto de registros seleccionados de un origen de datos.  
  
## Sintaxis  
  
```  
class CRecordset : public CObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecordset::CRecordset](../Topic/CRecordset::CRecordset.md)|Crea un objeto `CRecordset`.  La clase derivada debe proporcionar un constructor que llame a éste.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecordset::AddNew](../Topic/CRecordset::AddNew.md)|Se prepara para agregar un nuevo registro.  Llamada `Update` para completar la suma.|  
|[CRecordset::CanAppend](../Topic/CRecordset::CanAppend.md)|Devuelve cero si los nuevos registros se pueden agregar al conjunto de registros mediante la función miembro de `AddNew` .|  
|[CRecordset::CanBookmark](../Topic/CRecordset::CanBookmark.md)|Devuelve cero si el conjunto de registros admite marcadores.|  
|[CRecordset::Cancel](../Topic/CRecordset::Cancel.md)|Cancela una operación asincrónica o un proceso de segundo subproceso.|  
|[CRecordset::CancelUpdate](../Topic/CRecordset::CancelUpdate.md)|cancela cualquier actualización pendiente debido a una operación de `AddNew` o de `Edit` .|  
|[CRecordset::CanRestart](../Topic/CRecordset::CanRestart.md)|Devuelve cero si `Requery` se puede llamar a para ejecutar la consulta de conjunto de registros de nuevo.|  
|[CRecordset::CanScroll](../Topic/CRecordset::CanScroll.md)|Devuelve cero si puede desplazarse por los registros.|  
|[CRecordset::CanTransact](../Topic/CRecordset::CanTransact.md)|Devuelve cero si el origen de datos admite transacciones.|  
|[CRecordset::CanUpdate](../Topic/CRecordset::CanUpdate.md)|Devuelve cero si el conjunto de registros se puede actualizar \(puede agregar, actualizar, o eliminar registros\).|  
|[CRecordset::CheckRowsetError](../Topic/CRecordset::CheckRowsetError.md)|Denominado para controlar los errores generados durante la obtención de registro.|  
|[CRecordset::Close](../Topic/CRecordset::Close.md)|Cierre el conjunto de registros y ODBC **HSTMT** asociado.|  
|[CRecordset::Delete](../Topic/CRecordset::Delete.md)|Elimina el registro actual del conjunto de registros.  Debe explícitamente desplazarse a otro registro después de la eliminación.|  
|[CRecordset::DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md)|Denominado para cambiar filas masivas de datos desde el origen de datos al conjunto de registros.  Implementa el intercambio masivo de campos de registros \(RFX Masivo\).|  
|[CRecordset::DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md)|Denominado para intercambiar los datos \(en ambas direcciones\) entre los miembros de datos de campo de conjunto de registros y el registro correspondiente en el origen de datos.  Implementa el intercambio masivo de campos de registros.|  
|[CRecordset::Edit](../Topic/CRecordset::Edit.md)|Se prepara para los cambios del registro actual.  Llame a `Update` para finalizar la edición.|  
|[CRecordset::FlushResultSet](../Topic/CRecordset::FlushResultSet.md)|Devuelve cero si hay otro conjunto de resultados que se recupere, al usar una consulta predefinida.|  
|[CRecordset::GetBookmark](../Topic/CRecordset::GetBookmark.md)|Asigna el valor del marcador de un registro al objeto de parámetro.|  
|[CRecordset::GetDefaultConnect](../Topic/CRecordset::GetDefaultConnect.md)|denominado para obtener la cadena de conexión predeterminada.|  
|[CRecordset::GetDefaultSQL](../Topic/CRecordset::GetDefaultSQL.md)|Denominado para obtener la cadena SQL predeterminada para ejecutarse.|  
|[CRecordset::GetFieldValue](../Topic/CRecordset::GetFieldValue.md)|Devuelve el valor de un campo de un conjunto de registros.|  
|[CRecordset::GetODBCFieldCount](../Topic/CRecordset::GetODBCFieldCount.md)|Devuelve el número de campos del conjunto de registros.|  
|[CRecordset::GetODBCFieldInfo](../Topic/CRecordset::GetODBCFieldInfo.md)|Devuelve los tipos de información concreta sobre los campos de un conjunto de registros.|  
|[CRecordset::GetRecordCount](../Topic/CRecordset::GetRecordCount.md)|Devuelve el número de registros del conjunto de registros.|  
|[CRecordset::GetRowsetSize](../Topic/CRecordset::GetRowsetSize.md)|Devuelve el número de registros que desea en la recuperación durante una sola búsqueda.|  
|[CRecordset::GetRowsFetched](../Topic/CRecordset::GetRowsFetched.md)|devuelve el número de filas real recuperadas durante una búsqueda.|  
|[CRecordset::GetRowStatus](../Topic/CRecordset::GetRowStatus.md)|Devuelve el estado de fila después de una búsqueda.|  
|[CRecordset::GetSQL](../Topic/CRecordset::GetSQL.md)|Obtiene la cadena SQL utilizada para seleccionar registros del conjunto de registros.|  
|[CRecordset::GetStatus](../Topic/CRecordset::GetStatus.md)|Obtiene el estado del conjunto de registros: el índice del registro actual y si un recuento final de registros se ha obtenido.|  
|[CRecordset::GetTableName](../Topic/CRecordset::GetTableName.md)|Obtiene el nombre de la tabla en la que se basa el conjunto de registros.|  
|[CRecordset::IsBOF](../Topic/CRecordset::IsBOF.md)|Devuelve cero si se ha colocado el conjunto de registros antes del primer registro.  No hay ningún registro actual.|  
|[CRecordset::IsDeleted](../Topic/CRecordset::IsDeleted.md)|Devuelve cero si colocan el conjunto de registros en un registro eliminado.|  
|[CRecordset::IsEOF](../Topic/CRecordset::IsEOF.md)|Devuelve cero si se ha colocado el conjunto de registros después del último registro.  No hay ningún registro actual.|  
|[CRecordset::IsFieldDirty](../Topic/CRecordset::IsFieldDirty.md)|Devuelve cero si el campo especificado en el registro actual se ha cambiado.|  
|[CRecordset::IsFieldNull](../Topic/CRecordset::IsFieldNull.md)|Devuelve cero si el campo especificado en el registro actual es null \(no tiene ningún valor.|  
|[CRecordset::IsFieldNullable](../Topic/CRecordset::IsFieldNullable.md)|Devuelve cero si el campo especificado en el registro actual se puede establecer en null \(no tener ningún valor\).|  
|[CRecordset::IsOpen](../Topic/CRecordset::IsOpen.md)|Devuelve cero si `Open` se ha llamado previamente.|  
|[CRecordset::Move](../Topic/CRecordset::Move.md)|Coloca el conjunto de registros en un número de registros especificado del registro actual en cualquier dirección.|  
|[CRecordset::MoveFirst](../Topic/CRecordset::MoveFirst.md)|Coloca el registro actual respecto al primer registro del conjunto de registros.  prueba para `IsBOF` primero.|  
|[CRecordset::MoveLast](../Topic/CRecordset::MoveLast.md)|Coloca el registro actual respecto al último registro o respecto al último conjunto de filas.  prueba para `IsEOF` primero.|  
|[CRecordset::MoveNext](../Topic/CRecordset::MoveNext.md)|Coloca el registro actual respecto al registro siguiente o respecto al siguiente conjunto de filas.  prueba para `IsEOF` primero.|  
|[CRecordset::MovePrev](../Topic/CRecordset::MovePrev.md)|Coloca el registro actual respecto al registro anterior o respecto al conjunto de filas anterior.  prueba para `IsBOF` primero.|  
|[CRecordset::OnSetOptions](../Topic/CRecordset::OnSetOptions.md)|Denominado para establecer opciones \(utilizadas en la selección\) para la instrucción especificada de ODBC.|  
|[CRecordset::OnSetUpdateOptions](../Topic/CRecordset::OnSetUpdateOptions.md)|Denominado para establecer opciones \(utilizadas en actualización\) para la instrucción especificada de ODBC.|  
|[CRecordset::Open](../Topic/CRecordset::Open.md)|Abra el conjunto de registros recuperando la tabla o realizando la consulta que el conjunto de registros representa.|  
|[CRecordset::RefreshRowset](../Topic/CRecordset::RefreshRowset.md)|actualiza los datos y el estado de las filas especificadas.|  
|[CRecordset::Requery](../Topic/CRecordset::Requery.md)|Ejecuta la consulta de conjunto de registros de nuevo para actualizar los registros seleccionados.|  
|[CRecordset::SetAbsolutePosition](../Topic/CRecordset::SetAbsolutePosition.md)|Coloca el conjunto de registros respecto al registro correspondiente al número de registro especificado.|  
|[CRecordset::SetBookmark](../Topic/CRecordset::SetBookmark.md)|Coloca el conjunto de registros respecto al registro especificado por el marcador.|  
|[CRecordset::SetFieldDirty](../Topic/CRecordset::SetFieldDirty.md)|Marca el campo especificado en el registro actual como cambiado.|  
|[CRecordset::SetFieldNull](../Topic/CRecordset::SetFieldNull.md)|Establece el valor del campo especificado en el registro actual en null \(no tener ningún valor\).|  
|[CRecordset::SetLockingMode](../Topic/CRecordset::SetLockingMode.md)|Establece bloquear “optimista” del modo de bloqueo \(valor predeterminado\) o bloquear “pesimista”.  determina cómo los registros están bloqueados para las actualizaciones.|  
|[CRecordset::SetParamNull](../Topic/CRecordset::SetParamNull.md)|Establece el parámetro especificado en null \(no tener ningún valor\).|  
|[CRecordset::SetRowsetCursorPosition](../Topic/CRecordset::SetRowsetCursorPosition.md)|Coloca el cursor respecto a la fila especificada dentro del conjunto de filas.|  
|[CRecordset::SetRowsetSize](../Topic/CRecordset::SetRowsetSize.md)|Especifica el número de registros que desea en la recuperación durante una búsqueda.|  
|[CRecordset::Update](../Topic/CRecordset::Update.md)|Completa una operación de `AddNew` o de `Edit` guardar nuevos o editar datos en el origen de datos.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecordset::m\_hstmt](../Topic/CRecordset::m_hstmt.md)|contiene el identificador de instrucciones de ODBC para el conjunto de registros.  Escriba `HSTMT`.|  
|[CRecordset::m\_nFields](../Topic/CRecordset::m_nFields.md)|Contiene el número de miembros de datos de campo del conjunto de registros.  Escriba `UINT`.|  
|[CRecordset::m\_nParams](../Topic/CRecordset::m_nParams.md)|Contiene el número de miembros de datos de parámetro en el conjunto de registros.  Escriba `UINT`.|  
|[CRecordset::m\_pDatabase](../Topic/CRecordset::m_pDatabase.md)|Contiene un puntero al objeto de `CDatabase` a través del que el conjunto de registros está conectado con un origen de datos.|  
|[CRecordset::m\_strFilter](../Topic/CRecordset::m_strFilter.md)|Contiene `CString` que especifica una cláusula \(SQL\) de `WHERE` de lenguaje de consulta estructurado.  Se utiliza como filtro para seleccionar sólo los registros que cumplen ciertos criterios.|  
|[CRecordset::m\_strSort](../Topic/CRecordset::m_strSort.md)|Contiene `CString` que especifica una cláusula SQL `ORDER BY` .  Utilizado para controlar cómo se ordenan los registros.|  
  
## Comentarios  
 Conocido como “conjuntos de registros”, los objetos de `CRecordset` se utilizan normalmente en dos formas: conjuntos de registros dinámicos e instantáneas.  Un conjunto permanece sincronizado con las actualizaciones de datos creadas por otros usuarios.  una instantánea es una vista estática de los datos.  Cada formulario representa un conjunto de registros corregidos cuando abre el conjunto de registros, pero cuando se desplace a un registro en un conjunto, refleja los cambios realizados posteriormente en el registro, por otros usuarios o por otros conjuntos de registros de la aplicación.  
  
> [!NOTE]
>  Si trabaja con las clases \(DAO\) de Objetos de acceso a datos en lugar de las clases de ODBC, utilice la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) en su lugar.  Para obtener más información, vea el artículo [información general: programación de la base de datos](../../data/data-access-programming-mfc-atl.md).  
  
 Para trabajar con cualquier tipo de conjunto de registros, se deriva normalmente una clase específica de la aplicación de conjunto de registros `CRecordset`.  Se seleccionan los registros de un origen de datos, y a continuación:  
  
-   Desplácese por los registros.  
  
-   Actualizar registros y especifique un modo de bloqueo.  
  
-   Filtre el conjunto de registros para restringir qué registros se seleccionan de los disponibles en el origen de datos.  
  
-   Ordenar el conjunto de registros.  
  
-   Parametrizar el conjunto de registros para personalizar la selección con información no conocida hasta el tiempo de ejecución.  
  
 Para utilizar la clase, abra una base de datos y crear un objeto de conjunto de registros, pasando al constructor un puntero al objeto de `CDatabase` .  Llamar a continuación a la función miembro de **Abrir** de conjunto de registros, donde puede especificar si el objeto es de tipo dinámico o una instantánea.  La llamada **Abrir** selecciona los datos del origen de datos.  Después de abrir el objeto de conjunto de registros, utilice las funciones y miembros de datos de miembro para desplazarse por los registros y para operarlos en.  Las operaciones disponibles dependen de si el objeto es de tipo dinámico o una instantánea, si es actualizable o de sólo lectura \(éste depende de la capacidad del origen de datos de ODBC\), y si está implementada la obtención masiva de filas.  Para actualizar registros que hayan sido modificados o haber sido agregados desde la llamada de **Abrir** , llama a la función miembro de **Requery** del objeto.  Llame a la función miembro de **Cerrar** de objeto y destruya el objeto cuando acaba con él.  
  
 En una clase derivada de `CRecordset` , el intercambio masivo de campos de registro o el intercambio masivo de campos de registros \(RFX Masivo\) se utiliza para admitir la lectura y actualización de campos de registros.  
  
 Para obtener más información sobre conjuntos de registros y el intercambio de campos, vea los artículos [información general: programación de la base de datos](../../data/data-access-programming-mfc-atl.md), [conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md), [conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md), y [Intercambio de campos de registros](../../data/odbc/record-field-exchange-rfx.md).  Para un enfoque en conjuntos de registros dinámicos e instantáneas, vea los artículos [Dinámico](../../data/odbc/dynaset.md) y [Instantánea](../../data/odbc/snapshot.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CRecordset`  
  
## Requisitos  
 **encabezado:** afxdb.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CRecordView Class](../../mfc/reference/crecordview-class.md)