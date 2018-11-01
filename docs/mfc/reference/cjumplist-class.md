---
title: CJumpList (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: 7248c86f71780ef1867a1ce7edf871f27fc67643
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642187"
---
# <a name="cjumplist-class"></a>CJumpList (clase)

Un `CJumpList` es la lista de métodos abreviados revelada al que haga clic en un icono en la barra de tareas.

## <a name="syntax"></a>Sintaxis

```
class CJumpList;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CJumpList::CJumpList](#cjumplist)|Construye un objeto `CJumpList`.|
|[CJumpList:: ~ CJumpList](#cjumplist__~cjumplist)|Destruye un objeto `CJumpList`.|

|nombre|Descripción|
|----------|-----------------|
|[CJumpList::AbortList](#abortlist)|Anula una creación de lista de transacciones sin confirmar.|
|[CJumpList::AddDestination](#adddestination)|Sobrecargado. Agrega el destino a la lista.|
|[CJumpList::AddKnownCategory](#addknowncategory)|Anexa una categoría conocidos a la lista.|
|[CJumpList::AddTask](#addtask)|Sobrecargado. Agrega elementos a la categoría de tareas canónica.|
|[CJumpList::AddTasks](#addtasks)|Agrega elementos a la categoría de tareas canónica.|
|[CJumpList::AddTaskSeparator](#addtaskseparator)|Agrega un separador entre las tareas.|
|[CJumpList::ClearAll](#clearall)|Quita todas las tareas y destinos que se han agregado a la instancia actual de `CJumpList` hasta ahora.|
|[CJumpList::ClearAllDestinations](#clearalldestinations)|Quita todos los destinos que se han agregado a la instancia actual de `CJumpList` hasta ahora.|
|[CJumpList::CommitList](#commitlist)|Finaliza una transacción de creación de la lista y confirma la lista notificada en el almacén asociado (el registro en este caso).|
|[CJumpList::GetDestinationList](#getdestinationlist)|Recupera un puntero de interfaz a la lista de destino.|
|[CJumpList::GetMaxSlots](#getmaxslots)|Recupera el número máximo de elementos, incluidos los encabezados de categoría que se pueden mostrar en el menú de destino de la aplicación que realiza la llamada.|
|[CJumpList::GetRemovedItems](#getremoveditems)|Devuelve una matriz de elementos que representan quita destinos.|
|[CJumpList::InitializeList](#initializelist)|Comienza una transacción de creación de la lista.|
|[CJumpList::SetAppID](#setappid)|Establece el identificador de modelo de aplicación de usuario para la lista que se compilará.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CJumpList](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxadv.h

##  <a name="_dtorcjumplist"></a>  CJumpList:: ~ CJumpList

Destruye un objeto `CJumpList`.

```
~CJumpList();
```

##  <a name="abortlist"></a>  CJumpList::AbortList

Anula una creación de lista de transacciones sin confirmar.

```
void AbortList();
```

### <a name="remarks"></a>Comentarios

Llamar a este método tiene el mismo efecto que destruir `CJumpList` sin llamar a `CommitList`.

##  <a name="adddestination"></a>  CJumpList::AddDestination

Agrega el destino a la lista.

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
Especifica un vínculo de Shell que representa el destino que se va a agregar.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

La instancia de `CJumpList` internamente acumula los destinos se ha agregado y, a continuación, se confirma en `CommitList`.

##  <a name="addknowncategory"></a>  CJumpList::AddKnownCategory

Anexa una categoría conocidos a la lista.

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>Parámetros

*category*<br/>
Especifica un tipo de categoría conocidos. Puede ser KDC_RECENT o KDC_KNOWN.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

Conoce las categorías son las categorías con frecuencia y recientes que se va a calcular automáticamente para todas las aplicaciones que utilizan `SHAddToRecentDocs` (o indirectamente lo usa como el shell llamará en nombre de la aplicación en algunos casos).

##  <a name="addtask"></a>  CJumpList::AddTask

Agrega elementos a la categoría de tareas canónica.

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
Especifica los argumentos de línea de comandos del archivo ejecutable especificado por strTargetExecutablePath.

*strTitle*<br/>
Nombre de la tarea que se mostrará en la lista de destino.

*strIconLocation*<br/>
Ubicación del icono que se mostrará en la lista de destino junto con el título.

*iIconIndex*<br/>
Índice del icono.

*pShellLink*<br/>
Vínculo de shell que representa una tarea que se va a agregar.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

La instancia de `CJumpList` acumula las tareas especificadas y los agrega a la lista de destino durante la `CommitList`. Elementos de tarea aparecerán en una categoría en la parte inferior del menú de la aplicación de destino. Esta categoría tiene prioridad sobre todas las demás categorías cuando se llena en la interfaz de usuario.

##  <a name="addtasks"></a>  CJumpList::AddTasks

Agrega elementos a la categoría de tareas canónica.

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>Parámetros

*pObjectCollection*<br/>
Una colección de tareas va a agregar.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

La instancia de CJumpList acumula las tareas especificadas y agregarlos a la lista de destino durante la `CommitList`. Elementos de tarea aparecerán en una categoría en la parte inferior del menú de la aplicación de destino. Esta categoría tiene prioridad sobre todas las demás categorías cuando se llena en la interfaz de usuario.

##  <a name="addtaskseparator"></a>  CJumpList::AddTaskSeparator

Agrega un separador entre las tareas.

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es correcto, 0 si no lo está.

##  <a name="cjumplist"></a>  CJumpList::CJumpList

Construye un objeto `CJumpList`.

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>Parámetros

*bAutoCommit*<br/>
Si este parámetro es FALSE no se confirma automáticamente la lista en el destructor.

##  <a name="clearall"></a>  CJumpList::ClearAll

Quita todas las tareas y destinos que se han agregado a la instancia actual de `CJumpList` hasta ahora.

```
void ClearAll();
```

### <a name="remarks"></a>Comentarios

Este método borra y libera todos los datos y las interfaces internas.

##  <a name="clearalldestinations"></a>  CJumpList::ClearAllDestinations

Quita todos los destinos que se han agregado a la instancia actual de CJumpList hasta ahora.

```
void ClearAllDestinations();
```

### <a name="remarks"></a>Comentarios

Si tiene que quitar todos los destinos que se han agregado hasta el momento de la sesión actual de creación de la lista de destino y vuelva a agregar otros destinos, llame a esta función. Si el texto interno `ICustomDestinationList` ha sido inicializado, se deja activo.

##  <a name="commitlist"></a>  CJumpList::CommitList

Finaliza una transacción de creación de la lista y confirma la lista notificada en el almacén asociado (el registro en este caso).

```
BOOL CommitList();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

La confirmación es atómica. Si se produce un error en la confirmación, se devolverá un error.  Cuando `CommitList` se denomina actual se borra la lista de elementos eliminados. Llamar a este método restablece el objeto para que no tiene una transacción activa de la creación de la lista. Para actualizar la lista, `BeginList` debe llamarse a intentarlo.

##  <a name="getdestinationlist"></a>  CJumpList::GetDestinationList

Recupera un puntero de interfaz a la lista de destino.

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

Si la lista de salto no se ha inicializado, o se ha confirmado o anulado, el valor devuelto será NULL.

##  <a name="getmaxslots"></a>  CJumpList::GetMaxSlots

Recupera el número máximo de elementos, incluidos los encabezados de categoría que se pueden mostrar en el menú de destino de la aplicación que realiza la llamada.

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

Las aplicaciones solo pueden informar un número de elementos y los encabezados de categoría combinados hasta este valor. Si las llamadas a `AppendCategory`, `AppendKnownCategory`, o `AddUserTasks` supera este número, devolverán un error.

##  <a name="getremoveditems"></a>  CJumpList::GetRemovedItems

Devuelve una matriz de elementos que representan quita destinos.

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

Se recuperan los destinos que se quitó durante la inicialización de la jump list de. Cuando se genera una nueva lista de destino, se esperan que las aplicaciones procesar primero la lista de destinos quitado, borrar sus datos de seguimiento para cualquier elemento devuelto por el enumerador de lista quitado. Si una aplicación intenta proporcionar un elemento que se acaba de quitar en la transacción de llamada actual a `BeginList` iniciado, la llamada al método que se vuelva a agrega ese elemento se producirá un error, para asegurarse de que las aplicaciones están respetando la lista quitada.

##  <a name="initializelist"></a>  CJumpList::InitializeList

Comienza una transacción de creación de la lista.

```
BOOL InitializeList();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

No es necesario llamar a este método explícitamente a menos que desee recuperar un puntero a `ICustomDestinationList` mediante `GetDestinationList`, el número de ranuras disponibles mediante `GetMaxSlots`, o una lista de los elementos quitados mediante `GetRemovedItems`.

##  <a name="setappid"></a>  CJumpList::SetAppID

Establece el identificador de modelo de aplicación de usuario para la lista que se compilará.

```
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>Parámetros

*strAppID*<br/>
Una cadena que especifica el identificador de modelo de aplicación de usuario.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
