---
title: CMutex (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
dev_langs:
- C++
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23270275103faac3af48a3627a5f5833140645e2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066756"
---
# <a name="cmutex-class"></a>CMutex (clase)

Representa un "mutex", un objeto de sincronización que permite que un subproceso tenga acceso de manera mutuamente a un recurso.

## <a name="syntax"></a>Sintaxis

```
class CMutex : public CSyncObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMutex::CMutex](#cmutex)|Construye un objeto `CMutex`.|

## <a name="remarks"></a>Comentarios

Las exclusiones mutuas son útiles cuando solo un subproceso a la vez puede permitir modificar datos o algún otro recurso controlado. Por ejemplo, agregar nodos a una lista vinculada es un proceso que solo se permite un subproceso a la vez. Mediante el uso de un `CMutex` objeto para controlar la lista vinculada, solo un subproceso a la vez puede obtener acceso a la lista.

Para usar un `CMutex` objeto, construya el `CMutex` objeto cuando sea necesario. Especifique el nombre de la exclusión mutua que desea esperar y que la aplicación debe inicialmente es su propietario. A continuación, puede tener acceso a la exclusión mutua cuando devuelve el constructor. Llame a [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) cuando haya terminado acceder al recurso controlado.

Un método alternativo para el uso de `CMutex` objetos consiste en Agregar una variable de tipo `CMutex` como un miembro de datos a la clase que desee controlar. Durante la construcción del objeto controlado, llame al constructor de la `CMutex` miembro de datos que especifica si la exclusión mutua inicialmente tiene propietario, el nombre de la exclusión mutua (si se usará en los límites de proceso) y desea los atributos de seguridad.

Para acceder a los recursos controlados por `CMutex` objetos de este modo, primero cree una variable de cualquier tipo [CSingleLock](../../mfc/reference/csinglelock-class.md) o tipo [CMultiLock](../../mfc/reference/cmultilock-class.md) en función de miembro de acceso de su recurso. Utilizamos el objeto de bloqueo `Lock` función miembro (por ejemplo, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). En este momento, el subproceso se obtienen acceso al recurso, espere a que el recurso se libera y obtener acceso o esperar a que el recurso que se libere y el tiempo de espera, no se puede obtener acceso al recurso. En cualquier caso, se obtuvo acceso a los recursos de una manera segura para subprocesos. Para liberar el recurso, use el objeto de bloqueo `Unlock` función miembro (por ejemplo, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), o permitir que el objeto de bloqueo se encuentran fuera del ámbito.

Para obtener más información sobre el uso de `CMutex` objetos, consulte el artículo [Multithreading: uso de las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

##  <a name="cmutex"></a>  CMutex::CMutex

Construye una con o sin nombre `CMutex` objeto.

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parámetros

*bInitiallyOwn*<br/>
Especifica si el subproceso que crea el `CMutex` objeto inicialmente tiene acceso al recurso que se controla mediante la exclusión mutua.

*lpszName*<br/>
Nombre del objeto `CMutex`. Si existe otro exclusión mutua con el mismo nombre, *lpszName* se debe proporcionar si el objeto que se va a utilizar los límites del proceso. Si **NULL**, la exclusión mutua estará sin nombre. Si el nombre coincide con una exclusión mutua existente, el constructor crea un nuevo `CMutex` objeto que hace referencia a la exclusión mutua de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es una exclusión mutua, se producirá un error en la construcción.

*lpsaAttribute*<br/>
Atributos de seguridad para el objeto de exclusión mutua. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Para obtener acceso a o liberar una `CMutex` , cree un [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llamar a su [bloqueo](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones de miembro. Si el `CMutex` se usan objetos independientes, llame a su `Unlock` función miembro para liberarlo.

> [!IMPORTANT]
>  Después de crear el `CMutex` de objeto, utilice [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) para asegurarse de que la exclusión mutua no existía. Si la exclusión mutua existía inesperadamente, puede indicar un proceso invasor es uso inapropiado y es posible que pretende usar la exclusión mutua de forma malintencionada. En este caso, el procedimiento recomendado de preocupados por la seguridad es cerrar el identificador y continuar como si se produjo un error en la creación del objeto.

## <a name="see-also"></a>Vea también

[CSyncObject (clase)](../../mfc/reference/csyncobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

