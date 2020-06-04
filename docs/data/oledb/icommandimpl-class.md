---
title: ICommandImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ICommandImpl
- ICommandImpl::Cancel
- Cancel
- ICommandImpl.Cancel
- ICommandImpl::CancelExecution
- ATL::ICommandImpl::CancelExecution
- ATL.ICommandImpl.CancelExecution
- CancelExecution
- ICommandImpl.CancelExecution
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
- ICommandImpl::Execute
- ICommandImpl.Execute
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
- ATL.ICommandImpl.ICommandImpl
- ATL::ICommandImpl::ICommandImpl
- ICommandImpl::ICommandImpl
- ICommandImpl.ICommandImpl
- ICommandImpl::m_bCancel
- ICommandImpl.m_bCancel
- m_bCancel
- ATL::ICommandImpl::m_bCancel
- ATL.ICommandImpl.m_bCancel
- ICommandImpl::m_bCancelWhenExecuting
- ICommandImpl.m_bCancelWhenExecuting
- ATL::ICommandImpl::m_bCancelWhenExecuting
- m_bCancelWhenExecuting
- ATL.ICommandImpl.m_bCancelWhenExecuting
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
helpviewer_keywords:
- ICommandImpl class
- Cancel method
- CancelExecution method
- CreateRowset method
- Execute method
- GetDBSession method
- ICommandImpl constructor
- ICommandImpl class, constructor
- m_bCancel
- m_bCancelWhenExecuting
- m_bIsExecuting
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
ms.openlocfilehash: f04885ef61841ac20f87ab07ce73d3c9342fe39c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212167"
---
# <a name="icommandimpl-class"></a>ICommandImpl (Clase)

Proporciona la implementación para la interfaz [ICommand](/previous-versions/windows/desktop/ms709737(v=vs.85)) .

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `ICommandImpl`.

*CommandBase*<br/>
Interfaz de comandos. El valor predeterminado es `ICommand`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[Cancelar](#cancel)|Cancela la ejecución del comando actual.|
|[CancelExecution](#cancelexecution)|Cancela la ejecución del comando actual.|
|[CreateRowset](#createrowset)|Crea un objeto de conjunto de filas.|
|[Ejecutar](#execute)|Ejecuta el comando.|
|[GetDBSession](#getdbsession)|Devuelve un puntero de interfaz a la sesión que creó el comando.|
|[ICommandImpl](#icommandimpl)|El constructor.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_bCancel](#bcancel)|Indica si el comando se va a cancelar.|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|Indica si el comando se va a cancelar cuando se ejecute.|
|[m_bIsExecuting](#bisexecuting)|Indica si el comando se está ejecutando actualmente.|

## <a name="remarks"></a>Observaciones

Interfaz obligatoria en el objeto de comando.

## <a name="icommandimplcancel"></a><a name="cancel"></a>ICommandImpl:: CANCEL

Cancela la ejecución del comando actual.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>Observaciones

Vea [ICommand:: CANCEL](/previous-versions/windows/desktop/ms714402(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="icommandimplcancelexecution"></a><a name="cancelexecution"></a>ICommandImpl:: CancelExecution

Cancela la ejecución del comando actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CancelExecution();
```

## <a name="icommandimplcreaterowset"></a><a name="createrowset"></a>ICommandImpl:: CreateRowset

Llamado por [Execute](../../data/oledb/icommandimpl-execute.md) para crear un conjunto de filas único.

### <a name="syntax"></a>Sintaxis

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>Parámetros

*RowsetClass*<br/>
Un miembro de clase de plantilla que representa la clase de conjunto de filas del usuario. Normalmente generado por el asistente.

*pUnkOuter*<br/>
de Puntero al control `IUnknown` interfaz si el conjunto de filas se crea como parte de un agregado; de lo contrario, es NULL.

*riid*<br/>
de Corresponde a *riid* en `ICommand::Execute`.

*pParams*<br/>
[in/out] Corresponde a *pParams* en `ICommand::Execute`.

*pcRowsAffected*<br/>
Corresponde a *pcRowsAffected* en `ICommand::Execute`.

*ppRowset*<br/>
[in/out] Corresponde a *ppRowset* en `ICommand::Execute`.

*pRowsetObj*<br/>
enuncia Un puntero a un objeto de conjunto de filas. Normalmente, este parámetro no se usa, pero se puede usar si debe realizar más trabajo en el conjunto de filas antes de pasarlo a un objeto COM. La duración de *pRowsetObj* está limitada por *ppRowset*.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar. Consulte `ICommand::Execute` para obtener una lista de valores típicos.

### <a name="remarks"></a>Observaciones

Para crear más de un conjunto de filas, o para proporcionar sus propias condiciones para la creación de conjuntos de filas diferentes, coloque diferentes llamadas a `CreateRowset` desde dentro de `Execute`.

Vea [ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) en la *Referencia del programador de OLE DB.*

## <a name="icommandimplexecute"></a><a name="execute"></a>ICommandImpl:: Execute

Ejecuta el comando.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Execute(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>Parámetros

Vea [ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

La interfaz de salida solicitada será una interfaz adquirida del objeto de conjunto de filas que crea esta función.

`Execute` llama a [CreateRowset](../../data/oledb/icommandimpl-createrowset.md). Invalide la implementación predeterminada para crear más de un conjunto de filas o para proporcionar sus propias condiciones para crear conjuntos de filas diferentes.

## <a name="icommandimplgetdbsession"></a><a name="getdbsession"></a>ICommandImpl:: GetDBSession

Devuelve un puntero de interfaz a la sesión que creó el comando.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>Parámetros

Vea [ICommand:: GetDBSession](/previous-versions/windows/desktop/ms719622(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

Resulta útil para recuperar propiedades de la sesión.

## <a name="icommandimplicommandimpl"></a><a name="icommandimpl"></a>ICommandImpl:: ICommandImpl

El constructor.

### <a name="syntax"></a>Sintaxis

```cpp
ICommandImpl();
```

## <a name="icommandimplm_bcancel"></a><a name="bcancel"></a>ICommandImpl:: m_bCancel

Indica si se ha cancelado el comando.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>Observaciones

Puede recuperar esta variable en el método `Execute` de la clase Command y cancelarla según corresponda.

## <a name="icommandimplm_bcancelwhenexecuting"></a><a name="bcancelwhenexecuting"></a>ICommandImpl:: m_bCancelWhenExecuting

Indica si el comando se puede cancelar cuando se ejecuta.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>Observaciones

El valor predeterminado **es true** (se puede cancelar).

## <a name="icommandimplm_bisexecuting"></a><a name="bisexecuting"></a>ICommandImpl:: m_bIsExecuting

Indica si el comando se está ejecutando actualmente.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>Observaciones

El método `Execute` de la clase Command puede establecer esta variable en **true**.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
