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
ms.openlocfilehash: 2d65af79971aab88884efe1f92d1090194b737d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459571"
---
# <a name="csinglelock-class"></a>CSingleLock (clase)

Representa el mecanismo de control de acceso utilizado para controlar el acceso a un recurso en un programa de multithreading.

## <a name="syntax"></a>Sintaxis

```
class CSingleLock
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSingleLock::CSingleLock](#csinglelock)|Construye un objeto `CSingleLock`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSingleLock::IsLocked](#islocked)|Determina si el objeto está bloqueado.|
|[CSingleLock::Lock](#lock)|Se espera en un objeto de sincronización.|
|[CSingleLock::Unlock](#unlock)|Libera un objeto de sincronización.|

## <a name="remarks"></a>Comentarios

`CSingleLock` no tiene una clase base.

Para poder usar las clases de sincronización [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), y [CEvent](../../mfc/reference/cevent-class.md), se debe crear un `CSingleLock` o [CMultiLock](../../mfc/reference/cmultilock-class.md) objeto se va a esperar y liberar el objeto de sincronización. Use `CSingleLock` cuando sólo deba esperar en un objeto a la vez. Usar `CMultiLock` cuando hay varios objetos que puede usar en un momento determinado.

Para usar un `CSingleLock` de objetos, llamar a su constructor dentro de una función miembro de clase del recurso controlado. A continuación, llame a la [IsLocked](#islocked) función miembro para determinar si el recurso está disponible. Si es así, continúe con el resto de la función miembro. Si el recurso no está disponible, espere durante un período de tiempo que se libere el recurso especificado, o devolver un error. Una vez completado el uso del recurso, llame a la [Unlock](#unlock) funcionar si el `CSingleLock` objeto consiste en volver a utilizar o permitir el `CSingleLock` destrucción del objeto.

`CSingleLock` objetos requieren la presencia de un objeto derivado de [CSyncObject](../../mfc/reference/csyncobject-class.md). Esto suele ser un miembro de datos de clase del recurso controlado. Para obtener más información sobre cómo usar `CSingleLock` objetos, consulte el artículo [Multithreading: uso de las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CSingleLock`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

##  <a name="csinglelock"></a>  CSingleLock::CSingleLock

Construye un objeto `CSingleLock`.

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parámetros

*pObject*<br/>
Puntos a tener acceso el objeto de sincronización. No puede ser nulo.

*bInitialLock*<br/>
Especifica si un intento de obtener acceso al objeto proporcionado.

### <a name="remarks"></a>Comentarios

Por lo general, esta función se llama desde dentro de una función miembro de acceso del recurso controlado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

##  <a name="islocked"></a>  CSingleLock::IsLocked

Determina si el objeto asociado con el `CSingleLock` objeto es no señalado (no disponible).

```
BOOL IsLocked();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto está bloqueado; en caso contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

##  <a name="lock"></a>  CSingleLock::Lock

Llame a esta función para obtener acceso al recurso controlado por el objeto de sincronización proporcionado a la `CSingleLock` constructor.

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>Parámetros

*dwTimeOut*<br/>
Especifica la cantidad de tiempo de espera para que el objeto de sincronización esté disponible (señalado). Si es infinito, `Lock` esperará hasta que se señaliza el objeto antes de devolver.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si el objeto de sincronización se señala, `Lock` devolverá correctamente y el subproceso posee ahora el objeto. Si el objeto de sincronización es no señalado (no disponible), `Lock` esperará a que el objeto de sincronización que se señale hasta el número de milisegundos especificado en el *dwTimeOut* parámetro. Si el objeto de sincronización no señalará en la cantidad especificada de tiempo, `Lock` devuelve un error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

##  <a name="unlock"></a>  CSingleLock::Unlock

Libera el objeto de sincronización que pertenecen a `CSingleLock`.

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parámetros

*lCount*<br/>
Número de accesos a liberar. Debe ser mayor que 0. Si la cantidad especificada produciría el recuento del objeto supere el máximo, no se cambia el recuento y la función devuelve FALSE.

*lPrevCount*<br/>
Señala a una variable que recibirá el recuento anterior del objeto de sincronización. Si es NULL, no se devuelve el recuento anterior.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función se invoca `CSingleLock`del destructor.

Si necesita liberar más de un número de acceso de un semáforo, use la segunda forma de `Unlock` y especifique el número de accesos a liberar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMultiLock (clase)](../../mfc/reference/cmultilock-class.md)
