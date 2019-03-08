---
title: CMenu (clase)
ms.date: 11/04/2016
f1_keywords:
- CMenu
- AFXWIN/CMenu
- AFXWIN/CMenu::CMenu
- AFXWIN/CMenu::AppendMenu
- AFXWIN/CMenu::Attach
- AFXWIN/CMenu::CheckMenuItem
- AFXWIN/CMenu::CheckMenuRadioItem
- AFXWIN/CMenu::CreateMenu
- AFXWIN/CMenu::CreatePopupMenu
- AFXWIN/CMenu::DeleteMenu
- AFXWIN/CMenu::DeleteTempMap
- AFXWIN/CMenu::DestroyMenu
- AFXWIN/CMenu::Detach
- AFXWIN/CMenu::DrawItem
- AFXWIN/CMenu::EnableMenuItem
- AFXWIN/CMenu::FromHandle
- AFXWIN/CMenu::GetDefaultItem
- AFXWIN/CMenu::GetMenuContextHelpId
- AFXWIN/CMenu::GetMenuInfo
- AFXWIN/CMenu::GetMenuItemCount
- AFXWIN/CMenu::GetMenuItemID
- AFXWIN/CMenu::GetMenuItemInfo
- AFXWIN/CMenu::GetMenuState
- AFXWIN/CMenu::GetMenuString
- AFXWIN/CMenu::GetSafeHmenu
- AFXWIN/CMenu::GetSubMenu
- AFXWIN/CMenu::InsertMenu
- AFXWIN/CMenu::InsertMenuItem
- AFXWIN/CMenu::LoadMenu
- AFXWIN/CMenu::LoadMenuIndirect
- AFXWIN/CMenu::MeasureItem
- AFXWIN/CMenu::ModifyMenu
- AFXWIN/CMenu::RemoveMenu
- AFXWIN/CMenu::SetDefaultItem
- AFXWIN/CMenu::SetMenuContextHelpId
- AFXWIN/CMenu::SetMenuInfo
- AFXWIN/CMenu::SetMenuItemBitmaps
- AFXWIN/CMenu::SetMenuItemInfo
- AFXWIN/CMenu::TrackPopupMenu
- AFXWIN/CMenu::TrackPopupMenuEx
- AFXWIN/CMenu::m_hMenu
helpviewer_keywords:
- CMenu [MFC], CMenu
- CMenu [MFC], AppendMenu
- CMenu [MFC], Attach
- CMenu [MFC], CheckMenuItem
- CMenu [MFC], CheckMenuRadioItem
- CMenu [MFC], CreateMenu
- CMenu [MFC], CreatePopupMenu
- CMenu [MFC], DeleteMenu
- CMenu [MFC], DeleteTempMap
- CMenu [MFC], DestroyMenu
- CMenu [MFC], Detach
- CMenu [MFC], DrawItem
- CMenu [MFC], EnableMenuItem
- CMenu [MFC], FromHandle
- CMenu [MFC], GetDefaultItem
- CMenu [MFC], GetMenuContextHelpId
- CMenu [MFC], GetMenuInfo
- CMenu [MFC], GetMenuItemCount
- CMenu [MFC], GetMenuItemID
- CMenu [MFC], GetMenuItemInfo
- CMenu [MFC], GetMenuState
- CMenu [MFC], GetMenuString
- CMenu [MFC], GetSafeHmenu
- CMenu [MFC], GetSubMenu
- CMenu [MFC], InsertMenu
- CMenu [MFC], InsertMenuItem
- CMenu [MFC], LoadMenu
- CMenu [MFC], LoadMenuIndirect
- CMenu [MFC], MeasureItem
- CMenu [MFC], ModifyMenu
- CMenu [MFC], RemoveMenu
- CMenu [MFC], SetDefaultItem
- CMenu [MFC], SetMenuContextHelpId
- CMenu [MFC], SetMenuInfo
- CMenu [MFC], SetMenuItemBitmaps
- CMenu [MFC], SetMenuItemInfo
- CMenu [MFC], TrackPopupMenu
- CMenu [MFC], TrackPopupMenuEx
- CMenu [MFC], m_hMenu
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
ms.openlocfilehash: bdc5f2ebf20949f63b3892ee8e8c6eedf05e2838
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293867"
---
# <a name="cmenu-class"></a>CMenu (clase)

Una encapsulación de `HMENU`de Windows.

## <a name="syntax"></a>Sintaxis

```
class CMenu : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMenu::CMenu](#cmenu)|Construye un objeto `CMenu`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|Anexa un nuevo elemento al final de este menú.|
|[CMenu::Attach](#attach)|Asocia un identificador de menú de Windows para un `CMenu` objeto.|
|[CMenu::CheckMenuItem](#checkmenuitem)|Coloca una marca de verificación junto a o quita una marca de verificación de un elemento de menú en el menú emergente.|
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|Coloca un botón de radio junto a un elemento de menú y quitará el botón de radio de todos los demás elementos de menú en el grupo.|
|[CMenu::CreateMenu](#createmenu)|Crea un menú vacío y lo asocia a un `CMenu` objeto.|
|[CMenu::CreatePopupMenu](#createpopupmenu)|Crea un menú emergente vacío y lo asocia a un `CMenu` objeto.|
|[CMenu::DeleteMenu](#deletemenu)|Elimina un elemento especificado en el menú. Si el elemento de menú tiene un menú emergente asociado, destruye el identificador del menú emergente y libera la memoria usada por ella.|
|[CMenu::DeleteTempMap](#deletetempmap)|Elimina cualquier temporal `CMenu` los objetos creados por el `FromHandle` función miembro.|
|[CMenu::DestroyMenu](#destroymenu)|Destruye el menú que se adjunta a un `CMenu` de objeto y libera la memoria que ocupaban el menú.|
|[CMenu::Detach](#detach)|Desasocia un identificador de menú de Windows desde un `CMenu` de objeto y devuelve el identificador.|
|[CMenu::DrawItem](#drawitem)|Lo llama el marco cuando un aspecto visual de los cambios de un menú dibujado por el propietario.|
|[CMenu::EnableMenuItem](#enablemenuitem)|Habilita, deshabilita o se atenúa (grises) un elemento de menú.|
|[CMenu::FromHandle](#fromhandle)|Devuelve un puntero a un `CMenu` objeto, dado un identificador de menú de Windows.|
|[CMenu::GetDefaultItem](#getdefaultitem)|Determina el elemento de menú predeterminado en el menú especificado.|
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|Recupera el identificador de contexto de ayuda asociado con el menú.|
|[CMenu::GetMenuInfo](#getmenuinfo)|Recupera información sobre un menú específico.|
|[CMenu::GetMenuItemCount](#getmenuitemcount)|Determina el número de elementos de un menú emergente o de nivel superior.|
|[CMenu::GetMenuItemID](#getmenuitemid)|Obtiene el identificador de elemento de menú para un elemento de menú que se encuentra en la posición especificada.|
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|Recupera información sobre un elemento de menú.|
|[CMenu::GetMenuState](#getmenustate)|Devuelve el estado de elemento de menú especificado o el número de elementos de un menú emergente.|
|[CMenu::GetMenuString](#getmenustring)|Recupera la etiqueta del elemento de menú especificado.|
|[CMenu::GetSafeHmenu](#getsafehmenu)|Devuelve el `m_hMenu` encapsulado por este `CMenu` objeto.|
|[CMenu::GetSubMenu](#getsubmenu)|Recupera un puntero a un menú emergente.|
|[CMenu::InsertMenu](#insertmenu)|Inserta un nuevo elemento de menú en la posición especificada, mover otros elementos del menú desplegable.|
|[CMenu::InsertMenuItem](#insertmenuitem)|Inserta un nuevo elemento de menú en la posición especificada en un menú.|
|[CMenu::LoadMenu](#loadmenu)|Carga un recurso de menú desde el archivo ejecutable y lo adjunta a un `CMenu` objeto.|
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|Carga un menú desde una plantilla de menú en la memoria y lo asocia a un `CMenu` objeto.|
|[CMenu::MeasureItem](#measureitem)|Lo llama el marco de trabajo para determinar las dimensiones de menú cuando se crea un menú dibujado por el propietario.|
|[CMenu::ModifyMenu](#modifymenu)|Cambia un elemento de menú existente en la posición especificada.|
|[CMenu::RemoveMenu](#removemenu)|Elimina un elemento de menú con un menú emergente asociado en el menú especificado.|
|[CMenu::SetDefaultItem](#setdefaultitem)|Establece el elemento de menú predeterminado para el menú especificado.|
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|Establece el identificador de contexto de ayuda que se asociará con el menú.|
|[CMenu::SetMenuInfo](#setmenuinfo)|Establece la información en un menú específico.|
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|Los mapas de bits de marca de verificación especificado se asocia con un elemento de menú.|
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|Cambia la información sobre un elemento de menú.|
|[CMenu::TrackPopupMenu](#trackpopupmenu)|Muestra un menú emergente flotante en la ubicación especificada y realiza el seguimiento de la selección de elementos en el menú emergente.|
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|Muestra un menú emergente flotante en la ubicación especificada y realiza el seguimiento de la selección de elementos en el menú emergente.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CMenu::operator HMENU](#operator_hmenu)|Recupera el identificador del objeto menu.|
|[CMenu::operator! =](#operator_neq)|Determina si dos objetos de menú no son iguales.|
|[CMenu::operator ==](#operator_eq_eq)|Determina si dos objetos de menú son iguales.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CMenu::m_hMenu](#m_hmenu)|Especifica el identificador del menú de Windows asociado a la `CMenu` objeto.|

## <a name="remarks"></a>Comentarios

Proporciona funciones miembro para crear, seguimiento, actualizar y destruir un menú.

Crear un `CMenu` objeto en el marco de pila como una variable local, a continuación, llame a `CMenu`de las funciones miembro para manipular el nuevo menú según sea necesario. A continuación, llame a [CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu) establecer el menú en una ventana, seguido inmediatamente por una llamada a la `CMenu` del objeto [Detach](#detach) función miembro. El `CWnd::SetMenu` función miembro establece el menú Ventana en el menú nuevo, hace que la ventana se vuelva a dibujar para reflejar el cambio de menú y también pasa la propiedad del menú de la ventana. La llamada a `Detach` desasocia el HMENU desde el `CMenu` lo objeto, que, cuando local `CMenu` variable sale del ámbito, el `CMenu` destructor de objeto no intenta destruir un menú ya no posee. El propio menú se destruye automáticamente cuando se destruye la ventana.

Puede usar el [LoadMenuIndirect](#loadmenuindirect) para crear un menú desde una plantilla en la memoria, pero un menú creado a partir de un recurso mediante una llamada a función miembro [LoadMenu](#loadmenu) resulta más fácil de mantener y el propio recurso de menú se pueden crear y modificar mediante el editor de menús.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="appendmenu"></a>  CMenu::AppendMenu

Anexa un nuevo elemento al final de un menú.

```
BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>Parámetros

*nFlags*<br/>
Especifica información sobre el estado del nuevo elemento de menú cuando se agrega al menú. Consta de uno o varios de los valores enumerados en la sección Comentarios.

*nIDNewItem*<br/>
Especifica el identificador de comando del elemento de menú nuevo o, si *nFlags* está establecido en MF_POPUP, el identificador de menú ( `HMENU`) de un menú emergente. El *nIDNewItem* parámetro se omite (no es necesario) si *nFlags* está establecido en MF_SEPARATOR.

*lpszNewItem*<br/>
Especifica el contenido del nuevo elemento de menú. El *nFlags* parámetro se usa para interpretar *lpszNewItem* de la manera siguiente:

|nFlags|Interpretación de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contiene un valor de 32 bits proporcionada por la aplicación que la aplicación puede usar para mantener datos adicionales asociados con el elemento de menú. Este valor de 32 bits está disponible para la aplicación cuando procesa mensajes WM_MEASUREITEM y WM_DRAWITEM. El valor se almacena en el `itemData` miembro de la estructura que se suministra con esos mensajes.|
|MF_STRING|Contiene un puntero a una cadena terminada en null. Se trata de la interpretación predeterminada.|
|MF_SEPARATOR|El *lpszNewItem* parámetro se omite (no es necesario).|

*pBmp*<br/>
Apunta a un `CBitmap` objeto que se usará como el elemento de menú.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La aplicación puede especificar el estado del elemento de menú mediante el establecimiento de valores en *nFlags*. Cuando *nIDNewItem* especifica un menú emergente, se convierte en parte del menú al que se anexa. Si se destruye el menú, también se destruirá el menú anexado. Un menú anexado se debe desasociar de un `CMenu` objeto para evitar el conflicto. Tenga en cuenta que no son válidas para la versión de mapa de bits de MF_STRING y MF_OWNERDRAW `AppendMenu`.

En la lista siguiente describe las marcas que se pueden establecer en *nFlags*:

- MF_CHECKED actúa como un botón de alternancia con MF_UNCHECKED para colocar el valor predeterminado Compruebe marca junto al elemento. Cuando la aplicación proporciona mapas de bits de marca de verificación (consulte la [SetMenuItemBitmaps](#setmenuitembitmaps) función miembro), se muestra el mapa de bits "marca de verificación en".

- MF_UNCHECKED actúa como un botón de alternancia con MF_CHECKED para quitar una marca de verificación situada junto al elemento. Cuando la aplicación proporciona mapas de bits de marca de verificación (consulte la `SetMenuItemBitmaps` función miembro), se muestra el mapa de bits "marca de verificación Desactivar".

- MF_DISABLED deshabilita el elemento de menú para que no se puede seleccionar pero no lo dim.

- MF_ENABLED permite que el elemento de menú para que se pueden seleccionar y restaurarlo desde su estado atenuado.

- MF_GRAYED deshabilita el elemento de menú para que no se pueden seleccionar y se atenúa.

- MF_MENUBARBREAK coloca el elemento en una nueva línea en los menús estáticos, o en una nueva columna en los menús emergentes. Una línea divisoria vertical separará la nueva columna de un menú emergente de la columna antigua.

- MF_MENUBREAK coloca el elemento en una nueva línea en los menús estáticos, o en una nueva columna en los menús emergentes. No se coloca línea divisoria entre las columnas.

- MF_OWNERDRAW especifica que el elemento es un elemento dibujado por el propietario. Cuando el menú se muestra por primera vez, la ventana que posee el menú recibe un mensaje WM_MEASUREITEM, que recupera el alto y ancho del elemento de menú. El mensaje WM_DRAWITEM es lo que se envía cada vez que el propietario debe actualizar la apariencia visual del elemento de menú. Esta opción no es válida para un elemento de menú de nivel superior.

- MF_POPUP especifica que el elemento de menú tiene un menú emergente asociado con él. El parámetro ID especifica un identificador de un menú emergente que se va a asociar con el elemento. Esto se utiliza para agregar un menú emergente de nivel superior o un menú emergente jerárquico a un elemento de menú emergente.

- MF_SEPARATOR dibuja una línea divisoria horizontal. Solo puede usarse en un menú emergente. Esta línea no puede ser atenuada, deshabilitada o resaltada. Se omiten los demás parámetros.

- MF_STRING especifica que el elemento de menú es una cadena de caracteres.

Cada uno de los grupos siguientes enumera las marcas que se excluyen mutuamente y no pueden usarse juntos:

- MF_DISABLED MF_ENABLED y MF_GRAYED

- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR y la versión de mapa de bits

- MF_MENUBARBREAK y MF_MENUBREAK

- MF_CHECKED y MF_UNCHECKED

Cada vez que un menú que reside en una ventana se cambia (sean o no se muestra la ventana), la aplicación debe llamar a [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::CreateMenu](#createmenu).

##  <a name="attach"></a>  CMenu::Attach

Asocia un menú de Windows existente a un `CMenu` objeto.

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>Parámetros

*hMenu*<br/>
Especifica un identificador de un menú de Windows.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

No se debe llamar esta función si un menú ya está asociado a la `CMenu` objeto. El identificador de menú se almacena en el `m_hMenu` miembro de datos.

Si el menú que desea manipular ya está asociado a una ventana, puede usar el [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu) función para obtener un identificador del menú.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="checkmenuitem"></a>  CMenu::CheckMenuItem

Marcas de verificación que se agrega o quita las marcas de verificación de los elementos de menú en el menú emergente.

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>Parámetros

*nIDCheckItem*<br/>
Especifica el elemento de menú debe comprobarse, según lo determinado por *nCompruebe*.

*nCheck*<br/>
Especifica cómo comprobar el elemento de menú y cómo determinar la posición del elemento en el menú. El *nCompruebe* parámetro puede ser una combinación de MF_CHECKED o MF_UNCHECKED con indicadores MF_BYPOSITION o MF_BYCOMMAND. Estas marcas se pueden combinar mediante el operador OR bit a bit. Tienen los significados siguientes:

- MF_BYCOMMAND especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado.

- MF_BYPOSITION especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.

- MF_CHECKED actúa como un botón de alternancia con MF_UNCHECKED para colocar el valor predeterminado Compruebe marca junto al elemento.

- MF_UNCHECKED actúa como un botón de alternancia con MF_CHECKED para quitar una marca de verificación situada junto al elemento.

### <a name="return-value"></a>Valor devuelto

El estado anterior del elemento: MF_CHECKED o MF_UNCHECKED o 0xFFFFFFFF si no existe el elemento de menú.

### <a name="remarks"></a>Comentarios

El *nIDCheckItem* parámetro especifica el elemento que se puede modificar.

El *nIDCheckItem* parámetro puede identificar un elemento de menú emergente, así como un elemento de menú. Se necesita ningún paso especial para comprobar un elemento de menú emergente. No se puede comprobar los elementos de menú de nivel superior. Un elemento de menú emergente debe comprobarse por posición, puesto que no tiene un identificador de elemento de menú asociado con él.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::GetMenuState](#getmenustate).

##  <a name="checkmenuradioitem"></a>  CMenu::CheckMenuRadioItem

Comprueba un elemento de menú especificado y lo convierte en un elemento de radio.

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

*nIDFirst*<br/>
Especifica (como un identificador o el desplazamiento, dependiendo del valor de *nFlags*) el primer elemento de menú en el grupo de botones de radio.

*nIDLast*<br/>
Especifica (como un identificador o el desplazamiento, dependiendo del valor de *nFlags*) el último elemento de menú en el grupo de botones de radio.

*nIDItem*<br/>
Especifica (como un identificador o el desplazamiento, dependiendo del valor de *nFlags*) del elemento en el grupo que se comprobará con un botón de radio.

*nFlags*<br/>
Especifica la interpretación de *nIDFirst*, *nIDLast*, y *nIDItem* de la manera siguiente:

|nFlags|Interpretación|
|------------|--------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.|

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; en caso contrario, 0

### <a name="remarks"></a>Comentarios

Al mismo tiempo, la función desactiva todos los demás elementos de menú en el grupo asociado y borra la marca de tipo de elemento de radio para esos elementos. Elemento activado se muestra utilizando un mapa de bits de botón (o viñetas) de radio en lugar de un mapa de bits de marca de verificación.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).

##  <a name="cmenu"></a>  CMenu::CMenu

Crea un menú vacío y lo asocia a un `CMenu` objeto.

```
CMenu();
```

### <a name="remarks"></a>Comentarios

El menú no se crea hasta que se llame a uno de crear o cargar las funciones miembro de `CMenu:`

- [CreateMenu](#createmenu)

- [CreatePopupMenu](#createpopupmenu)

- [LoadMenu](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [Asociar](#attach)

##  <a name="createmenu"></a>  CMenu::CreateMenu

Crea un menú y lo adjunta a la `CMenu` objeto.

```
BOOL CreateMenu();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el menú se creó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

El menú inicialmente está vacío. Se pueden agregar elementos de menú mediante el uso de la `AppendMenu` o `InsertMenu` función miembro.

Si el menú se asigna a una ventana, se destruye automáticamente cuando se destruye la ventana.

Antes de salir, una aplicación debe liberar los recursos del sistema asociados a un menú si el menú no está asignado a una ventana. Una aplicación libera un menú mediante una llamada a la [DestroyMenu](#destroymenu) función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

##  <a name="createpopupmenu"></a>  CMenu::CreatePopupMenu

Crea un menú emergente y lo adjunta a la `CMenu` objeto.

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha creado correctamente el menú emergente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

El menú inicialmente está vacío. Se pueden agregar elementos de menú mediante el uso de la `AppendMenu` o `InsertMenu` función miembro. La aplicación puede agregar el menú emergente a un menú existente o un menú emergente. El `TrackPopupMenu` función miembro puede usarse para mostrar de este menú como menú emergente flotante y para realizar el seguimiento de las selecciones en el menú emergente.

Si el menú se asigna a una ventana, se destruye automáticamente cuando se destruye la ventana. Si el menú se agrega a un menú existente, se destruye automáticamente cuando se destruye ese menú.

Antes de salir, una aplicación debe liberar los recursos del sistema asociados a un menú emergente si el menú no está asignado a una ventana. Una aplicación libera un menú mediante una llamada a la [DestroyMenu](#destroymenu) función miembro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::CreateMenu](#createmenu).

##  <a name="deletemenu"></a>  CMenu::DeleteMenu

Elimina un elemento en el menú.

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

*nPosition*<br/>
Especifica el elemento de menú que se va a eliminar, según lo determinado por *nFlags*.

*nFlags*<br/>
Se usa para interpretar *Nposición* de la manera siguiente:

|nFlags|Interpretación de Nposición|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.|

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Si el elemento de menú tiene un menú emergente asociado, `DeleteMenu` destruye el identificador del menú emergente y libera la memoria utilizada por el menú emergente.

Cada vez que un menú que reside en una ventana se cambia (sean o no se muestra la ventana), la aplicación debe llamar a [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="deletetempmap"></a>  CMenu::DeleteTempMap

Llama de forma automática el `CWinApp` controlador de tiempo de inactividad, elimina cualquier temporal `CMenu` los objetos creados por el [FromHandle](#fromhandle) función miembro.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Comentarios

`DeleteTempMap` Desasocia el objeto de menú de Windows asociado a un archivo temporal `CMenu` objeto antes de eliminar el `CMenu` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

##  <a name="destroymenu"></a>  CMenu::DestroyMenu

Destruye el menú y los recursos de Windows que se usaron.

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se destruye el menú; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

El menú se separa de la `CMenu` objeto antes de ser destruido. El Windows `DestroyMenu` función es invocada automáticamente el `CMenu` destructor.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::CreateMenu](#createmenu).

##  <a name="detach"></a>  CMenu::Detach

Desasocia un menú de Windows desde un `CMenu` de objeto y devuelve el identificador.

```
HMENU Detach();
```

### <a name="return-value"></a>Valor devuelto

El identificador de tipo HMENU, a un menú de Windows, si se realiza correctamente; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

El `m_hMenu` miembro de datos se establece en NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="drawitem"></a>  CMenu::DrawItem

Lo llama el marco cuando un aspecto visual de los cambios de un menú dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Un puntero a un [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) estructura que contiene información sobre el tipo de dibujo necesaria.

### <a name="remarks"></a>Comentarios

El `itemAction` miembro de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que se realiza. Reemplace esta función miembro para implementar un dibujado por el propietario del dibujo `CMenu` objeto. La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para proporciona el contexto de presentación en *lpDrawItemStruct* antes de la finalización de esta función miembro.

Consulte [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) para obtener una descripción de la `DRAWITEMSTRUCT` estructura.

### <a name="example"></a>Ejemplo

El código siguiente procede de la MFC [CTRLTEST](../../visual-cpp-samples.md) ejemplo:

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

##  <a name="enablemenuitem"></a>  CMenu::EnableMenuItem

Habilita, deshabilita o se atenúa un elemento de menú.

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>Parámetros

*nIDEnableItem*<br/>
Especifica el elemento de menú esté habilitado, según lo determinado por *nEnable*. Elementos de menú emergente, así como elementos de menú estándar, puede especificar este parámetro.

*nEnable*<br/>
Especifica la acción que se realizará. Puede ser una combinación de MF_DISABLED, MF_ENABLED o MF_GRAYED con MF_BYCOMMAND o MF_BYPOSITION. Estos valores se pueden combinar mediante el operador OR bit a bit. Estos valores tienen los significados siguientes:

- MF_BYCOMMAND especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado.

- MF_BYPOSITION especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.

- MF_DISABLED deshabilita el elemento de menú para que no se puede seleccionar pero no lo dim.

- MF_ENABLED permite que el elemento de menú para que se pueden seleccionar y restaurarlo desde su estado atenuado.

- MF_GRAYED deshabilita el elemento de menú para que no se pueden seleccionar y se atenúa.

### <a name="return-value"></a>Valor devuelto

Estado anterior (MF_DISABLED, MF_ENABLED o MF_GRAYED) o -1 si no es válido.

### <a name="remarks"></a>Comentarios

El [CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu), y [LoadMenuIndirect](#loadmenuindirect) funciones miembro también pueden establecer el estado (habilitado, deshabilitar o atenuado) de un elemento de menú.

Con el valor MF_BYPOSITION requiere una aplicación para usar el valor correcto `CMenu`. Si el `CMenu` del menú de barra se usa, se ve afectado un elemento de menú de nivel superior (un elemento en la barra de menús). Para establecer el estado de un elemento en un menú emergente de ventanas emergente o anidado por posición, una aplicación debe especificar el `CMenu` del menú emergente.

Cuando una aplicación especifica la marca MF_BYCOMMAND, Windows comprueba todos los elementos de menú emergente que están subordinados a la `CMenu`; por lo tanto, a menos que los elementos de menú duplicados están presentes, utilizando el `CMenu` del menú de barra es suficiente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

##  <a name="fromhandle"></a>  CMenu::FromHandle

Devuelve un puntero a un `CMenu` objeto especifica un identificador de Windows a un menú.

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>Parámetros

*hMenu*<br/>
Identificador de Windows a un menú.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CMenu` que puede ser temporal o permanente.

### <a name="remarks"></a>Comentarios

Si un `CMenu` objeto no está asociado al objeto de menú de Windows, un archivo temporal `CMenu` objeto creado y conectado.

Este temporal `CMenu` objeto solo es válido hasta la próxima vez que la aplicación tiene tiempo de inactividad en su bucle de eventos, momento en el que se eliminan todos los objetos temporales.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::CreateMenu](#createmenu).

##  <a name="getdefaultitem"></a>  CMenu::GetDefaultItem

Determina el elemento de menú predeterminado en el menú especificado.

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parámetros

*gmdiFlags*<br/>
Valor que especifica cómo la función busca los elementos de menú. Este parámetro puede ser ninguno, uno o una combinación de los siguientes valores:

|Valor|Significado|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|Especifica que, si el elemento predeterminado es uno que se abre un submenú, la función es buscar de forma recursiva en el submenú correspondiente. Si el submenú no tiene ningún elemento de forma predeterminada, el valor devuelto identifica el elemento que se abre el submenú.<br /><br /> De forma predeterminada, la función devuelve el primer elemento de forma predeterminada en el menú especificado, independientemente de si es un elemento que se abre un submenú.|
|GMDI_USEDISABLED|Especifica que la función es devolver un elemento de forma predeterminada, incluso si está deshabilitado.<br /><br /> De forma predeterminada, la función omite los elementos deshabilitados o no accesible.|

*fByPos*<br/>
Valor que especifica si se debe recuperar el identificador del elemento de menú o su posición. Si este parámetro es FALSE, se devuelve el identificador. En caso contrario, se devuelve la posición.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es el identificador o la posición del elemento de menú. Si se produce un error en la función, el valor devuelto es - 1.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento de la función de Win32 [GetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-getmenudefaultitem), tal y como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

##  <a name="getmenucontexthelpid"></a>  CMenu::GetMenuContextHelpId

Recupera el Id. de asociado de ayuda contextual `CMenu`.

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>Valor devuelto

La Ayuda contextual ID asociado actualmente `CMenu` si existe; en caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

##  <a name="getmenuinfo"></a>  CMenu::GetMenuInfo

Recupera información de un menú.

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>Parámetros

*lpcmi*<br/>
Un puntero a un [MENUINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuinfo) estructura que contiene información para el menú.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero; en caso contrario, el valor devuelto es cero.

### <a name="remarks"></a>Comentarios

Llame a esta función para recuperar información sobre el menú.

##  <a name="getmenuitemcount"></a>  CMenu::GetMenuItemCount

Determina el número de elementos de un menú emergente o de nivel superior.

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos en el menú si la función se realiza correctamente; en caso contrario,-1.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="getmenuitemid"></a>  CMenu::GetMenuItemID

Obtiene el identificador de elemento de menú para un elemento de menú situado en la posición definida por *nPos*.

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Especifica la posición (basado en cero) del elemento de menú cuyo identificador se van a recuperar.

### <a name="return-value"></a>Valor devuelto

El identificador del elemento para el elemento especificado en un menú emergente si la función es correcta. Si el elemento especificado es un menú emergente (en lugar de un elemento en el menú emergente), el valor devuelto es -1. Si *nPos* corresponde a un elemento de menú separador, el valor devuelto es 0.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

##  <a name="getmenuiteminfo"></a>  CMenu::GetMenuItemInfo

Recupera información sobre un elemento de menú.

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parámetros

*uItem*<br/>
Identificador o la posición del elemento de menú para obtener información acerca de. El significado de este parámetro depende del valor de `ByPos`.

*lpMenuItemInfo*<br/>
Un puntero a un [MENUITEMINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuiteminfoa), tal y como se describe en el SDK de Windows, que contiene información sobre el menú.

*fByPos*<br/>
Valor que especifica el significado de `nIDItem`. De forma predeterminada, `ByPos` es FALSE, lo que indica que uItem es un identificador de elemento de menú. Si `ByPos` no está establecida en FALSE, indica una posición de elemento de menú.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero. Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, use la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360), tal y como se describe en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento de la de la función de Win32 [GetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-getmenuiteminfoa), tal y como se describe en el SDK de Windows. Tenga en cuenta que en la implementación de MFC `GetMenuItemInfo`, no use un identificador de un menú.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

##  <a name="getmenustate"></a>  CMenu::GetMenuState

Devuelve el estado de elemento de menú especificado o el número de elementos de un menú emergente.

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Especifica el identificador de elemento de menú, según lo determinado por *nFlags*.

*nFlags*<br/>
Especifica la naturaleza de *nID*. Puede ser uno de los siguientes valores:

- MF_BYCOMMAND especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado.

- MF_BYPOSITION especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.

### <a name="return-value"></a>Valor devuelto

El valor 0xFFFFFFFF si el elemento especificado no existe. Si *nId* identifica un menú emergente, el byte de orden superior contiene el número de elementos en el menú emergente y el byte de orden inferior contiene las marcas de menú asociadas con el menú emergente. En caso contrario, el valor devuelto es una máscara (booleano o) de los valores de la lista siguiente (esta máscara describe el estado del menú de elemento que *nId* identifica):

- MF_CHECKED actúa como un botón de alternancia con MF_UNCHECKED para colocar el valor predeterminado Compruebe marca junto al elemento. Cuando la aplicación proporciona mapas de bits de marca de verificación (consulte la `SetMenuItemBitmaps` función miembro), se muestra el mapa de bits "marca de verificación en".

- MF_DISABLED deshabilita el elemento de menú para que no se puede seleccionar pero no lo dim.

- MF_ENABLED permite que el elemento de menú para que se pueden seleccionar y restaurarlo desde su estado atenuado. Tenga en cuenta que el valor de esta constante es 0; una aplicación no debe probar en 0 para un error cuando se usa este valor.

- MF_GRAYED deshabilita el elemento de menú para que no se pueden seleccionar y se atenúa.

- MF_MENUBARBREAK coloca el elemento en una nueva línea en los menús estáticos, o en una nueva columna en los menús emergentes. Una línea divisoria vertical separará la nueva columna de un menú emergente de la columna antigua.

- MF_MENUBREAK coloca el elemento en una nueva línea en los menús estáticos, o en una nueva columna en los menús emergentes. No se coloca línea divisoria entre las columnas.

- MF_SEPARATOR dibuja una línea divisoria horizontal. Solo puede usarse en un menú emergente. Esta línea no puede ser atenuada, deshabilitada o resaltada. Se omiten los demás parámetros.

- MF_UNCHECKED actúa como un botón de alternancia con MF_CHECKED para quitar una marca de verificación situada junto al elemento. Cuando la aplicación proporciona mapas de bits de marca de verificación (consulte la `SetMenuItemBitmaps` función miembro), se muestra el mapa de bits "marca de verificación Desactivar". Tenga en cuenta que el valor de esta constante es 0; una aplicación no debe probar en 0 para un error cuando se usa este valor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

##  <a name="getmenustring"></a>  CMenu::GetMenuString

Copia la etiqueta del elemento de menú especificado en el búfer especificado.

```
int GetMenuString(
    UINT nIDItem,
    LPTSTR lpString,
    int nMaxCount,
    UINT nFlags) const;

int GetMenuString(
    UINT nIDItem,
    CString& rString,
    UINT nFlags) const;
```

### <a name="parameters"></a>Parámetros

*nIDItem*<br/>
Especifica el identificador entero del elemento de menú o el desplazamiento del elemento de menú en el menú, dependiendo del valor de *nFlags*.

*lpString*<br/>
Señala el búfer que va a recibir la etiqueta.

*rString*<br/>
Una referencia a un `CString` objeto que va a recibir la cadena copiada de menú.

*nMaxCount*<br/>
Especifica la longitud máxima (en caracteres) de la etiqueta que se va a copiar. Si es mayor que el máximo especificado en la etiqueta *nMaxCount*, se truncan los caracteres adicionales.

*nFlags*<br/>
Especifica la interpretación de los *nIDItem* parámetro. Puede ser uno de los siguientes valores:

|nFlags|Interpretación de nIDItem|
|------------|-------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.|

### <a name="return-value"></a>Valor devuelto

Especifica el número real de caracteres copiados en el búfer, sin incluir el terminador nulo.

### <a name="remarks"></a>Comentarios

El *nMaxCount* parámetro debe ser mayor que el número de caracteres de la etiqueta para acomodar el carácter null que finaliza una cadena de uno.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

##  <a name="getsafehmenu"></a>  CMenu::GetSafeHmenu

Devuelve el HMENU encapsulado por este `CMenu` objeto o un valor NULL`CMenu` puntero.

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::LoadMenu](#loadmenu).

##  <a name="getsubmenu"></a>  CMenu::GetSubMenu

Recupera el `CMenu` objeto de un menú emergente.

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Especifica la posición del menú contenido en el menú emergente. Los valores de posición empiezan en 0 para el primer elemento de menú. Identificador del menú emergente no se puede usar en esta función.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CMenu` cuyo `m_hMenu` miembro contiene un identificador del menú emergente si existe un menú emergente en la posición especificada; de lo contrario, NULL. Si un `CMenu` objeto no existe, a continuación, se crea uno temporal. El `CMenu` puntero devuelto no debe almacenarse.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::TrackPopupMenu](#trackpopupmenu).

##  <a name="insertmenu"></a>  CMenu::InsertMenu

Inserta un nuevo elemento de menú en la posición especificada por *Nposición* y otros elementos se mueve el menú desplegable.

```
BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>Parámetros

*nPosition*<br/>
Especifica el elemento de menú antes de que el nuevo elemento de menú es va a insertar. El *nFlags* parámetro puede usarse para interpretar *Nposición* de las maneras siguientes:

|nFlags|Interpretación de Nposición|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0. Si *Nposición* es -1, el nuevo elemento de menú se anexa al final del menú.|

*nFlags*<br/>
Especifica cómo *Nposición* se interpreta y especifica información sobre el estado del nuevo elemento de menú cuando se agrega al menú. Para obtener una lista de las marcas que se pueden establecer, consulte el [AppendMenu](#appendmenu) función miembro. Para especificar más de un valor, use el operador OR bit a bit para combinarlos con la marca MF_BYCOMMAND o MF_BYPOSITION.

*nIDNewItem*<br/>
Especifica el identificador de comando del elemento de menú nuevo o, si *nFlags* está establecido en MF_POPUP, el identificador de menú (HMENU) del menú emergente. El *nIDNewItem* parámetro se omite (no es necesario) si *nFlags* está establecido en MF_SEPARATOR.

*lpszNewItem*<br/>
Especifica el contenido del nuevo elemento de menú. *nFlags* puede usarse para interpretar *lpszNewItem* de las maneras siguientes:

|nFlags|Interpretación de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contiene un valor de 32 bits proporcionada por la aplicación que la aplicación puede usar para mantener datos adicionales asociados con el elemento de menú. Este valor de 32 bits está disponible para la aplicación en el `itemData` miembro de la estructura proporcionada por el [WM_MEASUREITEM](/windows/desktop/Controls/wm-measureitem) y [WM_DRAWITEM](/windows/desktop/Controls/wm-drawitem) mensajes. Estos mensajes se envían cuando el elemento de menú se muestra inicialmente o se cambia.|
|MF_STRING|Contiene un puntero largo a una cadena terminada en null. Se trata de la interpretación predeterminada.|
|MF_SEPARATOR|El *lpszNewItem* parámetro se omite (no es necesario).|

*pBmp*<br/>
Apunta a un `CBitmap` objeto que se usará como el elemento de menú.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La aplicación puede especificar el estado del elemento de menú mediante el establecimiento de valores en *nFlags*.

Cada vez que un menú que reside en una ventana se cambia (sean o no se muestra la ventana), la aplicación debe llamar a `CWnd::DrawMenuBar`.

Cuando *nIDNewItem* especifica un menú emergente, se convierte en parte del menú en el que se inserta. Si se destruye el menú, también se destruirá el menú insertado. Un menú insertado se debe desasociar de un `CMenu` objeto para evitar el conflicto.

Si el activo se maximiza la ventana secundaria de varios documentos (MDI) de la interfaz y una aplicación inserta un menú emergente en el menú de la aplicación MDI mediante una llamada a esta función y se especificará el indicador MF_BYPOSITION, en el menú insertan una posición más hacia la izquierda que Esperado. Esto sucede porque el menú de Control de la ventana secundaria MDI activa se inserta en la primera posición de la barra de menús de la ventana de marco MDI. Para colocar el menú correctamente, la aplicación debe agregar 1 al valor de posición que se usará en caso contrario. Una aplicación puede usar el mensaje WM_MDIGETACTIVE para determinar si se maximiza la ventana secundaria activa actualmente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

##  <a name="insertmenuitem"></a>  CMenu::InsertMenuItem

Inserta un nuevo elemento de menú en la posición especificada en un menú.

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parámetros

*uItem*<br/>
Consulte la descripción de *uItem* en [InsertMenuItem](/windows/desktop/api/winuser/nf-winuser-insertmenuitema) en el SDK de Windows.

*lpMenuItemInfo*<br/>
Consulte la descripción de *lpmii* en `InsertMenuItem` en el SDK de Windows.

*fByPos*<br/>
Consulte la descripción de *fByPosition* en `InsertMenuItem` en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Esta función contiene [InsertMenuItem](/windows/desktop/api/winuser/nf-winuser-insertmenuitema), que se describen en el SDK de Windows.

##  <a name="loadmenu"></a>  CMenu::LoadMenu

Carga un recurso de menú de archivo ejecutable de la aplicación y lo adjunta a la `CMenu` objeto.

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Apunta a una cadena terminada en null que contiene el nombre del recurso de menú para cargar.

*nIDResource*<br/>
Especifica el identificador de menú del recurso de menú para cargar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el recurso de menú se ha cargado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Antes de salir, una aplicación debe liberar los recursos del sistema asociados a un menú si el menú no está asignado a una ventana. Una aplicación libera un menú mediante una llamada a la [DestroyMenu](#destroymenu) función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

##  <a name="loadmenuindirect"></a>  CMenu::LoadMenuIndirect

Carga un recurso desde una plantilla de menú en la memoria y lo adjunta a la `CMenu` objeto.

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>Parámetros

*lpMenuTemplate*<br/>
Apunta a una plantilla de menú (que es una sola [MENUITEMTEMPLATEHEADER](/windows/desktop/api/winuser/ns-winuser-menuitemtemplateheader) estructura y una colección de uno o varios [MENUITEMTEMPLATE](/windows/desktop/api/winuser/ns-winuser-menuitemtemplate) estructuras). Para obtener más información sobre estas dos estructuras, vea el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el recurso de menú se ha cargado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Una plantilla de menú es un encabezado seguido de una colección de uno o varios [MENUITEMTEMPLATE](/windows/desktop/api/winuser/ns-winuser-menuitemtemplate) estructuras, cada uno de los cuales puede contener uno o varios elementos de menú y menús emergentes.

El número de versión debe ser 0.

El `mtOption` marcas deben incluir MF_END del último elemento en una lista emergente y el último elemento en la lista principal. Consulte la `AppendMenu` función miembro para otras marcas. El `mtId` se debe omitir el miembro de la estructura MENUITEMTEMPLATE cuando se especifica MF_POPUP en `mtOption`.

El espacio asignado para la estructura MENUITEMTEMPLATE debe ser lo suficientemente grande como para `mtString` para contener el nombre del elemento de menú como una cadena terminada en null.

Antes de salir, una aplicación debe liberar los recursos del sistema asociados a un menú si el menú no está asignado a una ventana. Una aplicación libera un menú mediante una llamada a la [DestroyMenu](#destroymenu) función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

##  <a name="m_hmenu"></a>  CMenu::m_hMenu

Especifica el identificador HMENU del menú de Windows asociado a la `CMenu` objeto.

```
HMENU m_hMenu;
```

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::LoadMenu](#loadmenu).

##  <a name="measureitem"></a>  CMenu::MeasureItem

Lo llama el marco de trabajo cuando se crea un menú con el estilo de dibujo del propietario.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpMeasureItemStruct*<br/>
Un puntero a un `MEASUREITEMSTRUCT` estructura.

### <a name="remarks"></a>Comentarios

De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro y rellene el `MEASUREITEMSTRUCT` estructura para informar a Windows de las dimensiones del menú.

Consulte [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) para obtener una descripción de la `MEASUREITEMSTRUCT` estructura.

### <a name="example"></a>Ejemplo

El código siguiente procede de la MFC [CTRLTEST](../../visual-cpp-samples.md) ejemplo:

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

##  <a name="modifymenu"></a>  CMenu::ModifyMenu

Cambia un elemento de menú existente en la posición especificada por *Nposición*.

```
BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>Parámetros

*nPosition*<br/>
Especifica el elemento de menú que se puede cambiar. El *nFlags* parámetro puede usarse para interpretar *Nposición* de las maneras siguientes:

|nFlags|Interpretación de Nposición|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.|

*nFlags*<br/>
Especifica cómo *Nposición* se interpreta y se proporciona información sobre los cambios que se realizan al elemento de menú. Para obtener una lista de marcas que se pueden establecer, consulte el [AppendMenu](#appendmenu) función miembro.

*nIDNewItem*<br/>
Especifica el identificador de comando del elemento de menú modificada o, si *nFlags* está establecido en MF_POPUP, el identificador de menú (HMENU) de un menú emergente. El *nIDNewItem* parámetro se omite (no es necesario) si *nFlags* está establecido en MF_SEPARATOR.

*lpszNewItem*<br/>
Especifica el contenido del nuevo elemento de menú. El *nFlags* parámetro puede usarse para interpretar *lpszNewItem* de las maneras siguientes:

|nFlags|Interpretación de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contiene un valor de 32 bits proporcionada por la aplicación que la aplicación puede usar para mantener datos adicionales asociados con el elemento de menú. Este valor de 32 bits está disponible para la aplicación cuando procesa MF_MEASUREITEM y MF_DRAWITEM.|
|MF_STRING|Contiene un puntero largo a una cadena terminada en null o a un `CString`.|
|MF_SEPARATOR|El *lpszNewItem* parámetro se omite (no es necesario).|

*pBmp*<br/>
Apunta a un `CBitmap` objeto que se usará como el elemento de menú.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La aplicación especifica el nuevo estado del elemento de menú mediante el establecimiento de valores en *nFlags*. Si esta función reemplaza a un menú emergente asociado al elemento de menú, destruye el menú emergente antiguo y libera la memoria utilizada por el menú emergente.

Cuando *nIDNewItem* especifica un menú emergente, se convierte en parte del menú en el que se inserta. Si se destruye el menú, también se destruirá el menú insertado. Un menú insertado se debe desasociar de un `CMenu` objeto para evitar el conflicto.

Cada vez que un menú que reside en una ventana se cambia (sean o no se muestra la ventana), la aplicación debe llamar a `CWnd::DrawMenuBar`. Para cambiar los atributos de elementos de menú existentes, es mucho más rápido utilizar el `CheckMenuItem` y `EnableMenuItem` funciones miembro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

##  <a name="operator_hmenu"></a>  CMenu::operator HMENU

Utilice este operador para recuperar el identificador de la `CMenu` objeto.

```
operator HMENU() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el identificador de la `CMenu` objeto; de lo contrario, devuelve NULL.

### <a name="remarks"></a>Comentarios

Puede usar el identificador para llamar directamente a las API de Windows.

##  <a name="operator_neq"></a>  CMenu::operator! =

Determina si dos menús lógicamente no son iguales.

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>Parámetros

*menu*<br/>
Un `CMenu` objeto para la comparación.

### <a name="remarks"></a>Comentarios

Comprueba si un objeto de menú en el lado izquierdo no es igual a un objeto de menú en el lado derecho.

##  <a name="operator_eq_eq"></a>  CMenu::operator ==

Determina si dos menús son lógicamente iguales.

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>Parámetros

*menu*<br/>
Un `CMenu` objeto para la comparación.

### <a name="remarks"></a>Comentarios

Comprueba si un objeto de menú en el lado izquierdo es igual a (de acuerdo con el valor HMENU) a un objeto de menú en el lado derecho.

##  <a name="removemenu"></a>  CMenu::RemoveMenu

Elimina un elemento de menú con un menú emergente asociado en el menú.

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

*nPosition*<br/>
Especifica el elemento de menú que se va a quitar. El *nFlags* parámetro puede usarse para interpretar *Nposición* de las maneras siguientes:

|nFlags|Interpretación de Nposición|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.|

*nFlags*<br/>
Especifica cómo *Nposición* se interpreta.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Destruye el identificador de un menú emergente, por lo que se puede reutilizar el menú. Antes de llamar a esta función, la aplicación puede llamar a la `GetSubMenu` función miembro para recuperar el elemento emergente `CMenu` objeto para su reutilización.

Cada vez que un menú que reside en una ventana se cambia (sean o no se muestra la ventana), la aplicación debe llamar a `CWnd::DrawMenuBar`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

##  <a name="setdefaultitem"></a>  CMenu::SetDefaultItem

Establece el elemento de menú predeterminado para el menú especificado.

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parámetros

*uItem*<br/>
Identificador o la posición del nuevo elemento de menú predeterminado o - 1 para ningún elemento de forma predeterminada. El significado de este parámetro depende del valor de *fByPos*.

*fByPos*<br/>
Valor que especifica el significado de *uItem*. Si este parámetro es FALSE, *uItem* es un identificador de elemento de menú. En caso contrario, es una posición de elemento de menú.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero. Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, use la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360), tal y como se describe en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento de la función de Win32 [SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem), tal y como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

##  <a name="setmenucontexthelpid"></a>  CMenu::SetMenuContextHelpId

Asocia un identificador de ayuda contextual con `CMenu`.

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>Parámetros

*dwContextHelpId*<br/>
Identificador de ayuda contextual para asociar `CMenu`.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; en caso contrario, 0

### <a name="remarks"></a>Comentarios

Todos los elementos en el menú comparten este identificador, no es posible adjuntar un identificador de contexto de ayuda a los elementos de menú individuales.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

##  <a name="setmenuinfo"></a>  CMenu::SetMenuInfo

Establece la información de un menú.

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>Parámetros

*lpcmi*<br/>
Un puntero a un [MENUINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuinfo) estructura que contiene información para el menú.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero; en caso contrario, el valor devuelto es cero.

### <a name="remarks"></a>Comentarios

Llame a esta función para establecer la información específica acerca del menú.

##  <a name="setmenuitembitmaps"></a>  CMenu::SetMenuItemBitmaps

Los mapas de bits especificado se asocia con un elemento de menú.

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>Parámetros

*nPosition*<br/>
Especifica el elemento de menú que se puede cambiar. El *nFlags* parámetro puede usarse para interpretar *Nposición* de las maneras siguientes:

|nFlags|Interpretación de Nposición|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.|

*nFlags*<br/>
Especifica cómo *Nposición* se interpreta.

*pBmpUnchecked*<br/>
Especifica el mapa de bits que se usará para los elementos de menú que no se comprueban.

*pBmpChecked*<br/>
Especifica el mapa de bits que se usará para los elementos de menú que se comprueban.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Si el elemento de menú está activado o desactivado, Windows muestra el mapa de bits adecuado al lado del elemento de menú.

Si bien *pBmpUnchecked* o *pBmpChecked* es NULL, Windows muestra nada al lado del elemento de menú para el atributo correspondiente. Si ambos parámetros son NULL, Windows utiliza la marca de verificación de forma predeterminada, cuando el elemento está activado y quita la marca de verificación cuando el elemento está desactivado.

Cuando se destruye el menú, no se destruyen estos mapas de bits; la aplicación debe destruirlos.

El Windows `GetMenuCheckMarkDimensions` función recupera las dimensiones de la marca de verificación predeterminado usado para los elementos de menú. La aplicación usa estos valores para determinar el tamaño adecuado para los mapas de bits que se suministra con esta función. Obtener el tamaño, crear los mapas de bits y, después, configurarlos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

##  <a name="setmenuiteminfo"></a>  CMenu::SetMenuItemInfo

Cambia la información sobre un elemento de menú.

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parámetros

*uItem*<br/>
Consulte la descripción de *uItem* en [SetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-setmenuiteminfoa) en el SDK de Windows.

*lpMenuItemInfo*<br/>
Consulte la descripción de *lpmii* en `SetMenuItemInfo` en el SDK de Windows.

*fByPos*<br/>
Consulte la descripción de *fByPosition* en `SetMenuItemInfo` en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Esta función contiene [SetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-setmenuiteminfoa), que se describen en el SDK de Windows.

##  <a name="trackpopupmenu"></a>  CMenu::TrackPopupMenu

Muestra un menú emergente flotante en la ubicación especificada y realiza el seguimiento de la selección de elementos en el menú emergente.

```
BOOL TrackPopupMenu(
    UINT nFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPCRECT lpRect = 0);
```

### <a name="parameters"></a>Parámetros

*nFlags*<br/>
Especifica los marcadores de posición de la pantalla y la posición del mouse. Consulte [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) para obtener una lista de los indicadores disponibles.

*x*<br/>
Especifica la posición horizontal, en coordenadas de pantalla del menú emergente. Dependiendo del valor de la *nFlags* parámetro, el menú puede ser alineado a la izquierda, alineado a la derecha o centrada en relación con esta posición.

*y*<br/>
Especifica la posición vertical, en coordenadas de pantalla de la parte superior del menú en la pantalla.

*pWnd*<br/>
Identifica la ventana que posee el menú emergente. Este parámetro no puede ser NULL, incluso si se especifica la marca TPM_NONOTIFY. Esta ventana recibe todos los mensajes WM_COMMAND en el menú. En las versiones 3.1 y posteriores de Windows, la ventana no recibe mensajes WM_COMMAND hasta `TrackPopupMenu` devuelve. En Windows 3.0, la ventana recibe mensajes WM_COMMAND antes `TrackPopupMenu` devuelve.

*lpRect*<br/>
ignorado.

### <a name="return-value"></a>Valor devuelto

Este método devuelve el resultado de llamar a [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Un menú emergente flotante puede aparecer en cualquier lugar en la pantalla.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

##  <a name="trackpopupmenuex"></a>  CMenu::TrackPopupMenuEx

Muestra un menú emergente flotante en la ubicación especificada y realiza el seguimiento de la selección de elementos en el menú emergente.

```
BOOL TrackPopupMenuEx(
    UINT fuFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPTPMPARAMS lptpm);
```

### <a name="parameters"></a>Parámetros

*fuFlags*<br/>
Especifica diversas funciones para el menú extendido. Para obtener una lista de todos los valores y su significado, consulte [TrackPopupMenuEx](/windows/desktop/api/winuser/nf-winuser-trackpopupmenuex).

*x*<br/>
Especifica la posición horizontal, en coordenadas de pantalla del menú emergente.

*y*<br/>
Especifica la posición vertical, en coordenadas de pantalla de la parte superior del menú en la pantalla.

*pWnd*<br/>
Un puntero a la ventana propietaria del menú emergente y recibir los mensajes en el menú creado. Esta ventana puede ser cualquier ventana de la aplicación actual pero no puede ser NULL. Si especifica TPM_NONOTIFY en el *fuFlags* parámetro, la función no envía ningún mensaje para *conquistado*. La función debe devolver para la ventana apuntada *conquistado* para recibir el mensaje WM_COMMAND.

*lptpm*<br/>
Puntero a un [TPMPARAMS](/windows/desktop/api/winuser/ns-winuser-tagtpmparams) no debe superponerse a estructura que especifica un área de la pantalla del menú. Este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si especifica TPM_RETURNCMD en el *fuFlags* parámetro, el valor devuelto es el identificador del elemento de menú del elemento que el usuario seleccionado. Si el usuario cancela el menú sin realizar una selección, o si se produce un error, el valor devuelto es 0.

Si no especifica TPM_RETURNCMD en el *fuFlags* parámetro, el valor devuelto es distinto de cero si la función se realiza correctamente y 0 si se produce un error. Para obtener información de error extendida, llame a [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Comentarios

Un menú emergente flotante puede aparecer en cualquier lugar en la pantalla. Para obtener más información sobre cómo controlar errores al crear el menú emergente, consulte [TrackPopupMenuEx](/windows/desktop/api/winuser/nf-winuser-trackpopupmenuex).

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CTRLTEST](../../visual-cpp-samples.md)<br/>
[Ejemplo de MFC DYNAMENU](../../visual-cpp-samples.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)
