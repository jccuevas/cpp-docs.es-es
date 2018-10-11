---
title: CSession (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CSession class
- Abort method
- Close method
- Commit method
- GetTransactionInfo method
- Open method
- StartTransaction method
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8cbfa7dc712755790b3a398db3377a8faccd4525
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2018
ms.locfileid: "49084027"
---
# <a name="csession-class"></a>CSession (Clase)

Representa una sesión de acceso de la base de datos única.  
  
## <a name="syntax"></a>Sintaxis

```cpp
class CSession  
```  

## <a name="requirements"></a>Requisitos  

**Encabezado:** atldbcli.h  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[Abort](#abort)|Cancela (termina) la transacción.|  
|[Cerrar](#close)|Cierra la sesión.|  
|[Confirmación](#commit)|Confirma la transacción.|  
|[GetTransactionInfo](#gettransactioninfo)|Devuelve información relativa a una transacción.|  
|[Abrir](#open)|Se abre una nueva sesión para el objeto de origen de datos.|  
|[StartTransaction](#starttransaction)|Inicia una transacción nueva para esta sesión.|  
  
## <a name="remarks"></a>Comentarios  

Una o varias sesiones se pueden asociadas con cada conexión del proveedor (origen de datos), que se representa mediante un [CDataSource](../../data/oledb/cdatasource-class.md) objeto. Para crear un nuevo `CSession` para un `CDataSource`, llame a [CSession:: Open](../../data/oledb/csession-open.md). Para iniciar una transacción de base de datos, `CSession` proporciona el `StartTransaction` método. Una vez que se inicia una transacción, puede confirmar a ella mediante el `Commit` método, o cancelarlo mediante el `Abort` método.  
  
## <a name="abort"></a> CSession:: Abort

Finaliza la transacción.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Abort(BOID* pboidReason = NULL,   
   BOOL bRetaining = FALSE,   
   BOOL bAsync = FALSE) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  

Consulte [ITransaction:: Abort](/previous-versions/windows/desktop/ms709833) en el *referencia del programador OLE DB*.  
  
### <a name="return-value"></a>Valor devuelto  

Un HRESULT estándar. 

## <a name="close"></a> CSession:: Close

Cierra la sesión, lo que se abrió por [CSession:: Open](../../data/oledb/csession-open.md).  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
void Close() throw();  
```  
  
### <a name="remarks"></a>Comentarios  

Las versiones del `m_spOpenRowset` puntero.  

## <a name="commit"></a> CSession:: Commit

Confirma la transacción.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Commit(BOOL bRetaining = FALSE,   
   DWORD grfTC = XACTTC_SYNC,   
   DWORD grfRM = 0) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  

Consulte [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008) en el *referencia del programador OLE DB*.  
  
### <a name="return-value"></a>Valor devuelto  

Un HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  

Para obtener más información, consulte [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008).  

## <a name="gettransactioninfo"></a> CSession:: Gettransactioninfo

Devuelve información relativa a una transacción.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  

Consulte [ITransaction::GetTransactionInfo](/previous-versions/windows/desktop/ms714975) en el *referencia del programador OLE DB*.  
  
### <a name="return-value"></a>Valor devuelto  

Un HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  

Para obtener más información, consulte [ITransaction::GetTransactionInfo](/previous-versions/windows/desktop/ms714975) en el *referencia del programador de OLE DB*. 

## <a name="open"></a> CSession:: Open

Se abre una nueva sesión para el objeto de origen de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Open(const CDataSource& ds,  
   DBPROPSET *pPropSet = NULL,  
   ULONG ulPropSets = 0) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  

*DS*<br/>
[in] El origen de datos para el que la sesión consiste en Abrir.  
  
*pPropSet*<br/>
[in] Un puntero a una matriz de [DBPROPSET](/previous-versions/windows/desktop/ms714367) estructuras que contienen las propiedades y valores que desea establecer. Consulte [conjuntos de propiedades y grupos de propiedades](/previous-versions/windows/desktop/ms713696) en el *referencia del programador OLE DB* en el SDK de Windows.  
  
*ulPropSets*<br/>
[in] El número de [DBPROPSET](/previous-versions/windows/desktop/ms714367) pasan las estructuras en el *pPropSet* argumento.  
  
### <a name="return-value"></a>Valor devuelto  

Un HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  

Debe abrir el objeto de origen de datos mediante [CDataSource:: Open](../../data/oledb/cdatasource-open.md) antes de pasarlo a `CSession::Open`.  

## <a name="starttransaction"></a> CSession:: StartTransaction

Inicia una transacción nueva para esta sesión.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,  
   ULONG isoFlags = 0,  
   ITransactionOptions* pOtherOptions = NULL,  
   ULONG* pulTransactionLevel = NULL) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  

Consulte [ITransactionLocal:: StartTransaction](/previous-versions/windows/desktop/ms709786) en el *referencia del programador OLE DB*.  
  
### <a name="return-value"></a>Valor devuelto  

Un HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  

Para obtener más información, consulte [ITransactionLocal:: StartTransaction](/previous-versions/windows/desktop/ms709786) en el *referencia del programador de OLE DB*. 
  
## <a name="see-also"></a>Vea también  

[CatDB](../../visual-cpp-samples.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)