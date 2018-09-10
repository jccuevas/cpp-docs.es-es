---
title: Macros y funciones globales de base de datos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDB/AFX_ODBC_CALL
- AFXDB/AFX_SQL_ASYNC
- AFXDB/AFX_SQL_SYNC
- AFXDB/AfxGetHENV
dev_langs:
- C++
helpviewer_keywords:
- global database functions [MFC]
- database macros [MFC]
- database globals [MFC]
- global functions [MFC], database functions
- macros [MFC], MFC database
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8668ad3f803416956b67041df9e80c99e6337482
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314721"
---
# <a name="database-macros-and-globals"></a>Macros y variables globales de base de datos
Las macros y variables globales que se enumeran a continuación se aplican a las aplicaciones de base de datos basadas en ODBC. No se usan con las aplicaciones basadas en DAO.  
  
 Antes de MFC 4.2, las macros `AFX_SQL_ASYNC` y `AFX_SQL_SYNC` dio una oportunidad para producir tiempo a otros procesos de operaciones asincrónicas. A partir de MFC 4.2, la implementación de estas macros que se puede cambiado porque las clases ODBC de MFC usan sólo las operaciones sincrónicas. La macro `AFX_ODBC_CALL` era nuevo en MFC 4.2.  
  
### <a name="database-macros"></a>Macros de la base de datos  
  
|||  
|-|-|  
|[AFX_ODBC_CALL](#afx_odbc_call)|Llama a una función de la API de ODBC que devuelve `SQL_STILL_EXECUTING`. `AFX_ODBC_CALL` llamará repetidamente a la función hasta que ya no devuelve `SQL_STILL_EXECUTING`.|  
|[AFX_SQL_ASYNC](#afx_sql_async)|Llama a `AFX_ODBC_CALL`.|  
|[AFX_SQL_SYNC](#afx_sql_sync)|Llama a una función de la API de ODBC que no devuelve `SQL_STILL_EXECUTING`.|  
  
### <a name="database-globals"></a>Variables globales de base de datos  
  
|||  
|-|-| 
|[AfxDbInitModule](#afxdbinitmodule)|Agrega compatibilidad de base de datos para una DLL de MFC normal que se vincule dinámicamente a MFC.| 
|[AfxGetHENV](#afxgethenv)|Recupera un identificador para el entorno de ODBC actualmente en uso por MFC. Puede usar este identificador en llamadas directas de ODBC.|  


## <a name="afxdbinitmodule"></a> AfxDbInitModule
Para compatibilidad de base de datos MFC (o DAO) desde una DLL de MFC normal que se vincule dinámicamente a MFC, agregue una llamada a esta función en su MFC DLL regular `CWinApp::InitInstance` DLL de base de datos de esa función para inicializar la MFC.  
   
### <a name="syntax"></a>Sintaxis    
```
void AFXAPI AfxDbInitModule( );    
```  
   
### <a name="remarks"></a>Comentarios  
 Asegúrese de que esta llamada se produce antes de cualquier llamada de clase base o cualquier código que tiene acceso a la base de datos MFC DLL agregado. El archivo DLL de la base de datos MFC es una extensión MFC DLL; para una DLL de extensión MFC que puedan obtener conectados con un `CDynLinkLibrary` cadena, debe crear un `CDynLinkLibrary` objeto en el contexto de cada módulo que lo va a usar. `AfxDbInitModule` crea el `CDynLinkLibrary` objeto en contexto de su MFC DLL regular para que se obtiene con cable en el `CDynLinkLibrary` objeto de cadena de la DLL de MFC regular.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** \<afxdll_.h >  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)
 
  

##  <a name="afx_odbc_call"></a>  AFX_ODBC_CALL  
 Use esta macro para llamar a cualquier función de la API de ODBC que se puede devolver `SQL_STILL_EXECUTING`.  
  
```  
AFX_ODBC_CALL(SQLFunc)  
```  
  
### <a name="parameters"></a>Parámetros  
 *SQLFunc*  
 Una función de la API de ODBC. Para obtener más información acerca de las funciones de API de ODBC, consulte el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 `AFX_ODBC_CALL` llama repetidamente a la función hasta que ya no devuelve `SQL_STILL_EXECUTING`.  
  
 Antes de invocar `AFX_ODBC_CALL`, debe declarar una variable, `nRetCode`, de tipo RETCODE.  
  
 Tenga en cuenta que el ODBC de MFC clases procesamiento sincrónico solo de uso ahora. Con el fin de llevar a cabo una operación asincrónica, debe llamar a la función de la API de ODBC `SQLSetConnectOption`. Para obtener más información, vea el tema "Ejecutar funciones de manera asincrónica" en el SDK de Windows.  

  
### <a name="example"></a>Ejemplo  
 Este ejemplo se utiliza `AFX_ODBC_CALL` para llamar a la `SQLColumns` función de la API de ODBC, que devuelve una lista de las columnas de la tabla con el nombre `strTableName`. Tenga en cuenta la declaración de `nRetCode` y el uso de los miembros de datos del conjunto de registros para pasar parámetros a la función. Este ejemplo también muestra los resultados de la llamada con la comprobación `Check`, una función miembro de clase `CRecordset`. La variable `prs` es un puntero a un `CRecordset` objeto, declarado en otro lugar.  
  
 [!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

##  <a name="afx_sql_async"></a>  AFX_SQL_ASYNC  
 La implementación de esta macro cambiada en MFC 4.2.  
  
```   
AFX_SQL_ASYNC(prs, SQLFunc)   
```  
  
### <a name="parameters"></a>Parámetros  
 *incorporación de cambios*  
 Un puntero a un `CRecordset` objeto o un `CDatabase` objeto. A partir de MFC 4.2, se omite este valor de parámetro.  
  
 *SQLFunc*  
 Una función de la API de ODBC. Para obtener más información acerca de las funciones de API de ODBC, consulte el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 `AFX_SQL_ASYNC` simplemente llama a la macro [AFX_ODBC_CALL](#afx_odbc_call) y omite la *pr* parámetro. En las versiones de MFC anteriores 4.2, `AFX_SQL_ASYNC` se usó para llamar a funciones API de ODBC que podrían devolver `SQL_STILL_EXECUTING`. Si una función API de ODBC ha devuelto `SQL_STILL_EXECUTING`, a continuación, `AFX_SQL_ASYNC` llamaría `prs->OnWaitForDataSource`.  
  
> [!NOTE]
>  Las clases ODBC de MFC ahora utilizan el procesamiento sincrónico solo. Con el fin de llevar a cabo una operación asincrónica, debe llamar a la función de la API de ODBC `SQLSetConnectOption`. Para obtener más información, vea el tema "Ejecutar funciones de manera asincrónica" en el SDK de Windows.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdb.h  
  
##  <a name="afx_sql_sync"></a>  AFX_SQL_SYNC  
 El `AFX_SQL_SYNC` macro simplemente llama a la función `SQLFunc`.  
  
```   
AFX_SQL_SYNC(SQLFunc)   
```  
  
### <a name="parameters"></a>Parámetros  
 *SQLFunc*  
 Una función de la API de ODBC. Para obtener más información acerca de estas funciones, consulte el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Use esta macro para llamar a funciones API de ODBC que no se devolverán `SQL_STILL_EXECUTING`.  
  
 Antes de llamar a `AFX_SQL_SYNC`, debe declarar una variable, `nRetCode`, de tipo RETCODE. Puede comprobar el valor de `nRetCode` después de la llamada de macro.  
  
 Tenga en cuenta que la implementación de `AFX_SQL_SYNC` cambiado en MFC 4.2. Dado que ya no era necesaria, comprobar el estado del servidor `AFX_SQL_SYNC` simplemente asigna un valor a `nRetCode`. Por ejemplo, en lugar de realizar la llamada  
  
 [!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]  
  
 puede hacer que la asignación  
  
 [!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdb.h  
  
##  <a name="afxgethenv"></a>  AfxGetHENV  
 Puede usar el identificador devuelto en las llamadas directas de ODBC, pero no debe cerrar el identificador o se supone que el identificador es aún válida y está disponible después de cualquier existente `CDatabase`- o `CRecordset`-objetos derivados que se hayan destruido.  
  
```   
HENV AFXAPI AfxGetHENV(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador para el entorno de ODBC actualmente en uso por MFC. Puede ser `SQL_HENV_NULL` si no hay ningún [CDatabase](../../mfc/reference/cdatabase-class.md) objetos y no [CRecordset](../../mfc/reference/crecordset-class.md) objetos en uso.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdb.h  
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
