---
title: FtmBase (clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-windows
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e8a1dcd96ab42f48c91bbed2057475fa412c8925
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432810"
---
# <a name="ftmbase-class"></a>FtmBase (clase)

Representa un objeto de cálculo de referencias con subprocesamiento libre.

## <a name="syntax"></a>Sintaxis

```cpp
class FtmBase : public Microsoft::WRL::Implements<
   Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
   Microsoft::WRL::CloakedIid<IMarshal> >;
```

## <a name="remarks"></a>Comentarios

Para obtener más información, consulte [RuntimeClass (clase)](runtimeclass-class.md).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

| Name                         | Descripción                                        |
| ---------------------------- | -------------------------------------------------- |
| [Ftmbase](#ftmbase) | Inicializa una nueva instancia de la clase `FtmBase`. |

### <a name="public-methods"></a>Métodos públicos

| Name                                                               | Descripción                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Createglobalinterfacetable](#createglobalinterfacetable) | Crea una tabla de interfaz global (GIT).                                                                                                                              |
| [DisconnectObject](#disconnectobject)                     | Forzosamente libera todas las conexiones externas a un objeto. Servidor del objeto llama a la implementación del objeto de este método antes de apagar.                |
| [GetMarshalSizeMax](#getmarshalsizemax)                   | Obtenga el límite superior en el número de bytes necesarios para serializar el puntero de interfaz especificado en el objeto especificado.                                                |
| [GetUnmarshalClass](#getunmarshalclass)                   | Obtiene el CLSID que COM que se utiliza para localizar el archivo DLL que contiene el código para el proxy correspondiente. COM carga este archivo DLL para crear una instancia del proxy no inicializada. |
| [MarshalInterface](#marshalinterface)                     | Escribe los datos necesarios para inicializar un objeto de proxy en algún proceso de cliente en una secuencia.                                                                          |
| [ReleaseMarshalData](#releasemarshaldata)                 | Destruye un paquete de cálculo de referencias de datos.                                                                                                                                    |
| [UnmarshalInterface](#unmarshalinterface)                 | Inicializa a un proxy recién creado y devuelve un puntero de interfaz a ese proxy.                                                                                    |

### <a name="public-data-members"></a>Miembros de datos públicos

| Name                                | Descripción                                       |
| ----------------------------------- | ------------------------------------------------- |
| [Marshaller_](#marshaller) | Contiene una referencia para el contador de referencias de subproceso libre. |

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`FtmBase`

## <a name="requirements"></a>Requisitos

**Encabezado:** ftm.h

**Espacio de nombres:** Microsoft::WRL

## <a name="createglobalinterfacetable"></a>Createglobalinterfacetable

Crea una tabla de interfaz global (GIT).

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Parámetros

*GIT*<br/>
Cuando se completa esta operación, un puntero a una tabla de interfaz global.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte el `IGlobalInterfaceTable` tema en el `COM Interfaces` subtema del `COM Reference` tema en MSDN Library.

## <a name="disconnectobject"></a>DisconnectObject

Forzosamente libera todas las conexiones externas a un objeto. Servidor del objeto llama a la implementación del objeto de este método antes de apagar.

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>Parámetros

*dwReservado*<br/>
Reservado para uso futuro; debe ser cero.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="ftmbase"></a>Ftmbase

Inicializa una nueva instancia de la clase `FtmBase`.

```cpp
FtmBase();
```

## <a name="getmarshalsizemax"></a>GetMarshalSizeMax

Obtenga el límite superior en el número de bytes necesarios para serializar el puntero de interfaz especificado en el objeto especificado.

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
Referencia al identificador de la interfaz que se van a calcular.

*PV*<br/>
Puntero de interfaz se van a calcular; puede ser NULL.

*dwDestContext*<br/>
Contexto de destino donde se puede deserializar la interfaz especificada.

Especifique uno o más valores de enumeración MSHCTX.

Actualmente, la resolución de referencias puede producirse en otro contenedor del proceso actual (MSHCTX_INPROC) o en otro proceso en el mismo equipo que el proceso actual (MSHCTX_LOCAL).

*pvDestContext*<br/>
Reservado para uso futuro; debe ser NULL.

*mshlflags*<br/>
Marca que indica si los datos se van a calcular están que se transmitan al proceso de cliente, el caso típico, o se escriben en una tabla global, donde se puede recuperar varios clientes. Especifique uno o más valores de enumeración MSHLFLAGS.

*pSize*<br/>
Cuando se completa esta operación, el puntero para el límite superior de la cantidad de datos se escriban en la secuencia de serialización.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_FAIL o E_NOINTERFACE.

## <a name="getunmarshalclass"></a>GetUnmarshalClass

Obtiene el CLSID que COM que se utiliza para localizar el archivo DLL que contiene el código para el proxy correspondiente. COM carga este archivo DLL para crear una instancia del proxy no inicializada.

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
Referencia al identificador de la interfaz que se van a calcular.

*PV*<br/>
Puntero a la interfaz que se van a calcular; puede ser NULL si el llamador no tiene un puntero a la interfaz deseada.

*dwDestContext*<br/>
Contexto de destino donde se puede deserializar la interfaz especificada.

Especifique uno o más valores de enumeración MSHCTX.

Resolución de referencias puede producirse en otro contenedor del proceso actual (MSHCTX_INPROC) o en otro proceso en el mismo equipo que el proceso actual (MSHCTX_LOCAL).

*pvDestContext*<br/>
Reservado para uso futuro; debe ser NULL.

*mshlflags*<br/>
Cuando se completa esta operación, puntero al CLSID que se usará para crear un proxy en el proceso del cliente.

*pCid*

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, S_FALSE.

## <a name="marshalinterface"></a>MarshalInterface

Escribe los datos necesarios para inicializar un objeto de proxy en algún proceso de cliente en una secuencia.

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
Puntero a la secuencia que se usará durante la serialización.

*riid*<br/>
Referencia al identificador de la interfaz que se van a calcular. Esta interfaz debe derivarse de la `IUnknown` interfaz.

*PV*<br/>
Puntero al puntero de interfaz que se van a calcular; puede ser NULL si el llamador no tiene un puntero a la interfaz deseada.

*dwDestContext*<br/>
Contexto de destino donde se puede deserializar la interfaz especificada.

Especifique uno o más valores de enumeración MSHCTX.

Resolución de referencias puede ocurrir en otro contenedor del proceso actual (MSHCTX_INPROC) o en otro proceso en el mismo equipo que el proceso actual (MSHCTX_LOCAL).

*pvDestContext*<br/>
Reservado para uso futuro; debe ser cero.

*mshlflags*<br/>
Especifica si los datos se van a calcular están que se transmitan al proceso de cliente, el caso típico, o se escriben en una tabla global, donde se puede recuperar varios clientes.

### <a name="return-value"></a>Valor devuelto

S_OK el puntero de interfaz se serializó correctamente.

E_NOINTERFACE no se admite la interfaz especificada.

STG_E_MEDIUMFULL la secuencia está lleno.

No se pudo E_FAIL la operación.

## <a name="marshaller"></a>Marshaller_

Contiene una referencia para el contador de referencias de subproceso libre.

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="releasemarshaldata"></a>ReleaseMarshalData

Destruye un paquete de cálculo de referencias de datos.

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

## <a name="unmarshalinterface"></a>UnmarshalInterface

Inicializa a un proxy recién creado y devuelve un puntero de interfaz a ese proxy.

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>Parámetros

*pStm*<br/>
Puntero a la secuencia desde la que se puede deserializar el puntero de interfaz.

*riid*<br/>
Referencia al identificador de la interfaz que puede deserializar.

*PPV*<br/>
Cuando finalice esta operación, la dirección de una variable de puntero que recibe el puntero de interfaz solicitado en *riid*. Si esta operación se realiza correctamente, **ppv* contiene el puntero de interfaz solicitada de la interfaz que puede deserializar.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_NOINTERFACE o E_FAIL.
