---
title: CSemaphore (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
dev_langs:
- C++
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19d43d108888d1d89b4fa6173ab3ebd0e8e55bbc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400255"
---
# <a name="csemaphore-class"></a>CSemaphore (clase)

Un objeto de clase `CSemaphore` representa un "semáforo", un objeto de sincronización que permite que un número limitado de subprocesos de uno o varios procesos tengan acceso a mantener un recuento del número de subprocesos que actualmente tienen acceso a un recurso especificado.

## <a name="syntax"></a>Sintaxis

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSemaphore::CSemaphore](#csemaphore)|Construye un objeto `CSemaphore`.|

## <a name="remarks"></a>Comentarios

Los semáforos son útiles para controlar el acceso a un recurso compartido que puede admitir solo un número limitado de usuarios. El recuento actual de la `CSemaphore` objeto es el número de usuarios adicionales permitidos. Cuando el recuento llega a cero, todos los intentos de usar el recurso controlado por la `CSemaphore` objeto se insertará en una cola del sistema y espere hasta que finalice cualquier tiempo de espera o el número está por encima de 0. El número máximo de usuarios que pueden tener acceso al recurso controlado al mismo tiempo que se especifica durante la construcción de la `CSemaphore` objeto.

Para usar un `CSemaphore` objeto, construya el `CSemaphore` objeto cuando sea necesario. Especifique el nombre del semáforo que desea esperar y que la aplicación debe inicialmente es su propietario. A continuación, puede tener acceso el semáforo cuando se devuelve el constructor. Llame a [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) cuando haya terminado acceder al recurso controlado.

Un método alternativo para el uso de `CSemaphore` objetos consiste en Agregar una variable de tipo `CSemaphore` como un miembro de datos a la clase que desee controlar. Durante la construcción del objeto controlado, llame al constructor de la `CSemaphore` miembro de datos especificando la inicial acceso recuento, recuento máximo de acceso, nombre del semáforo (si se usará en los límites de proceso) y deseadas de los atributos de seguridad.

Para acceder a los recursos controlados por `CSemaphore` objetos de este modo, primero cree una variable de cualquier tipo [CSingleLock](../../mfc/reference/csinglelock-class.md) o tipo [CMultiLock](../../mfc/reference/cmultilock-class.md) en función de miembro de acceso de su recurso. Utilizamos el objeto de bloqueo `Lock` función miembro (por ejemplo, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). En este momento, el subproceso se obtienen acceso al recurso, espere a que el recurso se libera y obtener acceso o esperar a que el recurso que se libere y el tiempo de espera, no se puede obtener acceso al recurso. En cualquier caso, se obtuvo acceso a los recursos de una manera segura para subprocesos. Para liberar el recurso, use el objeto de bloqueo `Unlock` función miembro (por ejemplo, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), o permitir que el objeto de bloqueo se encuentran fuera del ámbito.

Como alternativa, puede crear un `CSemaphore` objeto independiente y acceder a ella explícitamente antes de intentar tener acceso al recurso controlado. Este método, mientras mejor a alguien leer el código fuente, es más propenso a errores.

Para obtener más información sobre cómo usar `CSemaphore` objetos, consulte el artículo [Multithreading: uso de las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

##  <a name="csemaphore"></a>  CSemaphore::CSemaphore

Construye una con o sin nombre `CSemaphore` objeto.

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>Parámetros

*lInitialCount*<br/>
El contador de uso inicial para el semáforo. Debe ser mayor o igual a 0 y menor o igual a *lMaxCount*.

*lMaxCount*<br/>
El recuento de uso máximo para el semáforo. Debe ser mayor que 0.

*pstrName*<br/>
El nombre del semáforo. Se debe proporcionar si el semáforo se accederá a los límites del proceso. Si `NULL`, el objeto estará sin nombre. Si el nombre coincide con un semáforo existente, el constructor crea un nuevo `CSemaphore` objeto que hace referencia el semáforo de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es un semáforo, se producirá un error en la construcción.

*lpsaAttributes*<br/>
Atributos de seguridad para el objeto de semáforo. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Para obtener acceso a o liberar una `CSemaphore` , cree un [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llamar a su [bloqueo](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones de miembro.

> [!IMPORTANT]
>  Después de crear el `CSemaphore` de objeto, utilice [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) para asegurarse de que la exclusión mutua no existía. Si la exclusión mutua existía inesperadamente, puede indicar un proceso invasor es uso inapropiado y es posible que pretende usar la exclusión mutua de forma malintencionada. En este caso, el procedimiento recomendado de preocupados por la seguridad es cerrar el identificador y continuar como si se produjo un error en la creación del objeto.

## <a name="see-also"></a>Vea también

[CSyncObject (clase)](../../mfc/reference/csyncobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



