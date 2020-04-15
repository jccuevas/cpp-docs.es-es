---
title: CSemaphore (clase)
ms.date: 11/04/2016
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
ms.openlocfilehash: 26e1fd55d321b221f4732874d57d02a79c4c6398
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318502"
---
# <a name="csemaphore-class"></a>CSemaphore (clase)

Un objeto `CSemaphore` de clase representa un "semáforo", un objeto de sincronización que permite que un número limitado de subprocesos en uno o varios procesos tenga acceso a un Mantiene un recuento del número de subprocesos que tienen acceso a un recurso especificado.

## <a name="syntax"></a>Sintaxis

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSemaphore::CSemaphore](#csemaphore)|Construye un objeto `CSemaphore`.|

## <a name="remarks"></a>Observaciones

Los semáforos son útiles para controlar el acceso a un recurso compartido que solo puede admitir un número limitado de usuarios. El recuento actual `CSemaphore` del objeto es el número de usuarios adicionales permitidos. Cuando el recuento llega a cero, todos los `CSemaphore` intentos de usar el recurso controlado por el objeto se insertarán en una cola del sistema y esperarán hasta que se agota el tiempo de espera o el recuento se eleva por encima de 0. El número máximo de usuarios que pueden tener acceso al recurso `CSemaphore` controlado a la vez se especifica durante la construcción del objeto.

Para utilizar `CSemaphore` un objeto, construya el `CSemaphore` objeto cuando sea necesario. Especifique el nombre del semáforo en el que desea esperar y que la aplicación debe poseerlo inicialmente. A continuación, puede tener acceso al semáforo cuando el constructor devuelve. Llame a [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) cuando haya terminado de acceder al recurso controlado.

Un método alternativo `CSemaphore` para usar objetos `CSemaphore` es agregar una variable de tipo como miembro de datos a la clase que desea controlar. Durante la construcción del objeto controlado, `CSemaphore` llame al constructor del miembro de datos especificando el recuento de acceso inicial, el recuento máximo de acceso, el nombre del semáforo (si se usará a través de los límites del proceso) y los atributos de seguridad deseados.

Para tener acceso `CSemaphore` a los recursos controlados por objetos de esta manera, primero cree una variable de tipo [CSingleLock](../../mfc/reference/csinglelock-class.md) o escriba [CMultiLock](../../mfc/reference/cmultilock-class.md) en la función miembro de acceso del recurso. A continuación, llame `Lock` a la función miembro del objeto lock (por ejemplo, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). En este punto, el subproceso obtendrá acceso al recurso, esperará a que el recurso se libere y obtenga acceso, o esperará a que el recurso se libere y tiempo de espera, sin poder obtener acceso al recurso. En cualquier caso, se ha tenido acceso al recurso de forma segura para subprocesos. Para liberar el recurso, utilice `Unlock` la función miembro del objeto de bloqueo (por ejemplo, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)) o permita que el objeto de bloqueo quede fuera del ámbito.

Como alternativa, puede `CSemaphore` crear un objeto independiente y tener acceso a él explícitamente antes de intentar tener acceso al recurso controlado. Este método, aunque más claro para alguien que lee el código fuente, es más propenso a errores.

Para obtener más información `CSemaphore` sobre cómo utilizar objetos, vea el artículo [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

## <a name="csemaphorecsemaphore"></a><a name="csemaphore"></a>CSemaphore::CSemaphore

Construye un objeto con `CSemaphore` nombre o sin nombre.

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>Parámetros

*lInitialCount*<br/>
El recuento de uso inicial para el semáforo. Debe ser mayor o igual que 0, y menor o igual que *lMaxCount*.

*lMaxCount*<br/>
El número máximo de uso para el semáforo. Debe ser mayor que 0.

*pstrName*<br/>
El nombre del semáforo. Debe proporcionarse si se accederá al semáforo a través de los límites del proceso. Si `NULL`, el objeto no tendrá nombre. Si el nombre coincide con un semáforo existente, `CSemaphore` el constructor crea un nuevo objeto que hace referencia al semáforo de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es un semáforo, se producirá un error en la construcción.

*lpsaAttributes*<br/>
Atributos de seguridad para el objeto de semáforo. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Para tener acceso `CSemaphore` o liberar un objeto, cree un [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llame a su [Lock](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones miembro.

> [!IMPORTANT]
> Después `CSemaphore` de crear el objeto, utilice [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para asegurarse de que la exclusión mutua no existía. Si la exclusión mutua existió inesperadamente, puede indicar que un proceso pícaro está en cuclillas y puede tener la intención de utilizar la exclusión mutua maliciosamente. En este caso, el procedimiento recomendado para la seguridad es cerrar el identificador y continuar como si se hubiera producido un error al crear el objeto.

## <a name="see-also"></a>Consulte también

[Clase CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
