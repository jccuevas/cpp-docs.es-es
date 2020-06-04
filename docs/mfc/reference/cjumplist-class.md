---
title: Clase CJumpList
ms.date: 03/27/2019
f1_keywords:
- CJumpList
- AFXADV/CJumpList
- AFXADV/CJumpList::CJumpList
- AFXADV/CJumpList::AbortList
- AFXADV/CJumpList::AddDestination
- AFXADV/CJumpList::AddKnownCategory
- AFXADV/CJumpList::AddTask
- AFXADV/CJumpList::AddTasks
- AFXADV/CJumpList::AddTaskSeparator
- AFXADV/CJumpList::ClearAll
- AFXADV/CJumpList::ClearAllDestinations
- AFXADV/CJumpList::CommitList
- AFXADV/CJumpList::GetDestinationList
- AFXADV/CJumpList::GetMaxSlots
- AFXADV/CJumpList::GetRemovedItems
- AFXADV/CJumpList::InitializeList
- AFXADV/CJumpList::SetAppID
helpviewer_keywords:
- CJumpList [MFC], CJumpList
- CJumpList [MFC], AbortList
- CJumpList [MFC], AddDestination
- CJumpList [MFC], AddKnownCategory
- CJumpList [MFC], AddTask
- CJumpList [MFC], AddTasks
- CJumpList [MFC], AddTaskSeparator
- CJumpList [MFC], ClearAll
- CJumpList [MFC], ClearAllDestinations
- CJumpList [MFC], CommitList
- CJumpList [MFC], GetDestinationList
- CJumpList [MFC], GetMaxSlots
- CJumpList [MFC], GetRemovedItems
- CJumpList [MFC], InitializeList
- CJumpList [MFC], SetAppID
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
ms.openlocfilehash: 2e45e2e58bd51d36b6412940b7ed01aa119017ed
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754941"
---
# <a name="cjumplist-class"></a>Clase CJumpList

A `CJumpList` es la lista de accesos directos que se revelan al hacer clic con el botón derecho en un icono de la barra de tareas.

## <a name="syntax"></a>Sintaxis

```
class CJumpList;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CJumpList::CJumpList](#cjumplist)|Construye un objeto `CJumpList`.|
|[CJumpList::-CJumpList](#_dtorcjumplist)|Destruye un objeto `CJumpList` .|

|Nombre|Descripción|
|----------|-----------------|
|[CJumpList::AbortList](#abortlist)|Anula una transacción de creación de listas sin confirmar.|
|[CJumpList::AddDestination](#adddestination)|Sobrecargado. Agrega destino a la lista.|
|[CJumpList::AddKnownCategory](#addknowncategory)|Anexa una categoría conocida a la lista.|
|[CJumpList::AddTask](#addtask)|Sobrecargado. Agrega elementos a la categoría Tareas canónicas.|
|[CJumpList::AddTasks](#addtasks)|Agrega elementos a la categoría Tareas canónicas.|
|[CJumpList::AddTaskSeparator](#addtaskseparator)|Agrega un separador entre tareas.|
|[CJumpList::ClearAll](#clearall)|Quita todas las tareas y destinos que se `CJumpList` han agregado a la instancia actual de hasta ahora.|
|[CJumpList::ClearAllDestinations](#clearalldestinations)|Quita todos los destinos que se han `CJumpList` agregado a la instancia actual de hasta ahora.|
|[CJumpList::CommitList](#commitlist)|Finaliza una transacción de creación de listas y confirma la lista notificada en el almacén asociado (el registro en este caso.)|
|[CJumpList::GetDestinationList](#getdestinationlist)|Recupera un puntero de interfaz a la lista de destino.|
|[CJumpList::GetMaxSlots](#getmaxslots)|Recupera el número máximo de elementos, incluidos los encabezados de categoría que se pueden mostrar en el menú de destino de la aplicación que realiza la llamada.|
|[CJumpList::GetRemovedItems](#getremoveditems)|Devuelve la matriz de elementos que representan destinos eliminados.|
|[CJumpList::InitializeList](#initializelist)|Comienza una transacción de creación de listas.|
|[CJumpList::SetAppID](#setappid)|Establece el identificador de modelo de usuario de aplicación para la lista que se va a compilar.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CJumpList](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxadv.h

## <a name="cjumplistcjumplist"></a><a name="_dtorcjumplist"></a>CJumpList::-CJumpList

Destruye un objeto `CJumpList` .

```
~CJumpList();
```

## <a name="cjumplistabortlist"></a><a name="abortlist"></a>CJumpList::AbortList

Anula una transacción de creación de listas sin confirmar.

```cpp
void AbortList();
```

### <a name="remarks"></a>Observaciones

Llamar a este método tiene `CJumpList` el `CommitList`mismo efecto que destruir sin llamar a .

## <a name="cjumplistadddestination"></a><a name="adddestination"></a>CJumpList::AddDestination

Agrega destino a la lista.

```
BOOL AddDestination(
    LPCTSTR lpcszCategoryName,
    LPCTSTR strDestinationPath);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellItem* pShellItem);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellLink* pShellLink);
```

### <a name="parameters"></a>Parámetros

*lpcszCategoryName*<br/>
Especifica un nombre de categoría. Si la categoría especificada no existe, se creará.

*strDestinationPath*<br/>
Especifica una ruta de acceso al archivo de destino.

*strCategoryName*<br/>
Especifica un nombre de categoría. Si la categoría especificada no existe, se creará.

*pShellItem*<br/>
Especifica un elemento de Shell que representa el destino que se va a agregar.

*pShellLink*<br/>
Especifica un vínculo de shell que representa el destino que se va a agregar.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

La instancia `CJumpList` de internamente acumula destinos agregados y, a continuación, los confirma en `CommitList`.

## <a name="cjumplistaddknowncategory"></a><a name="addknowncategory"></a>CJumpList::AddKnownCategory

Anexa una categoría conocida a la lista.

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>Parámetros

*category*<br/>
Especifica un tipo de categoría conocido. Puede ser KDC_RECENT, o KDC_KNOWN.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

Categorías conocidas son las categorías frecuentes y recientes que `SHAddToRecentDocs` calcularemos automáticamente para cada aplicación que utiliza (o indirectamente lo usa como el shell lo llamará en nombre de la aplicación en algunos escenarios).

## <a name="cjumplistaddtask"></a><a name="addtask"></a>CJumpList::AddTask

Agrega elementos a la categoría Tareas canónicas.

```
BOOL AddTask(
    LPCTSTR strTargetExecutablePath,
    LPCTSTR strCommandLineArgs,
    LPCTSTR strTitle,
    LPCTSTR strIconLocation,
    int iIconIndex);

BOOL AddTask(IShellLink* pShellLink);
```

### <a name="parameters"></a>Parámetros

*strTargetExecutablePath*<br/>
Especifica la ruta de acceso de la tarea de destino.

*strCommandLineArgs*<br/>
Especifica los argumentos de línea de comandos del ejecutable especificado por *strTargetExecutablePath*.

*strTitle*<br/>
Nombre de tarea que se mostrará en la lista de destinos.

*strIconLocation*<br/>
Ubicación del icono que se mostrará en la Lista de destinos junto con el título.

*iIconIndex*<br/>
Indice de icono.

*pShellLink*<br/>
Vínculo de shell que representa una tarea que se va a agregar.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

La instancia `CJumpList` de acumula tareas especificadas y las `CommitList`agrega a la lista de destinos durante . Los elementos de tarea aparecerán en una categoría en la parte inferior del menú de destino de la aplicación. Esta categoría tiene prioridad sobre todas las demás categorías cuando se rellena en la interfaz de usuario.

## <a name="cjumplistaddtasks"></a><a name="addtasks"></a>CJumpList::AddTasks

Agrega elementos a la categoría Tareas canónicas.

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>Parámetros

*pObjectCollection*<br/>
Una colección de tareas que se van a agregar.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

La instancia de CJumpList acumula tareas especificadas y las `CommitList`agrega a la lista de destinos durante . Los elementos de tarea aparecerán en una categoría en la parte inferior del menú de destino de la aplicación. Esta categoría tiene prioridad sobre todas las demás categorías cuando se rellena en la interfaz de usuario.

## <a name="cjumplistaddtaskseparator"></a><a name="addtaskseparator"></a>CJumpList::AddTaskSeparator

Agrega un separador entre tareas.

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, 0 si no lo es.

## <a name="cjumplistcjumplist"></a><a name="cjumplist"></a>CJumpList::CJumpList

Construye un objeto `CJumpList`.

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>Parámetros

*bAutoCommit*<br/>
Si este parámetro es FALSE, la lista no se confirma automáticamente en el destructor.

## <a name="cjumplistclearall"></a><a name="clearall"></a>CJumpList::ClearAll

Quita todas las tareas y destinos que se `CJumpList` han agregado a la instancia actual de hasta ahora.

```cpp
void ClearAll();
```

### <a name="remarks"></a>Observaciones

Este método borra y libera todos los datos y las interfaces internas.

## <a name="cjumplistclearalldestinations"></a><a name="clearalldestinations"></a>CJumpList::ClearAllDestinations

Quita todos los destinos que se han agregado a la instancia actual de CJumpList hasta ahora.

```cpp
void ClearAllDestinations();
```

### <a name="remarks"></a>Observaciones

Llame a esta función si necesita quitar todos los destinos que se han agregado hasta ahora en la sesión actual de creación de lista de destino y agregar otros destinos de nuevo. Si el `ICustomDestinationList` interno se ha inicializado, se deja vivo.

## <a name="cjumplistcommitlist"></a><a name="commitlist"></a>CJumpList::CommitList

Finaliza una transacción de creación de listas y confirma la lista notificada en el almacén asociado (el registro en este caso).

```
BOOL CommitList();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

La confirmación es atómica. Se devolverá un error si se produce un error en la confirmación.  Cuando `CommitList` se llama, se limpiará la lista actual de elementos eliminados. Al llamar a este método se restablece el objeto para que no tenga una transacción de creación de listas activa. Para actualizar la `BeginList` lista, debe llamarse de nuevo.

## <a name="cjumplistgetdestinationlist"></a><a name="getdestinationlist"></a>CJumpList::GetDestinationList

Recupera un puntero de interfaz a la lista de destino.

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

Si la lista de saltos no se ha inicializado o se ha confirmado o anulado, el valor devuelto será NULL.

## <a name="cjumplistgetmaxslots"></a><a name="getmaxslots"></a>CJumpList::GetMaxSlots

Recupera el número máximo de elementos, incluidos los encabezados de categoría que se pueden mostrar en el menú de destino de la aplicación que realiza la llamada.

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

Las aplicaciones solo pueden notificar una serie de elementos y encabezados de categoría combinados hasta este valor. Si las `AppendCategory` `AppendKnownCategory`llamadas `AddUserTasks` a , , o superan este número, devolverán el error.

## <a name="cjumplistgetremoveditems"></a><a name="getremoveditems"></a>CJumpList::GetRemovedItems

Devuelve la matriz de elementos que representan destinos eliminados.

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

Los destinos eliminados se recuperan durante la inicialización de la lista de saltos. Al generar una nueva lista de destino, se espera que las aplicaciones procesen primero la lista de destinos quitados, borrando sus datos de seguimiento para cualquier elemento devuelto por el enumerador de lista quitado. Si una aplicación intenta proporcionar un elemento que se acaba `BeginList` de quitar en la transacción que se inicia la llamada actual a se inició, la llamada al método que volvió a agregar ese elemento producirá un error, para asegurarse de que las aplicaciones respetan la lista quitada.

## <a name="cjumplistinitializelist"></a><a name="initializelist"></a>CJumpList::InitializeList

Comienza una transacción de creación de listas.

```
BOOL InitializeList();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

No es necesario llamar a este método explícitamente a `ICustomDestinationList` menos `GetDestinationList`que desee recuperar `GetMaxSlots`un puntero a `GetRemovedItems`using , el número de ranuras disponibles mediante , o la lista de elementos eliminados mediante .

## <a name="cjumplistsetappid"></a><a name="setappid"></a>CJumpList::SetAppID

Establece el identificador de modelo de usuario de aplicación para la lista que se va a compilar.

```cpp
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>Parámetros

*strAppID*<br/>
Cadena que especifica el identificador de modelo de usuario de aplicación.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
