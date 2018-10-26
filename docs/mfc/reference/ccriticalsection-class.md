---
title: CCriticalSection (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
dev_langs:
- C++
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 159d452c3b0a813c52d8486f52d67b9817c3a558
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069287"
---
# <a name="ccriticalsection-class"></a>CCriticalSection (clase)

Representa una "sección crítica", un objeto de sincronización que permite que un subproceso cada vez para tener acceso a un recurso o sección de código.

## <a name="syntax"></a>Sintaxis

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CCriticalSection::CCriticalSection](#ccriticalsection)|Construye un objeto `CCriticalSection`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CCriticalSection::Lock](#lock)|Usar para tener acceso a la `CCriticalSection` objeto.|
|[CCriticalSection::Unlock](#unlock)|Libera el objeto `CCriticalSection`.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CCriticalSection::operator CRITICAL_SECTION *](#operator_critical_section_star)|Recupera un puntero al objeto CRITICAL_SECTION interno.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CCriticalSection::m_sect](#m_sect)|Un objeto CRITICAL_SECTION.|

## <a name="remarks"></a>Comentarios

Las secciones críticas son útiles cuando solo un subproceso a la vez puede permitir modificar datos o algún otro recurso controlado. Por ejemplo, agregar nodos a una lista vinculada es un proceso que solo se permite un subproceso a la vez. Mediante el uso de un `CCriticalSection` objeto para controlar la lista vinculada, solo un subproceso a la vez puede obtener acceso a la lista.

> [!NOTE]
>  La funcionalidad de la `CCriticalSection` clase proporciona un objeto CRITICAL_SECTION de Win32.

Las secciones críticas se utilizan en lugar de las exclusiones mutuas (consulte [CMutex](../../mfc/reference/cmutex-class.md)) cuando la velocidad es fundamental y no se usará el recurso a través de los límites del proceso.

Hay dos métodos para utilizar un `CCriticalSection` objeto: independientes como incrustadas en una clase.

- Método independiente que se usará una independiente `CCriticalSection` objeto, construya el `CCriticalSection` objeto cuando sea necesario. Después de una devolución es correcta desde el constructor, bloquear explícitamente el objeto con una llamada a [bloqueo](#lock). Llame a [Unlock](#unlock) cuando haya terminado obtener acceso a la sección crítica. Este método, mientras mejor a alguien leer el código fuente, es más propenso a errores, como debe recordar bloquear y desbloquear la sección crítica antes y después de acceso.

   Un método preferible consiste en usar el [CSingleLock](../../mfc/reference/csinglelock-class.md) clase. También tiene un `Lock` y `Unlock` método, pero no tiene que preocuparse por desbloqueando el recurso si se produce una excepción.

- Incrustar el método también puede compartir una clase con varios subprocesos mediante la adición de un `CCriticalSection`-miembro de datos de tipo a la clase y bloquear el miembro de datos cuando sea necesario.

Para obtener más información sobre el uso de `CCriticalSection` objetos, consulte el artículo [Multithreading: uso de las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

##  <a name="ccriticalsection"></a>  CCriticalSection::CCriticalSection

Construye un objeto `CCriticalSection`.

```
CCriticalSection();
```

### <a name="remarks"></a>Comentarios

Para obtener acceso a o liberar una `CCriticalSection` , cree un [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llamar a su [bloqueo](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones miembro. Si el `CCriticalSection` se usan objetos independientes, llame a su [Unlock](#unlock) función miembro para liberarlo.

Si el constructor no se puede asignar la memoria necesaria del sistema, una excepción de memoria (de tipo [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) se inicia automáticamente.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CCriticalSection::Lock](#lock).

##  <a name="lock"></a>  CCriticalSection::Lock

Llame a esta función miembro para tener acceso al objeto de sección crítica.

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>Parámetros

*dwTimeout*<br/>
`Lock` omite este valor de parámetro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

`Lock` es una llamada de bloqueo que no regresará hasta que se señaliza el objeto de sección crítica (disponible).

Si se necesitan esperas cronometradas, puede usar un [CMutex](../../mfc/reference/cmutex-class.md) en lugar del objeto un `CCriticalSection` objeto.

Si `Lock` no puede asignar la memoria del sistema necesarias, una excepción de memoria (de tipo [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) se inicia automáticamente.

### <a name="example"></a>Ejemplo

En este ejemplo se muestra el enfoque de sección crítica anidada controlando el acceso a un recurso compartido (estático `_strShared` objeto) con un compartido `CCriticalSection` objeto. El `SomeMethod` función demuestra cómo actualizar un recurso compartido de una manera segura.

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

##  <a name="m_sect"></a>  CCriticalSection::m_sect

Contiene un objeto de sección crítica que usen todas `CCriticalSection` métodos.

```
CRITICAL_SECTION m_sect;
```

##  <a name="operator_critical_section_star"></a>  CCriticalSection::operator CRITICAL_SECTION *

Recupera un objeto CRITICAL_SECTION.

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>Comentarios

Llame a esta función para recuperar un puntero al objeto CRITICAL_SECTION interno.

##  <a name="unlock"></a>  CCriticalSection::Unlock

Las versiones del `CCriticalSection` objeto para su uso por otro subproceso.

```
BOOL Unlock();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el `CCriticalSection` objeto pertenecía el subproceso y la versión fue correcta; de lo contrario, 0.

### <a name="remarks"></a>Comentarios

Si el `CCriticalSection` independiente, se está usando `Unlock` se debe llamar inmediatamente después de completar el uso del recurso controlado por la sección crítica. Si un [CSingleLock](../../mfc/reference/csinglelock-class.md) se está usando el objeto, `CCriticalSection::Unlock` será llamado por el objeto de bloqueo `Unlock` función miembro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CCriticalSection::Lock](#lock).

## <a name="see-also"></a>Vea también

[CSyncObject (clase)](../../mfc/reference/csyncobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMutex (clase)](../../mfc/reference/cmutex-class.md)
