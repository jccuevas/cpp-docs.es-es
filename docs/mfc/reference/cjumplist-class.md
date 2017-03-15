---
title: Clase CJumpList | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxadv/CJumpList
- CJumpList
dev_langs:
- C++
helpviewer_keywords:
- CJumpList class
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b3662bd00f7c757df3a77f5920c48389bbd749fb
ms.lasthandoff: 02/24/2017

---
# <a name="cjumplist-class"></a>Clase CJumpList
Un `CJumpList` es la lista de métodos abreviados revelada al haga clic en un icono de la barra de tareas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CJumpList;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CJumpList::CJumpList](#cjumplist)|Construye un objeto `CJumpList`.|  
|[CJumpList:: ~ CJumpList](#cjumplist__~cjumplist)|Destruye un objeto `CJumpList`.|  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CJumpList::AbortList](#abortlist)|Anula una creación de la lista de transacciones sin confirmar.|  
|[CJumpList::AddDestination](#adddestination)|Sobrecargado. Agrega el destino a la lista.|  
|[CJumpList::AddKnownCategory](#addknowncategory)|Anexa una categoría conocidos a la lista.|  
|[CJumpList::AddTask](#addtask)|Sobrecargado. Agrega elementos a la categoría de tareas canónica.|  
|[CJumpList::AddTasks](#addtasks)|Agrega elementos a la categoría de tareas canónica.|  
|[CJumpList::AddTaskSeparator](#addtaskseparator)|Agrega un separador entre las tareas.|  
|[CJumpList::ClearAll](#clearall)|Quita todas las tareas y destinos que se han agregado a la instancia actual de `CJumpList` hasta ahora.|  
|[CJumpList::ClearAllDestinations](#clearalldestinations)|Quita todos los destinos que se han agregado a la instancia actual de `CJumpList` hasta ahora.|  
|[CJumpList::CommitList](#commitlist)|Finaliza una transacción de creación de la lista y confirma la lista incluida en el almacén asociado (el registro en este caso).|  
|[CJumpList::GetDestinationList](#getdestinationlist)|Recupera un puntero de interfaz a la lista de destino.|  
|[CJumpList::GetMaxSlots](#getmaxslots)|Recupera el número máximo de elementos, incluidos los encabezados de categoría que se pueden mostrar en el menú de destino de la aplicación que realiza la llamada.|  
|[CJumpList::GetRemovedItems](#getremoveditems)|Devuelve una matriz de elementos que representan quita destinos.|  
|[CJumpList::InitializeList](#initializelist)|Inicia una transacción de creación de la lista.|  
|[CJumpList::SetAppID](#setappid)|Establece el identificador de modelo de aplicación de usuario de la lista que se generarán.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CJumpList](../../mfc/reference/cjumplist-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxadv.h  
  
##  <a name="a-namedtorcjumplista--cjumplistcjumplist"></a><a name="_dtorcjumplist"></a>CJumpList:: ~ CJumpList  
 Destruye un objeto `CJumpList`.  
  
```  
~CJumpList();
```  
  
##  <a name="a-nameabortlista--cjumplistabortlist"></a><a name="abortlist"></a>CJumpList::AbortList  
 Anula una creación de la lista de transacciones sin confirmar.  
  
```  
void AbortList();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método tiene el mismo efecto que destruir `CJumpList` sin llamar a `CommitList`.  
  
##  <a name="a-nameadddestinationa--cjumplistadddestination"></a><a name="adddestination"></a>CJumpList::AddDestination  
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
 `lpcszCategoryName`  
 Especifica un nombre de categoría. Si la categoría especificada no existe, se creará.  
  
 `strDestinationPath`  
 Especifica una ruta de acceso al archivo de destino.  
  
 `strCategoryName`  
 Especifica un nombre de categoría. Si la categoría especificada no existe, se creará.  
  
 `pShellItem`  
 Especifica un elemento de Shell que representa el destino que se va a agregar.  
  
 `pShellLink`  
 Especifica un vínculo del Shell que representa el destino que se va a agregar.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 La instancia de `CJumpList` internamente acumula los destinos agregados y, a continuación, se confirma en `CommitList`.  
  
##  <a name="a-nameaddknowncategorya--cjumplistaddknowncategory"></a><a name="addknowncategory"></a>CJumpList::AddKnownCategory  
 Anexa una categoría conocidos a la lista.  
  
```  
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```  
  
### <a name="parameters"></a>Parámetros  
 `category`  
 Especifica un tipo de categoría conocidos. Puede ser `KDC_RECENT`, o `KDC_KNOWN`.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 Conoce las categorías son las categorías frecuente y reciente que se va a calcular automáticamente para cada aplicación que utilice `SHAddToRecentDocs` (o indirectamente lo utiliza como el shell llamará en nombre de la aplicación en algunos escenarios).  
  
##  <a name="a-nameaddtaska--cjumplistaddtask"></a><a name="addtask"></a>CJumpList::AddTask  
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
 `strTargetExecutablePath`  
 Especifica la ruta de acceso de la tarea de destino.  
  
 `strCommandLineArgs`  
 Especifica los argumentos de línea de comandos del archivo ejecutable especificado por strTargetExecutablePath.  
  
 `strTitle`  
 Nombre de la tarea que se mostrarán en la lista de destino.  
  
 `strIconLocation`  
 Ubicación del icono que se mostrará en la lista de destino junto con el título.  
  
 `iIconIndex`  
 Índice de icono.  
  
 `pShellLink`  
 Vínculo del shell que representa una tarea que se va a agregar.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 La instancia de `CJumpList` tareas especificadas se acumulan y los agrega a la lista de destino durante la `CommitList`. Elementos de tarea aparecerán en una categoría en la parte inferior del menú destino de la aplicación. Esta categoría tiene prioridad sobre todas las demás categorías cuando se llena en la interfaz de usuario.  
  
##  <a name="a-nameaddtasksa--cjumplistaddtasks"></a><a name="addtasks"></a>CJumpList::AddTasks  
 Agrega elementos a la categoría de tareas canónica.  
  
```  
BOOL AddTasks(IObjectArray* pObjectCollection);
```  
  
### <a name="parameters"></a>Parámetros  
 `pObjectCollection`  
 Una colección de tareas va a agregar.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 La instancia de CJumpList tareas especificadas se acumulan y se agrega a la lista de destino durante la `CommitList`. Elementos de tarea aparecerán en una categoría en la parte inferior del menú destino de la aplicación. Esta categoría tiene prioridad sobre todas las demás categorías cuando se llena en la interfaz de usuario.  
  
##  <a name="a-nameaddtaskseparatora--cjumplistaddtaskseparator"></a><a name="addtaskseparator"></a>CJumpList::AddTaskSeparator  
 Agrega un separador entre las tareas.  
  
```  
BOOL AddTaskSeparator();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto, 0 si no lo está.  
  
##  <a name="a-namecjumplista--cjumplistcjumplist"></a><a name="cjumplist"></a>CJumpList::CJumpList  
 Construye un objeto `CJumpList`.  
  
```  
CJumpList(BOOL bAutoCommit = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bAutoCommit`  
 Si este parámetro es FALSE no se confirma automáticamente la lista en el destructor.  
  
##  <a name="a-nameclearalla--cjumplistclearall"></a><a name="clearall"></a>CJumpList::ClearAll  
 Quita todas las tareas y destinos que se han agregado a la instancia actual de `CJumpList` hasta ahora.  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método borra y libera todos los datos e interfaces internas.  
  
##  <a name="a-nameclearalldestinationsa--cjumplistclearalldestinations"></a><a name="clearalldestinations"></a>CJumpList::ClearAllDestinations  
 Quita todos los destinos que se han agregado a la instancia actual de CJumpList hasta ahora.  
  
```  
void ClearAllDestinations();
```  
  
### <a name="remarks"></a>Comentarios  
 Si desea quitar todos los destinos que se han agregado hasta ahora en la sesión actual de creación de la lista de destino y vuelva a agregar otros destinos, llame a esta función. Si el texto interno `ICustomDestinationList` ha sido inicializado, se deja activo.  
  
##  <a name="a-namecommitlista--cjumplistcommitlist"></a><a name="commitlist"></a>CJumpList::CommitList  
 Finaliza una transacción de creación de la lista y confirma la lista incluida en el almacén asociado (en este caso, el registro).  
  
```  
BOOL CommitList();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 La confirmación es atómica. Se devolverá un error si se produce un error en la confirmación.  Cuando `CommitList` se denomina actual se limpiará la lista de elementos eliminados. Llamar a este método restablece el objeto para que no tiene una transacción activa de la creación de la lista. Para actualizar la lista, `BeginList` debe llamarse de nuevo.  
  
##  <a name="a-namegetdestinationlista--cjumplistgetdestinationlist"></a><a name="getdestinationlist"></a>CJumpList::GetDestinationList  
 Recupera un puntero de interfaz a la lista de destino.  
  
```  
ICustomDestinationList* GetDestinationList();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 Si la lista de salto no se ha inicializado, o se ha confirmado o anulado, el valor devuelto será `NULL`.  
  
##  <a name="a-namegetmaxslotsa--cjumplistgetmaxslots"></a><a name="getmaxslots"></a>CJumpList::GetMaxSlots  
 Recupera el número máximo de elementos, incluidos los encabezados de categoría que se pueden mostrar en el menú de destino de la aplicación que realiza la llamada.  
  
```  
UINT GetMaxSlots() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 Las aplicaciones solo pueden informar de un número de elementos y los encabezados de categoría combinados hasta este valor. Si llama a `AppendCategory`, `AppendKnownCategory`, o `AddUserTasks` supera este número, devolverán un error.  
  
##  <a name="a-namegetremoveditemsa--cjumplistgetremoveditems"></a><a name="getremoveditems"></a>CJumpList::GetRemovedItems  
 Devuelve una matriz de elementos que representan quita destinos.  
  
```  
IObjectArray* GetRemovedItems();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 Los destinos quitados se recuperan durante la inicialización de la jump list. Cuando se genera una nueva lista de destino, las aplicaciones deben procesar primero la lista de destinos quitado borrar los datos de seguimiento para cualquier elemento devuelto por el enumerador de lista eliminado. Si una aplicación intenta proporcionar un elemento que se acaba de quitar en la transacción que la llamada actual al `BeginList` iniciado, la llamada al método que volver a agrega ese elemento se producirá un error, para asegurarse de que las aplicaciones respetan la lista quitada.  
  
##  <a name="a-nameinitializelista--cjumplistinitializelist"></a><a name="initializelist"></a>CJumpList::InitializeList  
 Inicia una transacción de creación de la lista.  
  
```  
BOOL InitializeList();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 No es necesario llamar explícitamente a este método a menos que desee recuperar un puntero a `ICustomDestinationList` con `GetDestinationList`, el número de ranuras disponibles mediante `GetMaxSlots`, o una lista de los elementos eliminados mediante `GetRemovedItems`.  
  
##  <a name="a-namesetappida--cjumplistsetappid"></a><a name="setappid"></a>CJumpList::SetAppID  
 Establece el identificador de modelo de aplicación de usuario de la lista que se generarán.  
  
```  
void SetAppID(LPCTSTR strAppID);
```  
  
### <a name="parameters"></a>Parámetros  
 `strAppID`  
 Una cadena que especifica el identificador de modelo de usuario de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

