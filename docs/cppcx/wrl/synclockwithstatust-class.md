---
title: SyncLockWithStatusT (Clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT class
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT, constructor
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
ms.openlocfilehash: 77bcb8336e4650de7ed01a067fa1bdd7ec0ba3e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374264"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT (Clase)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Parámetros

*SyncTraits*<br/>
Tipo que puede tomar la propiedad exclusiva o compartida de un recurso.

## <a name="remarks"></a>Observaciones

Representa un tipo que puede tomar la propiedad exclusiva o compartida de un recurso.

La `SyncLockWithStatusT` clase se utiliza para implementar las clases [Mutex](mutex-class.md) y [Semaphore.](semaphore-class.md)

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                                             | Descripción
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Inicializa una nueva instancia de la clase `SyncLockWithStatusT`.

### <a name="protected-constructors"></a>Constructores protegidos

Nombre                                                             | Descripción
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Inicializa una nueva instancia de la clase `SyncLockWithStatusT`.

### <a name="public-methods"></a>Métodos públicos

Nombre                                         | Descripción
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::GetStatus](#getstatus) | Recupera el estado de `SyncLockWithStatusT` espera del objeto actual.
[SyncLockWithStatusT::Islocked](#islocked)   | Indica si el `SyncLockWithStatusT` objeto actual posee un recurso; es decir, `SyncLockWithStatusT` el objeto está *bloqueado.*

### <a name="protected-data-members"></a>Miembros de datos protegidos

Nombre                                    | Descripción
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::status_](#status) | Contiene el resultado de la operación de espera subyacente después `SyncLockWithStatusT` de una operación de bloqueo en un objeto basado en el objeto actual.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers::Details

## <a name="synclockwithstatustgetstatus"></a><a name="getstatus"></a>SyncLockWithStatusT::GetStatus

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>Valor devuelto

El resultado de una operación de espera `SyncLockWithStatusT` en el objeto que se basa en la clase, como [Mutex](mutex-class.md) o [Semaphore](semaphore-class.md). Cero (0) indica que la operación de espera devolvió el estado señalado; de lo contrario, se produjo otro estado, como el valor de tiempo de espera transcurrido.

### <a name="remarks"></a>Observaciones

Recupera el estado de `SyncLockWithStatusT` espera del objeto actual.

La función GetStatus() recupera el valor del miembro de datos [status_](#status) subyacente. Cuando un objeto `SyncLockWithStatusT` basado en la clase realiza una operación de bloqueo, el objeto espera primero a que el objeto esté disponible. El resultado de esa operación de espera se almacena en el `status_` miembro de datos. Los valores posibles `status_` del miembro de datos son los valores devueltos de la operación de espera. Para obtener más información, consulte `WaitForSingleObjectEx()` los valores devueltos de la función en MSDN Library.

## <a name="synclockwithstatustislocked"></a><a name="islocked"></a>SyncLockWithStatusT::Islocked

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Observaciones

Indica si el `SyncLockWithStatusT` objeto actual posee un recurso; es decir, `SyncLockWithStatusT` el objeto está *bloqueado.*

### <a name="return-value"></a>Valor devuelto

**true** si `SyncLockWithStatusT` el objeto está bloqueado; de lo contrario, **false**.

## <a name="synclockwithstatuststatus_"></a><a name="status"></a>SyncLockWithStatusT::status_

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
DWORD status_;
```

### <a name="remarks"></a>Observaciones

Contiene el resultado de la operación de espera subyacente después `SyncLockWithStatusT` de una operación de bloqueo en un objeto basado en el objeto actual.

## <a name="synclockwithstatustsynclockwithstatust"></a><a name="synclockwithstatust"></a>SyncLockWithStatusT::SyncLockWithStatusT

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
SyncLockWithStatusT(
   _Inout_ SyncLockWithStatusT&& other
);

explicit SyncLockWithStatusT(
   typename SyncTraits::Type sync,
   DWORD status
);
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Una referencia rvalue `SyncLockWithStatusT` a otro objeto.

*Sincronizar*<br/>
Una referencia `SyncLockWithStatusT` a otro objeto.

*status*<br/>
El valor del [status_](#status) miembro de datos del *otro* parámetro o del parámetro *sync.*

### <a name="remarks"></a>Observaciones

Inicializa una nueva instancia de la clase `SyncLockWithStatusT`.

El primer constructor inicializa `SyncLockWithStatusT` el `SyncLockWithStatusT` objeto actual desde otro especificado por el `SyncLockWithStatusT` parámetro *other*y, a continuación, invalida el otro objeto. El segundo `protected`constructor es , `SyncLockWithStatusT` e inicializa el objeto actual en un estado no válido.
