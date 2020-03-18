---
title: Macros y variables globales de base de datos
ms.date: 11/04/2016
f1_keywords:
- AFXDB/AFX_ODBC_CALL
- AFXDB/AFX_SQL_ASYNC
- AFXDB/AFX_SQL_SYNC
- AFXDB/AfxGetHENV
helpviewer_keywords:
- global database functions [MFC]
- database macros [MFC]
- database globals [MFC]
- global functions [MFC], database functions
- macros [MFC], MFC database
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
ms.openlocfilehash: 47a1bb434801c24ab8eee048d9ef8f93793101cc
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426274"
---
# <a name="database-macros-and-globals"></a>Macros y variables globales de base de datos

Las macros y las variables globales que se enumeran a continuación se aplican a las aplicaciones de base de datos basadas en ODBC. No se utilizan con aplicaciones basadas en DAO.

Antes de MFC 4,2, las macros `AFX_SQL_ASYNC` y `AFX_SQL_SYNC` dieron a las operaciones asincrónicas la oportunidad de dar tiempo a otros procesos. A partir de MFC 4,2, la implementación de estas macros ha cambiado porque las clases ODBC de MFC solo usaban operaciones sincrónicas. La macro `AFX_ODBC_CALL` era nueva en MFC 4,2.

### <a name="database-macros"></a>Macros de base de datos

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Llama a una función de la API de ODBC que devuelve `SQL_STILL_EXECUTING`. `AFX_ODBC_CALL` llamará repetidamente a la función hasta que ya no devuelva `SQL_STILL_EXECUTING`.|
|[AFX_SQL_ASYNC](#afx_sql_async)|Llama a `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Llama a una función de la API de ODBC que no devuelve `SQL_STILL_EXECUTING`.|

### <a name="database-globals"></a>Globales de base de datos

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Agrega compatibilidad con bases de datos para un archivo DLL de MFC normal que está vinculado dinámicamente a MFC.|
|[AfxGetHENV](#afxgethenv)|Recupera un identificador del entorno ODBC actualmente en uso por MFC. Puede usar este identificador en llamadas ODBC directas.|

## <a name="afxdbinitmodule"></a>AfxDbInitModule

Para la compatibilidad con la base de datos MFC (o DAO) desde un archivo DLL de MFC normal que está vinculado dinámicamente a MFC, agregue una llamada a esta función en la función `CWinApp::InitInstance` de la DLL de MFC normal para inicializar el archivo DLL de base de datos MFC.

### <a name="syntax"></a>Sintaxis

```
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Observaciones

Asegúrese de que esta llamada se produce antes de cualquier llamada de clase base o cualquier código agregado que tenga acceso al archivo DLL de base de datos MFC. La DLL de base de datos MFC es un archivo DLL de extensión MFC; para que un archivo DLL de extensión de MFC se pueda conectar a una cadena de `CDynLinkLibrary`, debe crear un objeto `CDynLinkLibrary` en el contexto de cada módulo que lo vaya a utilizar. `AfxDbInitModule` crea el objeto `CDynLinkLibrary` en el contexto del archivo DLL de MFC normal, de modo que se conecta a la cadena de objetos `CDynLinkLibrary` del archivo DLL de MFC normal.

### <a name="requirements"></a>Requisitos

**Encabezado:** \<afxdll_. h >

##  <a name="afx_odbc_call"></a>AFX_ODBC_CALL

Utilice esta macro para llamar a cualquier función de la API de ODBC que pueda devolver `SQL_STILL_EXECUTING`.

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Parámetros

*SQLFunc*<br/>
Una función de la API de ODBC. Para obtener más información sobre las funciones de la API de ODBC, vea el Windows SDK.

### <a name="remarks"></a>Observaciones

`AFX_ODBC_CALL` llama a la función repetidamente hasta que ya no devuelve `SQL_STILL_EXECUTING`.

Antes de invocar `AFX_ODBC_CALL`, debe declarar una variable, `nRetCode`, de tipo RETCODE.

Tenga en cuenta que las clases ODBC de MFC ahora solo utilizan el procesamiento sincrónico. Para realizar una operación asincrónica, debe llamar a la función de la API de ODBC `SQLSetConnectOption`. Para obtener más información, vea el tema "ejecutar funciones de forma asincrónica" en la Windows SDK.

### <a name="example"></a>Ejemplo

En este ejemplo se usa `AFX_ODBC_CALL` para llamar a la función de la API de ODBC `SQLColumns`, que devuelve una lista de las columnas de la tabla denominada por `strTableName`. Observe la declaración de `nRetCode` y el uso de los miembros de datos de conjunto de registros para pasar parámetros a la función. En el ejemplo también se muestra la comprobación de los resultados de la llamada con `Check`, una función miembro de la clase `CRecordset`. La variable `prs` es un puntero a un objeto `CRecordset`, declarado en otro lugar.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdb. h

##  <a name="afx_sql_async"></a>AFX_SQL_ASYNC

La implementación de esta macro ha cambiado en MFC 4,2.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Parámetros

*incorporación*<br/>
Puntero a un objeto `CRecordset` o un objeto `CDatabase`. A partir de MFC 4,2, se omite este valor de parámetro.

*SQLFunc*<br/>
Una función de la API de ODBC. Para obtener más información sobre las funciones de la API de ODBC, vea el Windows SDK.

### <a name="remarks"></a>Observaciones

`AFX_SQL_ASYNC` simplemente llama a la macro [AFX_ODBC_CALL](#afx_odbc_call) y omite el parámetro *PRS* . En las versiones de MFC anteriores a 4,2, se usaba `AFX_SQL_ASYNC` para llamar a funciones de la API de ODBC que podrían devolver `SQL_STILL_EXECUTING`. Si una función de la API de ODBC devolvió `SQL_STILL_EXECUTING`, `AFX_SQL_ASYNC` llamaría a `prs->OnWaitForDataSource`.

> [!NOTE]
>  Las clases ODBC de MFC ahora solo utilizan el procesamiento sincrónico. Para realizar una operación asincrónica, debe llamar a la función de la API de ODBC `SQLSetConnectOption`. Para obtener más información, vea el tema "ejecutar funciones de forma asincrónica" en la Windows SDK.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdb. h

##  <a name="afx_sql_sync"></a>AFX_SQL_SYNC

La macro `AFX_SQL_SYNC` simplemente llama a la función `SQLFunc`.

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Parámetros

*SQLFunc*<br/>
Una función de la API de ODBC. Para obtener más información sobre estas funciones, vea el Windows SDK.

### <a name="remarks"></a>Observaciones

Utilice esta macro para llamar a funciones de la API de ODBC que no devolverán `SQL_STILL_EXECUTING`.

Antes de llamar a `AFX_SQL_SYNC`, debe declarar una variable, `nRetCode`, de tipo RETCODE. Puede comprobar el valor de `nRetCode` después de la llamada a la macro.

Tenga en cuenta que la implementación de `AFX_SQL_SYNC` cambiado en MFC 4,2. Dado que la comprobación del estado del servidor ya no era necesaria, `AFX_SQL_SYNC` simplemente asigna un valor a `nRetCode`. Por ejemplo, en lugar de efectuar la llamada

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

simplemente puede hacer la asignación

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdb. h

##  <a name="afxgethenv"></a>AfxGetHENV

Puede usar el identificador devuelto en llamadas ODBC directas, pero no debe cerrar el identificador ni asumir que el identificador todavía es válido y está disponible después de que se hayan destruido todos los objetos derivados de `CDatabase`o `CRecordset`.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Valor devuelto

Identificador del entorno ODBC actualmente en uso por MFC. Se puede `SQL_HENV_NULL` si no hay ningún objeto [CDatabase](../../mfc/reference/cdatabase-class.md) y no hay objetos [CRecordset](../../mfc/reference/crecordset-class.md) en uso.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdb. h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
