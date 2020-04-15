---
title: Clase CSyncObject
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
ms.openlocfilehash: ebfbc185cdca2effc96ce2e6d96d05f997c52bf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365973"
---
# <a name="csyncobject-class"></a>Clase CSyncObject

Una clase virtual pura que proporciona funcionalidad común para objetos de sincronización en Win32.

## <a name="syntax"></a>Sintaxis

```
class CSyncObject : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSyncObject::CSyncObject](#csyncobject)|Construye un objeto `CSyncObject`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSyncObject::Lock](#lock)|Obtiene acceso al objeto de sincronización.|
|[CSyncObject::Unlock](#unlock)|Obtiene acceso al objeto de sincronización.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSyncObject::operator HANDLE](#operator_handle)|Proporciona acceso al objeto de sincronización.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSyncObject::m_hObject](#m_hobject)|El identificador del objeto de sincronización subyacente.|

## <a name="remarks"></a>Observaciones

La biblioteca Microsoft Foundation Class proporciona `CSyncObject`varias clases derivadas de . Se trata de [CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)y [CSemaphore](../../mfc/reference/csemaphore-class.md).

Para obtener información sobre cómo utilizar los objetos de sincronización, vea el artículo [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

## <a name="csyncobjectcsyncobject"></a><a name="csyncobject"></a>CSyncObject::CSyncObject

Construye un objeto de sincronización con el nombre proporcionado.

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>Parámetros

*pstrName*<br/>
Nombre del objeto. Si NULL, *pstrName* será null.

## <a name="csyncobjectlock"></a><a name="lock"></a>CSyncObject::Lock

Llame a esta función para obtener acceso al recurso controlado por el objeto de sincronización.

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>Parámetros

*dwTimeout*<br/>
Especifica la cantidad de tiempo en milisegundos que se debe esperar a que el objeto de sincronización esté disponible (señalizado). Si INFINITE, `Lock` esperará hasta que se señale el objeto antes de volver.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si se señala el `Lock` objeto de sincronización, se devolverá correctamente y el subproceso ahora es el propietario del objeto. Si el objeto de sincronización no `Lock` está señalizado (no está disponible), esperará a que el objeto de sincronización se señale hasta el número de milisegundos especificado en el parámetro *dwTimeOut.* Si el objeto de sincronización no se señaló `Lock` en la cantidad de tiempo especificada, devuelve el error.

## <a name="csyncobjectm_hobject"></a><a name="m_hobject"></a>CSyncObject::m_hObject

El identificador del objeto de sincronización subyacente.

```
HANDLE m_hObject;
```

## <a name="csyncobjectoperator-handle"></a><a name="operator_handle"></a>CSyncObject::operator HANDLE

Utilice este operador para obtener `CSyncObject` el identificador del objeto.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el identificador del objeto de sincronización; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Puede usar el identificador para llamar a las API de Windows directamente.

## <a name="csyncobjectunlock"></a><a name="unlock"></a>CSyncObject::Unlock

La declaración de `Unlock` no tener parámetros es una función virtual `CSyncObject`pura y debe ser reemplazada por todas las clases derivadas de .

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>Parámetros

*lCount*<br/>
No se utiliza en la implementación predeterminada.

*lpPrevCount*<br/>
No se utiliza en la implementación predeterminada.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de la declaración con dos parámetros siempre devuelve TRUE. Esta función se llama para liberar el acceso al objeto de sincronización propiedad del subproceso que realiza la llamada. La segunda declaración se proporciona para objetos de sincronización como semáforos que permiten más de un acceso a un recurso controlado.

## <a name="see-also"></a>Consulte también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
