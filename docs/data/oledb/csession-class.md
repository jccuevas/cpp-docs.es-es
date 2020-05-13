---
title: CSession (Clase)
ms.date: 11/04/2016
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
- CSession.Abort
- CSession::Abort
- ATL.CSession.Abort
- ATL::CSession::Abort
- CSession::Close
- ATL.CSession.Close
- CSession.Close
- ATL::CSession::Close
- CSession.Commit
- ATL.CSession.Commit
- ATL::CSession::Commit
- CSession::Commit
- GetTransactionInfo
- CSession.GetTransactionInfo
- ATL.CSession.GetTransactionInfo
- CSession::GetTransactionInfo
- ATL::CSession::GetTransactionInfo
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
- CSession::StartTransaction
- StartTransaction
- ATL.CSession.StartTransaction
- CSession.StartTransaction
- ATL::CSession::StartTransaction
helpviewer_keywords:
- CSession class
- Abort method
- Close method
- Commit method
- GetTransactionInfo method
- Open method
- StartTransaction method
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
ms.openlocfilehash: 72797411b100480a06e27b71b000264070e57e32
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211138"
---
# <a name="csession-class"></a>CSession (Clase)

Representa una única sesión de acceso a bases de datos.

## <a name="syntax"></a>Sintaxis

```cpp
class CSession
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[Abort](#abort)|Cancela (finaliza) la transacción.|
|[Close](#close)|Cierra la sesión.|
|[Confirmar](#commit)|Confirma la transacción.|
|[GetTransactionInfo](#gettransactioninfo)|Devuelve información sobre una transacción.|
|[Abrir](#open)|Abre una nueva sesión para el objeto de origen de datos.|
|[StartTransaction](#starttransaction)|Inicia una nueva transacción para esta sesión.|

## <a name="remarks"></a>Observaciones

Una o varias sesiones se pueden asociar a cada conexión de proveedor (origen de datos), que se representa mediante un objeto [CDataSource](../../data/oledb/cdatasource-class.md) . Para crear un nuevo `CSession` para un `CDataSource`, llame a [CSession:: Open](../../data/oledb/csession-open.md). Para iniciar una transacción de base de datos, `CSession` proporciona el método `StartTransaction`. Una vez iniciada una transacción, puede confirmarla con el método `Commit` o cancelarla con el método `Abort`.

## <a name="csessionabort"></a><a name="abort"></a>CSession:: ABORT

Finaliza la transacción.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Abort(BOID* pboidReason = NULL,
   BOOL bRetaining = FALSE,
   BOOL bAsync = FALSE) const throw();
```

#### <a name="parameters"></a>Parámetros

Vea [ITransaction:: ABORT](/previous-versions/windows/desktop/ms709833(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="csessionclose"></a><a name="close"></a>CSession:: Close

Cierra la sesión, que se abrió con [CSession:: Open](../../data/oledb/csession-open.md).

### <a name="syntax"></a>Sintaxis

```cpp
void Close() throw();
```

### <a name="remarks"></a>Observaciones

Libera el puntero `m_spOpenRowset`.

## <a name="csessioncommit"></a><a name="commit"></a>CSession:: commit

Confirma la transacción.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Commit(BOOL bRetaining = FALSE,
   DWORD grfTC = XACTTC_SYNC,
   DWORD grfRM = 0) const throw();
```

#### <a name="parameters"></a>Parámetros

Vea [ITransaction:: commit](/previous-versions/windows/desktop/ms713008(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [ITransaction:: commit](/previous-versions/windows/desktop/ms713008(v=vs.85)).

## <a name="csessiongettransactioninfo"></a><a name="gettransactioninfo"></a>CSession:: GetTransactionInfo

Devuelve información sobre una transacción.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();
```

#### <a name="parameters"></a>Parámetros

Vea [ITransaction:: GetTransactionInfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [ITransaction:: GetTransactionInfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="csessionopen"></a><a name="open"></a>CSession:: Open

Abre una nueva sesión para el objeto de origen de datos.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Open(const CDataSource& ds,
   DBPROPSET *pPropSet = NULL,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>Parámetros

*directorio*<br/>
de Origen de datos para el que se va a abrir la sesión.

*pPropSet*<br/>
de Puntero a una matriz de estructuras [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) que contiene las propiedades y los valores que se van a establecer. Vea [conjuntos de propiedades y grupos de propiedades](/previous-versions/windows/desktop/ms713696(v=vs.85)) en la *Referencia del programador de OLE DB* en el Windows SDK.

*ulPropSets*<br/>
de El número de estructuras [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) pasadas en el argumento *pPropSet* .

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Debe abrir el objeto de origen de datos mediante [CDataSource:: Open](../../data/oledb/cdatasource-open.md) antes de pasarlo a `CSession::Open`.

## <a name="csessionstarttransaction"></a><a name="starttransaction"></a>CSession:: StartTransaction

Inicia una nueva transacción para esta sesión.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,
   ULONG isoFlags = 0,
   ITransactionOptions* pOtherOptions = NULL,
   ULONG* pulTransactionLevel = NULL) const throw();
```

#### <a name="parameters"></a>Parámetros

Vea [ITransactionLocal:: StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [ITransactionLocal:: StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="see-also"></a>Consulte también

[Ejemplos](../../overview/visual-cpp-samples.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
