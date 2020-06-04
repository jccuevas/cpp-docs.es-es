---
title: FtmBase (clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
- ftm/Microsoft::WRL::FtmBaseCreateGlobalInterfaceTable
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
- ftm/Microsoft::WRL::FtmBase::FtmBase
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
- ftm/Microsoft::WRL::FtmBase::marshaller_
- ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
helpviewer_keywords:
- Microsoft::WRL::FtmBase class
- Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable method
- Microsoft::WRL::FtmBase::DisconnectObject method
- Microsoft::WRL::FtmBase::FtmBase, constructor
- Microsoft::WRL::FtmBase::GetMarshalSizeMax method
- Microsoft::WRL::FtmBase::GetUnmarshalClass method
- Microsoft::WRL::FtmBase::MarshalInterface method
- Microsoft::WRL::FtmBase::marshaller_ data member
- Microsoft::WRL::FtmBase::ReleaseMarshalData method
- Microsoft::WRL::FtmBase::UnmarshalInterface method
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
ms.openlocfilehash: d37cdddda8cf8894016ed80b9055fe106b1600f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371515"
---
# <a name="ftmbase-class"></a>FtmBase (clase)

Representa un objeto de cálculo de referencias con subprocesamiento libre.

## <a name="syntax"></a>Sintaxis

```cpp
class FtmBase :
    public Microsoft::WRL::Implements<
        Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
        Microsoft::WRL::CloakedIid<IMarshal>
    >;
```

## <a name="remarks"></a>Observaciones

Para obtener más información, vea [RuntimeClass (Clase)](runtimeclass-class.md).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

| Nombre                         | Descripción                                        |
| ---------------------------- | -------------------------------------------------- |
| [FtmBase::FtmBase](#ftmbase) | Inicializa una nueva instancia de la clase `FtmBase`. |

### <a name="public-methods"></a>Métodos públicos

| Nombre                                                               | Descripción                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase::CreateGlobalInterfaceTable](#createglobalinterfacetable) | Crea una tabla de interfaz global (GIT).                                                                                                                              |
| [FtmBase::DisconnectObject](#disconnectobject)                     | Libera forzosamente todas las conexiones externas a un objeto. El servidor del objeto llama a la implementación de este método del objeto antes de cerrar.                |
| [FtmBase::GetMarshalSizeMax](#getmarshalsizemax)                   | Obtenga el límite superior en el número de bytes necesarios para calcular las referencias del puntero de interfaz especificado en el objeto especificado.                                                |
| [FtmBase::GetUnmarshalClass](#getunmarshalclass)                   | Obtiene el CLSID que COM utiliza para buscar el archivo DLL que contiene el código para el proxy correspondiente. COM carga este archivo DLL para crear una instancia no inicializada del proxy. |
| [FtmBase::MarshalInterface](#marshalinterface)                     | Escribe en una secuencia los datos necesarios para inicializar un objeto proxy en algún proceso de cliente.                                                                          |
| [FtmBase::ReleaseMarshalData](#releasemarshaldata)                 | Destruye un paquete de datos serializados.                                                                                                                                    |
| [FtmBase::UnmarshalInterface](#unmarshalinterface)                 | Inicializa un proxy recién creado y devuelve un puntero de interfaz a ese proxy.                                                                                    |

### <a name="public-data-members"></a>Miembros de datos públicos

| Nombre                                | Descripción                                       |
| ----------------------------------- | ------------------------------------------------- |
| [FtmBase::marshaller_](#marshaller) | Contiene una referencia al serializador de subprocesos libres. |

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`FtmBase`

## <a name="requirements"></a>Requisitos

**Encabezado:** ftm.h

**Espacio de nombres:** Microsoft::WRL

## <a name="ftmbasecreateglobalinterfacetable"></a><a name="createglobalinterfacetable"></a>FtmBase::CreateGlobalInterfaceTable

Crea una tabla de interfaz global (GIT).

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Parámetros

*Git*<br/>
Cuando se completa esta operación, un puntero a una tabla de interfaz global.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Observaciones

Para obtener más `IGlobalInterfaceTable` información, `COM Interfaces` consulte el `COM Reference` tema en el subtema del tema en MSDN Library.

## <a name="ftmbasedisconnectobject"></a><a name="disconnectobject"></a>FtmBase::DisconnectObject

Libera forzosamente todas las conexiones externas a un objeto. El servidor del objeto llama a la implementación de este método del objeto antes de cerrar.

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>Parámetros

*dwReserved*<br/>
Reservado para uso futuro; debe ser cero.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="ftmbaseftmbase"></a><a name="ftmbase"></a>FtmBase::FtmBase

Inicializa una nueva instancia de la clase `FtmBase`.

```cpp
FtmBase();
```

## <a name="ftmbasegetmarshalsizemax"></a><a name="getmarshalsizemax"></a>FtmBase::GetMarshalSizeMax

Obtenga el límite superior en el número de bytes necesarios para calcular las referencias del puntero de interfaz especificado en el objeto especificado.

```cpp
STDMETHODIMP GetMarshalSizeMax(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out DWORD *pSize
) override;
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Referencia al identificador de la interfaz que se va a serializar.

*Pv*<br/>
Puntero de interfaz que se va a serializar; puede ser NULL.

*dwDestContext*<br/>
Contexto de destino donde se va a desclasificar la interfaz especificada.

Especifique uno o varios valores de enumeración MSHCTX.

Actualmente, el desclasificar puede producirse en otro apartamento del proceso actual (MSHCTX_INPROC) o en otro proceso en el mismo equipo que el proceso actual (MSHCTX_LOCAL).

*pvDestContext*<br/>
Reservado para uso futuro; debe ser NULL.

*mshlflags*<br/>
Marcador que indica si los datos que se van a serializar se transmitirán de vuelta al proceso de cliente (el caso típico) o se escribirán en una tabla global, donde varios clientes pueden recuperarlos. Especifique uno o varios valores de enumeración MSHLFLAGS.

*pSize*<br/>
Cuando se complete esta operación, puntero al límite superior en la cantidad de datos que se escribirán en la secuencia de cálculo de referencias.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, E_FAIL o E_NOINTERFACE.

## <a name="ftmbasegetunmarshalclass"></a><a name="getunmarshalclass"></a>FtmBase::GetUnmarshalClass

Obtiene el CLSID que COM utiliza para buscar el archivo DLL que contiene el código para el proxy correspondiente. COM carga este archivo DLL para crear una instancia no inicializada del proxy.

```cpp
STDMETHODIMP GetUnmarshalClass(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out CLSID *pCid
) override;
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Referencia al identificador de la interfaz que se va a serializar.

*Pv*<br/>
Puntero a la interfaz que se va a serializar; puede ser NULL si el llamador no tiene un puntero a la interfaz deseada.

*dwDestContext*<br/>
Contexto de destino donde se va a desclasificar la interfaz especificada.

Especifique uno o varios valores de enumeración MSHCTX.

El desclasificar puede producirse en otro apartamento del proceso actual (MSHCTX_INPROC) o en otro proceso en el mismo equipo que el proceso actual (MSHCTX_LOCAL).

*pvDestContext*<br/>
Reservado para uso futuro; debe ser NULL.

*mshlflags*<br/>
Cuando se completa esta operación, puntero al CLSID que se usará para crear un proxy en el proceso de cliente.

*pCid*

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, S_FALSE.

## <a name="ftmbasemarshalinterface"></a><a name="marshalinterface"></a>FtmBase::MarshalInterface

Escribe en una secuencia los datos necesarios para inicializar un objeto proxy en algún proceso de cliente.

```cpp
STDMETHODIMP MarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags
) override;
```

### <a name="parameters"></a>Parámetros

*pStm*<br/>
Puntero a la secuencia que se usará durante el cálculo de referencias.

*riid*<br/>
Referencia al identificador de la interfaz que se va a serializar. Esta interfaz debe derivarse de la interfaz `IUnknown` .

*Pv*<br/>
Puntero al puntero de interfaz que se va a serializar; puede ser NULL si el llamador no tiene un puntero a la interfaz deseada.

*dwDestContext*<br/>
Contexto de destino donde se va a desclasificar la interfaz especificada.

Especifique uno o varios valores de enumeración MSHCTX.

El desclasificar puede producirse en otro apartamento del proceso actual (MSHCTX_INPROC) o en otro proceso en el mismo equipo que el proceso actual (MSHCTX_LOCAL).

*pvDestContext*<br/>
Reservado para uso futuro; debe ser cero.

*mshlflags*<br/>
Especifica si los datos que se van a serializar se transmitirán de vuelta al proceso de cliente (el caso típico) o se escribirán en una tabla global, donde varios clientes pueden recuperarlos.

### <a name="return-value"></a>Valor devuelto

S_OK El puntero de interfaz se ha serializado correctamente.

E_NOINTERFACE No se admite la interfaz especificada.

STG_E_MEDIUMFULL La secuencia está llena.

E_FAIL Error en la operación.

## <a name="ftmbasemarshaller_"></a><a name="marshaller"></a>FtmBase::marshaller_

Contiene una referencia al serializador de subprocesos libres.

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="ftmbasereleasemarshaldata"></a><a name="releasemarshaldata"></a>FtmBase::ReleaseMarshalData

Destruye un paquete de datos serializados.

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>Parámetros

*pStm*<br/>
Puntero a una secuencia que contiene el paquete de datos que se va a destruir.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="ftmbaseunmarshalinterface"></a><a name="unmarshalinterface"></a>FtmBase::UnmarshalInterface

Inicializa un proxy recién creado y devuelve un puntero de interfaz a ese proxy.

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>Parámetros

*pStm*<br/>
Puntero a la secuencia desde la que se va a desclasificar el puntero de interfaz.

*riid*<br/>
Referencia al identificador de la interfaz que se va a desclasificar.

*Ppv*<br/>
Cuando se completa esta operación, la dirección de una variable de puntero que recibe el puntero de interfaz solicitado en *riid*. Si esta operación se realiza correctamente, **ppv* contiene el puntero de interfaz solicitado de la interfaz que se va a desclasificar.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, E_NOINTERFACE o E_FAIL.
