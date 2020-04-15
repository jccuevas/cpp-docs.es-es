---
title: CSingleLock (clase)
ms.date: 11/04/2016
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
ms.openlocfilehash: 231397228d94e58665602453b5d377571e24a967
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318271"
---
# <a name="csinglelock-class"></a>CSingleLock (clase)

Representa el mecanismo de control de acceso utilizado para controlar el acceso a un recurso en un programa de multithreading.

## <a name="syntax"></a>Sintaxis

```
class CSingleLock
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSingleLock::CSingleLock](#csinglelock)|Construye un objeto `CSingleLock`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSingleLock::IsLocked](#islocked)|Determina si el objeto está bloqueado.|
|[CSingleLock::Lock](#lock)|Espera en un objeto de sincronización.|
|[CSingleLock::Unlock](#unlock)|Libera un objeto de sincronización.|

## <a name="remarks"></a>Observaciones

`CSingleLock`no tiene una clase base.

Para utilizar las clases de sincronización [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)y [CEvent](../../mfc/reference/cevent-class.md), debe crear un `CSingleLock` objeto o [CMultiLock](../../mfc/reference/cmultilock-class.md) para esperar y liberar el objeto de sincronización. Utilícelo `CSingleLock` cuando solo necesite esperar en un objeto a la vez. Utilícelo `CMultiLock` cuando haya varios objetos que pueda usar en un momento determinado.

Para usar `CSingleLock` un objeto, llame a su constructor dentro de una función miembro en la clase del recurso controlado. A continuación, llame a la [IsLocked](#islocked) función miembro para determinar si el recurso está disponible. Si es así, continúe con el resto de la función miembro. Si el recurso no está disponible, espere a que se libere una cantidad de tiempo especificada para que se libere el recurso o devuelva un error. Una vez completado el uso del [Unlock](#unlock) recurso, `CSingleLock` llame a la función Unlock `CSingleLock` si el objeto se va a utilizar de nuevo o permita que se destruya el objeto.

`CSingleLock`objetos requieren la presencia de un objeto derivado de [CSyncObject](../../mfc/reference/csyncobject-class.md). Normalmente se trata de un miembro de datos de la clase del recurso controlado. Para obtener más información `CSingleLock` sobre cómo utilizar objetos, vea el artículo [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CSingleLock`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

## <a name="csinglelockcsinglelock"></a><a name="csinglelock"></a>CSingleLock::CSingleLock

Construye un objeto `CSingleLock`.

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parámetros

*pObject*<br/>
Señala el objeto de sincronización al que se va a acceder. No puede ser NULL.

*bInitialLock*<br/>
Especifica si se debe intentar inicialmente tener acceso al objeto proporcionado.

### <a name="remarks"></a>Observaciones

Esta función se llama generalmente desde dentro de una función miembro de acceso del recurso controlado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

## <a name="csinglelockislocked"></a><a name="islocked"></a>CSingleLock::IsLocked

Determina si el objeto `CSingleLock` asociado al objeto no está señalizado (no está disponible).

```
BOOL IsLocked();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto está bloqueado; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

## <a name="csinglelocklock"></a><a name="lock"></a>CSingleLock::Lock

Llame a esta función para obtener acceso al recurso `CSingleLock` controlado por el objeto de sincronización proporcionado al constructor.

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>Parámetros

*dwTimeOut*<br/>
Especifica la cantidad de tiempo que debe esperar a que el objeto de sincronización esté disponible (señalizado). Si INFINITE, `Lock` esperará hasta que se señale el objeto antes de volver.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si se señala el `Lock` objeto de sincronización, se devolverá correctamente y el subproceso ahora es el propietario del objeto. Si el objeto de sincronización no `Lock` está señalizado (no está disponible), esperará a que el objeto de sincronización se señale hasta el número de milisegundos especificado en el parámetro *dwTimeOut.* Si el objeto de sincronización no se señaló `Lock` en la cantidad de tiempo especificada, devuelve el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="csinglelockunlock"></a><a name="unlock"></a>CSingleLock::Unlock

Libera el objeto `CSingleLock`de sincronización propiedad de .

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parámetros

*lCount*<br/>
Número de accesos a la versión. Debe ser mayor que 0. Si el importe especificado haría que el recuento del objeto supere su máximo, el recuento no cambia y la función devuelve FALSE.

*lPrevCount*<br/>
Apunta a una variable para recibir el recuento anterior del objeto de sincronización. Si NULL, no se devuelve el recuento anterior.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función `CSingleLock`es llamada por 's destructor.

Si necesita liberar más de un recuento de accesos de un `Unlock` semáforo, utilice la segunda forma de liberar y especifique el número de accesos que desea liberar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMultiLock (clase)](../../mfc/reference/cmultilock-class.md)
