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
ms.openlocfilehash: d5a0e4187107aaab7cedf4e7a0e2fc47b9f9f305
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502581"
---
# <a name="csemaphore-class"></a>CSemaphore (clase)

Un objeto de la `CSemaphore` clase representa un "semáforo": un objeto de sincronización que permite que un número limitado de subprocesos en uno o varios procesos obtenga acceso a mantiene un recuento del número de subprocesos que actualmente tienen acceso a un recurso especificado.

## <a name="syntax"></a>Sintaxis

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSemaphore::CSemaphore](#csemaphore)|Construye un objeto `CSemaphore`.|

## <a name="remarks"></a>Comentarios

Los semáforos son útiles para controlar el acceso a un recurso compartido que solo puede admitir un número limitado de usuarios. El recuento actual del `CSemaphore` objeto es el número de usuarios adicionales permitidos. Cuando el recuento llegue a cero, todos los intentos de usar el recurso `CSemaphore` controlado por el objeto se insertarán en una cola del sistema y esperarán hasta que se agote el tiempo de espera o hasta que el número aumente por encima de 0. El número máximo de usuarios que pueden tener acceso al recurso controlado al mismo tiempo se especifica durante la `CSemaphore` construcción del objeto.

Para usar un `CSemaphore` objeto, construya el `CSemaphore` objeto cuando sea necesario. Especifique el nombre del semáforo en el que desea esperar y que la aplicación debe poseer inicialmente. Después, puede tener acceso al semáforo cuando el constructor vuelva. Llame a [CSyncObject:: Unlock](../../mfc/reference/csyncobject-class.md#unlock) cuando haya terminado de tener acceso al recurso controlado.

Un método alternativo para usar `CSemaphore` objetos es agregar una variable de tipo `CSemaphore` como miembro de datos a la clase que desea controlar. Durante la construcción del objeto controlado, llame al constructor del miembro `CSemaphore` de datos especificando el recuento de acceso inicial, el recuento máximo de acceso, el nombre del semáforo (si se va a usar en los límites del proceso) y los atributos de seguridad deseados.

Para tener acceso a los `CSemaphore` recursos controlados por objetos de esta manera, cree primero una variable de tipo [CSingleLock](../../mfc/reference/csinglelock-class.md) o escriba [CMultiLock](../../mfc/reference/cmultilock-class.md) en la función miembro de acceso del recurso. A continuación, llame a la `Lock` función miembro del objeto de bloqueo (por ejemplo, [CSingleLock:: Lock](../../mfc/reference/csinglelock-class.md#lock)). En este momento, el subproceso obtendrá acceso al recurso, esperará a que se libere el recurso y obtendrá acceso, o bien a esperar a que el recurso se libere y se agote el tiempo de espera, con lo que no se podrá obtener acceso al recurso. En cualquier caso, se ha tenido acceso a su recurso de una manera segura para subprocesos. Para liberar el recurso, utilice la función miembro del `Unlock` objeto de bloqueo (por ejemplo, [CSingleLock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock)) o permita que el objeto de bloqueo quede fuera del ámbito.

Como alternativa, puede crear un `CSemaphore` objeto independiente y acceder a él explícitamente antes de intentar tener acceso al recurso controlado. Este método, aunque es más claro para alguien que lee el código fuente, es más propenso a errores.

Para obtener más información sobre cómo usar `CSemaphore` objetos, vea el artículo [multithreading: Cómo usar las clases](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)de sincronización.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt. h

##  <a name="csemaphore"></a>  CSemaphore::CSemaphore

Construye un `CSemaphore` objeto con nombre o sin nombre.

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>Parámetros

*lInitialCount*<br/>
El recuento inicial de uso del semáforo. Debe ser mayor o igual que 0 y menor o igual que *lMaxCount*.

*lMaxCount*<br/>
El recuento máximo de uso para el semáforo. Debe ser mayor que 0.

*pstrName*<br/>
Nombre del semáforo. Se debe proporcionar si se va a tener acceso al semáforo a través de los límites del proceso. Si `NULL`es, el objeto no tendrá nombre. Si el nombre coincide con un semáforo existente, el constructor crea un nuevo `CSemaphore` objeto que hace referencia al semáforo de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es un semáforo, se producirá un error en la construcción.

*lpsaAttributes*<br/>
Atributos de seguridad para el objeto Semaphore. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Para obtener acceso a un `CSemaphore` objeto o liberarlo, cree un objeto [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) y llame a sus funciones miembro [Lock](../../mfc/reference/csinglelock-class.md#lock) y [unlock.](../../mfc/reference/csinglelock-class.md#unlock)

> [!IMPORTANT]
>  Después de crear `CSemaphore` el objeto, utilice [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para asegurarse de que la exclusión mutua no exista todavía. Si la exclusión mutua existía de manera inesperada, puede indicar que un proceso no autorizado es Squatting y puede estar intentando usar la exclusión mutua de forma malintencionada. En este caso, el procedimiento recomendado para la seguridad es cerrar el identificador y continuar como si se produjera un error al crear el objeto.

## <a name="see-also"></a>Vea también

[CSyncObject (clase)](../../mfc/reference/csyncobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
