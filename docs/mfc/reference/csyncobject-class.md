---
title: CSyncObject (clase)
ms.date: 11/04/2016
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
ms.openlocfilehash: d72d167be874d0776ce8da02784c2e0c267c9175
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547438"
---
# <a name="csyncobject-class"></a>CSyncObject (clase)

Una clase virtual pura que proporciona funcionalidad común para objetos de sincronización en Win32.

## <a name="syntax"></a>Sintaxis

```
class CSyncObject : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSyncObject::CSyncObject](#csyncobject)|Construye un objeto `CSyncObject`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSyncObject::Lock](#lock)|Obtiene acceso al objeto de sincronización.|
|[CSyncObject::Unlock](#unlock)|Obtiene acceso al objeto de sincronización.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CSyncObject::operator identificador](#operator_handle)|Proporciona acceso al objeto de sincronización.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CSyncObject::m_hObject](#m_hobject)|El identificador del objeto de sincronización subyacente.|

## <a name="remarks"></a>Comentarios

La biblioteca Microsoft Foundation Class proporciona varias clases derivadas de `CSyncObject`. Estos son [CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), y [CSemaphore](../../mfc/reference/csemaphore-class.md).

Para obtener información sobre cómo usar los objetos de sincronización, vea el artículo [Multithreading: uso de las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

##  <a name="csyncobject"></a>  CSyncObject::CSyncObject

Construye un objeto de sincronización con el nombre proporcionado.

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>Parámetros

*pstrName*<br/>
El nombre del objeto. Si es NULL, *pstrName* será null.

##  <a name="lock"></a>  CSyncObject::Lock

Llame a esta función para obtener acceso al recurso controlado por el objeto de sincronización.

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>Parámetros

*dwTimeout*<br/>
Especifica la cantidad de tiempo en milisegundos de espera para que el objeto de sincronización esté disponible (señalado). Si es infinito, `Lock` esperará hasta que se señaliza el objeto antes de devolver.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si el objeto de sincronización se señala, `Lock` devolverá correctamente y el subproceso posee ahora el objeto. Si el objeto de sincronización es no señalado (no disponible), `Lock` esperará a que el objeto de sincronización que se señale hasta el número de milisegundos especificado en el *dwTimeOut* parámetro. Si el objeto de sincronización no señalará en la cantidad especificada de tiempo, `Lock` devuelve un error.

##  <a name="m_hobject"></a>  CSyncObject::m_hObject

El identificador del objeto de sincronización subyacente.

```
HANDLE m_hObject;
```

##  <a name="operator_handle"></a>  CSyncObject::operator identificador

Utilice este operador para obtener el identificador de la `CSyncObject` objeto.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el identificador del objeto de sincronización; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Puede usar el identificador para llamar directamente a las API de Windows.

##  <a name="unlock"></a>  CSyncObject::Unlock

La declaración de `Unlock` sin parámetros es una función virtual pura y debe reemplazarse por todas las clases derivadas de `CSyncObject`.

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>Parámetros

*lCount*<br/>
Implementación predeterminada no usado.

*lpPrevCount*<br/>
Implementación predeterminada no usado.

### <a name="return-value"></a>Valor devuelto

Implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de la declaración con dos parámetros siempre devuelve TRUE. Esta función se invoca para liberar el acceso al objeto de sincronización que pertenece al subproceso que realiza la llamada. La segunda declaración se proporciona para los objetos de sincronización como semáforos que permiten tener más de un acceso de un recurso controlado.

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

