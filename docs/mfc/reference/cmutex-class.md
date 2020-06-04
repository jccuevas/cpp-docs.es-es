---
title: Clase CMutex
ms.date: 11/04/2016
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
ms.openlocfilehash: 2d6f637ab4828b3e70df205ebf359ae45a940d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363277"
---
# <a name="cmutex-class"></a>Clase CMutex

Representa una "mutex", un objeto de sincronización que permite a un subproceso acceso mutuamente exclusivo a un recurso.

## <a name="syntax"></a>Sintaxis

```
class CMutex : public CSyncObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMutex::CMutex](#cmutex)|Construye un objeto `CMutex`.|

## <a name="remarks"></a>Observaciones

Las exclusiones mutuas son útiles cuando solo se puede permitir que un subproceso a la vez modifique datos o algún otro recurso controlado. Por ejemplo, agregar nodos a una lista vinculada es un proceso que solo debe permitirse un subproceso a la vez. Mediante el `CMutex` uso de un objeto para controlar la lista vinculada, solo un subproceso a la vez puede obtener acceso a la lista.

Para utilizar `CMutex` un objeto, construya el `CMutex` objeto cuando sea necesario. Especifique el nombre de la exclusión mutua en la que desea esperar y que la aplicación debe poseerla inicialmente. A continuación, puede tener acceso a la exclusión mutua cuando se devuelve el constructor. Llame a [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) cuando haya terminado de acceder al recurso controlado.

Un método alternativo `CMutex` para usar objetos `CMutex` es agregar una variable de tipo como miembro de datos a la clase que desea controlar. Durante la construcción del objeto controlado, `CMutex` llame al constructor del miembro de datos especificando si la exclusión mutua es inicialmente propiedad, el nombre de la exclusión mutua (si se usará a través de los límites del proceso) y los atributos de seguridad deseados.

Para tener acceso `CMutex` a los recursos controlados por objetos de esta manera, primero cree una variable de tipo [CSingleLock](../../mfc/reference/csinglelock-class.md) o escriba [CMultiLock](../../mfc/reference/cmultilock-class.md) en la función miembro de acceso del recurso. A continuación, llame `Lock` a la función miembro del objeto lock (por ejemplo, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). En este punto, el subproceso obtendrá acceso al recurso, esperará a que el recurso se libere y obtenga acceso, o esperará a que el recurso se libere y tiempo de espera, sin poder obtener acceso al recurso. En cualquier caso, se ha tenido acceso al recurso de forma segura para subprocesos. Para liberar el recurso, utilice `Unlock` la función miembro del objeto de bloqueo (por ejemplo, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)) o permita que el objeto de bloqueo quede fuera del ámbito.

Para obtener más `CMutex` información sobre el uso de objetos, consulte el artículo [Multithreading: Cómo utilizar las clases](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)de sincronización .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

## <a name="cmutexcmutex"></a><a name="cmutex"></a>CMutex::CMutex

Construye un objeto con `CMutex` nombre o sin nombre.

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parámetros

*bInitiallyOwn*<br/>
Especifica si el subproceso `CMutex` que crea el objeto inicialmente tiene acceso al recurso controlado por la exclusión mutua.

*lpszName*<br/>
Nombre del objeto `CMutex`. Si existe otra exclusión mutua con el mismo nombre, se debe proporcionar *lpszName* si el objeto se usará a través de los límites del proceso. Si **NULL**, la exclusión mutua no tendrá nombre. Si el nombre coincide con una exclusión `CMutex` mutua existente, el constructor crea un nuevo objeto que hace referencia a la exclusión mutua de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es una exclusión mutua, se producirá un error en la construcción.

*lpsaAttribute*<br/>
Atributos de seguridad para el objeto mutex. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Para tener acceso `CMutex` o liberar un objeto, cree un [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llame a su [Lock](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones miembro. Si `CMutex` el objeto se utiliza de `Unlock` forma independiente, llame a su función miembro para liberarlo.

> [!IMPORTANT]
> Después `CMutex` de crear el objeto, utilice [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para asegurarse de que la exclusión mutua no existía. Si la exclusión mutua existió inesperadamente, puede indicar que un proceso pícaro está en cuclillas y puede tener la intención de utilizar la exclusión mutua maliciosamente. En este caso, el procedimiento recomendado para la seguridad es cerrar el identificador y continuar como si se hubiera producido un error al crear el objeto.

## <a name="see-also"></a>Consulte también

[Clase CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
