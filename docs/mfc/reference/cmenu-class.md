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
ms.openlocfilehash: 1cd7be72dc6c9a38fae4f5ccc1a15c184a2d4466
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855642"
---
# <a name="cmenu-class"></a>CMenu (clase)

Una encapsulación de `HMENU`de Windows.

## <a name="syntax"></a>Sintaxis

```
class CMenu : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMenu:: CMenu](#cmenu)|Construye un objeto `CMenu`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|Anexa un nuevo elemento al final de este menú.|
|[CMenu:: Attach](#attach)|Asocia un identificador de menú de Windows a un objeto `CMenu`.|
|[CMenu:: CheckMenuItem](#checkmenuitem)|Coloca una marca de verificación junto a o quita una marca de verificación de un elemento de menú del menú emergente.|
|[CMenu:: CheckMenuRadioItem](#checkmenuradioitem)|Coloca un botón de radio junto a un elemento de menú y quita el botón de radio de todos los demás elementos de menú del grupo.|
|[CMenu:: CreateMenu](#createmenu)|Crea un menú vacío y lo adjunta a un objeto `CMenu`.|
|[CMenu:: CreatePopupMenu](#createpopupmenu)|Crea un menú emergente vacío y lo adjunta a un objeto `CMenu`.|
|[CMenu::D eleteMenu](#deletemenu)|Elimina un elemento especificado del menú. Si el elemento de menú tiene un menú emergente asociado, destruye el identificador en el menú emergente y libera la memoria que usa.|
|[CMenu::D eleteTempMap](#deletetempmap)|Elimina los objetos `CMenu` temporales creados por la función miembro `FromHandle`.|
|[CMenu::D estroyMenu](#destroymenu)|Destruye el menú asociado a un `CMenu` objeto y libera cualquier memoria ocupada por el menú.|
|[CMenu::D Etach](#detach)|Desasocia un identificador de menú de Windows de un objeto `CMenu` y devuelve el identificador.|
|[CMenu::D rawItem](#drawitem)|Lo llama el marco de trabajo cuando cambia un aspecto visual de un menú dibujado por el propietario.|
|[CMenu:: EnableMenuItem](#enablemenuitem)|Habilita, deshabilita o atenúa (atenúa) un elemento de menú.|
|[CMenu:: FromHandle](#fromhandle)|Devuelve un puntero a un objeto `CMenu` dado un identificador de menú de Windows.|
|[CMenu:: GetDefaultItem](#getdefaultitem)|Determina el elemento de menú predeterminado en el menú especificado.|
|[CMenu:: GetMenuContextHelpId](#getmenucontexthelpid)|Recupera el identificador de contexto de ayuda asociado al menú.|
|[CMenu:: GetMenuInfo](#getmenuinfo)|Recupera información en un menú específico.|
|[CMenu:: GetMenuItemCount](#getmenuitemcount)|Determina el número de elementos de un menú emergente o de nivel superior.|
|[CMenu:: GetMenuItemID](#getmenuitemid)|Obtiene el identificador del elemento de menú para un elemento de menú situado en la posición especificada.|
|[CMenu:: GetMenuItemInfo](#getmenuiteminfo)|Recupera información sobre un elemento de menú.|
|[CMenu:: GetMenuState](#getmenustate)|Devuelve el estado del elemento de menú especificado o el número de elementos de un menú emergente.|
|[CMenu:: GetMenuString](#getmenustring)|Recupera la etiqueta del elemento de menú especificado.|
|[CMenu:: GetSafeHmenu](#getsafehmenu)|Devuelve el `m_hMenu` encapsulado por este objeto `CMenu`.|
|[CMenu:: GetSubMenu](#getsubmenu)|Recupera un puntero a un menú emergente.|
|[CMenu::InsertMenu](#insertmenu)|Inserta un nuevo elemento de menú en la posición especificada y mueve otros elementos hacia abajo en el menú.|
|[CMenu:: InsertMenuItem](#insertmenuitem)|Inserta un nuevo elemento de menú en la posición especificada de un menú.|
|[CMenu:: LoadMenu](#loadmenu)|Carga un recurso de menú desde el archivo ejecutable y lo adjunta a un objeto `CMenu`.|
|[CMenu:: LoadMenuIndirect](#loadmenuindirect)|Carga un menú de una plantilla de menú en la memoria y lo adjunta a un objeto `CMenu`.|
|[CMenu:: MeasureItem](#measureitem)|Lo llama el marco de trabajo para determinar las dimensiones de menú cuando se crea un menú dibujado por el propietario.|
|[CMenu::ModifyMenu](#modifymenu)|Cambia un elemento de menú existente en la posición especificada.|
|[CMenu:: RemoveMenu](#removemenu)|Elimina un elemento de menú con un menú emergente asociado del menú especificado.|
|[CMenu:: SetDefaultItem](#setdefaultitem)|Establece el elemento de menú predeterminado para el menú especificado.|
|[CMenu:: SetMenuContextHelpId](#setmenucontexthelpid)|Establece el identificador de contexto de ayuda que se va a asociar al menú.|
|[CMenu:: SetMenuInfo](#setmenuinfo)|Establece información en un menú específico.|
|[CMenu:: SetMenuItemBitmaps](#setmenuitembitmaps)|Asocia los mapas de bits de la marca de verificación especificados a un elemento de menú.|
|[CMenu:: SetMenuItemInfo](#setmenuiteminfo)|Cambia la información sobre un elemento de menú.|
|[CMenu:: TrackPopupMenu](#trackpopupmenu)|Muestra un menú emergente flotante en la ubicación especificada y realiza un seguimiento de la selección de elementos en el menú emergente.|
|[CMenu:: TrackPopupMenuEx](#trackpopupmenuex)|Muestra un menú emergente flotante en la ubicación especificada y realiza un seguimiento de la selección de elementos en el menú emergente.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMenu:: Operator HMENU](#operator_hmenu)|Recupera el identificador del objeto de menú.|
|[CMenu:: Operator! =](#operator_neq)|Determina si dos objetos de menú no son iguales.|
|[CMenu:: Operator = =](#operator_eq_eq)|Determina si dos objetos de menú son iguales.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMenu:: m_hMenu](#m_hmenu)|Especifica el identificador del menú de Windows asociado al objeto de `CMenu`.|

## <a name="remarks"></a>Observaciones

Proporciona funciones miembro para crear, realizar el seguimiento, actualizar y destruir un menú.

Cree un objeto `CMenu` en el marco de pila como local y, a continuación, llame a las funciones miembro de `CMenu`para manipular el nuevo menú según sea necesario. Después, llame a [CWnd:: SetMenu](../../mfc/reference/cwnd-class.md#setmenu) para establecer el menú en una ventana, seguida inmediatamente por una llamada a la función miembro [Detach](#detach) del objeto `CMenu`. La función miembro `CWnd::SetMenu` establece el menú de la ventana en el nuevo menú, hace que la ventana se vuelva a dibujar para reflejar el cambio de menú y también pasa la propiedad del menú a la ventana. La llamada a `Detach` Desasocia el HMENU del objeto `CMenu`, de modo que cuando la variable local `CMenu` pase fuera del ámbito, el destructor del objeto `CMenu` no intente destruir un menú que ya no posea. El menú en sí se destruye automáticamente cuando se destruye la ventana.

Puede usar la función miembro [LoadMenuIndirect](#loadmenuindirect) para crear un menú a partir de una plantilla en memoria, pero un menú creado a partir de un recurso mediante una llamada a [LoadMenu](#loadmenu) se mantiene más fácilmente y el propio recurso de menú se puede crear y modificar mediante el editor de menús.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="appendmenu"></a>CMenu:: AppendMenu

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
Especifica información sobre el estado del nuevo elemento de menú cuando se agrega al menú. Consta de uno o varios de los valores que se muestran en la sección Comentarios.

*nIDNewItem*<br/>
Especifica el identificador de comando del nuevo elemento de menú o, si *nFlags* está establecido en MF_POPUP, el identificador de menú (`HMENU`) de un menú emergente. El parámetro *nIDNewItem* se omite (no es necesario) si *nFlags* está establecido en MF_SEPARATOR.

*lpszNewItem*<br/>
Especifica el contenido del nuevo elemento de menú. El parámetro *nFlags* se usa para interpretar *lpszNewItem* de la siguiente manera:

|nFlags|Interpretación de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contiene un valor de 32 bits proporcionado por la aplicación que la aplicación puede usar para mantener datos adicionales asociados al elemento de menú. Este valor de 32 bits está disponible para la aplicación cuando procesa WM_MEASUREITEM y WM_DRAWITEM mensajes. El valor se almacena en el `itemData` miembro de la estructura suministrada con esos mensajes.|
|MF_STRING|Contiene un puntero a una cadena terminada en NULL. Esta es la interpretación predeterminada.|
|MF_SEPARATOR|El parámetro *lpszNewItem* se omite (no es necesario).|

*pBmp*<br/>
Señala a un objeto `CBitmap` que se utilizará como elemento de menú.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La aplicación puede especificar el estado del elemento de menú estableciendo valores en *nFlags*. Cuando *nIDNewItem* especifica un menú emergente, se convierte en parte del menú al que se anexa. Si se destruye el menú, también se destruirá el menú anexado. Un menú anexado se debe Desasociar de un objeto `CMenu` para evitar conflictos. Tenga en cuenta que MF_STRING y MF_OWNERDRAW no son válidos para la versión de mapa de bits de `AppendMenu`.

En la lista siguiente se describen las marcas que se pueden establecer en *nFlags*:

- MF_CHECKED actúa como alternancia con MF_UNCHECKED para colocar la marca de verificación predeterminada junto al elemento. Cuando la aplicación proporciona mapas de bits de marca de verificación (vea la función miembro [SetMenuItemBitmaps](#setmenuitembitmaps) ), se muestra el mapa de bits "marca de verificación en".

- MF_UNCHECKED actúa como alternancia con MF_CHECKED para quitar una marca de verificación junto al elemento. Cuando la aplicación proporciona mapas de bits de marca de verificación (vea la función miembro `SetMenuItemBitmaps`), se muestra el mapa de bits "marca de verificación desactivada".

- MF_DISABLED deshabilita el elemento de menú para que no se pueda seleccionar, pero no lo atenúa.

- MF_ENABLED habilita el elemento de menú para que se pueda seleccionar y restaurar desde su estado atenuado.

- MF_GRAYED deshabilita el elemento de menú para que no se pueda seleccionar y atenúa.

- MF_MENUBARBREAK coloca el elemento en una nueva línea en los menús estáticos o en una nueva columna en los menús emergentes. La nueva columna del menú emergente se separará de la columna antigua mediante una línea vertical.

- MF_MENUBREAK coloca el elemento en una nueva línea en los menús estáticos o en una nueva columna en los menús emergentes. No se coloca una línea divisoria entre las columnas.

- MF_OWNERDRAW especifica que el elemento es un elemento dibujado por el propietario. Cuando se muestra el menú por primera vez, la ventana que posee el menú recibe un WM_MEASUREITEM mensaje, que recupera el alto y el ancho del elemento de menú. El mensaje WM_DRAWITEM es el que se envía cuando el propietario debe actualizar la apariencia visual del elemento de menú. Esta opción no es válida para un elemento de menú de nivel superior.

- MF_POPUP especifica que el elemento de menú tiene un menú emergente asociado a él. El parámetro ID especifica un identificador para un menú emergente que se va a asociar al elemento. Esta opción se usa para agregar un menú emergente de nivel superior o un menú emergente jerárquico a un elemento de menú emergente.

- MF_SEPARATOR dibuja una línea de división horizontal. Solo se puede usar en un menú emergente. Esta línea no puede estar atenuada, deshabilitada o resaltada. Otros parámetros se omiten.

- MF_STRING especifica que el elemento de menú es una cadena de caracteres.

En cada uno de los grupos siguientes se enumeran las marcas que se excluyen mutuamente y no se pueden usar juntas:

- MF_DISABLED, MF_ENABLED y MF_GRAYED

- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR y la versión de mapa de bits

- MF_MENUBARBREAK y MF_MENUBREAK

- MF_CHECKED y MF_UNCHECKED

Siempre que se cambie un menú que resida en una ventana (tanto si se muestra como si no), la aplicación debe llamar a [CWnd::D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: CreateMenu](#createmenu).

##  <a name="attach"></a>CMenu:: Attach

Asocia un menú de Windows existente a un objeto `CMenu`.

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>Parámetros

*hMenu*<br/>
Especifica un identificador para un menú de Windows.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

No se debe llamar a esta función si ya hay un menú asociado al objeto `CMenu`. El identificador de menú se almacena en el miembro de datos `m_hMenu`.

Si el menú que desea manipular ya está asociado a una ventana, puede usar la función [CWnd:: GetMenu](../../mfc/reference/cwnd-class.md#getmenu) para obtener un identificador para el menú.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="checkmenuitem"></a>CMenu:: CheckMenuItem

Agrega o quita marcas de verificación de los elementos de menú del menú emergente.

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>Parámetros

*nIDCheckItem*<br/>
Especifica el elemento de menú que se va a comprobar, según lo determinado por *nCompruebe*.

*nCompruebe*<br/>
Especifica cómo comprobar el elemento de menú y cómo determinar la posición del elemento en el menú. El parámetro *nCompruebe* puede ser una combinación de MF_CHECKED o MF_UNCHECKED con marcas de MF_BYPOSITION o MF_BYCOMMAND. Estas marcas se pueden combinar mediante el operador OR bit a bit. Tienen los significados siguientes:

- MF_BYCOMMAND especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado.

- MF_BYPOSITION especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.

- MF_CHECKED actúa como alternancia con MF_UNCHECKED para colocar la marca de verificación predeterminada junto al elemento.

- MF_UNCHECKED actúa como alternancia con MF_CHECKED para quitar una marca de verificación junto al elemento.

### <a name="return-value"></a>Valor devuelto

Estado anterior del elemento: MF_CHECKED o MF_UNCHECKED, o 0xFFFFFFFF si el elemento de menú no existía.

### <a name="remarks"></a>Observaciones

El parámetro *nIDCheckItem* especifica el elemento que se va a modificar.

El parámetro *nIDCheckItem* puede identificar un elemento de menú emergente y un elemento de menú. No se requieren pasos especiales para comprobar un elemento de menú emergente. No se pueden comprobar los elementos de menú de nivel superior. Un elemento de menú emergente debe estar activado por posición, ya que no tiene un identificador de elemento de menú asociado a él.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: GetMenuState](#getmenustate).

##  <a name="checkmenuradioitem"></a>CMenu:: CheckMenuRadioItem

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
Especifica (como un identificador o un desplazamiento, según el valor de *nFlags*) el primer elemento de menú del grupo de botones de radio.

*nIDLast*<br/>
Especifica (como un identificador o un desplazamiento, según el valor de *nFlags*) el último elemento de menú del grupo de botones de radio.

*nIDItem*<br/>
Especifica (como un identificador o un desplazamiento, según el valor de *nFlags*) el elemento del grupo que se comprobará con un botón de radio.

*nFlags*<br/>
Especifica la interpretación de *nIDFirst*, *nIDLast*y *nIDItem* de la siguiente manera:

|nFlags|Interpretación|
|------------|--------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece ni MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.|

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; de lo contrario, 0

### <a name="remarks"></a>Observaciones

Al mismo tiempo, la función anula la selección de todos los demás elementos de menú del grupo asociado y borra el indicador de tipo de elemento de radio de esos elementos. El elemento activado se muestra mediante un mapa de bits de botón de radio (o de viñeta) en lugar de un mapa de bits de marca de verificación.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).

##  <a name="cmenu"></a>CMenu:: CMenu

Crea un menú vacío y lo adjunta a un objeto `CMenu`.

```
CMenu();
```

### <a name="remarks"></a>Observaciones

El menú no se crea hasta que se llama a una de las funciones miembro Create o Load de `CMenu:`

- [CreateMenu](#createmenu)

- [CreatePopupMenu](#createpopupmenu)

- [LoadMenu](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [Adjuntar](#attach)

##  <a name="createmenu"></a>CMenu:: CreateMenu

Crea un menú y lo adjunta al objeto `CMenu`.

```
BOOL CreateMenu();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el menú se creó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

El menú está inicialmente vacío. Los elementos de menú se pueden agregar mediante la función miembro `AppendMenu` o `InsertMenu`.

Si el menú está asignado a una ventana, se destruye automáticamente cuando se destruye la ventana.

Antes de salir, una aplicación debe liberar los recursos del sistema asociados a un menú si el menú no está asignado a una ventana. Una aplicación libera un menú mediante una llamada a la función miembro [DestroyMenu](#destroymenu) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

##  <a name="createpopupmenu"></a>CMenu:: CreatePopupMenu

Crea un menú emergente y lo adjunta al objeto `CMenu`.

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el menú emergente se ha creado correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

El menú está inicialmente vacío. Los elementos de menú se pueden agregar mediante la función miembro `AppendMenu` o `InsertMenu`. La aplicación puede Agregar el menú emergente a un menú o menú emergente existente. La función miembro `TrackPopupMenu` se puede usar para mostrar este menú como menú emergente flotante y para realizar un seguimiento de las selecciones en el menú emergente.

Si el menú está asignado a una ventana, se destruye automáticamente cuando se destruye la ventana. Si el menú se agrega a un menú existente, se destruye automáticamente cuando se destruye el menú.

Antes de salir, una aplicación debe liberar los recursos del sistema asociados a un menú emergente si el menú no está asignado a una ventana. Una aplicación libera un menú mediante una llamada a la función miembro [DestroyMenu](#destroymenu) .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: CreateMenu](#createmenu).

##  <a name="deletemenu"></a>CMenu::D eleteMenu

Elimina un elemento del menú.

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

*Nposición a*<br/>
Especifica el elemento de menú que se va a eliminar, según lo determinado por *nFlags*.

*nFlags*<br/>
Se usa para interpretar *nposición a* de la siguiente manera:

|nFlags|Interpretación de Nposición a|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece ni MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.|

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Si el elemento de menú tiene un menú emergente asociado, `DeleteMenu` destruye el identificador en el menú emergente y libera la memoria usada por el menú emergente.

Siempre que se cambie un menú que resida en una ventana (tanto si se muestra como si no), la aplicación debe llamar a [CWnd::D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd:: GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="deletetempmap"></a>CMenu::D eleteTempMap

Llamado automáticamente por el controlador de tiempo de inactividad de `CWinApp`, elimina todos los objetos de `CMenu` temporales creados por la función miembro [FromHandle](#fromhandle) .

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Observaciones

`DeleteTempMap` Desasocia el objeto de menú de Windows asociado a un objeto de `CMenu` temporal antes de eliminar el objeto `CMenu`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

##  <a name="destroymenu"></a>CMenu::D estroyMenu

Destruye el menú y los recursos de Windows que se usaron.

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se destruye el menú; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

El menú se desasocia del objeto `CMenu` antes de que se destruya. La función `DestroyMenu` de Windows se llama automáticamente en el destructor `CMenu`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: CreateMenu](#createmenu).

##  <a name="detach"></a>CMenu::D Etach

Desasocia un menú de Windows de un objeto `CMenu` y devuelve el identificador.

```
HMENU Detach();
```

### <a name="return-value"></a>Valor devuelto

Identificador de tipo HMENU, en un menú de Windows, si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

El miembro de datos `m_hMenu` se establece en NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="drawitem"></a>CMenu::D rawItem

Lo llama el marco de trabajo cuando cambia un aspecto visual de un menú dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero a una estructura [drawitemstruct (](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que contiene información sobre el tipo de dibujo necesario.

### <a name="remarks"></a>Observaciones

El miembro `itemAction` de la estructura `DRAWITEMSTRUCT` define la acción de dibujo que se va a realizar. Invalide esta función miembro para implementar el dibujo de un objeto de `CMenu` dibujado por el propietario. La aplicación debe restaurar todos los objetos de la interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de presentación proporcionado en *lpDrawItemStruct* antes de la finalización de esta función miembro.

Vea [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) para obtener una descripción de la estructura `DRAWITEMSTRUCT`.

### <a name="example"></a>Ejemplo

El código siguiente procede del ejemplo [CTRLTEST](../../overview/visual-cpp-samples.md) de MFC:

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

##  <a name="enablemenuitem"></a>CMenu:: EnableMenuItem

Habilita, deshabilita o atenúa un elemento de menú.

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>Parámetros

*nIDEnableItem*<br/>
Especifica el elemento de menú que se va a habilitar, según lo determinado por *nEnable*. Este parámetro puede especificar elementos de menú emergente y elementos de menú estándar.

*nEnable*<br/>
Especifica la acción que se debe realizar. Puede ser una combinación de MF_DISABLED, MF_ENABLED o MF_GRAYED, con MF_BYCOMMAND o MF_BYPOSITION. Estos valores se pueden combinar mediante el operador OR bit a bit. Estos valores tienen los significados siguientes:

- MF_BYCOMMAND especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado.

- MF_BYPOSITION especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.

- MF_DISABLED deshabilita el elemento de menú para que no se pueda seleccionar, pero no lo atenúa.

- MF_ENABLED habilita el elemento de menú para que se pueda seleccionar y restaurar desde su estado atenuado.

- MF_GRAYED deshabilita el elemento de menú para que no se pueda seleccionar y atenúa.

### <a name="return-value"></a>Valor devuelto

Estado anterior (MF_DISABLED, MF_ENABLED o MF_GRAYED) o-1 si no es válido.

### <a name="remarks"></a>Observaciones

Las funciones miembro [CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu)y [LoadMenuIndirect](#loadmenuindirect) también pueden establecer el estado (habilitado, deshabilitado o atenuado) de un elemento de menú.

El uso del valor MF_BYPOSITION requiere que una aplicación use el `CMenu`correcto. Si se usa el `CMenu` de la barra de menús, se verá afectado un elemento de menú de nivel superior (un elemento en la barra de menús). Para establecer el estado de un elemento en un menú emergente emergente o anidado por posición, una aplicación debe especificar el `CMenu` del menú emergente...

Cuando una aplicación especifica la marca MF_BYCOMMAND, Windows comprueba todos los elementos de menú emergentes subordinados a la `CMenu`; por lo tanto, a menos que estén presentes elementos de menú duplicados, el uso de la `CMenu` de la barra de menús es suficiente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

##  <a name="fromhandle"></a>CMenu:: FromHandle

Devuelve un puntero a un objeto `CMenu` dado un identificador de Windows a un menú.

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>Parámetros

*hMenu*<br/>
Identificador de Windows de un menú.

### <a name="return-value"></a>Valor devuelto

Puntero a un `CMenu` que puede ser temporal o permanente.

### <a name="remarks"></a>Observaciones

Si un objeto de `CMenu` no está ya asociado al objeto de menú de Windows, se crea y se adjunta un objeto de `CMenu` temporal.

Este objeto de `CMenu` temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminarán todos los objetos temporales.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: CreateMenu](#createmenu).

##  <a name="getdefaultitem"></a>CMenu:: GetDefaultItem

Determina el elemento de menú predeterminado en el menú especificado.

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parámetros

*gmdiFlags*<br/>
Valor que especifica cómo la función busca elementos de menú. Este parámetro puede ser ninguno, uno o una combinación de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|Especifica que, si el elemento predeterminado es uno que abre un submenú, la función busca en el submenú correspondiente de forma recursiva. Si el submenú no tiene ningún elemento predeterminado, el valor devuelto identifica el elemento que abre el submenú.<br /><br /> De forma predeterminada, la función devuelve el primer elemento predeterminado del menú especificado, independientemente de si se trata de un elemento que abre un submenú.|
|GMDI_USEDISABLED|Especifica que la función va a devolver un elemento predeterminado, aunque esté deshabilitado.<br /><br /> De forma predeterminada, la función omite los elementos deshabilitados o atenuados.|

*fByPos*<br/>
Valor que especifica si se debe recuperar el identificador del elemento de menú o su posición. Si este parámetro es FALSE, se devuelve el identificador. De lo contrario, se devuelve la posición.

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es el identificador o la posición del elemento de menú. Si se produce un error en la función, el valor devuelto es-1.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la función [GetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem)de Win32, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: InsertMenu](#insertmenu).

##  <a name="getmenucontexthelpid"></a>CMenu:: GetMenuContextHelpId

Recupera el identificador de ayuda contextual asociado a `CMenu`.

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador de ayuda contextual asociado actualmente a `CMenu` si tiene uno; en caso contrario, cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: InsertMenu](#insertmenu).

##  <a name="getmenuinfo"></a>CMenu:: GetMenuInfo

Recupera información de un menú.

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>Parámetros

*lpcmi*<br/>
Puntero a una estructura [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) que contiene información para el menú.

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero; de lo contrario, el valor devuelto es cero.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar información sobre el menú.

##  <a name="getmenuitemcount"></a>CMenu:: GetMenuItemCount

Determina el número de elementos de un menú emergente o de nivel superior.

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos en el menú si la función se realiza correctamente; de lo contrario,-1.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd:: GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="getmenuitemid"></a>CMenu:: GetMenuItemID

Obtiene el identificador del elemento de menú para un elemento de menú situado en la posición definida por *NPOs*.

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Especifica la posición (basada en cero) del elemento de menú cuyo identificador se recupera.

### <a name="return-value"></a>Valor devuelto

El identificador de elemento para el elemento especificado en un menú emergente si la función se realiza correctamente. Si el elemento especificado es un menú emergente (en oposición a un elemento del menú emergente), el valor devuelto es-1. Si *NPOs* corresponde a un elemento de menú separador, el valor devuelto es 0.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: InsertMenu](#insertmenu).

##  <a name="getmenuiteminfo"></a>CMenu:: GetMenuItemInfo

Recupera información sobre un elemento de menú.

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parámetros

*uItem*<br/>
Identificador o posición del elemento de menú del que se va a obtener información. El significado de este parámetro depende del valor de `ByPos`.

*lpMenuItemInfo*<br/>
Un puntero a un [MENUITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow), como se describe en el Windows SDK, que contiene información sobre el menú.

*fByPos*<br/>
Valor que especifica el significado de `nIDItem`. De forma predeterminada, `ByPos` es FALSE, lo que indica que uItem es un identificador de elemento de menú. Si `ByPos` no está establecido en FALSE, indica una posición de elemento de menú.

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero. Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, utilice la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)de Win32, tal como se describe en el Windows SDK.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la función [GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow)de Win32, como se describe en el Windows SDK. Tenga en cuenta que en la implementación de MFC de `GetMenuItemInfo`, no se utiliza un identificador para un menú.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

##  <a name="getmenustate"></a>CMenu:: GetMenuState

Devuelve el estado del elemento de menú especificado o el número de elementos de un menú emergente.

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Especifica el identificador del elemento de menú, determinado por *nFlags*.

*nFlags*<br/>
Especifica la naturaleza de *nID*. Puede ser uno de los siguientes valores:

- MF_BYCOMMAND especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado.

- MF_BYPOSITION especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.

### <a name="return-value"></a>Valor devuelto

El valor 0xFFFFFFFF si el elemento especificado no existe. Si *nId* identifica un menú emergente, el byte de orden superior contiene el número de elementos en el menú emergente y el byte de orden inferior contiene las marcas de menú asociadas al menú emergente. De lo contrario, el valor devuelto es una máscara (booleano o) de los valores de la lista siguiente (esta máscara describe el estado del elemento de menú que se identifica mediante *nId* ):

- MF_CHECKED actúa como alternancia con MF_UNCHECKED para colocar la marca de verificación predeterminada junto al elemento. Cuando la aplicación proporciona los mapas de bits de la marca de verificación (vea la función miembro `SetMenuItemBitmaps`), se muestra el mapa de bits "marca de verificación en".

- MF_DISABLED deshabilita el elemento de menú para que no se pueda seleccionar, pero no lo atenúa.

- MF_ENABLED habilita el elemento de menú para que se pueda seleccionar y restaurar desde su estado atenuado. Tenga en cuenta que el valor de esta constante es 0; una aplicación no debe probar con 0 si se produce un error al utilizar este valor.

- MF_GRAYED deshabilita el elemento de menú para que no se pueda seleccionar y atenúa.

- MF_MENUBARBREAK coloca el elemento en una nueva línea en los menús estáticos o en una nueva columna en los menús emergentes. La nueva columna del menú emergente se separará de la columna antigua mediante una línea vertical.

- MF_MENUBREAK coloca el elemento en una nueva línea en los menús estáticos o en una nueva columna en los menús emergentes. No se coloca una línea divisoria entre las columnas.

- MF_SEPARATOR dibuja una línea de división horizontal. Solo se puede usar en un menú emergente. Esta línea no puede estar atenuada, deshabilitada o resaltada. Otros parámetros se omiten.

- MF_UNCHECKED actúa como alternancia con MF_CHECKED para quitar una marca de verificación junto al elemento. Cuando la aplicación proporciona mapas de bits de marca de verificación (vea la función miembro `SetMenuItemBitmaps`), se muestra el mapa de bits "marca de verificación desactivada". Tenga en cuenta que el valor de esta constante es 0; una aplicación no debe probar con 0 si se produce un error al utilizar este valor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

##  <a name="getmenustring"></a>CMenu:: GetMenuString

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
Apunta al búfer que va a recibir la etiqueta.

*rString*<br/>
Referencia a un objeto `CString` que va a recibir la cadena de menú copiada.

*nMaxCount*<br/>
Especifica la longitud máxima (en caracteres) de la etiqueta que se va a copiar. Si la etiqueta es mayor que el valor máximo especificado en *nMaxCount*, se truncan los caracteres adicionales.

*nFlags*<br/>
Especifica la interpretación del parámetro *nIDItem* . Puede ser uno de los siguientes valores:

|nFlags|Interpretación de nIDItem|
|------------|-------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece ni MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.|

### <a name="return-value"></a>Valor devuelto

Especifica el número real de caracteres copiados en el búfer, sin incluir el terminador null.

### <a name="remarks"></a>Observaciones

El parámetro *nMaxCount* debe ser uno mayor que el número de caracteres de la etiqueta para alojar el carácter nulo que termina una cadena.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: InsertMenu](#insertmenu).

##  <a name="getsafehmenu"></a>CMenu:: GetSafeHmenu

Devuelve el HMENU encapsulado por este objeto `CMenu` o un puntero`CMenu` nulo.

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: LoadMenu](#loadmenu).

##  <a name="getsubmenu"></a>CMenu:: GetSubMenu

Recupera el objeto de `CMenu` de un menú emergente.

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Especifica la posición del menú emergente incluido en el menú. Los valores de posición comienzan en 0 para el primer elemento de menú. El identificador del menú emergente no se puede usar en esta función.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto de `CMenu` cuyo miembro de `m_hMenu` contiene un identificador para el menú emergente si existe un menú emergente en la posición especificada; de lo contrario, NULL. Si no existe un objeto de `CMenu`, se crea uno temporal. No se debe almacenar el puntero `CMenu` devuelto.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: TrackPopupMenu](#trackpopupmenu).

##  <a name="insertmenu"></a>CMenu:: InsertMenu

Inserta un nuevo elemento de menú en la posición especificada por *nposición a* y mueve otros elementos hacia abajo en el menú.

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

*Nposición a*<br/>
Especifica el elemento de menú antes del que se va a insertar el nuevo elemento de menú. El parámetro *nFlags* se puede usar para interpretar *nposición a* de las siguientes maneras:

|nFlags|Interpretación de Nposición a|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece ni MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0. Si *nposición a* es-1, el nuevo elemento de menú se anexa al final del menú.|

*nFlags*<br/>
Especifica cómo se interpreta *nposición a* y especifica información sobre el estado del nuevo elemento de menú cuando se agrega al menú. Para obtener una lista de las marcas que se pueden establecer, vea la función miembro [AppendMenu](#appendmenu) . Para especificar más de un valor, use el operador OR bit a bit para combinarlos con la marca MF_BYCOMMAND o MF_BYPOSITION.

*nIDNewItem*<br/>
Especifica el identificador de comando del nuevo elemento de menú o, si *nFlags* está establecido en MF_POPUP, el identificador de menú (HMENU) del menú emergente. El parámetro *nIDNewItem* se omite (no es necesario) si *nFlags* está establecido en MF_SEPARATOR.

*lpszNewItem*<br/>
Especifica el contenido del nuevo elemento de menú. *nFlags* se puede usar para interpretar *lpszNewItem* de las maneras siguientes:

|nFlags|Interpretación de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contiene un valor de 32 bits proporcionado por la aplicación que la aplicación puede usar para mantener datos adicionales asociados al elemento de menú. Este valor de 32 bits está disponible para la aplicación en el `itemData` miembro de la estructura proporcionada por los mensajes [WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem) y [WM_DRAWITEM](/windows/win32/Controls/wm-drawitem) . Estos mensajes se envían cuando se muestra o se cambia inicialmente el elemento de menú.|
|MF_STRING|Contiene un puntero largo a una cadena terminada en NULL. Esta es la interpretación predeterminada.|
|MF_SEPARATOR|El parámetro *lpszNewItem* se omite (no es necesario).|

*pBmp*<br/>
Señala a un objeto `CBitmap` que se utilizará como elemento de menú.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La aplicación puede especificar el estado del elemento de menú estableciendo valores en *nFlags*.

Cada vez que se cambia un menú que reside en una ventana (tanto si se muestra como si no), la aplicación debe llamar a `CWnd::DrawMenuBar`.

Cuando *nIDNewItem* especifica un menú emergente, se convierte en parte del menú en el que se inserta. Si se destruye el menú, también se destruirá el menú insertado. Un menú insertado se debe Desasociar de un objeto `CMenu` para evitar conflictos.

Si se maximiza la ventana secundaria de la interfaz de múltiples documentos (MDI) activa y una aplicación inserta un menú emergente en el menú de la aplicación MDI llamando a esta función y especificando la marca de MF_BYPOSITION, el menú se inserta una posición más hacia la izquierda. correctamente. Esto sucede porque el menú control de la ventana secundaria MDI activa se inserta en la primera posición de la barra de menús de la ventana de marco MDI. Para colocar el menú correctamente, la aplicación debe agregar 1 al valor de posición que, de lo contrario, se utilizaría. Una aplicación puede usar el mensaje WM_MDIGETACTIVE para determinar si la ventana secundaria actualmente activa está maximizada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

##  <a name="insertmenuitem"></a>CMenu:: InsertMenuItem

Inserta un nuevo elemento de menú en la posición especificada de un menú.

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parámetros

*uItem*<br/>
Vea la descripción de *uItem* en [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw) en el Windows SDK.

*lpMenuItemInfo*<br/>
Vea la descripción de *lpmii* en `InsertMenuItem` en el Windows SDK.

*fByPos*<br/>
Vea la descripción de *fByPosition* en `InsertMenuItem` en el Windows SDK.

### <a name="remarks"></a>Observaciones

Esta función contiene [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw), que se describe en el Windows SDK.

##  <a name="loadmenu"></a>CMenu:: LoadMenu

Carga un recurso de menú desde el archivo ejecutable de la aplicación y lo adjunta al objeto `CMenu`.

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Apunta a una cadena terminada en null que contiene el nombre del recurso de menú que se va a cargar.

*nIDResource*<br/>
Especifica el identificador de menú del recurso de menú que se va a cargar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el recurso de menú se cargó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Antes de salir, una aplicación debe liberar los recursos del sistema asociados a un menú si el menú no está asignado a una ventana. Una aplicación libera un menú mediante una llamada a la función miembro [DestroyMenu](#destroymenu) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

##  <a name="loadmenuindirect"></a>CMenu:: LoadMenuIndirect

Carga un recurso de una plantilla de menú en la memoria y lo adjunta al objeto `CMenu`.

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>Parámetros

*lpMenuTemplate*<br/>
Apunta a una plantilla de menú (que es una única estructura [MENUITEMTEMPLATEHEADER](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader) y una colección de una o varias estructuras [MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) ). Para obtener más información sobre estas dos estructuras, vea el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el recurso de menú se cargó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Una plantilla de menú es un encabezado seguido de una colección de una o más estructuras [MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) , cada una de las cuales puede contener uno o más elementos de menú y menús emergentes.

El número de versión debe ser 0.

Las marcas de `mtOption` deben incluir MF_END para el último elemento de una lista emergente y para el último elemento de la lista principal. Vea la función miembro `AppendMenu` para otras marcas. El miembro de `mtId` se debe omitir de la estructura MENUITEMTEMPLATE cuando MF_POPUP se especifica en `mtOption`.

El espacio asignado para la estructura MENUITEMTEMPLATE debe ser lo suficientemente grande como para que `mtString` contenga el nombre del elemento de menú como una cadena terminada en NULL.

Antes de salir, una aplicación debe liberar los recursos del sistema asociados a un menú si el menú no está asignado a una ventana. Una aplicación libera un menú mediante una llamada a la función miembro [DestroyMenu](#destroymenu) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

##  <a name="m_hmenu"></a>CMenu:: m_hMenu

Especifica el identificador de HMENU del menú de Windows asociado al objeto de `CMenu`.

```
HMENU m_hMenu;
```

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: LoadMenu](#loadmenu).

##  <a name="measureitem"></a>CMenu:: MeasureItem

Lo llama el marco de trabajo cuando se crea un menú con el estilo de dibujo del propietario.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpMeasureItemStruct*<br/>
Puntero a una estructura de `MEASUREITEMSTRUCT`.

### <a name="remarks"></a>Observaciones

De forma predeterminada, esta función miembro no hace nada. Invalide esta función miembro y rellene la estructura `MEASUREITEMSTRUCT` para informar a las ventanas de las dimensiones del menú.

Vea [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) para obtener una descripción de la estructura `MEASUREITEMSTRUCT`.

### <a name="example"></a>Ejemplo

El código siguiente procede del ejemplo [CTRLTEST](../../overview/visual-cpp-samples.md) de MFC:

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

##  <a name="modifymenu"></a>CMenu:: ModifyMenu

Cambia un elemento de menú existente en la posición especificada por *nposición a*.

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

*Nposición a*<br/>
Especifica el elemento de menú que se va a cambiar. El parámetro *nFlags* se puede usar para interpretar *nposición a* de las siguientes maneras:

|nFlags|Interpretación de Nposición a|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece ni MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.|

*nFlags*<br/>
Especifica cómo se interpreta *nposición a* y proporciona información sobre los cambios que se van a realizar en el elemento de menú. Para obtener una lista de las marcas que se pueden establecer, vea la función miembro [AppendMenu](#appendmenu) .

*nIDNewItem*<br/>
Especifica el identificador de comando del elemento de menú modificado o, si *nFlags* está establecido en MF_POPUP, el identificador de menú (HMENU) de un menú emergente. El parámetro *nIDNewItem* se omite (no es necesario) si *nFlags* está establecido en MF_SEPARATOR.

*lpszNewItem*<br/>
Especifica el contenido del nuevo elemento de menú. El parámetro *nFlags* se puede usar para interpretar *lpszNewItem* de las siguientes maneras:

|nFlags|Interpretación de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contiene un valor de 32 bits proporcionado por la aplicación que la aplicación puede usar para mantener datos adicionales asociados al elemento de menú. Este valor de 32 bits está disponible para la aplicación cuando procesa MF_MEASUREITEM y MF_DRAWITEM.|
|MF_STRING|Contiene un puntero largo a una cadena terminada en null o a un `CString`.|
|MF_SEPARATOR|El parámetro *lpszNewItem* se omite (no es necesario).|

*pBmp*<br/>
Señala a un objeto `CBitmap` que se utilizará como elemento de menú.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La aplicación especifica el nuevo estado del elemento de menú estableciendo valores en *nFlags*. Si esta función reemplaza un menú emergente asociado con el elemento de menú, destruye el menú emergente anterior y libera la memoria usada por el menú emergente de la.

Cuando *nIDNewItem* especifica un menú emergente, se convierte en parte del menú en el que se inserta. Si se destruye el menú, también se destruirá el menú insertado. Un menú insertado se debe Desasociar de un objeto `CMenu` para evitar conflictos.

Cada vez que se cambia un menú que reside en una ventana (tanto si se muestra como si no), la aplicación debe llamar a `CWnd::DrawMenuBar`. Para cambiar los atributos de los elementos de menú existentes, es mucho más rápido usar las funciones miembro `CheckMenuItem` y `EnableMenuItem`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: InsertMenu](#insertmenu).

##  <a name="operator_hmenu"></a>CMenu:: Operator HMENU

Utilice este operador para recuperar el identificador del objeto `CMenu`.

```
operator HMENU() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, el identificador del objeto `CMenu`; de lo contrario, es NULL.

### <a name="remarks"></a>Observaciones

Puede utilizar el identificador para llamar a las API de Windows directamente.

##  <a name="operator_neq"></a>CMenu:: Operator! =

Determina si dos menús no son iguales lógicamente.

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>Parámetros

*MENU*<br/>
Un objeto `CMenu` para la comparación.

### <a name="remarks"></a>Observaciones

Comprueba si un objeto de menú en el lado izquierdo no es igual que un objeto de menú del lado derecho.

##  <a name="operator_eq_eq"></a>CMenu:: Operator = =

Determina si dos menús son lógicamente iguales.

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>Parámetros

*MENU*<br/>
Un objeto `CMenu` para la comparación.

### <a name="remarks"></a>Observaciones

Comprueba si un objeto de menú en el lado izquierdo es igual (en términos del valor de HMENU) a un objeto de menú del lado derecho.

##  <a name="removemenu"></a>CMenu:: RemoveMenu

Elimina un elemento de menú con un menú emergente asociado del menú.

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

*Nposición a*<br/>
Especifica el elemento de menú que se va a quitar. El parámetro *nFlags* se puede usar para interpretar *nposición a* de las siguientes maneras:

|nFlags|Interpretación de Nposición a|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece ni MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.|

*nFlags*<br/>
Especifica cómo se interpreta *nposición a* .

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

No destruye el identificador de un menú emergente, por lo que se puede volver a usar el menú. Antes de llamar a esta función, la aplicación puede llamar a la función miembro `GetSubMenu` para recuperar el objeto de `CMenu` emergente para reutilizarlo.

Cada vez que se cambia un menú que reside en una ventana (tanto si se muestra como si no), la aplicación debe llamar a `CWnd::DrawMenuBar`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: InsertMenu](#insertmenu).

##  <a name="setdefaultitem"></a>CMenu:: SetDefaultItem

Establece el elemento de menú predeterminado para el menú especificado.

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parámetros

*uItem*<br/>
Identificador o posición del nuevo elemento de menú predeterminado o-1 para ningún elemento predeterminado. El significado de este parámetro depende del valor de *fByPos*.

*fByPos*<br/>
Valor que especifica el significado de *uItem*. Si este parámetro es FALSE, *uItem* es un identificador de elemento de menú. De lo contrario, es una posición de elemento de menú.

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero. Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, utilice la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)de Win32, tal como se describe en el Windows SDK.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la función [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)de Win32, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: InsertMenu](#insertmenu).

##  <a name="setmenucontexthelpid"></a>CMenu:: SetMenuContextHelpId

Asocia un identificador de ayuda contextual a `CMenu`.

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>Parámetros

*dwContextHelpId*<br/>
IDENTIFICADOR de ayuda contextual que se va a asociar a `CMenu`.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; de lo contrario, 0

### <a name="remarks"></a>Observaciones

Todos los elementos del menú comparten este identificador; no es posible adjuntar un identificador de contexto de ayuda a los elementos de menú individuales.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu:: InsertMenu](#insertmenu).

##  <a name="setmenuinfo"></a>CMenu:: SetMenuInfo

Establece la información de un menú.

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>Parámetros

*lpcmi*<br/>
Puntero a una estructura [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) que contiene información para el menú.

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero; de lo contrario, el valor devuelto es cero.

### <a name="remarks"></a>Observaciones

Llame a esta función para establecer información específica sobre el menú.

##  <a name="setmenuitembitmaps"></a>CMenu:: SetMenuItemBitmaps

Asocia los mapas de bits especificados a un elemento de menú.

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>Parámetros

*Nposición a*<br/>
Especifica el elemento de menú que se va a cambiar. El parámetro *nFlags* se puede usar para interpretar *nposición a* de las siguientes maneras:

|nFlags|Interpretación de Nposición a|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece ni MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.|

*nFlags*<br/>
Especifica cómo se interpreta *nposición a* .

*pBmpUnchecked*<br/>
Especifica el mapa de bits que se va a usar para los elementos de menú que no están comprobados.

*pBmpChecked*<br/>
Especifica el mapa de bits que se va a usar para los elementos de menú que se comprueban.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Si el elemento de menú está activado o desactivado, Windows muestra el mapa de bits adecuado junto al elemento de menú.

Si *pBmpUnchecked* o *pBmpChecked* es null, Windows no muestra nada junto al elemento de menú para el atributo correspondiente. Si ambos parámetros son NULL, Windows usa la marca de verificación predeterminada cuando el elemento está activado y quita la marca de verificación cuando el elemento está desactivado.

Cuando se destruye el menú, estos mapas de bits no se destruyen; la aplicación debe destruirlos.

La función `GetMenuCheckMarkDimensions` de Windows recupera las dimensiones de la marca de verificación predeterminada utilizada para los elementos de menú. La aplicación utiliza estos valores para determinar el tamaño adecuado para los mapas de bits proporcionados con esta función. Obtenga el tamaño, cree los mapas de bits y, a continuación, establézcalo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

##  <a name="setmenuiteminfo"></a>CMenu:: SetMenuItemInfo

Cambia la información sobre un elemento de menú.

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parámetros

*uItem*<br/>
Vea la descripción de *uItem* en [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow) en el Windows SDK.

*lpMenuItemInfo*<br/>
Vea la descripción de *lpmii* en `SetMenuItemInfo` en el Windows SDK.

*fByPos*<br/>
Vea la descripción de *fByPosition* en `SetMenuItemInfo` en el Windows SDK.

### <a name="remarks"></a>Observaciones

Esta función contiene [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow), que se describe en el Windows SDK.

##  <a name="trackpopupmenu"></a>CMenu:: TrackPopupMenu

Muestra un menú emergente flotante en la ubicación especificada y realiza un seguimiento de la selección de elementos en el menú emergente.

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
Especifica las marcas de posición de la pantalla y del mouse. Consulte [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) para obtener una lista de las marcas disponibles.

*x*<br/>
Especifica la posición horizontal en las coordenadas de pantalla del menú emergente. Dependiendo del valor del parámetro *nFlags* , el menú puede estar alineado a la izquierda, alineado a la derecha o centrado con respecto a esta posición.

*y*<br/>
Especifica la posición vertical en las coordenadas de la pantalla de la parte superior del menú en la pantalla.

*pWnd*<br/>
Identifica la ventana que posee el menú emergente. Este parámetro no puede ser NULL, incluso si se especifica la marca TPM_NONOTIFY. Esta ventana recibe todos los mensajes de WM_COMMAND desde el menú. En las versiones 3,1 y posteriores de Windows, la ventana no recibe mensajes WM_COMMAND hasta que `TrackPopupMenu` devuelve. En Windows 3,0, la ventana recibe mensajes WM_COMMAND antes de que `TrackPopupMenu` devuelva.

*lpRect*<br/>
Se omite.

### <a name="return-value"></a>Valor devuelto

Este método devuelve el resultado de llamar a [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Un menú emergente flotante puede aparecer en cualquier parte de la pantalla.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

##  <a name="trackpopupmenuex"></a>CMenu:: TrackPopupMenuEx

Muestra un menú emergente flotante en la ubicación especificada y realiza un seguimiento de la selección de elementos en el menú emergente.

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
Especifica varias funciones para el menú extendido. Para obtener una lista de todos los valores y su significado, vea [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

*x*<br/>
Especifica la posición horizontal en las coordenadas de pantalla del menú emergente.

*y*<br/>
Especifica la posición vertical en las coordenadas de la pantalla de la parte superior del menú en la pantalla.

*pWnd*<br/>
Un puntero a la ventana que posee el menú emergente y que recibe los mensajes del menú creado. Esta ventana puede ser cualquier ventana de la aplicación actual, pero no puede ser NULL. Si especifica TPM_NONOTIFY en el parámetro *fuFlags* , la función no envía ningún mensaje a *PWND*. La función debe devolver para la ventana a la que señala *PWND* para recibir el mensaje de WM_COMMAND.

*lptpm*<br/>
Puntero a una estructura [TPMPARAMS](/windows/win32/api/winuser/ns-winuser-tpmparams) que especifica un área de la pantalla en la que el menú no debe superponerse. Este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si especifica TPM_RETURNCMD en el parámetro *fuFlags* , el valor devuelto es el identificador del elemento de menú del elemento que el usuario seleccionó. Si el usuario cancela el menú sin efectuar una selección, o si se produce un error, el valor devuelto es 0.

Si no especifica TPM_RETURNCMD en el parámetro *fuFlags* , el valor devuelto es distinto de cero si la función se ejecuta correctamente y 0 si se produce un error. Para obtener información de error extendida, llame a [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Observaciones

Un menú emergente flotante puede aparecer en cualquier parte de la pantalla. Para obtener más información sobre cómo controlar los errores al crear el menú emergente, vea [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)
