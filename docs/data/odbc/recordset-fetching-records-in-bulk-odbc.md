---
title: "Conjunto de registros: Obtener registros de forma masiva (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "intercambio masivo de campos de registros"
  - "funciones de RFX masivo"
  - "obtención de filas masiva"
  - "obtención de filas masiva, implementar"
  - "DoBulkFieldExchange (método)"
  - "obtención masiva de registros ODBC"
  - "conjuntos de registros ODBC, obtención de filas masiva"
  - "conjuntos de registros, obtención de filas masiva"
  - "RFX (ODBC), masivo"
  - "RFX (ODBC), obtención de filas masiva"
  - "conjuntos de filas, obtención de filas masiva"
ms.assetid: 20d10fe9-c58a-414a-b675-cdf9aa283e4f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Conjunto de registros: Obtener registros de forma masiva (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 La clase `CRecordset` proporciona compatibilidad con la obtención de filas masiva, lo cual significa que es posible recuperar múltiples registros al mismo tiempo durante una sola operación de obtención, en lugar de recuperar del origen de datos un registro cada vez.  Únicamente se puede implementar la obtención de filas masiva en una clase derivada de `CRecordset`.  El proceso de transferir datos desde el origen de datos al objeto de conjunto de registros se denomina intercambio masivo de campos de registro \(RFX masivo\).  Observe que, si no utiliza la obtención de filas masiva en una clase derivada de `CRecordset`, los datos se transfieren mediante intercambio de campos de registros \(RFX\).  Para obtener más información, vea [Intercambio de campos de registros \(RFX\)](../../data/odbc/record-field-exchange-rfx.md).  
  
 En este tema se explica:  
  
-   [Cómo admite CRecordset la obtención de filas masiva](#_core_how_crecordset_supports_bulk_row_fetching).  
  
-   [Consideraciones especiales al utilizar la obtención de filas masiva](#_core_special_considerations).  
  
-   [Cómo implementar el intercambio masivo de campos de registros](#_core_how_to_implement_bulk_record_field_exchange).  
  
##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a> Cómo admite CRecordset la obtención de filas masiva  
 Antes de abrir el objeto de conjunto de registros, se puede definir un tamaño de conjunto de filas mediante la función miembro `SetRowsetSize`.  El tamaño del conjunto de filas especifica cuántos registros deben recuperarse durante una sola operación de obtención.  Cuando se implementa la obtención masiva de filas, el tamaño del conjunto de filas predeterminado es de 25.  De lo contrario, el tamaño del conjunto de filas se mantiene fijo en 1.  
  
 Después de inicializar el tamaño del conjunto de filas, llame a la función miembro [Open](../Topic/CRecordset::Open.md).  Para implementar la obtención masiva de filas, se debe especificar aquí la opción `CRecordset::useMultiRowFetch` del parámetro **dwOptions**.  Adicionalmente, se puede establecer la opción **CRecordset::userAllocMultiRowBuffers**.  El mecanismo de intercambio masivo de campos de registros utiliza matrices para almacenar las múltiples filas de datos recuperadas durante la obtención.  Estos búferes de almacenamiento los puede asignar automáticamente el marco de trabajo o asignarse manualmente.  Especificar la opción **CRecordset::userAllocMultiRowBuffers** implica que se realizará la asignación manualmente.  
  
 La siguiente tabla enumera las funciones miembro proporcionadas por `CRecordset` para la compatibilidad con la obtención de filas masiva.  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[CheckRowsetError](../Topic/CRecordset::CheckRowsetError.md)|Función virtual que controla cualquier error producido durante la obtención.|  
|[DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md)|Implementa el intercambio masivo de campos de registros.  Se llama automáticamente para transferir múltiples filas de datos desde el origen de datos al objeto de conjunto de registros.|  
|[GetRowsetSize](../Topic/CRecordset::GetRowsetSize.md)|Recupera el valor actual del tamaño de conjunto de filas.|  
|[GetRowsFetched](../Topic/CRecordset::GetRowsFetched.md)|Informa de cuántas filas se recuperaron realmente después de una operación de obtención determinada.  En la mayoría de los casos, este valor representa el tamaño del conjunto de filas, a menos que se haya obtenido un conjunto de filas incompleto.|  
|[GetRowStatus](../Topic/CRecordset::GetRowStatus.md)|Devuelve el estado de obtención para una fila particular de un conjunto de filas.|  
|[RefreshRowset](../Topic/CRecordset::RefreshRowset.md)|Actualiza los datos y el estado de una fila particular dentro de un conjunto de filas.|  
|[SetRowsetCursorPosition](../Topic/CRecordset::SetRowsetCursorPosition.md)|Mueve el cursor a una fila particular de un conjunto de filas.|  
|[SetRowsetSize](../Topic/CRecordset::SetRowsetSize.md)|Función virtual que cambia el valor de tamaño del conjunto de filas por el valor especificado.|  
  
##  <a name="_core_special_considerations"></a> Consideraciones especiales  
 Si bien la obtención de filas masiva supone un aumento del rendimiento, algunas características funcionan de manera diferente.  Antes de decidirse a implementar la obtención de filas masiva, debe considerarse lo siguiente:  
  
-   El marco de trabajo llama automáticamente a la función miembro `DoBulkFieldExchange` para transferir datos desde el origen de datos al objeto del conjunto de registros.  Sin embargo, no se transfieren datos desde el conjunto de registros al origen de datos.  Llamar a las funciones miembro `AddNew`, **Edit**, **Delete** o **Update** dará como resultado un error de aserción.  Si bien la clase `CRecordset` no proporciona actualmente un mecanismo para actualizar filas masivas de datos, es posible crear sus propias funciones mediante la función de la API ODBC **SQLSetPos**.  Para obtener más información sobre **SQLSetPos**, vea la *Referencia del programador del SDK de ODBC* en la documentación de MSDN.  
  
-   Las funciones miembro `IsDeleted`, `IsFieldDirty`, `IsFieldNull`, `IsFieldNullable`, `SetFieldDirty` y `SetFieldNull` no pueden utilizarse en conjuntos de registros que implementen la obtención de filas masiva.  Sin embargo, se puede llamar a `GetRowStatus` en lugar de `IsDeleted`, y a `GetODBCFieldInfo` en lugar de `IsFieldNullable`.  
  
-   Las operaciones **Move** cambian de posición el conjunto de registros por conjunto de filas.  Por ejemplo, suponga que abre un conjunto de registros que contiene 100 registros con un tamaño inicial del conjunto de filas de 10.  **Open** obtiene las filas 1 a 10, con el registro activo en la fila 1.  Una llamada a `MoveNext` obtiene el siguiente conjunto de filas, pero no la siguiente fila.  Este conjunto de filas está formado por las filas 11 a 20, con el registro activo en la fila 11.  Tenga en cuenta que `MoveNext` y **Move\( 1 \)** no son equivalentes cuando se implementa la obtención masiva de filas.  **Move\( 1 \)** obtiene el conjunto de filas que comienza una fila a partir del registro actual.  En este ejemplo, al llamar a **Move\( 1 \)** después de llamar a **Open** se obtiene el conjunto de filas formado por las filas 2 a 11, con el registro actual colocado en la fila 2.  Para obtener más información, vea la función miembro [Move](../Topic/CRecordset::Move.md).  
  
-   A diferencia de lo que ocurre con el intercambio de campos de registros, los asistentes no admiten el intercambio de campos de registros masivo.  Es decir, se deben declarar manualmente los miembros de datos de campo, así como reemplazar manualmente la función `DoBulkFieldExchange` creando llamadas a las funciones de RFX masivo.  Para obtener más información, vea [Funciones del intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md) en la *Referencia de la biblioteca de clases*.  
  
##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a> Cómo implementar el Intercambio masivo de campos de registros  
 El intercambio masivo de campos de registro sólo transfiere los datos desde el origen de datos hasta el objeto de conjunto de registros.  Las funciones de RFX masivo usan matrices para almacenar estos datos, así como para almacenar la longitud de cada uno de los elementos de datos del conjunto de filas.  En la definición de clase, se deben definir los miembros de datos de campo como punteros para tener acceso a las matrices de datos.  Asimismo, se debe definir un conjunto de punteros para tener acceso a las matrices de longitudes.  No se debe declarar ningún miembro de datos de parámetro como puntero; declarar miembros de datos de parámetro cuando se utiliza el intercambio masivo de campos de registros es igual que declararlos cuando se utiliza el intercambio de campos de registros.  El siguiente código muestra un sencillo ejemplo:  
  
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
  
 Se pueden asignar estos archivos de almacenamiento manualmente o hacer que el marco de trabajo realice la asignación.  Para asignar los búferes personalmente, se debe especificar la opción **CRecordset::userAllocMultiRowBuffers** del parámetro **dwOptions** en la función miembro **Open**.  Asegúrese de establecer los tamaños de las matrices en un valor igual, al menos, al tamaño del conjunto de filas.  Si desea que el marco de trabajo realice la asignación, debe inicializar los punteros como **NULL**. Esto suele hacerse en el constructor del objeto de conjunto de registros.  
  
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
  
 Por último, se debe reemplazar la función miembro `DoBulkFieldExchange`.  Para los miembros de datos de campo, llame a las funciones de RFX masivo; para cualquier otro miembro de datos de parámetro, llame a las funciones RFX.  Si se abrió el conjunto de registros pasando una instrucción SQL o procedimiento almacenado a **Open**, el orden en que se realicen las llamadas a RFX masivo debe corresponder al orden de las columnas en el conjunto de registros. De igual forma, el orden de las llamadas a RFX para los parámetros debe corresponder al orden de los parámetros en la instrucción SQL o procedimiento almacenado.  
  
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
>  Se debe llamar a la función miembro **Close** para que la clase derivada de `CRecordset` quede fuera del ámbito.  De esta forma, se garantiza que se libere la memoria asignada por el marco de trabajo.  Es una buena práctica de programación llamar siempre de forma explícita a **Close**, sin importar si está o no implementada la obtención masiva de filas.  
  
 Para obtener más información acerca del intercambio de campos de registros \(RFX\), vea [Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  Para obtener más información sobre el uso de parámetros, vea [CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md) y [Conjunto de registros: Parametrizar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::m\_nFields](../Topic/CRecordset::m_nFields.md)   
 [CRecordset::m\_nParams](../Topic/CRecordset::m_nParams.md)