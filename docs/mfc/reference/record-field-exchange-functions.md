---
title: Funciones de intercambio de campos de registro | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AFXDB/RFX_Binary
- AFXDB/RFX_Bool
- AFXDB/RFX_Byte
- AFXDB/RFX_Date
- AFXDB/RFX_Double
- AFXDB/RFX_Int
- AFXDB/RFX_Long
- AFXDB/RFX_LongBinary
- AFXDB/RFX_Single
- AFXDB/RFX_Text
- AFXDB/RFX_Binary_Bulk
- AFXDB/RFX_Bool_Bulk
- AFXDB/RFX_Byte_Bulk
- AFXDB/RFX_Date_Bulk
- AFXDB/RFX_Double_Bulk
- AFXDB/RFX_Int_Bulk
- AFXDB/RFX_Long_Bulk
- AFXDB/RFX_Single_Bulk
- AFXDB/RFX_Text_Bulk
- AFXDB/DFX_Binary
- AFXDB/DFX_Bool
- AFXDB/DFX_Byte
- AFXDB/DFX_Currency
- AFXDB/DFX_DateTime
- AFXDB/DFX_Double
- AFXDB/DFX_Long
- AFXDB/DFX_LongBinary
- AFXDB/DFX_Short
- AFXDB/DFX_Single
- AFXDB/DFX_Text
dev_langs: C++
helpviewer_keywords:
- DAO (Data Access Objects), record field exchange (DFX)
- ODBC, bulk RFX data exchange functions [MFC]
- RFX (record field exchange), ODBC classes
- DFX (DAO record field exchange), data exchange functions [MFC]
- DFX functions [MFC]
- bulk RFX functions [MFC]
- DFX (DAO record field exchange)
- RFX (record field exchange), DAO classes
- ODBC, RFX
- RFX (record field exchange), data exchange functions [MFC]
- RFX (record field exchange)
ms.assetid: 6e4c5c1c-acb7-4c18-bf51-bf7959a696cd
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94491a2df64017ea381377af8518414e80130d6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="record-field-exchange-functions"></a>Funciones de intercambio de campos de registros
Este tema enumeran el intercambio de campos de registro (RFX, RFX masivo y DFX) funciones que se usan para automatizar la transferencia de datos entre un objeto de conjunto de registros y su origen de datos y realizar otras operaciones en los datos.  
  
 Si está usando las clases basadas en ODBC y ha implementado la obtención masiva de filas, debe reemplazar manualmente la función miembro `DoBulkFieldExchange` de `CRecordset` por las funciones de RFX masivo para cada miembro de datos correspondiente a una columna de origen de datos.  
  
 Si no ha implementado la obtención masiva de filas en las clases basadas en ODBC, o si está usando las clases basadas en DAO, entonces ClassWizard reemplazará la función miembro `DoFieldExchange` de `CRecordset` o `CDaoRecordset` llamando a las funciones de RFX (para las clases ODBC) o a las funciones de DFX (para las clases DAO) para cada miembro de datos de campos del conjunto de registros.  
  
 Las funciones de intercambio de campos de registros transfieren datos cada vez que el marco de trabajo llama a `DoFieldExchange` o `DoBulkFieldExchange`. Cada función transfiere un tipo de datos específico.  
  
 Para obtener más información sobre cómo se usan estas funciones, vea los artículos [Intercambio de campos de registros: Funcionamiento de RFX (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Para las columnas de datos que enlaza dinámicamente, también puede llamar a las funciones de RFX o DFX como se explica en los artículos [Conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). Además, puede escribir sus propias rutinas personalizadas de RFX o DFX, como se explica en la nota técnica [43](../../mfc/tn043-rfx-routines.md) (para ODBC) y en la nota técnica [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (para DAO).  
  
 Para obtener un ejemplo de RFX y RFX masivo funciona tal y como aparecen en la `DoFieldExchange` y `DoBulkFieldExchange` funciones, vea [RFX_Text](#rfx_text) y rfx_text_bulk de # [RFX_Text_Bulk]). Las funciones de DFX son muy similares a las funciones de RFX.  
  
### <a name="rfx-functions-odbc"></a>Funciones de RFX (ODBC)  
  
|||  
|-|-|  
|[RFX_Binary](#rfx_binary)|Transfiere matrices de bytes del tipo [CByteArray](cbytearray-class.md).|  
|[RFX_Bool](#rfx_bool)|Transfiere datos Boolean.|  
|[RFX_Byte](#rfx_byte)|Transfiere un solo byte de datos.|  
|[RFX_Date](#rfx_date)|Transfiere los datos de fecha y hora con [CTime](../../atl-mfc-shared/reference/ctime-class.md) o **TIMESTAMP_STRUCT**.|  
|[RFX_Double](#rfx_double)|Transfiere datos Float de doble precisión.|  
|[RFX_Int](#rfx_int)|Transfiere datos enteros.|  
|[RFX_Long](#rfx_long)|Transfiere datos enteros largos.|  
|[RFX_LongBinary](#rfx_longbinary)|Transfiere datos de objetos binarios grandes (BLOB) con un objeto de la clase [CLongBinary](clongbinary-class.md) .|  
|[RFX_Single](#rfx_single)|Transfiere datos Float.|  
|[RFX_Text](#rfx_text)|Transfiere datos String.|  
  
### <a name="bulk-rfx-functions-odbc"></a>Funciones de RFX masivo (ODBC)  
  
|||  
|-|-|  
|[RFX_Binary_Bulk](#rfx_binary_bulk)|Transfiere matrices de datos Byte.|  
|[RFX_Bool_Bulk](#rfx_bool_bulk)|Transfiere matrices de datos Boolean.|  
|[RFX_Byte_Bulk](#rfx_byte_bulk)|Transfiere matrices de un solo byte.|  
|[RFX_Date_Bulk](#rfx_date_bulk)|Transfiere matrices de datos del tipo **TIMESTAMP_STRUCT**.|  
|[RFX_Double_Bulk](#rfx_double_bulk)|Transfiere matrices de datos de punto flotante de doble precisión.|  
|[RFX_Int_Bulk](#rfx_int_bulk)|Transfiere matrices de datos enteros.|  
|[RFX_Long_Bulk](#rfx_long_bulk)|Transfiere matrices de datos enteros largos.|  
|[RFX_Single_Bulk](#rfx_single_bulk)|Transfiere matrices de datos de punto flotante.|  
|[RFX_Text_Bulk](#rfx_text_bulk)|Transfiere matrices de datos de tipo **LPSTR**.|  
  
### <a name="dfx-functions-dao"></a>Funciones de DFX (DAO)  
  
|||
|-|-|  
|[DFX_Binary](#dfx_binary)|Transfiere matrices de bytes del tipo [CByteArray](cbytearray-class.md).|  
|[DFX_Bool](#dfx_bool)|Transfiere datos Boolean.|  
|[DFX_Byte](#dfx_byte)|Transfiere un solo byte de datos.|  
|[DFX_Currency](#dfx_currency)|Transfiere datos de divisa del tipo [COleCurrency](colecurrency-class.md).|  
|[DFX_DateTime](#dfx_datetime)|Transfiere datos de fecha y hora del tipo [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md).|  
|[DFX_Double](#dfx_double)|Transfiere datos Float de doble precisión.|  
|[DFX_Long](#dfx_long)|Transfiere datos enteros largos.|  
|[DFX_LongBinary](#dfx_longbinary)|Transfiere datos de objetos binarios grandes (BLOB) con un objeto de la clase `CLongBinary` . Para DAO, se recomienda que use [DFX_Binary](#dfx_binary) en su lugar.|  
|[DFX_Short](#dfx_short)|Transfiere datos enteros cortos.|  
|[DFX_Single](#dfx_single)|Transfiere datos Float.|  
|[DFX_Text](#dfx_text)|Transfiere datos String.|  

 =============================================

## <a name="rfx_binary"></a>  RFX_Binary
Transfiere matrices de bytes entre los miembros de datos de campo de un `CRecordset` objeto y las columnas de un registro en el origen de datos de tipo ODBC **SQL_BINARY**, **SQL_VARBINARY**, o **SQL_ LONGVARBINARY**.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Binary(  
   CFieldExchange* pFX,  
   const char* szName,  
   CByteArray& value,  
   int nMaxLength = 255);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CFieldExchange](cfieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información acerca de las operaciones un `CFieldExchange` objeto puede especificar, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo [CByteArray](cbytearray-class.md), se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 `nMaxLength`  
 La longitud máxima permitida de la cadena o matriz que se va a transferir. El valor predeterminado de `nMaxLength` es 255. Los valores válidos son de 1 a `INT_MAX`. El marco de trabajo asigna esta cantidad de espacio para los datos. Para obtener el mejor rendimiento, pase un valor lo suficientemente grande como para alojar el elemento de datos más grande que espera.  
  
### <a name="remarks"></a>Comentarios  
 Los datos del origen de datos de estos tipos se asignan a y desde el tipo `CByteArray` en el conjunto de registros.  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="rfx_bool"></a>  RFX_Bool
Transfiere datos Boolean entre los miembros de datos de campo de un `CRecordset` objeto y las columnas de un registro en el origen de datos de tipo ODBC **SQL_BIT**.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Bool(  
   CFieldExchange* pFX,  
   const char* szName,  
   BOOL& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CFieldExchange](cfieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información acerca de las operaciones un `CFieldExchange` objeto puede especificar, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo **BOOL**, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="rfx_byte"></a>  RFX_Byte
Las transferencias único bytes entre los miembros de datos de campo de un `CRecordset` objeto y las columnas de un registro en el origen de datos de tipo ODBC **SQL_TINYINT**.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Byte(  
   CFieldExchange* pFX,  
   const char* szName,  
   BYTE& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CFieldExchange](cfieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información acerca de las operaciones un `CFieldExchange` objeto puede especificar, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo **bytes**, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="rfx_date"></a>  RFX_Date
Las transferencias de `CTime` o **TIMESTAMP_STRUCT** datos entre los miembros de datos de campo de un `CRecordset` objeto y las columnas de un registro en el origen de datos de tipo ODBC **SQL_DATE**, **SQL_TIME**, o **SQL_TIMESTAMP**.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Date(  
   CFieldExchange* pFX,  
   const char* szName,  
   CTime& value);
  
void RFX_Date(  
   CFieldExchange* pFX,  
   const char* szName,  
   TIMESTAMP_STRUCT& value);
  
void RFX_Date(  
   CFieldExchange* pFX,  
   const char* szName,  
   COleDateTime& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CFieldExchange](cfieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información acerca de las operaciones un `CFieldExchange` objeto puede especificar, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado; valor que se transferirán. Las distintas versiones de la función realizar diferentes tipos de datos de valor:  
  
 La primera versión de la función toma una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto. Para una transferencia de conjunto de registros al origen de datos, este valor se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 La segunda versión de la función toma una referencia a un **TIMESTAMP_STRUCT** estructura. Debe configurar esta estructura usted mismo antes de la llamada. Ningún intercambio de datos de cuadros de diálogo (DDX) admiten ni código asistente son compatibles con esta versión. La tercera versión de la función funciona de forma similar a la primera versión salvo por que utiliza una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `CTime` versión de la función impone la sobrecarga que supone algún procesamiento intermedio y tiene una duración limitada. Si encuentra alguno de estos factores muy restrictivo, use la segunda versión de la función. Pero tenga en cuenta su falta de Asistente para código y soporte técnico DDX y el requisito de que se establezca la estructura.  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="rfx_double"></a>  RFX_Double
Las transferencias de **flotante doble** datos entre los miembros de datos de campo de un `CRecordset` objeto y las columnas de un registro en el origen de datos de tipo ODBC **SQL_DOUBLE**.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Double(  
   CFieldExchange* pFX,  
   const char* szName,  
   double& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CFieldExchange](cfieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información acerca de las operaciones un `CFieldExchange` objeto puede especificar, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo **doble**, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="rfx_int"></a>  RFX_Int
Transfiere datos enteros entre los miembros de datos de campo de un `CRecordset` objeto y las columnas de un registro en el origen de datos de tipo ODBC **SQL_SMALLINT**.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Int(  
   CFieldExchange* pFX,  
   const char* szName,  
   int& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CFieldExchange](cfieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información acerca de las operaciones un `CFieldExchange` objeto puede especificar, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo `int`, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="rfx_long"></a>  RFX_Long
Transfiere datos enteros largos entre los miembros de datos de campo de un `CRecordset` objeto y las columnas de un registro en el origen de datos de tipo ODBC **SQL_INTEGER**.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Long(  
   CFieldExchange* pFX,  
   const char* szName,  
   LONG&   
value );  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CFieldExchange](cfieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información acerca de las operaciones un `CFieldExchange` objeto puede especificar, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo **largo**, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  
## <a name="rfx_longbinary"></a>  RFX_LongBinary
Transfiere los datos de objeto binario grande (BLOB) mediante la clase [CLongBinary](clongbinary-class.md) entre los miembros de datos de campo de un `CRecordset` objeto y las columnas de un registro en el origen de datos de tipo ODBC **SQL_LONGVARBINARY**o **SQL_LONGVARCHAR**.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_LongBinary(  
   CFieldExchange* pFX,  
   const char* szName,  
   CLongBinary& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CFieldExchange](cfieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información acerca de las operaciones un `CFieldExchange` objeto puede especificar, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo `CLongBinary`, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="rfx_single"></a>  RFX_Single
Transferencias de datos de punto flotante entre los miembros de datos de campo de un `CRecordset` objeto y las columnas de un registro en el origen de datos de tipo ODBC **SQL_REAL**.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Single(  
   CFieldExchange* pFX,  
   const char* szName,  
   float& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CFieldExchange](cfieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información acerca de las operaciones un `CFieldExchange` objeto puede especificar, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo **float**, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  

## <a name="rfx_text"></a>  RFX_Text
Las transferencias de `CString` datos entre los miembros de datos de campo de un `CRecordset` objeto y las columnas de un registro en el origen de datos de tipo ODBC **SQL_LONGVARCHAR**, **SQL_CHAR**, **SQL_ VARCHAR**, **SQL_DECIMAL**, o **SQL_NUMERIC**.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Text(  
   CFieldExchange* pFX,  
   const char* szName,  
   CString& value,  
   int nMaxLength = 255,  
   int nColumnType = SQL_VARCHAR,  
   short nScale = 0);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase `CFieldExchange`. Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información acerca de las operaciones un `CFieldExchange` objeto puede especificar, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo `CString`, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 `nMaxLength`  
 La longitud máxima permitida de la cadena o matriz que se va a transferir. El valor predeterminado de `nMaxLength` es 255. Los valores válidos son de 1 a `INT_MAX`). El marco de trabajo asigna esta cantidad de espacio para los datos. Para obtener el mejor rendimiento, pase un valor lo suficientemente grande como para alojar el elemento de datos más grande que espera.  
  
 *nColumnType*  
 Se utiliza principalmente para los parámetros. Un entero que indica el tipo de datos del parámetro. El tipo es un tipo de datos ODBC del formulario **SQL_XXX**.  
  
 `nScale`  
 Especifica la escala de valores de tipo ODBC **SQL_DECIMAL** o **SQL_NUMERIC**. `nScale`sólo es útil al establecer los valores de parámetro. Para obtener más información, vea el tema "Precisión, escala, longitud y tamaño de presentación" en el apéndice D de la *referencia del programador del SDK de ODBC*.  
  
### <a name="remarks"></a>Comentarios  
 Los datos del origen de datos de todos estos tipos se asignan a y desde `CString` en el conjunto de registros.  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra varias llamadas a `RFX_Text`. Observe también las dos llamadas a `CFieldExchange::SetFieldType`. Para los parámetros se debe escribir la llamada a `SetFieldType` y su llamada RFX. La llamada de la columna de salida y sus llamadas RFX asociados se escriben normalmente mediante un asistente de código.  
  
```cpp  
void CCustomer::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   // Macros such as RFX_Text() and RFX_Int() are dependent on the
   // type of the member variable, not the type of the field in the database.
   // ODBC will try to automatically convert the column value to the requested type
   RFX_Long(pFX, _T("[CustomerID]"), m_CustomerID);
   RFX_Text(pFX, _T("[ContactFirstName]"), m_ContactFirstName);
   RFX_Text(pFX, _T("[PostalCode]"), m_PostalCode);
   RFX_Text(pFX, _T("[L_Name]"), m_L_Name);
   RFX_Long(pFX, _T("[BillingID]"), m_BillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  


## <a name="rfx_binary_bulk"></a>  RFX_Binary_Bulk
Transfiere varias filas de datos de bytes de una columna de un origen de datos ODBC a una matriz correspondiente en un `CRecordset`-objeto derivado.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Binary_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE** prgByteVals,  
   long** prgLengths,  
   int nMaxLength);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un [CFieldExchange](cfieldexchange-class.md) objeto. Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 `prgByteVals`  
 Un puntero a una matriz de **bytes** valores. Esta matriz almacenará los datos para ser transferidos desde el origen de datos para el conjunto de registros.  
  
 `prgLengths`  
 Un puntero a una matriz de enteros largos. Esta matriz almacenará la longitud en bytes de cada valor de la matriz señalada por `prgByteVals`. Tenga en cuenta que el valor **SQL_NULL_DATA** se almacenarán si el correspondiente elemento de datos contiene un valor Null. Para obtener más información, vea la función API de ODBC **SQLBindCol** en el *referencia del programador del SDK de ODBC*.  
  
 `nMaxLength`  
 El máximo permitido de longitud de los valores almacenados en la matriz señalada por `prgByteVals`. Para asegurarse de que los datos no se truncarán, pase un valor lo suficientemente grande como para alojar el elemento de datos más grande, se espera.  
  
### <a name="remarks"></a>Comentarios  
 La columna de origen de datos puede tener un tipo ODBC de **SQL_BINARY**, **SQL_VARBINARY**, o **SQL_LONGVARBINARY**. El conjunto de registros debe definir un miembro de datos de campo de tipo puntero a **bytes**.  
  
 Si inicializa `prgByteVals` y `prgLengths` a **NULL**, a continuación, las matrices que señalan se asignarán automáticamente, con los tamaños iguales al tamaño del conjunto de filas.  
  
> [!NOTE]
>  Intercambio masivo de campos de registros solo transfiere datos desde el origen de datos para el objeto de conjunto de registros. Para hacer que el conjunto de registros actualizables, debe usar la función de la API de ODBC **SQLSetPos**.  
  
 Para obtener más información, vea los artículos [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) y [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text_Bulk](#rfx_text_bulk).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="rfx_bool_bulk"></a>  RFX_Bool_Bulk
Transfiere varias filas de datos booleanos de una columna de un origen de datos ODBC a una matriz correspondiente en un `CRecordset`-objeto derivado.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Bool_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BOOL** prgBoolVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un [CFieldExchange](cfieldexchange-class.md) objeto. Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 `prgBoolVals`  
 Un puntero a una matriz de **BOOL** valores. Esta matriz almacenará los datos para ser transferidos desde el origen de datos para el conjunto de registros.  
  
 `prgLengths`  
 Un puntero a una matriz de enteros largos. Esta matriz almacenará la longitud en bytes de cada valor de la matriz señalada por `prgBoolVals`. Tenga en cuenta que el valor **SQL_NULL_DATA** se almacenarán si el correspondiente elemento de datos contiene un valor Null. Para obtener más información, vea la función API de ODBC **SQLBindCol** en el *referencia del programador del SDK de ODBC*.  
  
### <a name="remarks"></a>Comentarios  
 La columna de origen de datos debe tener un tipo ODBC de **SQL_BIT**. El conjunto de registros debe definir un miembro de datos de campo de tipo puntero a **BOOL**.  
  
 Si inicializa `prgBoolVals` y `prgLengths` a **NULL**, a continuación, las matrices que señalan se asignarán automáticamente, con los tamaños iguales al tamaño del conjunto de filas.  
  
> [!NOTE]
>  Intercambio masivo de campos de registros solo transfiere datos desde el origen de datos para el objeto de conjunto de registros. Para hacer que el conjunto de registros actualizables, debe usar la función de API de ODBC **SQLSetPos**.  
  
 Para obtener más información, vea los artículos [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) y [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text_Bulk](#rfx_text_bulk).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="rfx_byte_bulk"></a>  RFX_Byte_Bulk
Transfiere varias filas de un solo byte de una columna de un origen de datos ODBC a una matriz correspondiente en un `CRecordset`-objeto derivado.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Byte_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE** prgByteVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un [CFieldExchange](cfieldexchange-class.md) objeto. Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 `prgByteVals`  
 Un puntero a una matriz de **bytes** valores. Esta matriz almacenará los datos para ser transferidos desde el origen de datos para el conjunto de registros.  
  
 `prgLengths`  
 Un puntero a una matriz de enteros largos. Esta matriz almacenará la longitud en bytes de cada valor de la matriz señalada por `prgByteVals`. Tenga en cuenta que el valor **SQL_NULL_DATA** se almacenarán si el correspondiente elemento de datos contiene un valor Null. Para obtener más información, vea la función API de ODBC **SQLBindCol** en el *referencia del programador del SDK de ODBC*.  
  
### <a name="remarks"></a>Comentarios  
 La columna de origen de datos debe tener un tipo ODBC de **SQL_TINYINT**. El conjunto de registros debe definir un miembro de datos de campo de tipo puntero a **bytes**.  
  
 Si inicializa `prgByteVals` y `prgLengths` a **NULL**, a continuación, las matrices que señalan se asignarán automáticamente, con los tamaños iguales al tamaño del conjunto de filas.  
  
> [!NOTE]
>  Intercambio masivo de campos de registros solo transfiere datos desde el origen de datos para el objeto de conjunto de registros. Para hacer que el conjunto de registros actualizables, debe usar la función de API de ODBC **SQLSetPos**.  
  
 Para obtener más información, vea los artículos [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) y [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text_Bulk](#rfx_text_bulk).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  
## <a name="rfx_date_bulk"></a>  RFX_Date_Bulk
Transfiere varias filas de **TIMESTAMP_STRUCT** datos de una columna de un origen de datos ODBC a una matriz correspondiente en un `CRecordset`-objeto derivado.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Date_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   TIMESTAMP_STRUCT** prgTSVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un [CFieldExchange](cfieldexchange-class.md) objeto. Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 `prgTSVals`  
 Un puntero a una matriz de **TIMESTAMP_STRUCT** valores. Esta matriz almacenará los datos para ser transferidos desde el origen de datos para el conjunto de registros. Para obtener más información sobre la **TIMESTAMP_STRUCT** tipo de datos, vea el tema "Tipos de datos de C" en el apéndice D de la *referencia del programador del SDK de ODBC*.  
  
 `prgLengths`  
 Un puntero a una matriz de enteros largos. Esta matriz almacenará la longitud en bytes de cada valor de la matriz señalada por `prgTSVals`. Tenga en cuenta que el valor **SQL_NULL_DATA** se almacenarán si el correspondiente elemento de datos contiene un valor Null. Para obtener más información, vea la función API de ODBC **SQLBindCol** en el *referencia del programador del SDK de ODBC*.  
  
### <a name="remarks"></a>Comentarios  
 La columna de origen de datos puede tener un tipo ODBC de **SQL_DATE**, **SQL_TIME**, o **SQL_TIMESTAMP**. El conjunto de registros debe definir un miembro de datos de campo de tipo puntero a **TIMESTAMP_STRUCT**.  
  
 Si inicializa `prgTSVals` y `prgLengths` a **NULL**, a continuación, las matrices que señalan se asignarán automáticamente, con los tamaños iguales al tamaño del conjunto de filas.  
  
> [!NOTE]
>  Intercambio masivo de campos de registros solo transfiere datos desde el origen de datos para el objeto de conjunto de registros. Para hacer que el conjunto de registros actualizables, debe usar la función de API de ODBC **SQLSetPos**.  
  
 Para obtener más información, vea los artículos [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) y [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text_Bulk](#rfx_text_bulk).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="rfx_double_bulk"></a>  RFX_Double_Bulk
Transfiere varias filas de datos punto flotante de doble precisión de una columna de un origen de datos ODBC a una matriz correspondiente en un `CRecordset`-objeto derivado.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Double_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   double** prgDblVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un [CFieldExchange](cfieldexchange-class.md) objeto. Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 `prgDblVals`  
 Un puntero a una matriz de **doble** valores. Esta matriz almacenará los datos para ser transferidos desde el origen de datos para el conjunto de registros.  
  
 `prgLengths`  
 Un puntero a una matriz de enteros largos. Esta matriz almacenará la longitud en bytes de cada valor de la matriz señalada por `prgDblVals`. Tenga en cuenta que el valor **SQL_NULL_DATA** se almacenarán si el correspondiente elemento de datos contiene un valor Null. Para obtener más información, vea la función API de ODBC **SQLBindCol** en el *referencia del programador del SDK de ODBC*.  
  
### <a name="remarks"></a>Comentarios  
 La columna de origen de datos debe tener un tipo ODBC de **SQL_DOUBLE**. El conjunto de registros debe definir un miembro de datos de campo de tipo puntero a **doble**.  
  
 Si inicializa `prgDblVals` y `prgLengths` a **NULL**, a continuación, las matrices que señalan se asignarán automáticamente, con los tamaños iguales al tamaño del conjunto de filas.  
  
> [!NOTE]
>  Intercambio masivo de campos de registros solo transfiere datos desde el origen de datos para el objeto de conjunto de registros. Para hacer que el conjunto de registros actualizables, debe usar la función de API de ODBC **SQLSetPos**.  
  
 Para obtener más información, vea los artículos [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) y [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text_Bulk](#rfx_text_bulk).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="rfx_int_bulk"></a>  RFX_Int_Bulk
Transfiere datos enteros entre los miembros de datos de campo de un `CRecordset` objeto y las columnas de un registro en el origen de datos de tipo ODBC **SQL_SMALLINT**.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Int(  
   CFieldExchange* pFX,  
   const char* szName,  
   int& value);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CFieldExchange](cfieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información acerca de las operaciones un `CFieldExchange` objeto puede especificar, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo `int`, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="rfx_long_bulk"></a>  RFX_Long_Bulk
Transfiere varias filas de datos de entero largo de una columna de un origen de datos ODBC a una matriz correspondiente en un `CRecordset`-objeto derivado.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Long_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   long** prgLongVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un [CFieldExchange](cfieldexchange-class.md) objeto. Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 `prgLongVals`  
 Un puntero a una matriz de enteros largos. Esta matriz almacenará los datos para ser transferidos desde el origen de datos para el conjunto de registros.  
  
 `prgLengths`  
 Un puntero a una matriz de enteros largos. Esta matriz almacenará la longitud en bytes de cada valor de la matriz señalada por `prgLongVals`. Tenga en cuenta que el valor **SQL_NULL_DATA** se almacenarán si el correspondiente elemento de datos contiene un valor Null. Para obtener más información, vea la función API de ODBC **SQLBindCol** en el *referencia del programador del SDK de ODBC*.  
  
### <a name="remarks"></a>Comentarios  
 La columna de origen de datos debe tener un tipo ODBC de **SQL_INTEGER**. El conjunto de registros debe definir un miembro de datos de campo de tipo puntero a **largo**.  
  
 Si inicializa `prgLongVals` y `prgLengths` a **NULL**, a continuación, las matrices que señalan se asignarán automáticamente, con los tamaños iguales al tamaño del conjunto de filas.  
  
> [!NOTE]
>  Intercambio masivo de campos de registros solo transfiere datos desde el origen de datos para el objeto de conjunto de registros. Para hacer que el conjunto de registros actualizables, debe usar la función de API de ODBC **SQLSetPos**.  
  
 Para obtener más información, vea los artículos [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) y [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text_Bulk](#rfx_text_bulk).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="rfx_single_bulk"></a>  RFX_Single_Bulk
Transfiere varias filas de datos de punto flotante de una columna de un origen de datos ODBC a una matriz correspondiente en un `CRecordset`-objeto derivado.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Single_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   float** prgFltVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un [CFieldExchange](cfieldexchange-class.md) objeto. Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 `prgFltVals`  
 Un puntero a una matriz de **float** valores. Esta matriz almacenará los datos para ser transferidos desde el origen de datos para el conjunto de registros.  
  
 `prgLengths`  
 Un puntero a una matriz de enteros largos. Esta matriz almacenará la longitud en bytes de cada valor de la matriz señalada por `prgFltVals`. Tenga en cuenta que el valor **SQL_NULL_DATA** se almacenarán si el correspondiente elemento de datos contiene un valor Null. Para obtener más información, vea la función API de ODBC **SQLBindCol** en el *referencia del programador del SDK de ODBC*.  
  
### <a name="remarks"></a>Comentarios  
 La columna de origen de datos debe tener un tipo ODBC de **SQL_REAL**. El conjunto de registros debe definir un miembro de datos de campo de tipo puntero a **float**.  
  
 Si inicializa `prgFltVals` y `prgLengths` a **NULL**, a continuación, las matrices que señalan se asignarán automáticamente, con los tamaños iguales al tamaño del conjunto de filas.  
  
> [!NOTE]
>  Intercambio masivo de campos de registros solo transfiere datos desde el origen de datos para el objeto de conjunto de registros. Para hacer que el conjunto de registros actualizables, debe usar la función de API de ODBC **SQLSetPos**.  
  
 Para obtener más información, vea los artículos [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) y [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Ejemplo  
 Vea [RFX_Text_Bulk](#rfx_text_bulk).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  

## <a name="rfx_text_bulk"></a>  RFX_Text_Bulk
Transfiere varias filas de datos de caracteres de una columna de un origen de datos ODBC a una matriz correspondiente en un `CRecordset`-objeto derivado.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void RFX_Text_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   LPSTR* prgStrVals,  
   long** prgLengths,  
   int nMaxLength);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un [CFieldExchange](cfieldexchange-class.md) objeto. Este objeto contiene información para definir el contexto para cada llamada de la función. Para obtener más información, vea el artículo [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 El nombre de una columna de datos.  
  
 `prgStrVals`  
 Un puntero a una matriz de **LPSTR** valores. Esta matriz almacenará los datos para ser transferidos desde el origen de datos para el conjunto de registros. Tenga en cuenta que con la versión actual de ODBC, estos valores no pueden ser Unicode.  
  
 `prgLengths`  
 Un puntero a una matriz de enteros largos. Esta matriz almacenará la longitud en bytes de cada valor de la matriz señalada por `prgStrVals`. Esta longitud excluye el carácter de terminación null. Tenga en cuenta que el valor **SQL_NULL_DATA** se almacenarán si el correspondiente elemento de datos contiene un valor Null. Para obtener más información, vea la función API de ODBC **SQLBindCol** en el *referencia del programador del SDK de ODBC*.  
  
 `nMaxLength`  
 La longitud de los valores almacenados en la matriz señalada por máxima permitida `prgStrVals`, incluido el carácter de terminación null. Para asegurarse de que los datos no se truncarán, pase un valor lo suficientemente grande como para alojar el elemento de datos más grande, se espera.  
  
### <a name="remarks"></a>Comentarios  
 La columna de origen de datos puede tener un tipo ODBC de **SQL_LONGVARCHAR**, **SQL_CHAR**, **SQL_VARCHAR**, **SQL_DECIMAL**, o **SQL_NUMERIC**. El conjunto de registros debe definir un miembro de datos de campo de tipo **LPSTR**.  
  
 Si inicializa `prgStrVals` y `prgLengths` a **NULL**, a continuación, las matrices que señalan se asignarán automáticamente, con los tamaños iguales al tamaño del conjunto de filas.  
  
> [!NOTE]
>  Intercambio masivo de campos de registros solo transfiere datos desde el origen de datos para el objeto de conjunto de registros. Para hacer que el conjunto de registros actualizables, debe usar la función de API de ODBC **SQLSetPos**.  
  
 Para obtener más información, vea los artículos [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) y [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Ejemplo  
 Debe escribir manualmente las llamadas su `DoBulkFieldExchange` invalidar. Este ejemplo muestra una llamada a `RFX_Text_Bulk`, así como una llamada a `RFX_Long_Bulk`, la transferencia de datos. Estas llamadas están precedidas por una llamada a [CFieldExchange:: SetFieldType](CFieldExchange::SetFieldType.md). Tenga en cuenta que para los parámetros, debe llamar a las funciones de RFX en lugar de las funciones de RFX masivo.  
  
```cpp  
void CMultiCustomer::DoBulkFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Long_Bulk(pFX, _T("[CustomerID]"), &m_pCustomerID, &m_pcCustomerID);
   RFX_Text_Bulk(pFX, _T("[ContactFirstName]"), &m_pContactFirstName, &m_pcContactFirstName, 50);
   RFX_Text_Bulk(pFX, _T("[PostalCode]"), &m_pPostalCode, &m_pcPostalCode, 50);
   RFX_Text_Bulk(pFX, _T("[L_Name]"), &m_pL_Name, &m_pcL_Name, 50);
   RFX_Long_Bulk(pFX, _T("[BillingID]"), &m_pBillingID, &m_pcBillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
``` 
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

## <a name="dfx_binary"></a>  DFX_Binary
Transfiere matrices de bytes entre los miembros de datos de campo de un [CDaoRecordset](cdaorecordset-class.md) objeto y las columnas de un registro en el origen de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void AFXAPI DFX_Binary(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   CByteArray& value,  
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,  
   DWORD dwBindOptions = 0);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CDaoFieldExchange](cdaofieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función.  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo [CByteArray](cbytearray-class.md), se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 `nPreAllocSize`  
 El marco de trabajo preasigna esta cantidad de memoria. Si los datos están mayores, el marco de trabajo le asigna más espacio según sea necesario. Para mejorar el rendimiento, establezca este tamaño en un valor lo suficientemente grande como para evitar la reasignación. El tamaño predeterminado se define en el AFXDAO. Archivo H como **AFX_DAO_BINARY_DEFAULT_SIZE**.  
  
 `dwBindOptions`  
 Una opción que le permite aprovechar las ventajas del mecanismo de almacenamiento en búfer doble de MFC para detectar los campos de conjunto de registros que han cambiado. El valor predeterminado, `AFX_DAO_DISABLE_FIELD_CACHE`, no usar almacenamiento en búfer doble y se debe llamar a [SetFieldDirty](cdaorecordset-class.md#setfielddirty) y [SetFieldNull](cdaorecordset-class.md#setfieldnull) usted mismo. El valor posible, `AFX_DAO_ENABLE_FIELD_CACHE`, almacenamiento en búfer doble utiliza y no es necesario que realizar trabajo adicional para marcar campos desfasadas o Null. Por motivos de memoria y rendimiento, evite este valor a menos que los datos binarios están relativamente pequeños.  
  
> [!NOTE]
>  Puede controlar si los datos están dobles en el búfer para todos los campos de forma predeterminada estableciendo [CDaoRecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Comentarios  
 Los datos se asignan entre tipo **DAO_BYTES** en DAO y escriba [CByteArray](cbytearray-class.md) en el conjunto de registros.  
  
### <a name="example"></a>Ejemplo  
 Vea [DFX_Text](#dfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  

## <a name="dfx_bool"></a>  DFX_Bool
Transfiere datos Boolean entre los miembros de datos de campo de un [CDaoRecordset](cdaorecordset-class.md) objeto y las columnas de un registro en el origen de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void AFXAPI DFX_Bool(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   BOOL& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CDaoFieldExchange](cdaofieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función.  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo **BOOL**, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 `dwBindOptions`  
 Una opción que le permite aprovechar las ventajas del mecanismo de almacenamiento en búfer doble de MFC para detectar los campos de conjunto de registros que han cambiado. El valor predeterminado, `AFX_DAO_ENABLE_FIELD_CACHE`, usa el almacenamiento en búfer doble. El otro valor posible es `AFX_DAO_DISABLE_FIELD_CACHE`. Si especifica este valor, MFC no realiza ninguna comprobación en este campo. Debe llamar a `SetFieldDirty` y `SetFieldNull` usted mismo.  
  
> [!NOTE]
>  Puede controlar si los datos están dobles almacenamiento en búfer de forma predeterminada estableciendo [CDaoRecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Comentarios  
 Los datos se asignan entre tipo **DAO_BOOL** en DAO y escriba **BOOL** en el conjunto de registros.  
  
### <a name="example"></a>Ejemplo  
 Vea [DFX_Text](#dfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  

## <a name="dfx_byte"></a>  DFX_Byte
Las transferencias único bytes entre los miembros de datos de campo de un [CDaoRecordset](cdaorecordset-class.md) objeto y las columnas de un registro en el origen de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void AFXAPI DFX_Byte(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CDaoFieldExchange](cdaofieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función.  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo **bytes**, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 `dwBindOptions`  
 Una opción que le permite aprovechar las ventajas del mecanismo de almacenamiento en búfer doble de MFC para detectar los campos de conjunto de registros que han cambiado. El valor predeterminado, `AFX_DAO_ENABLE_FIELD_CACHE`, usa el almacenamiento en búfer doble. El otro valor posible es `AFX_DAO_DISABLE_FIELD_CACHE`. Si especifica este valor, MFC no realiza ninguna comprobación en este campo. Debe llamar a `SetFieldDirty` y `SetFieldNull` usted mismo.  
  
> [!NOTE]
>  Puede controlar si los datos están dobles almacenamiento en búfer de forma predeterminada estableciendo [CDaoRecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Comentarios  
 Los datos se asignan entre tipo **DAO_BYTES** en DAO y escriba **bytes** en el conjunto de registros.  
  
### <a name="example"></a>Ejemplo  
 Vea [DFX_Text](#dfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  

## <a name="dfx_currency"></a>  DFX_Currency
Transfiere datos de moneda entre los miembros de datos de campo de un [CDaoRecordset](cdaorecordset-class.md) objeto y las columnas de un registro en el origen de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void AFXAPI DFX_Currency(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   COleCurrency& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CDaoFieldExchange](cdaofieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función.  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, este valor se toma del miembro de datos especificado, de tipo [COleCurrency](colecurrency-class.md). Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 `dwBindOptions`  
 Una opción que le permite aprovechar las ventajas del mecanismo de almacenamiento en búfer doble de MFC para detectar los campos de conjunto de registros que han cambiado. El valor predeterminado, `AFX_DAO_ENABLE_FIELD_CACHE`, usa el almacenamiento en búfer doble. El otro valor posible es `AFX_DAO_DISABLE_FIELD_CACHE`. Si especifica este valor, MFC no realiza ninguna comprobación en este campo. Debe llamar a `SetFieldDirty` y `SetFieldNull` usted mismo.  
  
> [!NOTE]
>  Puede controlar si los datos están dobles almacenamiento en búfer de forma predeterminada estableciendo [CDaoRecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Comentarios  
 Los datos se asignan entre tipo **DAO_CURRENCY** en DAO y escriba [COleCurrency](colecurrency-class.md) en el conjunto de registros.  
  
### <a name="example"></a>Ejemplo  
 Vea [DFX_Text](#dfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  

## <a name="dfx_datetime"></a>  DFX_DateTime
Transfiere datos de fecha y hora entre los miembros de datos de campo de un [CDaoRecordset](cdaorecordset-class.md) objeto y las columnas de un registro en el origen de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void AFXAPI DFX_DateTime(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   COleDateTime& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CDaoFieldExchange](cdaofieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función.  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. La función toma una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto. Para una transferencia de conjunto de registros al origen de datos, este valor se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 `dwBindOptions`  
 Una opción que le permite aprovechar las ventajas del mecanismo de almacenamiento en búfer doble de MFC para detectar los campos de conjunto de registros que han cambiado. El valor predeterminado, `AFX_DAO_ENABLE_FIELD_CACHE`, usa el almacenamiento en búfer doble. El otro valor posible es `AFX_DAO_DISABLE_FIELD_CACHE`. Si especifica este valor, MFC no realiza ninguna comprobación en este campo. Debe llamar a `SetFieldDirty` y `SetFieldNull` usted mismo.  
  
> [!NOTE]
>  Puede controlar si los datos están dobles almacenamiento en búfer de forma predeterminada estableciendo [CDaoRecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Comentarios  
 Los datos se asignan entre tipo **DAO_DATE** en DAO y escriba [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) en el conjunto de registros.  
  
> [!NOTE]
>  `COleDateTime`reemplaza [CTime](../../atl-mfc-shared/reference/ctime-class.md) y **TIMESTAMP_STRUCT** para este propósito en las clases DAO. `CTime`y **TIMESTAMP_STRUCT** son todavía se utiliza para las clases de acceso de datos basadas en ODBC.  
  
### <a name="example"></a>Ejemplo  
 Vea [DFX_Text](#dfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  

## <a name="dfx_double"></a>  DFX_Double
Las transferencias de **flotante doble** datos entre los miembros de datos de campo de un [CDaoRecordset](cdaorecordset-class.md) objeto y las columnas de un registro en el origen de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void AFXAPI DFX_Double(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   double& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CDaoFieldExchange](cdaofieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función.  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo **doble**, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 `dwBindOptions`  
 Una opción que le permite aprovechar las ventajas del mecanismo de almacenamiento en búfer doble de MFC para detectar los campos de conjunto de registros que han cambiado. El valor predeterminado, `AFX_DAO_ENABLE_FIELD_CACHE`, usa el almacenamiento en búfer doble. El otro valor posible es `AFX_DAO_DISABLE_FIELD_CACHE`. Si especifica este valor, MFC no realiza ninguna comprobación en este campo. Debe llamar a `SetFieldDirty` y `SetFieldNull` usted mismo.  
  
> [!NOTE]
>  Puede controlar si los datos están dobles almacenamiento en búfer de forma predeterminada estableciendo [CDaoRecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Comentarios  
 Los datos se asignan entre tipo **DAO_R8** en DAO y escriba **flotante doble** en el conjunto de registros.  
  
### <a name="example"></a>Ejemplo  
 Vea [DFX_Text](#dfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  

## <a name="dfx_long"></a>  DFX_Long
Transfiere datos enteros largos entre los miembros de datos de campo de un [CDaoRecordset](cdaorecordset-class.md) objeto y las columnas de un registro en el origen de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void AFXAPI DFX_Long(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   long& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CDaoFieldExchange](cdaofieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función.  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo **largo**, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 `dwBindOptions`  
 Una opción que le permite aprovechar las ventajas del mecanismo de almacenamiento en búfer doble de MFC para detectar los campos de conjunto de registros que han cambiado. El valor predeterminado, `AFX_DAO_ENABLE_FIELD_CACHE`, usa el almacenamiento en búfer doble. El otro valor posible es `AFX_DAO_DISABLE_FIELD_CACHE`. Si especifica este valor, MFC no realiza ninguna comprobación en este campo. Debe llamar a `SetFieldDirty` y `SetFieldNull` usted mismo.  
  
> [!NOTE]
>  Puede controlar si los datos están dobles almacenamiento en búfer de forma predeterminada estableciendo [CDaoRecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Comentarios  
 Los datos se asignan entre tipo **DAO_I4** en DAO y escriba **largo** en el conjunto de registros.  
  
### <a name="example"></a>Ejemplo  
 Vea [DFX_Text](#dfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  

## <a name="dfx_longbinary"></a>  DFX_LongBinary
**Importante** se recomienda que use [DFX_Binary](#dfx_binary) en lugar de esta función.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void AFXAPI DFX_LongBinary(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   CLongBinary& value,  
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,  
   DWORD dwBindOptions = 0);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CDaoFieldExchange](cdaofieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función.  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo [CLongBinary](clongbinary-class.md), se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 *dwPreAllocSize*  
 El marco de trabajo preasigna esta cantidad de memoria. Si los datos están mayores, el marco de trabajo le asigna más espacio según sea necesario. Para mejorar el rendimiento, establezca este tamaño en un valor lo suficientemente grande como para evitar la reasignación.  
  
 `dwBindOptions`  
 Una opción que le permite aprovechar las ventajas del mecanismo de almacenamiento en búfer doble de MFC para detectar los campos de conjunto de registros que han cambiado. El valor predeterminado, **AFX_DISABLE_FIELD_CACHE**, no utiliza el almacenamiento en búfer doble. El otro valor posible es `AFX_DAO_ENABLE_FIELD_CACHE`. Almacenamiento en búfer doble utiliza y no es necesario que realizar trabajo adicional para marcar campos desfasadas o Null. Por motivos de memoria y rendimiento, evite este valor a menos que los datos binarios están relativamente pequeños.  
  
> [!NOTE]
>  Puede controlar si los datos están dobles almacenamiento en búfer de forma predeterminada estableciendo [CDaoRecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Comentarios  
 `DFX_LongBinary`se proporciona por compatibilidad con las clases ODBC de MFC. El `DFX_LongBinary` función transfiere datos binarios objetos grandes (BLOB) mediante la clase `CLongBinary` entre los miembros de datos de campo de un [CDaoRecordset](cdaorecordset-class.md) objeto y las columnas de un registro en el origen de datos. Los datos se asignan entre tipo **DAO_BYTES** en DAO y escriba [CLongBinary](clongbinary-class.md) en el conjunto de registros.  
  
### <a name="example"></a>Ejemplo  
 Vea [DFX_Text](#dfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  

## <a name="dfx_short"></a>  DFX_Short
Transfiere datos enteros entre los miembros de datos de campo de cortos un [CDaoRecordset](cdaorecordset-class.md) objeto y las columnas de un registro en el origen de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void AFXAPI DFX_Short(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   short& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CDaoFieldExchange](cdaofieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función.  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo **corto**, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 `dwBindOptions`  
 Una opción que le permite aprovechar las ventajas del mecanismo de almacenamiento en búfer doble de MFC para detectar los campos de conjunto de registros que han cambiado. El valor predeterminado, `AFX_DAO_ENABLE_FIELD_CACHE`, usa el almacenamiento en búfer doble. El otro valor posible es `AFX_DAO_DISABLE_FIELD_CACHE`. Si especifica este valor, MFC no realiza ninguna comprobación en este campo. Debe llamar a `SetFieldDirty` y `SetFieldNull` usted mismo.  
  
> [!NOTE]
>  Puede controlar si los datos están dobles almacenamiento en búfer de forma predeterminada estableciendo [CDaoRecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Comentarios  
 Los datos se asignan entre tipo **DAO_I2** en DAO y escriba **breve** en el conjunto de registros.  
  
> [!NOTE]
>  `DFX_Short`es equivalente a [RFX_Int](#rfx_int) para las clases basadas en ODBC.  
  
### <a name="example"></a>Ejemplo  
 Vea [DFX_Text](#dfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  

## <a name="dfx_single"></a>  DFX_Single
Transferencias de datos de punto flotante entre los miembros de datos de campo de un [CDaoRecordset](cdaorecordset-class.md) objeto y las columnas de un registro en el origen de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void AFXAPI DFX_Single(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   float& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CDaoFieldExchange](cdaofieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función.  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo **float**, se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 `dwBindOptions`  
 Una opción que le permite aprovechar las ventajas del mecanismo de almacenamiento en búfer doble de MFC para detectar los campos de conjunto de registros que han cambiado. El valor predeterminado, `AFX_DAO_ENABLE_FIELD_CACHE`, usa el almacenamiento en búfer doble. El otro valor posible es `AFX_DAO_DISABLE_FIELD_CACHE`. Si especifica este valor, MFC no realiza ninguna comprobación en este campo. Debe llamar a `SetFieldDirty` y `SetFieldNull` usted mismo.  
  
> [!NOTE]
>  Puede controlar si los datos están dobles almacenamiento en búfer de forma predeterminada estableciendo [CDaoRecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Comentarios  
 Los datos se asignan entre tipo **DAO_R4** en DAO y escriba **float** en el conjunto de registros.  
  
### <a name="example"></a>Ejemplo  
 Vea [DFX_Text](#dfx_text).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  

## <a name="dfx_text"></a>  DFX_Text
Las transferencias de `CString` datos entre los miembros de datos de campo de un [CDaoRecordset](cdaorecordset-class.md) objeto y las columnas de un registro en el origen de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```
void AFXAPI DFX_Text(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   CString& value,  
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pFX`  
 Un puntero a un objeto de clase [CDaoFieldExchange](cdaofieldexchange-class.md). Este objeto contiene información para definir el contexto para cada llamada de la función.  
  
 `szName`  
 El nombre de una columna de datos.  
  
 *valor*  
 El valor almacenado en el miembro de datos indicado, el valor que se transferirá. Para una transferencia de conjunto de registros al origen de datos, el valor de tipo [CString](../../atl-mfc-shared/reference/cstringt-class.md), se toma del miembro de datos especificado. Para una transferencia de origen de datos al conjunto de registros, el valor se almacena en el miembro de datos especificado.  
  
 `nPreAllocSize`  
 El marco de trabajo preasigna esta cantidad de memoria. Si los datos están mayores, el marco de trabajo le asigna más espacio según sea necesario. Para mejorar el rendimiento, establezca este tamaño en un valor lo suficientemente grande como para evitar la reasignación.  
  
 `dwBindOptions`  
 Una opción que le permite aprovechar las ventajas del mecanismo de almacenamiento en búfer doble de MFC para detectar los campos de conjunto de registros que han cambiado. El valor predeterminado, `AFX_DAO_ENABLE_FIELD_CACHE`, usa el almacenamiento en búfer doble. El otro valor posible es `AFX_DAO_DISABLE_FIELD_CACHE`. Si especifica este valor, MFC no realiza ninguna comprobación en este campo. Debe llamar a [SetFieldDirty](cdaorecordset-class.md#setfielddirty) y [SetFieldNull](cdaorecordset-class.md#setfieldnull) usted mismo.  
  
> [!NOTE]
>  Puede controlar si los datos están dobles almacenamiento en búfer de forma predeterminada estableciendo [CDaoRecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Comentarios  
 Los datos se asignan entre tipo **DAO_CHAR** en DAO (o, si el símbolo **_UNICODE** se define, **DAO_WCHAR**) y el tipo de [CString](../../atl-mfc-shared/reference/cstringt-class.md) en el conjunto de registros.  n
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra varias llamadas a `DFX_Text`. Observe también las dos llamadas a [CDaoFieldExchange:: SetFieldType](cdaofieldexchange-class.md#setfieldtype). Debe escribir la primera llamada a `SetFieldType` y su **DFX** llamar. La segunda llamada y su **DFX** llamadas se escriben normalmente por el Asistente de código que genera la clase.  
  
```cpp  
void CCustSet::DoFieldExchange(CDaoFieldExchange* pFX)
{
   pFX->SetFieldType(CDaoFieldExchange::param);
   DFX_Text(pFX, _T("Param"), m_strParam);
   pFX->SetFieldType(CDaoFieldExchange::outputColumn);
   DFX_Short(pFX, _T("EmployeeID"), m_EmployeeID);
   DFX_Text(pFX, _T("LastName"), m_LastName);
   DFX_Short(pFX, _T("Age"), m_Age);
   DFX_DateTime(pFX, _T("hire_date"), m_hire_date);
   DFX_DateTime(pFX, _T("termination_date"), m_termination_date);

   CDaoRecordset::DoFieldExchange(pFX);
}
```
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [CRecordset:: DoFieldExchange](crecordset-class.md#dofieldexchange)   
 [CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)   
 [CDaoRecordset](cdaorecordset-class.md#dofieldexchange)

