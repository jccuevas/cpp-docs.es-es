---
title: CCriticalSection (clase)
ms.date: 11/04/2016
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
ms.openlocfilehash: d79199a332f6930619e6b4995b04bc590b6ea580
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369363"
---
# <a name="ccriticalsection-class"></a>CCriticalSection (clase)

Representa una "sección crítica", un objeto de sincronización que permite que un subproceso a la vez tenga acceso a un recurso o sección de código.

## <a name="syntax"></a>Sintaxis

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCriticalSection::CCriticalSection](#ccriticalsection)|Construye un objeto `CCriticalSection`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCriticalSection::Lock](#lock)|Se utiliza para `CCriticalSection` obtener acceso al objeto.|
|[CCriticalSection::Unlock](#unlock)|Libera el objeto `CCriticalSection`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCriticalSection::operador CRITICAL_SECTION*](#operator_critical_section_star)|Recupera un puntero al objeto CRITICAL_SECTION interno.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCriticalSection::m_sect](#m_sect)|Un objeto CRITICAL_SECTION.|

## <a name="remarks"></a>Observaciones

Las secciones críticas son útiles cuando solo se puede permitir que un subproceso a la vez modifique datos o algún otro recurso controlado. Por ejemplo, agregar nodos a una lista vinculada es un proceso que solo debe permitirse un subproceso a la vez. Mediante el `CCriticalSection` uso de un objeto para controlar la lista vinculada, solo un subproceso a la vez puede obtener acceso a la lista.

> [!NOTE]
> La funcionalidad de `CCriticalSection` la clase la proporciona un objeto de CRITICAL_SECTION Win32 real.

Se utilizan secciones críticas en lugar de exclusiones mutuas (consulte [CMutex](../../mfc/reference/cmutex-class.md)) cuando la velocidad es crítica y el recurso no se utilizará a través de los límites del proceso.

Hay dos métodos `CCriticalSection` para usar un objeto: independiente e incrustado en una clase.

- Método independiente Para utilizar un `CCriticalSection` objeto independiente, `CCriticalSection` construya el objeto cuando sea necesario. Después de un retorno correcto del constructor, bloquee explícitamente el objeto con una llamada a [Lock](#lock). Llame a [Unlock](#unlock) cuando haya terminado de acceder a la sección crítica. Este método, aunque más claro para alguien que lee el código fuente, es más propenso a errores, ya que debe recordar bloquear y desbloquear la sección crítica antes y después del acceso.

   Un método más preferible es usar la [clase CSingleLock.](../../mfc/reference/csinglelock-class.md) También tiene `Lock` un `Unlock` método y, pero no tiene que preocuparse por desbloquear el recurso si se produce una excepción.

- Método incrustado También puede compartir una clase con `CCriticalSection`varios subprocesos agregando un miembro de datos -type a la clase y bloqueando el miembro de datos cuando sea necesario.

Para obtener más `CCriticalSection` información sobre el uso de objetos, consulte el artículo [Multithreading: Cómo utilizar las clases](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)de sincronización .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

## <a name="ccriticalsectionccriticalsection"></a><a name="ccriticalsection"></a>CCriticalSection::CCriticalSection

Construye un objeto `CCriticalSection`.

```
CCriticalSection();
```

### <a name="remarks"></a>Observaciones

Para tener acceso `CCriticalSection` o liberar un objeto, cree un [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llame a su [Lock](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones miembro. Si `CCriticalSection` el objeto se utiliza de forma independiente, llame a su [Unlock](#unlock) función miembro para liberarlo.

Si el constructor no puede asignar la memoria del sistema necesaria, se produce automáticamente una excepción de memoria (de tipo [CMemoryException](../../mfc/reference/cmemoryexception-class.md)).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CCriticalSection::Lock](#lock).

## <a name="ccriticalsectionlock"></a><a name="lock"></a>CCriticalSection::Lock

Llame a esta función miembro para obtener acceso al objeto de sección crítica.

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>Parámetros

*dwTimeout*<br/>
`Lock`omite este valor de parámetro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

`Lock`es una llamada de bloqueo que no volverá hasta que se señale el objeto de sección crítica (esté disponible).

Si las esperas temporizadas son necesarias, puede `CCriticalSection` utilizar un [CMutex](../../mfc/reference/cmutex-class.md) objeto en lugar de un objeto.

Si `Lock` no puede asignar la memoria del sistema necesaria, se produce automáticamente una excepción de memoria (de tipo [CMemoryException](../../mfc/reference/cmemoryexception-class.md)).

### <a name="example"></a>Ejemplo

En este ejemplo se muestra el enfoque de sección crítica `_strShared` anidada controlando `CCriticalSection` el acceso a un recurso compartido (el objeto estático) mediante un objeto compartido. La `SomeMethod` función muestra cómo actualizar un recurso compartido de forma segura.

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

## <a name="ccriticalsectionm_sect"></a><a name="m_sect"></a>CCriticalSection::m_sect

Contiene un objeto de sección `CCriticalSection` crítico que se utiliza en todos los métodos.

```
CRITICAL_SECTION m_sect;
```

## <a name="ccriticalsectionoperator-critical_section"></a><a name="operator_critical_section_star"></a>CCriticalSection::operador CRITICAL_SECTION*

Recupera un objeto CRITICAL_SECTION.

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar un puntero al objeto CRITICAL_SECTION interno.

## <a name="ccriticalsectionunlock"></a><a name="unlock"></a>CCriticalSection::Unlock

Libera `CCriticalSection` el objeto para su uso por otro subproceso.

```
BOOL Unlock();
```

### <a name="return-value"></a>Valor devuelto

Distinto de `CCriticalSection` cero si el objeto era propiedad del subproceso y la versión se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si `CCriticalSection` se usa de forma `Unlock` independiente, se debe llamar inmediatamente después de completar el uso del recurso controlado por la sección crítica. Si se utiliza un [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto, `CCriticalSection::Unlock` se llamará `Unlock` por la función miembro del objeto lock.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CCriticalSection::Lock](#lock).

## <a name="see-also"></a>Consulte también

[Clase CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CMutex](../../mfc/reference/cmutex-class.md)
