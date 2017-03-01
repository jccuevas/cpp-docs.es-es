---
title: Macros y funciones globales de la base de datos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- global database functions [C++]
- database macros [C++]
- database globals [C++]
- global functions [C++], database functions
- macros [C++], MFC database
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 9706c47d9bd5996c28873da6a15a687bf9b5e038
ms.lasthandoff: 02/24/2017

---
# <a name="database-macros-and-globals"></a>Macros y variables globales de base de datos
Las macros y variables globales que se enumeran a continuación se aplican a las aplicaciones de base de datos basadas en ODBC. No se usan con aplicaciones basadas en DAO.  
  
 Antes de MFC 4.2, las macros `AFX_SQL_ASYNC` y `AFX_SQL_SYNC` dio una oportunidad para ceder tiempo a otros procesos de operaciones asincrónicas. Comienzo con MFC 4.2, la implementación de estas macros cambiado porque las clases ODBC de MFC utilizan sólo las operaciones sincrónicas. La macro `AFX_ODBC_CALL` era nueva en MFC 4.2.  
  
### <a name="database-macros"></a>Macros de la base de datos  
  
|||  
|-|-|  
|[AFX_ODBC_CALL](#afx_odbc_call)|Llama a una función de API de ODBC devuelve `SQL_STILL_EXECUTING`. `AFX_ODBC_CALL`llamará repetidamente a la función hasta que ya no devuelve `SQL_STILL_EXECUTING`.|  
|[AFX_SQL_ASYNC](#afx_sql_async)|Llama a `AFX_ODBC_CALL`.|  
|[AFX_SQL_SYNC](#afx_sql_sync)|Llama a una función de la API de ODBC que no devuelve `SQL_STILL_EXECUTING`.|  
  
### <a name="database-globals"></a>Variables globales de la base de datos  
  
|||  
|-|-|  
|[AfxGetHENV](#afxgethenv)|Recupera un identificador para el entorno de ODBC en uso actualmente por MFC. Puede usar este identificador en llamadas directas de ODBC.|  
  
##  <a name="a-nameafxodbccalla--afxodbccall"></a><a name="afx_odbc_call"></a>AFX_ODBC_CALL  
 Utilizar esta macro para llamar a la función API de ODBC que puede devolver `SQL_STILL_EXECUTING`.  
  
```  
AFX_ODBC_CALL(SQLFunc)  
```  
  
### <a name="parameters"></a>Parámetros  
 `SQLFunc`  
 Una función de la API de ODBC. Para obtener más información acerca de las funciones de la API de ODBC, vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 `AFX_ODBC_CALL`llama repetidamente a la función hasta que ya no devuelve `SQL_STILL_EXECUTING`.  
  
 Antes de invocar `AFX_ODBC_CALL`, debe declarar una variable, `nRetCode`, del tipo **RETCODE**.  
  
 Tenga en cuenta que ODBC de MFC clases ahora utilizar sólo sincrónico el procesamiento. Para realizar una operación asincrónica, debe llamar a la función API de ODBC **SQLSetConnectOption**. Para obtener más información, vea el tema "Ejecutar funciones de forma asincrónica" en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  

  
### <a name="example"></a>Ejemplo  
 Este ejemplo utiliza `AFX_ODBC_CALL` para llamar a la **SQLColumns** función de la API de ODBC, que devuelve una lista de las columnas de la tabla con el nombre `strTableName`. Tenga en cuenta la declaración de `nRetCode` y el uso de miembros de datos del conjunto de registros para pasar parámetros a la función. El ejemplo también muestra los resultados de la llamada con la comprobación **comprobar**, una función miembro de clase `CRecordset`. La variable `prs` es un puntero a un `CRecordset` objeto, que se declara en otra parte.  
  
 [!code-cpp[NVC_MFCDatabase&#39;](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

##  <a name="a-nameafxsqlasynca--afxsqlasync"></a><a name="afx_sql_async"></a>AFX_SQL_ASYNC  
 La implementación de esta macro cambiada en MFC 4.2.  
  
```   
AFX_SQL_ASYNC(prs, SQLFunc)   
```  
  
### <a name="parameters"></a>Parámetros  
 `prs`  
 Un puntero a un `CRecordset` objeto o un `CDatabase` objeto. Empezando por MFC 4.2, se omite este valor de parámetro.  
  
 `SQLFunc`  
 Una función de la API de ODBC. Para obtener más información acerca de las funciones de la API de ODBC, vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 `AFX_SQL_ASYNC`llama a la macro [AFX_ODBC_CALL](#afx_odbc_call) y omite la `prs` parámetro. En las versiones de MFC anteriores 4.2, `AFX_SQL_ASYNC` se usó para llamar a funciones de API de ODBC que pueden devolver `SQL_STILL_EXECUTING`. Si ha devuelto una función API de ODBC `SQL_STILL_EXECUTING`, a continuación, `AFX_SQL_ASYNC` llamaría a `prs->OnWaitForDataSource`.  
  
> [!NOTE]
>  Las clases ODBC de MFC ahora utilizan el procesamiento sincrónico solo. Para realizar una operación asincrónica, debe llamar a la función API de ODBC **SQLSetConnectOption**. Para obtener más información, vea el tema "Ejecutar funciones de forma asincrónica" en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdb.h  
  
##  <a name="a-nameafxsqlsynca--afxsqlsync"></a><a name="afx_sql_sync"></a>AFX_SQL_SYNC  
 El `AFX_SQL_SYNC` macro simplemente llama a la función `SQLFunc`.  
  
```   
AFX_SQL_SYNC(SQLFunc)   
```  
  
### <a name="parameters"></a>Parámetros  
 `SQLFunc`  
 Una función de la API de ODBC. Para obtener más información acerca de estas funciones, consulte el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Utilizar esta macro para llamar a funciones de API de ODBC que no devolverá `SQL_STILL_EXECUTING`.  
  
 Antes de llamar a `AFX_SQL_SYNC`, debe declarar una variable, `nRetCode`, del tipo **RETCODE**. Puede comprobar el valor de `nRetCode` después de la llamada de macro.  
  
 Tenga en cuenta que la implementación de `AFX_SQL_SYNC` cambiado en MFC 4.2. Dado que ya no era necesaria, comprobar el estado del servidor `AFX_SQL_SYNC` simplemente asigna un valor a `nRetCode`. Por ejemplo, en lugar de realizar la llamada  
  
 [!code-cpp[NVC_MFCDatabase Nº&40;](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]  
  
 puede hacer que la asignación  
  
 [!code-cpp[NVC_MFCDatabase nº&41;](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdb.h  
  
##  <a name="a-nameafxgethenva--afxgethenv"></a><a name="afxgethenv"></a>AfxGetHENV  
 Puede utilizar el identificador devuelto en llamadas directas de ODBC, pero no debe cerrar el identificador o se supone que el identificador es aún válida y está disponible después de cualquier existente `CDatabase`- o `CRecordset`-objetos derivados que se hayan destruido.  
  
```   
HENV AFXAPI AfxGetHENV(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador para el entorno de ODBC en uso actualmente por MFC. Puede ser `SQL_HENV_NULL` si no hay ningún [CDatabase](../../mfc/reference/cdatabase-class.md) objetos y no [CRecordset](../../mfc/reference/crecordset-class.md) objetos en uso.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdb.h  
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

