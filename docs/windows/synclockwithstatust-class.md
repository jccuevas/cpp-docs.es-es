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
ms.openlocfilehash: a3c5c4306dd039a792fe0fd1e57f04d37cc67731
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663871"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT (Clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Parámetros

*SyncTraits*<br/>
Un tipo que puede tomar exclusivo o propiedad compartida de un recurso.

## <a name="remarks"></a>Comentarios

Representa un tipo que puede tardar exclusivo o propiedad compartida de un recurso.

El `SyncLockWithStatusT` clase se utiliza para implementar el [Mutex](../windows/mutex-class1.md) y [semáforo](../windows/semaphore-class.md) clases.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                                             | Descripción
---------------------------------------------------------------- | --------------------------------------------------------------
[Synclockwithstatust](#synclockwithstatust) | Inicializa una nueva instancia de la clase `SyncLockWithStatusT`.

### <a name="protected-constructors"></a>Constructores protegidos

Name                                                             | Descripción
---------------------------------------------------------------- | --------------------------------------------------------------
[Synclockwithstatust](#synclockwithstatust) | Inicializa una nueva instancia de la clase `SyncLockWithStatusT`.

### <a name="public-methods"></a>Métodos públicos

Name                                         | Descripción
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[Synclockwithstatust](#getstatus) | Recupera el estado de espera de la actual `SyncLockWithStatusT` objeto.
[Synclockwithstatust](#islocked)   | Indica si el actual `SyncLockWithStatusT` objeto posee un recurso; es decir, el `SyncLockWithStatusT` objeto es *bloqueado*.

### <a name="protected-data-members"></a>Miembros de datos protegidos

nombre                                    | Descripción
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[Status_](#status) | Contiene el resultado de la operación de espera subyacente después de una operación de bloqueo en un objeto basado en la actual `SyncLockWithStatusT` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="getstatus"></a>Synclockwithstatust

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>Valor devuelto

El resultado de una operación de espera en el objeto que se basa en el `SyncLockWithStatusT` clase, como un [Mutex](../windows/mutex-class1.md) o [semáforo](../windows/semaphore-class.md). Cero (0) indica que la operación de espera devuelve el estado señalado; en caso contrario, se produjo otro estado, como el valor de tiempo de espera transcurrido.

### <a name="remarks"></a>Comentarios

Recupera el estado de espera de la actual `SyncLockWithStatusT` objeto.

La función GetStatus() recupera el valor de subyacente [status_](#status) miembro de datos. Cuando un objeto basado en la `SyncLockWithStatusT` clase realiza una operación de bloqueo, el objeto de espera en primer lugar el objeto esté disponible. El resultado de esa operación de espera se almacena en el `status_` miembro de datos. Los valores posibles de la `status_` miembro de datos son los valores devueltos de la operación de espera. Para obtener más información, vea los valores devueltos de la `WaitForSingleObjectEx()` función de la biblioteca de MSDN.

## <a name="islocked"></a>Synclockwithstatust

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Comentarios

Indica si el actual `SyncLockWithStatusT` objeto posee un recurso; es decir, el `SyncLockWithStatusT` objeto es *bloqueado*.

### <a name="return-value"></a>Valor devuelto

**True** si el `SyncLockWithStatusT` objeto está bloqueado; en caso contrario, **false**.

## <a name="status"></a>Status_

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
DWORD status_;
```

### <a name="remarks"></a>Comentarios

Contiene el resultado de la operación de espera subyacente después de una operación de bloqueo en un objeto basado en la actual `SyncLockWithStatusT` objeto.

## <a name="synclockwithstatust"></a>Synclockwithstatust

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

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

*other*<br/>
Una referencia rvalue a otro `SyncLockWithStatusT` objeto.

*sync*<br/>
Una referencia a otro `SyncLockWithStatusT` objeto.

*status*<br/>
El valor de la [status_](#status) miembro de datos de la *otros* parámetro o el *sincronización* parámetro.

### <a name="remarks"></a>Comentarios

Inicializa una nueva instancia de la clase `SyncLockWithStatusT`.

El primer constructor inicializa actual `SyncLockWithStatusT` objeto desde otro `SyncLockWithStatusT` especificado por el parámetro *otros*y, a continuación, se invalidan otro `SyncLockWithStatusT` objeto. Es el segundo constructor `protected`e inicializa actual `SyncLockWithStatusT` objeto a un estado no válido.
