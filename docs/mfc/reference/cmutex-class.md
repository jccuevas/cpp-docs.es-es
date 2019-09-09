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
ms.openlocfilehash: 65f7f4db9489de1c9a380d760ed5cab41bfdc2ec
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504520"
---
# <a name="cmutex-class"></a>Clase CMutex

Representa una "exclusión mutua": un objeto de sincronización que permite que un subproceso tenga acceso exclusivo mutuamente a un recurso.

## <a name="syntax"></a>Sintaxis

```
class CMutex : public CSyncObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMutex::CMutex](#cmutex)|Construye un objeto `CMutex`.|

## <a name="remarks"></a>Comentarios

Las exclusiones mutuas son útiles cuando solo se puede permitir que un subproceso a la vez modifique los datos o algún otro recurso controlado. Por ejemplo, agregar nodos a una lista vinculada es un proceso que solo se debe permitir en un subproceso cada vez. Al usar un `CMutex` objeto para controlar la lista vinculada, solo un subproceso a la vez puede obtener acceso a la lista.

Para usar un `CMutex` objeto, construya el `CMutex` objeto cuando sea necesario. Especifique el nombre de la exclusión mutua en la que desea esperar y que la aplicación debe ser la propietaria inicialmente. Después, puede tener acceso a la exclusión mutua cuando el constructor vuelva. Llame a [CSyncObject:: Unlock](../../mfc/reference/csyncobject-class.md#unlock) cuando haya terminado de tener acceso al recurso controlado.

Un método alternativo para usar `CMutex` objetos es agregar una variable de tipo `CMutex` como miembro de datos a la clase que desea controlar. Durante la construcción del objeto controlado, llame al constructor del miembro `CMutex` de datos especificando si la exclusión mutua es propiedad inicialmente, el nombre de la exclusión mutua (si se va a utilizar en los límites del proceso) y los atributos de seguridad deseados.

Para tener acceso a los `CMutex` recursos controlados por objetos de esta manera, cree primero una variable de tipo [CSingleLock](../../mfc/reference/csinglelock-class.md) o escriba [CMultiLock](../../mfc/reference/cmultilock-class.md) en la función miembro de acceso del recurso. A continuación, llame a la `Lock` función miembro del objeto de bloqueo (por ejemplo, [CSingleLock:: Lock](../../mfc/reference/csinglelock-class.md#lock)). En este momento, el subproceso obtendrá acceso al recurso, esperará a que se libere el recurso y obtendrá acceso, o bien a esperar a que el recurso se libere y se agote el tiempo de espera, con lo que no se podrá obtener acceso al recurso. En cualquier caso, se ha tenido acceso a su recurso de una manera segura para subprocesos. Para liberar el recurso, utilice la función miembro del `Unlock` objeto de bloqueo (por ejemplo, [CSingleLock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock)) o permita que el objeto de bloqueo quede fuera del ámbito.

Para obtener más información sobre `CMutex` el uso de objetos, [vea el artículo multithreading: Cómo usar las clases](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)de sincronización.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt. h

##  <a name="cmutex"></a>  CMutex::CMutex

Construye un `CMutex` objeto con nombre o sin nombre.

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parámetros

*bInitiallyOwn*<br/>
Especifica si el subproceso que `CMutex` crea el objeto inicialmente tiene acceso al recurso controlado por la exclusión mutua.

*lpszName*<br/>
Nombre del objeto `CMutex`. Si existe otra exclusión mutua con el mismo nombre, se debe proporcionar *lpszName* si el objeto se va a usar en los límites del proceso. Si **es null**, la exclusión mutua no tendrá nombre. Si el nombre coincide con una exclusión mutua existente, el constructor crea `CMutex` un nuevo objeto que hace referencia a la exclusión mutua de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es una exclusión mutua, se producirá un error en la construcción.

*lpsaAttribute*<br/>
Atributos de seguridad para el objeto mutex. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Para obtener acceso a un `CMutex` objeto o liberarlo, cree un objeto [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) y llame a sus funciones miembro [Lock](../../mfc/reference/csinglelock-class.md#lock) y [unlock.](../../mfc/reference/csinglelock-class.md#unlock) Si el `CMutex` objeto se utiliza de manera independiente, llame a su `Unlock` función miembro para liberarlo.

> [!IMPORTANT]
>  Después de crear `CMutex` el objeto, utilice [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para asegurarse de que la exclusión mutua no exista todavía. Si la exclusión mutua existía de manera inesperada, puede indicar que un proceso no autorizado es Squatting y puede estar intentando usar la exclusión mutua de forma malintencionada. En este caso, el procedimiento recomendado para la seguridad es cerrar el identificador y continuar como si se produjera un error al crear el objeto.

## <a name="see-also"></a>Vea también

[CSyncObject (clase)](../../mfc/reference/csyncobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
