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
ms.openlocfilehash: 4e9700311bbc20ea017675357a91a56813cc4bde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376959"
---
# <a name="database-macros-and-globals"></a>Macros y variables globales de base de datos

Las macros y los valores globales que se enumeran a continuación se aplican a las aplicaciones de base de datos basadas en ODBC. No se utilizan con aplicaciones basadas en DAO.

Antes de MFC 4.2, las macros `AFX_SQL_ASYNC` y `AFX_SQL_SYNC` dio a las operaciones asincrónicas la oportunidad de producir tiempo a otros procesos. A partir de MFC 4.2, la implementación de estas macros cambió porque las clases ODBC de MFC solo usaban operaciones sincrónicas. La `AFX_ODBC_CALL` macro era nueva en MFC 4.2.

### <a name="database-macros"></a>Macros de base de datos

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Llama a una función de API ODBC que devuelve `SQL_STILL_EXECUTING`. `AFX_ODBC_CALL`llamará repetidamente a la función `SQL_STILL_EXECUTING`hasta que ya no devuelva .|
|[AFX_SQL_ASYNC](#afx_sql_async)|Llama a `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Llama a una función `SQL_STILL_EXECUTING`de API ODBC que no devuelve .|

### <a name="database-globals"></a>Globales de bases de datos

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Agrega compatibilidad de base de datos para un archivo DLL de MFC normal que está vinculado dinámicamente a MFC.|
|[AfxGetHENV](#afxgethenv)|Recupera un identificador para el entorno ODBC actualmente en uso por MFC. Puede usar este identificador en llamadas ODBC directas.|

## <a name="afxdbinitmodule"></a><a name="afxdbinitmodule"></a>AfxDbInitModule

Para la compatibilidad con la base de datos MFC (o DAO) desde un archivo DLL de MFC `CWinApp::InitInstance` normal que está vinculado dinámicamente a MFC, agregue una llamada a esta función en la función del archivo DLL de MFC normal para inicializar el archivo DLL de base de datos MFC.

### <a name="syntax"></a>Sintaxis

```
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Observaciones

Asegúrese de que esta llamada se produce antes de cualquier llamada de clase base o cualquier código agregado que tenga acceso a la DLL de base de datos MFC. El archivo DLL de base de datos MFC es un archivo DLL de extensión MFC; para que un archivo DLL de `CDynLinkLibrary` extensión MFC se `CDynLinkLibrary` conectara a una cadena, debe crear un objeto en el contexto de cada módulo que lo usará. `AfxDbInitModule`crea `CDynLinkLibrary` el objeto en el contexto del archivo DLL de `CDynLinkLibrary` MFC normal para que se conecta a la cadena de objetos de la DLL de MFC normal.

### <a name="requirements"></a>Requisitos

**Encabezado:** \<afxdll_.h>

## <a name="afx_odbc_call"></a><a name="afx_odbc_call"></a>AFX_ODBC_CALL

Utilice esta macro para llamar a `SQL_STILL_EXECUTING`cualquier función de API ODBC que pueda devolver .

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Parámetros

*SQLFunc*<br/>
Una función de API ODBC. Para obtener más información acerca de las funciones de la API ODBC, consulte el Windows SDK.

### <a name="remarks"></a>Observaciones

`AFX_ODBC_CALL`repetidamente llama a la función hasta que ya no devuelve `SQL_STILL_EXECUTING`.

Antes de `AFX_ODBC_CALL`invocar , debe `nRetCode`declarar una variable, , de tipo RETCODE.

Tenga en cuenta que las clases ODBC de MFC ahora solo usan el procesamiento sincrónico. Para realizar una operación asincrónica, debe llamar `SQLSetConnectOption`a la función de API ODBC . Para obtener más información, vea el tema "Ejecutar funciones de forma asincrónica" en el Windows SDK.

### <a name="example"></a>Ejemplo

En este `AFX_ODBC_CALL` ejemplo `SQLColumns` se utiliza para llamar a la función de `strTableName`API ODBC, que devuelve una lista de las columnas de la tabla denominada por . Tenga en `nRetCode` cuenta la declaración y el uso de miembros de datos de conjunto de registros para pasar parámetros a la función. El ejemplo también ilustra la comprobación `Check`de los resultados `CRecordset`de la llamada con , una función miembro de la clase . La `prs` variable es un `CRecordset` puntero a un objeto, declarado en otro lugar.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdb.h

## <a name="afx_sql_async"></a><a name="afx_sql_async"></a>AFX_SQL_ASYNC

La implementación de esta macro cambió en MFC 4.2.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Parámetros

*Prs*<br/>
Puntero a `CRecordset` un objeto `CDatabase` o a un objeto. A partir de MFC 4.2, se omite este valor de parámetro.

*SQLFunc*<br/>
Una función de API ODBC. Para obtener más información acerca de las funciones de la API ODBC, consulte el Windows SDK.

### <a name="remarks"></a>Observaciones

`AFX_SQL_ASYNC`simplemente llama a la [macro AFX_ODBC_CALL](#afx_odbc_call) e ignora el parámetro *prs.* En versiones de MFC anteriores a 4.2, `AFX_SQL_ASYNC` se `SQL_STILL_EXECUTING`usaba para llamar a funciones de API ODBC que podrían devolver . Si una función `SQL_STILL_EXECUTING`de `AFX_SQL_ASYNC` API `prs->OnWaitForDataSource`ODBC devolviera , llamaría a .

> [!NOTE]
> Las clases ODBC de MFC ahora solo usan el procesamiento sincrónico. Para realizar una operación asincrónica, debe llamar `SQLSetConnectOption`a la función de API ODBC . Para obtener más información, vea el tema "Ejecutar funciones de forma asincrónica" en el Windows SDK.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdb.h

## <a name="afx_sql_sync"></a><a name="afx_sql_sync"></a>AFX_SQL_SYNC

La `AFX_SQL_SYNC` macro simplemente `SQLFunc`llama a la función .

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Parámetros

*SQLFunc*<br/>
Una función de API ODBC. Para obtener más información acerca de estas funciones, consulte el Windows SDK.

### <a name="remarks"></a>Observaciones

Utilice esta macro para llamar a `SQL_STILL_EXECUTING`funciones de api ODBC que no devolverán .

Antes `AFX_SQL_SYNC`de llamar a , `nRetCode`debe declarar una variable, , de tipo RETCODE. Puede comprobar el `nRetCode` valor de después de la llamada de macro.

Tenga en cuenta `AFX_SQL_SYNC` que la implementación de cambió en MFC 4.2. Dado que la comprobación del `AFX_SQL_SYNC` estado del servidor `nRetCode`ya no era necesaria, simplemente asigna un valor a . Por ejemplo, en lugar de hacer la llamada

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

usted puede simplemente hacer la asignación

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdb.h

## <a name="afxgethenv"></a><a name="afxgethenv"></a>AfxGetHENV

Puede usar el identificador devuelto en llamadas ODBC directas, pero no debe cerrar el `CDatabase`identificador `CRecordset`ni asumir que el identificador sigue siendo válido y está disponible después de que se hayan destruido los objetos existentes o derivados.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Valor devuelto

El identificador para el entorno ODBC actualmente en uso por MFC. Puede `SQL_HENV_NULL` ser si no hay [ningún CDatabase](../../mfc/reference/cdatabase-class.md) objetos y no [CRecordset](../../mfc/reference/crecordset-class.md) objetos en uso.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdb.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
