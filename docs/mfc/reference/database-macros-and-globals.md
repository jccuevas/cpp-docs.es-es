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
- AFXDB/AFX_ODBC_CALL
- AFXDB/AFX_SQL_ASYNC
- AFXDB/AFX_SQL_SYNC
- AFXDB/AfxGetHENV
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
ms.sourcegitcommit: b943ef8dd652df061965fe81ecc9c08115636141
ms.openlocfilehash: ddf13f6458df387d6686a18ecd459938ef2ebafd
ms.lasthandoff: 04/04/2017

---
# <a name="database-macros-and-globals"></a>Macros y variables globales de base de datos
Las macros y variables globales que se enumeran a continuación se aplican a las aplicaciones de base de datos basadas en ODBC. No se usan con las aplicaciones basadas en DAO.  
  
 Antes de MFC 4.2, las macros `AFX_SQL_ASYNC` y `AFX_SQL_SYNC` operaciones asincrónicas que proporcionó una oportunidad para ceder tiempo a otros procesos. Comienzo con MFC 4.2, la implementación de estas macros cambiado porque las clases ODBC de MFC utilizan solo las operaciones sincrónicas. La macro `AFX_ODBC_CALL` era nuevo en MFC 4.2.  
  
### <a name="database-macros"></a>Macros de base de datos  
  
|||  
|-|-|  
|[AFX_ODBC_CALL](#afx_odbc_call)|Llama a una función de API de ODBC devuelve `SQL_STILL_EXECUTING`. `AFX_ODBC_CALL`llamará repetidamente a la función hasta que ya no devuelve `SQL_STILL_EXECUTING`.|  
|[AFX_SQL_ASYNC](#afx_sql_async)|Llama a `AFX_ODBC_CALL`.|  
|[AFX_SQL_SYNC](#afx_sql_sync)|Llama a una función de API de ODBC que no devuelve `SQL_STILL_EXECUTING`.|  
  
### <a name="database-globals"></a>Variables globales de la base de datos  
  
|||  
|-|-| 
|[AfxDbInitModule](#afxdbinitmodule)|Agrega compatibilidad de base de datos para un archivo DLL estándar vinculado dinámicamente a MFC.| 
|[AfxGetHENV](#afxgethenv)|Recupera un identificador para el entorno de ODBC actualmente en uso por MFC. Se puede usar este identificador en llamadas directas de ODBC.|  


## <a name="afxdbinitmodule"></a>AfxDbInitModule
Para base de datos MFC (o DAO) admite desde un archivo DLL estándar vinculado dinámicamente a MFC, agregue una llamada a esta función en el archivo DLL estándar **CWinApp:: InitInstance** DLL de base de datos de función para inicializar el MFC.  
   
### <a name="syntax"></a>Sintaxis    
```
void AFXAPI AfxDbInitModule( );    
```  
   
### <a name="remarks"></a>Comentarios  
 Asegúrese de que esta llamada se produce antes de cualquier llamada de clase base o cualquier código que tiene acceso a la base de datos MFC DLL agregado. El archivo DLL de la base de datos MFC es una extensión de archivo DLL; en orden para un archivo DLL de extensión para poder conectar a un **CDynLinkLibrary** cadena, debe crear un **CDynLinkLibrary** objeto en el contexto de cada módulo que lo va a usar. `AfxDbInitModule`crea el **CDynLinkLibrary** objeto en el contexto de los DLL normales para que se obtiene con cable en el **CDynLinkLibrary** objeto de cadena de la DLL normal.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:**<afxdll_.h></afxdll_.h>  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)
 
  

##  <a name="afx_odbc_call"></a>AFX_ODBC_CALL  
 Use esta macro para llamar a la función API de ODBC que puede devolver `SQL_STILL_EXECUTING`.  
  
```  
AFX_ODBC_CALL(SQLFunc)  
```  
  
### <a name="parameters"></a>Parámetros  
 `SQLFunc`  
 Una función API de ODBC. Para obtener más información acerca de las funciones de API de ODBC, consulte el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 `AFX_ODBC_CALL`llama repetidamente a la función hasta que ya no devuelve `SQL_STILL_EXECUTING`.  
  
 Antes de invocar `AFX_ODBC_CALL`, debe declarar una variable, `nRetCode`, del tipo **RETCODE**.  
  
 Tenga en cuenta que el ODBC de MFC clases procesamiento solo sincrónico de uso de ahora. Para llevar a cabo una operación asincrónica, debe llamar a la función API de ODBC **SQLSetConnectOption**. Para obtener más información, vea el tema "Ejecutar funciones de forma asincrónica" en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  

  
### <a name="example"></a>Ejemplo  
 Este ejemplo se utiliza `AFX_ODBC_CALL` para llamar a la **SQLColumns** función de la API de ODBC, que devuelve una lista de las columnas de la tabla con el nombre por `strTableName`. Tenga en cuenta la declaración de `nRetCode` y el uso de miembros de datos del conjunto de registros para pasar parámetros a la función. Este ejemplo también muestra la comprobación de los resultados de la llamada con **comprobar**, una función miembro de clase `CRecordset`. La variable `prs` es un puntero a un `CRecordset` objeto, declarado en otro lugar.  
  
 [!code-cpp[NVC_MFCDatabase #39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  

##  <a name="afx_sql_async"></a>AFX_SQL_ASYNC  
 La implementación de esta macro cambiada en MFC 4.2.  
  
```   
AFX_SQL_ASYNC(prs, SQLFunc)   
```  
  
### <a name="parameters"></a>Parámetros  
 `prs`  
 Un puntero a un `CRecordset` objeto o un `CDatabase` objeto. Empezando por MFC 4.2, se omite este valor de parámetro.  
  
 `SQLFunc`  
 Una función API de ODBC. Para obtener más información acerca de las funciones de API de ODBC, consulte el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 `AFX_SQL_ASYNC`simplemente llama a la macro [AFX_ODBC_CALL](#afx_odbc_call) y omite la `prs` parámetro. En las versiones de MFC anteriores 4.2, `AFX_SQL_ASYNC` se usó para llamar a funciones de API de ODBC que podrían devolver `SQL_STILL_EXECUTING`. Si una función API de ODBC ha devuelto `SQL_STILL_EXECUTING`, a continuación, `AFX_SQL_ASYNC` llamaría a `prs->OnWaitForDataSource`.  
  
> [!NOTE]
>  Las clases ODBC de MFC ahora utilizan el procesamiento sincrónico solo. Para llevar a cabo una operación asincrónica, debe llamar a la función API de ODBC **SQLSetConnectOption**. Para obtener más información, vea el tema "Ejecutar funciones de forma asincrónica" en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdb.h  
  
##  <a name="afx_sql_sync"></a>AFX_SQL_SYNC  
 El `AFX_SQL_SYNC` macro simplemente llama a la función `SQLFunc`.  
  
```   
AFX_SQL_SYNC(SQLFunc)   
```  
  
### <a name="parameters"></a>Parámetros  
 `SQLFunc`  
 Una función API de ODBC. Para obtener más información acerca de estas funciones, vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Use esta macro para llamar a funciones de API de ODBC que no devolverá `SQL_STILL_EXECUTING`.  
  
 Antes de llamar a `AFX_SQL_SYNC`, debe declarar una variable, `nRetCode`, del tipo **RETCODE**. Puede comprobar el valor de `nRetCode` después de la llamada de macro.  
  
 Tenga en cuenta que la implementación de `AFX_SQL_SYNC` cambiado en MFC 4.2. Dado que ya no se requiere, comprobando el estado del servidor `AFX_SQL_SYNC` simplemente asigna un valor a `nRetCode`. Por ejemplo, en lugar de realizar la llamada  
  
 [!code-cpp[NVC_MFCDatabase Nº 40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]  
  
 simplemente puede realizar la asignación  
  
 [!code-cpp[NVC_MFCDatabase #41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdb.h  
  
##  <a name="afxgethenv"></a>AfxGetHENV  
 Puede utilizar el identificador devuelto en llamadas directas de ODBC, pero no debe cerrar el identificador o se supone que el identificador es aún válida y estar disponible después de cualquier existente `CDatabase`- o `CRecordset`-objetos derivados que se hayan destruido.  
  
```   
HENV AFXAPI AfxGetHENV(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador para el entorno de ODBC actualmente en uso por MFC. Puede ser `SQL_HENV_NULL` si no hay ningún [CDatabase](../../mfc/reference/cdatabase-class.md) objetos y no [CRecordset](../../mfc/reference/crecordset-class.md) objetos en uso.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdb.h  
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

