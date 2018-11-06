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
- ICommandImpl
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
ms.openlocfilehash: a3520ed34f356c70163b9063178df48e4bc66a7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583591"
---
# <a name="icommandimpl-class"></a>ICommandImpl (Clase)

Proporciona la implementación de la [ICommand](/previous-versions/windows/desktop/ms709737) interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `ICommandImpl`.

*CommandBase*<br/>
Una interfaz de comandos. De manera predeterminada, es `ICommand`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Cancelar](#cancel)|Cancela la ejecución del comando actual.|
|[CancelExecution](#cancelexecution)|Cancela la ejecución del comando actual.|
|[CreateRowset](#createrowset)|Crea un objeto de conjunto de filas.|
|[Execute](#execute)|Ejecuta el comando.|
|[GetDBSession](#getdbsession)|Devuelve un puntero de interfaz a la sesión que creó el comando.|
|[ICommandImpl](#icommandimpl)|El constructor.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_bCancel](#bcancel)|Indica si el comando es cancelarse.|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|Indica si se cancelará cuando se ejecuta el comando.|
|[m_bIsExecuting](#bisexecuting)|Indica si el comando se está ejecutando actualmente.|

## <a name="remarks"></a>Comentarios

Una interfaz obligatoria en el objeto de comando.

## <a name="cancel"></a> ICommandImpl:: Cancel

Cancela la ejecución del comando actual.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>Comentarios

Consulte [ICommand::Cancel](/previous-versions/windows/desktop/ms714402) en el *referencia del programador OLE DB*.

## <a name="cancelexecution"></a> ICommandImpl:: Cancelexecution

Cancela la ejecución del comando actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CancelExecution();
```

## <a name="createrowset"></a> ICommandImpl:: CreateRowset

Lo llama [Execute](../../data/oledb/icommandimpl-execute.md) para crear un conjunto de filas único.

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
Un miembro de clase de plantilla que representa la clase de conjunto de filas del usuario. Normalmente, generado por el asistente.

*pUnkOuter*<br/>
[in] Un puntero al control `IUnknown` si se está creando el conjunto de filas como parte de un agregado de la interfaz; en caso contrario, es null.

*riid*<br/>
[in] Corresponde a *riid* en `ICommand::Execute`.

*pParams*<br/>
[entrada/salida] Corresponde a *pParams* en `ICommand::Execute`.

*pcRowsAffected*<br/>
Corresponde a *pcRowsAffected* en `ICommand::Execute`.

*ppRowset*<br/>
[entrada/salida] Corresponde a *ppRowset* en `ICommand::Execute`.

*pRowsetObj*<br/>
[out] Un puntero a un objeto de conjunto de filas. Normalmente no se usa este parámetro, pero puede usarse si tiene que realizar más trabajo en el conjunto de filas antes de pasarlo a un objeto COM. La duración de *pRowsetObj* está limitado por *ppRowset*.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar. Consulte `ICommand::Execute` para obtener una lista de los valores típicos.

### <a name="remarks"></a>Comentarios

Para crear más de un conjunto de filas, o para proporcionar sus propias condiciones para la creación de conjuntos de filas diferentes, realizar llamadas diferentes a `CreateRowset` desde `Execute`.

Consulte [ICommand:: Execute](/previous-versions/windows/desktop/ms718095) en el *referencia del programador OLE DB.*

## <a name="execute"></a> ICommandImpl:: Execute

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

Consulte [ICommand:: Execute](/previous-versions/windows/desktop/ms718095) en el *referencia del programador OLE DB*.

### <a name="remarks"></a>Comentarios

Solicita la interfaz de salida será una interfaz adquirida desde el objeto de conjunto de filas que crea esta función.

`Execute` las llamadas [CreateRowset](../../data/oledb/icommandimpl-createrowset.md). Invalidar la implementación predeterminada para crear más de un conjunto de filas o para proporcionar sus propias condiciones para la creación de conjuntos de filas diferentes.

## <a name="getdbsession"></a> ICommandImpl:: Getdbsession

Devuelve un puntero de interfaz a la sesión que creó el comando.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>Parámetros

Consulte [ICommand::GetDBSession](/previous-versions/windows/desktop/ms719622) en el *referencia del programador OLE DB*.

### <a name="remarks"></a>Comentarios

Es útil para recuperar las propiedades de la sesión.

## <a name="icommandimpl"></a> ICommandImpl:: ICommandImpl

El constructor.

### <a name="syntax"></a>Sintaxis

```cpp
ICommandImpl();
```

## <a name="bcancel"></a> ICommandImpl:: M_bcancel

Indica si se ha cancelado el comando.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>Comentarios

Puede recuperar esta variable en el `Execute` método de la clase de comando y cancelar según corresponda.

## <a name="bcancelwhenexecuting"></a> ICommandImpl:: M_bcancelwhenexecuting

Indica si se puede cancelar el comando cuando se ejecuta.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>Comentarios

El valor predeterminado es **true** (se puede cancelar).

## <a name="bisexecuting"></a> ICommandImpl:: M_bisexecuting

Indica si el comando se está ejecutando actualmente.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>Comentarios

El `Execute` método de la clase de comando puede establecer esta variable en **true**.

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)