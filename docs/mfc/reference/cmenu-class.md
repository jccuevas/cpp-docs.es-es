---
title: Clase CMenu
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
ms.openlocfilehash: 5ec97d8cf039034078f29b38fb6a41d6ff9a5e53
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369979"
---
# <a name="cmenu-class"></a>Clase CMenu

Una encapsulación de `HMENU`de Windows.

## <a name="syntax"></a>Sintaxis

```
class CMenu : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMenu::CMenu](#cmenu)|Construye un objeto `CMenu`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|Anexa un nuevo elemento al final de este menú.|
|[CMenu::Adjuntar](#attach)|Asocia un identificador de `CMenu` menú de Windows a un objeto.|
|[CMenu::CheckMenuItem](#checkmenuitem)|Coloca una marca de verificación junto a o quita una marca de verificación de un elemento de menú en el menú emergente.|
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|Coloca un botón de opción junto a un elemento de menú y elimina el botón de opción de todos los demás elementos de menú del grupo.|
|[CMenu::CreateMenu](#createmenu)|Crea un menú vacío y `CMenu` lo adjunta a un objeto.|
|[CMenu::CreatePopupMenu](#createpopupmenu)|Crea un menú emergente vacío y lo `CMenu` adjunta a un objeto.|
|[CMenu::DeleteMenu](#deletemenu)|Elimina un elemento especificado del menú. Si el elemento de menú tiene un menú emergente asociado, destruye el controlador en el menú emergente y libera la memoria utilizada por él.|
|[CMenu::DeleteTempMap](#deletetempmap)|Elimina los `CMenu` objetos temporales creados por la `FromHandle` función miembro.|
|[CMenu::DestroyMenu](#destroymenu)|Destruye el menú adjunto `CMenu` a un objeto y libera cualquier memoria ocupada por el menú.|
|[CMenu::Detach](#detach)|Separa un identificador de `CMenu` menú de Windows de un objeto y devuelve el identificador.|
|[CMenu::DrawItem](#drawitem)|Llamado por el marco de trabajo cuando cambia un aspecto visual de un menú dibujado por el propietario.|
|[CMenu::EnableMenuItem](#enablemenuitem)|Habilita, deshabilita o atenúa (grises) un elemento de menú.|
|[CMenu::FromHandle](#fromhandle)|Devuelve un puntero `CMenu` a un objeto dado un identificador de menú de Windows.|
|[CMenu::GetDefaultItem](#getdefaultitem)|Determina el elemento de menú predeterminado en el menú especificado.|
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|Recupera el identificador de contexto de ayuda asociado al menú.|
|[CMenu::GetMenuInfo](#getmenuinfo)|Recupera información en un menú específico.|
|[CMenu::GetMenuItemCount](#getmenuitemcount)|Determina el número de elementos de un menú emergente o de nivel superior.|
|[CMenu::GetMenuItemID](#getmenuitemid)|Obtiene el identificador de elemento de menú para un elemento de menú situado en la posición especificada.|
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|Recupera información sobre un elemento de menú.|
|[CMenu::GetMenuState](#getmenustate)|Devuelve el estado del elemento de menú especificado o el número de elementos de un menú emergente.|
|[CMenu::GetMenuString](#getmenustring)|Recupera la etiqueta del elemento de menú especificado.|
|[CMenu::GetSafeHmenu](#getsafehmenu)|Devuelve `m_hMenu` el ajustado `CMenu` por este objeto.|
|[CMenu::GetSubMenu](#getsubmenu)|Recupera un puntero a un menú emergente.|
|[CMenu::InsertMenu](#insertmenu)|Inserta un nuevo elemento de menú en la posición especificada, moviendo otros elementos hacia abajo en el menú.|
|[CMenu::InsertMenuItem](#insertmenuitem)|Inserta un nuevo elemento de menú en la posición especificada en un menú.|
|[CMenu::LoadMenu](#loadmenu)|Carga un recurso de menú desde el `CMenu` archivo ejecutable y lo adjunta a un objeto.|
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|Carga un menú de una plantilla de menú `CMenu` en la memoria y lo adjunta a un objeto.|
|[CMenu::MeasureItem](#measureitem)|Llamado por el marco de trabajo para determinar las dimensiones del menú cuando se crea un menú dibujado por el propietario.|
|[CMenu::ModifyMenu](#modifymenu)|Cambia un elemento de menú existente en la posición especificada.|
|[CMenu::RemoveMenu](#removemenu)|Elimina un elemento de menú con un menú emergente asociado del menú especificado.|
|[CMenu::SetDefaultItem](#setdefaultitem)|Establece el elemento de menú predeterminado para el menú especificado.|
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|Establece el identificador de contexto de ayuda que se asociará al menú.|
|[CMenu::SetMenuInfo](#setmenuinfo)|Establece información en un menú específico.|
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|Asocia los mapas de bits de marca de verificación especificados con un elemento de menú.|
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|Cambia la información sobre un elemento de menú.|
|[CMenu::TrackPopupMenu](#trackpopupmenu)|Muestra un menú emergente flotante en la ubicación especificada y realiza un seguimiento de la selección de elementos en el menú emergente.|
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|Muestra un menú emergente flotante en la ubicación especificada y realiza un seguimiento de la selección de elementos en el menú emergente.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMenu::operador HMENU](#operator_hmenu)|Recupera el identificador del objeto de menú.|
|[CMenu::operador !-](#operator_neq)|Determina si dos objetos de menú no son iguales.|
|[CMenu::operador ?](#operator_eq_eq)|Determina si dos objetos de menú son iguales.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMenu::m_hMenu](#m_hmenu)|Especifica el identificador del menú de `CMenu` Windows asociado al objeto.|

## <a name="remarks"></a>Observaciones

Proporciona funciones miembro para crear, realizar un seguimiento, actualizar y destruir un menú.

Cree `CMenu` un objeto en el marco de `CMenu`pila como un local y, a continuación, llame a las funciones miembro de 's para manipular el nuevo menú según sea necesario. A continuación, llame a [CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu) para establecer el menú `CMenu` en una ventana, seguido inmediatamente por una llamada a la función miembro [Detach](#detach) del objeto. La `CWnd::SetMenu` función miembro establece el menú de la ventana en el nuevo menú, hace que la ventana se vuelva a dibujar para reflejar el cambio de menú y también pasa la propiedad del menú a la ventana. La llamada `Detach` a separar el HMENU del `CMenu` objeto, `CMenu` de modo que cuando `CMenu` la variable local pasa fuera del ámbito, el destructor de objetos no intenta destruir un menú que ya no posee. El menú en sí se destruye automáticamente cuando se destruye la ventana.

Puede usar la función miembro [LoadMenuIndirect](#loadmenuindirect) para crear un menú a partir de una plantilla en memoria, pero un menú creado a partir de un recurso mediante una llamada a [LoadMenu](#loadmenu) se mantiene más fácilmente y el propio recurso de menú se puede crear y modificar mediante el editor de menús.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cmenuappendmenu"></a><a name="appendmenu"></a>CMenu::AppendMenu

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
Especifica información sobre el estado del nuevo elemento de menú cuando se agrega al menú. Consiste en uno o más de los valores enumerados en la sección Comentarios.

*nIDNewItem*<br/>
Especifica el identificador de comando del nuevo elemento de menú o, si `HMENU` *nFlags* está establecido en MF_POPUP, el identificador de menú ( ) de un menú emergente. El *nIDNewItem* parámetro se omite (no es necesario) si *nFlags* se establece en MF_SEPARATOR.

*lpszNewItem*<br/>
Especifica el contenido del nuevo elemento de menú. El *nFlags* parámetro se utiliza para interpretar *lpszNewItem de* la siguiente manera:

|nFlags|Interpretación de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contiene un valor de 32 bits proporcionado por la aplicación que la aplicación puede usar para mantener datos adicionales asociados con el elemento de menú. Este valor de 32 bits está disponible para la aplicación cuando procesa WM_MEASUREITEM y WM_DRAWITEM mensajes. El valor se `itemData` almacena en el miembro de la estructura proporcionada con esos mensajes.|
|MF_STRING|Contiene un puntero a una cadena terminada en null. Esta es la interpretación predeterminada.|
|MF_SEPARATOR|El parámetro *lpszNewItem* se omite (no es necesario).|

*pBmp*<br/>
Apunta a `CBitmap` un objeto que se utilizará como elemento de menú.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La aplicación puede especificar el estado del elemento de menú estableciendo valores en *nFlags*. Cuando *nIDNewItem* especifica un menú emergente, se convierte en parte del menú al que se anexa. Si se destruye ese menú, también se destruirá el menú adjunto. Un menú anexado debe `CMenu` separarse de un objeto para evitar conflictos. Tenga en cuenta que MF_STRING y MF_OWNERDRAW `AppendMenu`no son válidos para la versión de mapa de bits de .

La lista siguiente describe los indicadores que se pueden establecer en *nFlags:*

- MF_CHECKED Actúa como un conmutador con MF_UNCHECKED colocar la marca de verificación predeterminada junto al elemento. Cuando la aplicación proporciona mapas de bits de marca de verificación (consulte el [SetMenuItemBitmaps](#setmenuitembitmaps) función miembro), se muestra el mapa de bits "marca de verificación en".

- MF_UNCHECKED Actúa como un conmutador con MF_CHECKED para quitar una marca de verificación junto al elemento. Cuando la aplicación proporciona mapas de bits `SetMenuItemBitmaps` de marca de verificación (consulte la función miembro), se muestra el mapa de bits "marca de verificación desactivada".

- MF_DISABLED Deshabilita el elemento de menú para que no se pueda seleccionar, pero no lo atenúe.

- MF_ENABLED Habilita el elemento de menú para que se pueda seleccionar y lo restaura desde su estado atenuado.

- MF_GRAYED Deshabilita el elemento de menú para que no se pueda seleccionar y lo atenúe.

- MF_MENUBARBREAK Coloca el elemento en una nueva línea en los menús estáticos o en una nueva columna en los menús emergentes. La nueva columna del menú emergente se separará de la columna antigua por una línea divisoria vertical.

- MF_MENUBREAK Coloca el elemento en una nueva línea en los menús estáticos o en una nueva columna en los menús emergentes. No se coloca ninguna línea divisoria entre las columnas.

- MF_OWNERDRAW Especifica que el elemento es un elemento dibujado por el propietario. Cuando el menú se muestra por primera vez, la ventana que posee el menú recibe un mensaje de WM_MEASUREITEM, que recupera el alto y el ancho del elemento de menú. El mensaje WM_DRAWITEM es el que se envía siempre que el propietario debe actualizar la apariencia visual del elemento de menú. Esta opción no es válida para un elemento de menú de nivel superior.

- MF_POPUP Especifica que el elemento de menú tiene asociado un menú emergente. El parámetro ID especifica un identificador de un menú emergente que se va a asociar al elemento. Esto se utiliza para agregar un menú emergente de nivel superior o un menú emergente jerárquico a un elemento de menú emergente.

- MF_SEPARATOR Dibuja una línea divisoria horizontal. Solo se puede utilizar en un menú emergente. Esta línea no se puede atenuar, deshabilitar ni resaltar. Se omiten otros parámetros.

- MF_STRING Especifica que el elemento de menú es una cadena de caracteres.

Cada uno de los siguientes grupos enumera los indicadores que se excluyen mutuamente y no se pueden utilizar juntos:

- MF_DISABLED, MF_ENABLED y MF_GRAYED

- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR y la versión de mapa de bits

- MF_MENUBARBREAK y MF_MENUBREAK

- MF_CHECKED y MF_UNCHECKED

Cada vez que se cambia un menú que reside en una ventana (se muestra o no la ventana), la aplicación debe llamar a [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::CreateMenu](#createmenu).

## <a name="cmenuattach"></a><a name="attach"></a>CMenu::Adjuntar

Asocia un menú de `CMenu` Windows existente a un objeto.

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>Parámetros

*hMenú*<br/>
Especifica un identificador de un menú de Windows.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

No se debe llamar a esta función `CMenu` si ya hay un menú asociado al objeto. El identificador de menú `m_hMenu` se almacena en el miembro de datos.

Si el menú que desea manipular ya está asociado a una ventana, puede usar la función [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu) para obtener un identificador del menú.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenucheckmenuitem"></a><a name="checkmenuitem"></a>CMenu::CheckMenuItem

Agrega marcas de verificación o elimina marcas de verificación de los elementos de menú del menú emergente.

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>Parámetros

*nIDCheckItem*<br/>
Especifica el elemento de menú que se va a comprobar, según lo determinado por *nCheck*.

*nCheck*<br/>
Especifica cómo comprobar el elemento de menú y cómo determinar la posición del elemento en el menú. El parámetro *nCheck* puede ser una combinación de MF_CHECKED o MF_UNCHECKED con MF_BYPOSITION o MF_BYCOMMAND marcas. Estos indicadores se pueden combinar mediante el operador OR bit a bit. Tienen los siguientes significados:

- MF_BYCOMMAND Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado.

- MF_BYPOSITION Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.

- MF_CHECKED Actúa como un conmutador con MF_UNCHECKED colocar la marca de verificación predeterminada junto al elemento.

- MF_UNCHECKED Actúa como un conmutador con MF_CHECKED para quitar una marca de verificación junto al elemento.

### <a name="return-value"></a>Valor devuelto

El estado anterior del elemento: MF_CHECKED o MF_UNCHECKED, o 0xFFFFFFFF si el elemento de menú no existía.

### <a name="remarks"></a>Observaciones

El *nIDCheckItem* parámetro especifica el elemento que se va a modificar.

El *nIDCheckItem* parámetro puede identificar un elemento de menú emergente, así como un elemento de menú. No se requieren pasos especiales para comprobar un elemento de menú emergente. Los elementos de menú de nivel superior no se pueden comprobar. Un elemento de menú emergente debe comprobarse por posición, ya que no tiene asociado un identificador de elemento de menú.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::GetMenuState](#getmenustate).

## <a name="cmenucheckmenuradioitem"></a><a name="checkmenuradioitem"></a>CMenu::CheckMenuRadioItem

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
Especifica (como un identificador o desplazamiento, dependiendo del valor de *nFlags*) el primer elemento de menú en el grupo de botones de opción.

*nIDLast*<br/>
Especifica (como un identificador o desplazamiento, dependiendo del valor de *nFlags*) el último elemento de menú en el grupo de botones de opción.

*nIDItem*<br/>
Especifica (como un identificador o desplazamiento, dependiendo del valor de *nFlags*) el elemento en el grupo que se comprobará con un botón de opción.

*nFlags*<br/>
Especifica la interpretación de *nIDFirst*, *nIDLast*y *nIDItem* de la siguiente manera:

|nFlags|Interpretación|
|------------|--------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.|

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; de lo contrario 0

### <a name="remarks"></a>Observaciones

Al mismo tiempo, la función desmarca todos los demás elementos de menú del grupo asociado y borra el indicador de tipo de elemento de radio para esos elementos. El elemento marcado se muestra mediante un mapa de bits de botón de opción (o viñeta) en lugar de un mapa de bits de marca de verificación.

### <a name="example"></a>Ejemplo

  Consulte el ejemplo [de ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).

## <a name="cmenucmenu"></a><a name="cmenu"></a>CMenu::CMenu

Crea un menú vacío y `CMenu` lo adjunta a un objeto.

```
CMenu();
```

### <a name="remarks"></a>Observaciones

El menú no se crea hasta que se llama a una de las funciones miembro de creación o carga de`CMenu:`

- [CreateMenu](#createmenu)

- [CreatePopupMenu](#createpopupmenu)

- [LoadMenu](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [Attach](#attach)

## <a name="cmenucreatemenu"></a><a name="createmenu"></a>CMenu::CreateMenu

Crea un menú y lo `CMenu` adjunta al objeto.

```
BOOL CreateMenu();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el menú se creó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El menú está inicialmente vacío. Los elementos de menú `AppendMenu` `InsertMenu` se pueden agregar mediante la función miembro o.

Si el menú se asigna a una ventana, se destruye automáticamente cuando se destruye la ventana.

Antes de salir, una aplicación debe liberar los recursos del sistema asociados a un menú si el menú no está asignado a una ventana. Una aplicación libera un menú mediante una llamada a la [DestroyMenu](#destroymenu) función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

## <a name="cmenucreatepopupmenu"></a><a name="createpopupmenu"></a>CMenu::CreatePopupMenu

Crea un menú emergente y lo `CMenu` adjunta al objeto.

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el menú emergente se creó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El menú está inicialmente vacío. Los elementos de menú `AppendMenu` `InsertMenu` se pueden agregar mediante la función miembro o. La aplicación puede agregar el menú emergente a un menú existente o menú emergente. La `TrackPopupMenu` función miembro se puede utilizar para mostrar este menú como un menú emergente flotante y para realizar un seguimiento de las selecciones en el menú emergente.

Si el menú se asigna a una ventana, se destruye automáticamente cuando se destruye la ventana. Si el menú se agrega a un menú existente, se destruye automáticamente cuando se destruye ese menú.

Antes de salir, una aplicación debe liberar los recursos del sistema asociados a un menú emergente si el menú no está asignado a una ventana. Una aplicación libera un menú mediante una llamada a la [DestroyMenu](#destroymenu) función miembro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::CreateMenu](#createmenu).

## <a name="cmenudeletemenu"></a><a name="deletemenu"></a>CMenu::DeleteMenu

Elimina un elemento del menú.

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

*nPosición*<br/>
Especifica el elemento de menú que se va a eliminar, según lo determinado por *nFlags*.

*nFlags*<br/>
Se utiliza para interpretar *nPosition de* la siguiente manera:

|nFlags|Interpretación de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.|

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Si el elemento de menú tiene `DeleteMenu` un menú emergente asociado, destruye el controlador en el menú emergente y libera la memoria utilizada por el menú emergente.

Cada vez que se cambia un menú que reside en una ventana (se muestra o no la ventana), la aplicación debe llamar a [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

## <a name="cmenudeletetempmap"></a><a name="deletetempmap"></a>CMenu::DeleteTempMap

Llamado automáticamente `CWinApp` por el controlador de tiempo `CMenu` de inactividad, elimina los objetos temporales creados por el [FromHandle](#fromhandle) función miembro.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Observaciones

`DeleteTempMap`separa el objeto de menú `CMenu` de Windows asociado `CMenu` a un objeto temporal antes de eliminar el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

## <a name="cmenudestroymenu"></a><a name="destroymenu"></a>CMenu::DestroyMenu

Destruye el menú y los recursos de Windows que se usaron.

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se destruye el menú; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El menú se `CMenu` separa del objeto antes de que se destruya. La `DestroyMenu` función de Windows `CMenu` se llama automáticamente en el destructor.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::CreateMenu](#createmenu).

## <a name="cmenudetach"></a><a name="detach"></a>CMenu::Detach

Separa un menú de `CMenu` Windows de un objeto y devuelve el identificador.

```
HMENU Detach();
```

### <a name="return-value"></a>Valor devuelto

El identificador, de tipo HMENU, a un menú de Windows, si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

El `m_hMenu` miembro de datos se establece en NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenudrawitem"></a><a name="drawitem"></a>CMenu::DrawItem

Llamado por el marco de trabajo cuando cambia un aspecto visual de un menú dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero a una estructura [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que contiene información sobre el tipo de dibujo necesario.

### <a name="remarks"></a>Observaciones

El `itemAction` miembro `DRAWITEMSTRUCT` de la estructura define la acción de dibujo que se va a realizar. Invalidar esta función miembro para implementar `CMenu` el dibujo para un objeto de dibujo del propietario. La aplicación debe restaurar todos los objetos de interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de visualización proporcionado en *lpDrawItemStruct* antes de la terminación de esta función miembro.

Vea [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) para obtener `DRAWITEMSTRUCT` una descripción de la estructura.

### <a name="example"></a>Ejemplo

El código siguiente procede del ejemplo [CTRLTEST](../../overview/visual-cpp-samples.md) de MFC:

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

## <a name="cmenuenablemenuitem"></a><a name="enablemenuitem"></a>CMenu::EnableMenuItem

Habilita, deshabilita o atenúa un elemento de menú.

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>Parámetros

*nIDEnableItem*<br/>
Especifica el elemento de menú que se va a habilitar, según lo determinado por *nEnable*. Este parámetro puede especificar elementos de menú emergente, así como elementos de menú estándar.

*nHabilitar*<br/>
Especifica la acción que se va a realizar. Puede ser una combinación de MF_DISABLED, MF_ENABLED o MF_GRAYED, con MF_BYCOMMAND o MF_BYPOSITION. Estos valores se pueden combinar mediante el operador OR bit a bit. Estos valores tienen los significados siguientes:

- MF_BYCOMMAND Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado.

- MF_BYPOSITION Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.

- MF_DISABLED Deshabilita el elemento de menú para que no se pueda seleccionar, pero no lo atenúe.

- MF_ENABLED Habilita el elemento de menú para que se pueda seleccionar y lo restaura desde su estado atenuado.

- MF_GRAYED Deshabilita el elemento de menú para que no se pueda seleccionar y lo atenúe.

### <a name="return-value"></a>Valor devuelto

Estado anterior (MF_DISABLED, MF_ENABLED o MF_GRAYED) o -1 si no es válido.

### <a name="remarks"></a>Observaciones

Las funciones miembro [CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu)y [LoadMenuIndirect](#loadmenuindirect) también pueden establecer el estado (habilitado, deshabilitado o atenuado) de un elemento de menú.

El uso del valor MF_BYPOSITION requiere `CMenu`que una aplicación utilice el archivo . Si `CMenu` se utiliza la barra de menús, se ve afectado un elemento de menú de nivel superior (un elemento de la barra de menús). Para establecer el estado de un elemento en un menú emergente o anidado `CMenu` por posición, una aplicación debe especificar el menú emergente.

Cuando una aplicación especifica la marca MF_BYCOMMAND, Windows comprueba todos los `CMenu`elementos de menú emergente subordinados a la marca ; por lo tanto, a menos `CMenu` que los elementos de menú duplicados estén presentes, el uso de la barra de menús es suficiente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

## <a name="cmenufromhandle"></a><a name="fromhandle"></a>CMenu::FromHandle

Devuelve un puntero `CMenu` a un objeto dado un identificador de Windows a un menú.

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>Parámetros

*hMenú*<br/>
Un identificador de Windows a un menú.

### <a name="return-value"></a>Valor devuelto

Un puntero `CMenu` a un que puede ser temporal o permanente.

### <a name="remarks"></a>Observaciones

Si `CMenu` un objeto aún no está asociado al `CMenu` objeto de menú de Windows, se crea y adjunta un objeto temporal.

Este `CMenu` objeto temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminan todos los objetos temporales.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::CreateMenu](#createmenu).

## <a name="cmenugetdefaultitem"></a><a name="getdefaultitem"></a>CMenu::GetDefaultItem

Determina el elemento de menú predeterminado en el menú especificado.

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parámetros

*gmdiFlags*<br/>
Valor que especifica cómo busca la función los elementos de menú. Este parámetro puede ser ninguno, uno o una combinación de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|Especifica que, si el elemento predeterminado es uno que abre un submenú, la función debe buscar en el submenú correspondiente de forma recursiva. Si el submenú no tiene ningún elemento predeterminado, el valor devuelto identifica el elemento que abre el submenú.<br /><br /> De forma predeterminada, la función devuelve el primer elemento predeterminado en el menú especificado, independientemente de si es un elemento que abre un submenú.|
|GMDI_USEDISABLED|Especifica que la función debe devolver un elemento predeterminado, incluso si está deshabilitada.<br /><br /> De forma predeterminada, la función omite los elementos deshabilitados o atenuados.|

*fByPos*<br/>
Valor que especifica si se va a recuperar el identificador del elemento de menú o su posición. Si este parámetro es FALSE, se devuelve el identificador. De lo contrario, se devuelve la posición.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es el identificador o la posición del elemento de menú. Si se produce un error en la función, el valor devuelto es - 1.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la función [GetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem)de Win32 , como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetmenucontexthelpid"></a><a name="getmenucontexthelpid"></a>CMenu::GetMenuContextHelpId

Recupera el identificador de `CMenu`ayuda de contexto asociado a .

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador de ayuda `CMenu` de contexto asociado actualmente si tiene uno; cero de lo contrario.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetmenuinfo"></a><a name="getmenuinfo"></a>CMenu::GetMenuInfo

Recupera información para un menú.

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>Parámetros

*lpcmi*<br/>
Puntero a una estructura [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) que contiene información para el menú.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero; de lo contrario, el valor devuelto es cero.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar información sobre el menú.

## <a name="cmenugetmenuitemcount"></a><a name="getmenuitemcount"></a>CMenu::GetMenuItemCount

Determina el número de elementos de un menú emergente o de nivel superior.

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos del menú si la función se realiza correctamente; de lo contrario -1.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

## <a name="cmenugetmenuitemid"></a><a name="getmenuitemid"></a>CMenu::GetMenuItemID

Obtiene el identificador de elemento de menú para un elemento de menú situado en la posición definida por *nPos*.

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
Especifica la posición (basada en cero) del elemento de menú cuyo identificador se está recuperando.

### <a name="return-value"></a>Valor devuelto

El identificador de elemento para el elemento especificado en un menú emergente si la función se realiza correctamente. Si el elemento especificado es un menú emergente (a diferencia de un elemento dentro del menú emergente), el valor devuelto es -1. Si *nPos* corresponde a un elemento de menú SEPARADOR, el valor devuelto es 0.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetmenuiteminfo"></a><a name="getmenuiteminfo"></a>CMenu::GetMenuItemInfo

Recupera información sobre un elemento de menú.

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parámetros

*uItem*<br/>
Identificador o posición del elemento de menú para obtener información sobre. El significado de este parámetro `ByPos`depende del valor de .

*lpMenuItemInfo*<br/>
Un puntero a un [MENUITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow), como se describe en el Windows SDK, que contiene información sobre el menú.

*fByPos*<br/>
Valor que especifica `nIDItem`el significado de . De forma `ByPos` predeterminada, es FALSE, que indica que uItem es un identificador de elemento de menú. Si `ByPos` no se establece en FALSE, indica una posición de elemento de menú.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero. Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, use la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)de Win32 , como se describe en el Windows SDK.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la función [GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow)de Win32 , como se describe en el Windows SDK. Tenga en cuenta que `GetMenuItemInfo`en la implementación MFC de , no se usa un identificador para un menú.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

## <a name="cmenugetmenustate"></a><a name="getmenustate"></a>CMenu::GetMenuState

Devuelve el estado del elemento de menú especificado o el número de elementos de un menú emergente.

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Especifica el identificador del elemento de menú, según lo determinado por *nFlags*.

*nFlags*<br/>
Especifica la naturaleza de *nID*. Puede ser uno de los siguientes valores:

- MF_BYCOMMAND Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado.

- MF_BYPOSITION Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.

### <a name="return-value"></a>Valor devuelto

El valor 0xFFFFFFFF si el elemento especificado no existe. Si *nId* identifica un menú emergente, el byte de orden superior contiene el número de elementos del menú emergente y el byte de orden inferior contiene los indicadores de menú asociados al menú emergente. De lo contrario, el valor devuelto es una máscara (Boolean OR) de los valores de la lista siguiente (esta máscara describe el estado del elemento de menú que *nId* identifica):

- MF_CHECKED Actúa como un conmutador con MF_UNCHECKED colocar la marca de verificación predeterminada junto al elemento. Cuando la aplicación proporciona mapas de bits `SetMenuItemBitmaps` de marca de verificación (consulte la función miembro), se muestra el mapa de bits "marca de verificación activada".

- MF_DISABLED Deshabilita el elemento de menú para que no se pueda seleccionar, pero no lo atenúe.

- MF_ENABLED Habilita el elemento de menú para que se pueda seleccionar y lo restaura desde su estado atenuado. Tenga en cuenta que el valor de esta constante es 0; una aplicación no debe probar con 0 para el error al usar este valor.

- MF_GRAYED Deshabilita el elemento de menú para que no se pueda seleccionar y lo atenúe.

- MF_MENUBARBREAK Coloca el elemento en una nueva línea en los menús estáticos o en una nueva columna en los menús emergentes. La nueva columna del menú emergente se separará de la columna antigua por una línea divisoria vertical.

- MF_MENUBREAK Coloca el elemento en una nueva línea en los menús estáticos o en una nueva columna en los menús emergentes. No se coloca ninguna línea divisoria entre las columnas.

- MF_SEPARATOR Dibuja una línea divisoria horizontal. Solo se puede utilizar en un menú emergente. Esta línea no se puede atenuar, deshabilitar ni resaltar. Se omiten otros parámetros.

- MF_UNCHECKED Actúa como un conmutador con MF_CHECKED para quitar una marca de verificación junto al elemento. Cuando la aplicación proporciona mapas de bits `SetMenuItemBitmaps` de marca de verificación (consulte la función miembro), se muestra el mapa de bits "marca de verificación desactivada". Tenga en cuenta que el valor de esta constante es 0; una aplicación no debe probar con 0 para el error al usar este valor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

## <a name="cmenugetmenustring"></a><a name="getmenustring"></a>CMenu::GetMenuString

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
Especifica el identificador entero del elemento de menú o el desplazamiento del elemento de menú en el menú, en función del valor de *nFlags*.

*lpString*<br/>
Apunta al búfer que va a recibir la etiqueta.

*rString*<br/>
Una referencia `CString` a un objeto que va a recibir la cadena de menú copiada.

*nMaxCount*<br/>
Especifica la longitud máxima (en caracteres) de la etiqueta que se va a copiar. Si la etiqueta es mayor que el máximo especificado en *nMaxCount*, los caracteres adicionales se truncan.

*nFlags*<br/>
Especifica la interpretación del parámetro *nIDItem.* Puede ser uno de los siguientes valores:

|nFlags|Interpretación de nIDItem|
|------------|-------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.|

### <a name="return-value"></a>Valor devuelto

Especifica el número real de caracteres copiados en el búfer, sin incluir el terminador nulo.

### <a name="remarks"></a>Observaciones

El *nMaxCount* parámetro debe ser uno mayor que el número de caracteres de la etiqueta para dar cabida al carácter nulo que termina una cadena.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetsafehmenu"></a><a name="getsafehmenu"></a>CMenu::GetSafeHmenu

Devuelve el HMENU ajustado `CMenu` por este`CMenu` objeto o un puntero NULL.

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::LoadMenu](#loadmenu).

## <a name="cmenugetsubmenu"></a><a name="getsubmenu"></a>CMenu::GetSubMenu

Recupera el `CMenu` objeto de un menú emergente.

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
Especifica la posición del menú emergente contenido en el menú. Los valores de posición comienzan en 0 para el primer elemento de menú. El identificador del menú emergente no se puede utilizar en esta función.

### <a name="return-value"></a>Valor devuelto

Un puntero `CMenu` a `m_hMenu` un objeto cuyo miembro contiene un identificador para el menú emergente si existe un menú emergente en la posición dada; NULL. Si `CMenu` no existe un objeto, se crea uno temporal. El `CMenu` puntero devuelto no se debe almacenar.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::TrackPopupMenu](#trackpopupmenu).

## <a name="cmenuinsertmenu"></a><a name="insertmenu"></a>CMenu::InsertMenu

Inserta un nuevo elemento de menú en la posición especificada por *nPosition* y mueve otros elementos hacia abajo del menú.

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

*nPosición*<br/>
Especifica el elemento de menú antes del cual se va a insertar el nuevo elemento de menú. El parámetro *nFlags* se puede utilizar para interpretar *nPosition* de las siguientes maneras:

|nFlags|Interpretación de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0. Si *nPosition* es -1, el nuevo elemento de menú se anexa al final del menú.|

*nFlags*<br/>
Especifica cómo se interpreta *nPosition* y especifica información sobre el estado del nuevo elemento de menú cuando se agrega al menú. Para obtener una lista de los indicadores que se pueden establecer, vea el [AppendMenu](#appendmenu) función miembro. Para especificar más de un valor, utilice el operador OR bit a bit para combinarlos con la marca MF_BYCOMMAND o MF_BYPOSITION.

*nIDNewItem*<br/>
Especifica el identificador de comando del nuevo elemento de menú o, si *nFlags* está establecido en MF_POPUP, el identificador de menú ( HMENU) del menú emergente. El *nIDNewItem* parámetro se omite (no es necesario) si *nFlags* se establece en MF_SEPARATOR.

*lpszNewItem*<br/>
Especifica el contenido del nuevo elemento de menú. *nFlags* se pueden utilizar para interpretar *lpszNewItem de* las siguientes maneras:

|nFlags|Interpretación de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contiene un valor de 32 bits proporcionado por la aplicación que la aplicación puede usar para mantener datos adicionales asociados con el elemento de menú. Este valor de 32 bits está `itemData` disponible para la aplicación en el miembro de la estructura proporcionada por los [mensajes WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem) y [WM_DRAWITEM.](/windows/win32/Controls/wm-drawitem) Estos mensajes se envían cuando el elemento de menú se muestra inicialmente o se cambia.|
|MF_STRING|Contiene un puntero largo a una cadena terminada en null. Esta es la interpretación predeterminada.|
|MF_SEPARATOR|El parámetro *lpszNewItem* se omite (no es necesario).|

*pBmp*<br/>
Apunta a `CBitmap` un objeto que se utilizará como elemento de menú.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La aplicación puede especificar el estado del elemento de menú estableciendo valores en *nFlags*.

Cada vez que se cambia un menú que reside en una ventana (se muestra o no la ventana), la aplicación debe llamar a `CWnd::DrawMenuBar`.

Cuando *nIDNewItem* especifica un menú emergente, se convierte en parte del menú en el que se inserta. Si se destruye ese menú, el menú insertado también se destruirá. Un menú insertado debe separarse de un `CMenu` objeto para evitar conflictos.

Si se maximiza la ventana secundaria de la interfaz de varios documentos (MDI) activa y una aplicación inserta un menú emergente en el menú de la aplicación MDI llamando a esta función y especificando el indicador MF_BYPOSITION, el menú se inserta una posición más a la izquierda de lo esperado. Esto sucede porque el menú Control de la ventana secundaria MDI activa se inserta en la primera posición de la barra de menús de la ventana de marco MDI. Para colocar el menú correctamente, la aplicación debe agregar 1 al valor de posición que de otro modo se utilizaría. Una aplicación puede usar el mensaje WM_MDIGETACTIVE para determinar si se maximiza la ventana secundaria activa actualmente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

## <a name="cmenuinsertmenuitem"></a><a name="insertmenuitem"></a>CMenu::InsertMenuItem

Inserta un nuevo elemento de menú en la posición especificada en un menú.

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
Consulte la descripción `InsertMenuItem` de *lpmii* en el Windows SDK.

*fByPos*<br/>
Consulte la descripción `InsertMenuItem` de *fByPosition* en el Windows SDK.

### <a name="remarks"></a>Observaciones

Esta función ajusta [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw), que se describe en el Windows SDK.

## <a name="cmenuloadmenu"></a><a name="loadmenu"></a>CMenu::LoadMenu

Carga un recurso de menú desde el archivo ejecutable `CMenu` de la aplicación y lo adjunta al objeto.

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

Distinto de cero si el recurso de menú se cargó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Antes de salir, una aplicación debe liberar los recursos del sistema asociados a un menú si el menú no está asignado a una ventana. Una aplicación libera un menú mediante una llamada a la [DestroyMenu](#destroymenu) función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

## <a name="cmenuloadmenuindirect"></a><a name="loadmenuindirect"></a>CMenu::LoadMenuIndirect

Carga un recurso de una plantilla de menú `CMenu` en la memoria y lo adjunta al objeto.

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>Parámetros

*lpMenuTemplate*<br/>
Apunta a una plantilla de menú (que es una sola estructura [MENUITEMTEMPLATEHEADER](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader) y una colección de una o más estructuras [MENUITEMTEMPLATE).](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) Para obtener más información sobre estas dos estructuras, consulte el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el recurso de menú se cargó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Una plantilla de menú es un encabezado seguido de una colección de una o más estructuras [MENUITEMTEMPLATE,](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) cada una de las cuales puede contener uno o varios elementos de menú y menús emergentes.

El número de versión debe ser 0.

Las `mtOption` marcas deben incluir MF_END para el último elemento de una lista emergente y para el último elemento de la lista principal. Vea `AppendMenu` la función miembro para otros indicadores. El `mtId` miembro debe omitirse de la estructura MENUITEMTEMPLATE `mtOption`cuando se especifica MF_POPUP en .

El espacio asignado para la estructura MENUITEMTEMPLATE debe ser lo suficientemente grande como para `mtString` contener el nombre del elemento de menú como una cadena terminada en null.

Antes de salir, una aplicación debe liberar los recursos del sistema asociados a un menú si el menú no está asignado a una ventana. Una aplicación libera un menú mediante una llamada a la [DestroyMenu](#destroymenu) función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

## <a name="cmenum_hmenu"></a><a name="m_hmenu"></a>CMenu::m_hMenu

Especifica el identificador HMENU del menú `CMenu` de Windows asociado al objeto.

```
HMENU m_hMenu;
```

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::LoadMenu](#loadmenu).

## <a name="cmenumeasureitem"></a><a name="measureitem"></a>CMenu::MeasureItem

Llamado por el marco de trabajo cuando se crea un menú con el estilo de dibujo del propietario.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpMeasureItemStruct*<br/>
Un puntero `MEASUREITEMSTRUCT` a una estructura.

### <a name="remarks"></a>Observaciones

De forma predeterminada, esta función miembro no hace nada. Invalide esta función `MEASUREITEMSTRUCT` miembro y rellene la estructura para informar a Windows de las dimensiones del menú.

Vea [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) para obtener `MEASUREITEMSTRUCT` una descripción de la estructura.

### <a name="example"></a>Ejemplo

El código siguiente procede del ejemplo [CTRLTEST](../../overview/visual-cpp-samples.md) de MFC:

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

## <a name="cmenumodifymenu"></a><a name="modifymenu"></a>CMenu::ModifyMenu

Cambia un elemento de menú existente en la posición especificada por *nPosition*.

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

*nPosición*<br/>
Especifica el elemento de menú que se va a cambiar. El parámetro *nFlags* se puede utilizar para interpretar *nPosition* de las siguientes maneras:

|nFlags|Interpretación de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.|

*nFlags*<br/>
Especifica cómo se interpreta *nPosition* y proporciona información sobre los cambios que se realizarán en el elemento de menú. Para obtener una lista de indicadores que se pueden establecer, vea el [AppendMenu](#appendmenu) función miembro.

*nIDNewItem*<br/>
Especifica el identificador de comando del elemento de menú modificado o, si *nFlags* está establecido en MF_POPUP, el identificador de menú (HMENU) de un menú emergente. El *nIDNewItem* parámetro se omite (no es necesario) si *nFlags* se establece en MF_SEPARATOR.

*lpszNewItem*<br/>
Especifica el contenido del nuevo elemento de menú. El *nFlags* parámetro se puede utilizar para interpretar *lpszNewItem de* las siguientes maneras:

|nFlags|Interpretación de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contiene un valor de 32 bits proporcionado por la aplicación que la aplicación puede usar para mantener datos adicionales asociados con el elemento de menú. Este valor de 32 bits está disponible para la aplicación cuando procesa MF_MEASUREITEM y MF_DRAWITEM.|
|MF_STRING|Contiene un puntero largo a una cadena `CString`terminada en null o a un archivo .|
|MF_SEPARATOR|El parámetro *lpszNewItem* se omite (no es necesario).|

*pBmp*<br/>
Apunta a `CBitmap` un objeto que se utilizará como elemento de menú.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La aplicación especifica el nuevo estado del elemento de menú estableciendo valores en *nFlags*. Si esta función reemplaza un menú emergente asociado con el elemento de menú, destruye el antiguo menú emergente y libera la memoria utilizada por el menú emergente.

Cuando *nIDNewItem* especifica un menú emergente, se convierte en parte del menú en el que se inserta. Si se destruye ese menú, el menú insertado también se destruirá. Un menú insertado debe separarse de un `CMenu` objeto para evitar conflictos.

Cada vez que se cambia un menú que reside en una ventana (se muestra o no la ventana), la aplicación debe llamar a `CWnd::DrawMenuBar`. Para cambiar los atributos de los elementos `CheckMenuItem` de `EnableMenuItem` menú existentes, es mucho más rápido usar las funciones miembro y.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

## <a name="cmenuoperator-hmenu"></a><a name="operator_hmenu"></a>CMenu::operador HMENU

Utilice este operador para recuperar `CMenu` el identificador del objeto.

```
operator HMENU() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el identificador del `CMenu` objeto; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Puede usar el identificador para llamar a las API de Windows directamente.

## <a name="cmenuoperator-"></a><a name="operator_neq"></a>CMenu::operador !-

Determina si dos menús no son iguales lógicamente.

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>Parámetros

*Menú*<br/>
Un objeto `CMenu` para la comparación.

### <a name="remarks"></a>Observaciones

Comprueba si un objeto de menú en el lado izquierdo no es igual a un objeto de menú en el lado derecho.

## <a name="cmenuoperator-"></a><a name="operator_eq_eq"></a>CMenu::operador ?

Determina si dos menús son lógicamente iguales.

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>Parámetros

*Menú*<br/>
Un objeto `CMenu` para la comparación.

### <a name="remarks"></a>Observaciones

Comprueba si un objeto de menú en el lado izquierdo es igual (en términos del valor HMENU) a un objeto de menú en el lado derecho.

## <a name="cmenuremovemenu"></a><a name="removemenu"></a>CMenu::RemoveMenu

Elimina un elemento de menú con un menú emergente asociado del menú.

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

*nPosición*<br/>
Especifica el elemento de menú que se va a quitar. El parámetro *nFlags* se puede utilizar para interpretar *nPosition* de las siguientes maneras:

|nFlags|Interpretación de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.|

*nFlags*<br/>
Especifica cómo se interpreta *nPosition.*

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

No destruye el controlador para un menú emergente, por lo que el menú se puede reutilizar. Antes de llamar a esta `GetSubMenu` función, la aplicación `CMenu` puede llamar a la función miembro para recuperar el objeto emergente para su reutilización.

Cada vez que se cambia un menú que reside en una ventana (se muestra o no la ventana), la aplicación debe llamar a `CWnd::DrawMenuBar`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

## <a name="cmenusetdefaultitem"></a><a name="setdefaultitem"></a>CMenu::SetDefaultItem

Establece el elemento de menú predeterminado para el menú especificado.

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parámetros

*uItem*<br/>
Identificador o posición del nuevo elemento de menú predeterminado o - 1 para ningún elemento predeterminado. El significado de este parámetro depende del valor de *fByPos*.

*fByPos*<br/>
Valor que especifica el significado de *uItem*. Si este parámetro es FALSE, *uItem* es un identificador de elemento de menú. De lo contrario, es una posición de elemento de menú.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero. Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, use la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)de Win32 , como se describe en el Windows SDK.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la función de Win32 [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem), como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

## <a name="cmenusetmenucontexthelpid"></a><a name="setmenucontexthelpid"></a>CMenu::SetMenuContextHelpId

Asocia un identificador `CMenu`de ayuda de contexto con .

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>Parámetros

*dwContextHelpId*<br/>
Identificador de ayuda `CMenu`de contexto con el que asociarse .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; de lo contrario 0

### <a name="remarks"></a>Observaciones

Todos los elementos del menú comparten este identificador: no es posible adjuntar un identificador de contexto de ayuda a los elementos de menú individuales.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).

## <a name="cmenusetmenuinfo"></a><a name="setmenuinfo"></a>CMenu::SetMenuInfo

Establece la información de un menú.

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>Parámetros

*lpcmi*<br/>
Puntero a una estructura [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) que contiene información para el menú.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero; de lo contrario, el valor devuelto es cero.

### <a name="remarks"></a>Observaciones

Llame a esta función para establecer información específica sobre el menú.

## <a name="cmenusetmenuitembitmaps"></a><a name="setmenuitembitmaps"></a>CMenu::SetMenuItemBitmaps

Asocia los mapas de bits especificados con un elemento de menú.

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>Parámetros

*nPosición*<br/>
Especifica el elemento de menú que se va a cambiar. El parámetro *nFlags* se puede utilizar para interpretar *nPosition* de las siguientes maneras:

|nFlags|Interpretación de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado si no se establece MF_BYCOMMAND ni MF_BYPOSITION.|
|MF_BYPOSITION|Especifica que el parámetro proporciona la posición del elemento de menú existente. El primer elemento está en la posición 0.|

*nFlags*<br/>
Especifica cómo se interpreta *nPosition.*

*pBmpUnchecked*<br/>
Especifica el mapa de bits que se va a utilizar para los elementos de menú que no están marcados.

*pBmpChecked*<br/>
Especifica el mapa de bits que se va a utilizar para los elementos de menú que están marcados.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Si el elemento de menú está marcado o desactivado, Windows muestra el mapa de bits adecuado junto al elemento de menú.

Si *pBmpUnchecked* o *pBmpChecked* es NULL, Windows no muestra nada junto al elemento de menú para el atributo correspondiente. Si ambos parámetros son NULL, Windows usa la marca de verificación predeterminada cuando se marca el elemento y quita la marca de verificación cuando el elemento está desmarcado.

Cuando se destruye el menú, estos mapas de bits no se destruyen; la aplicación debe destruirlos.

La `GetMenuCheckMarkDimensions` función Windows recupera las dimensiones de la marca de verificación predeterminada utilizada para los elementos de menú. La aplicación utiliza estos valores para determinar el tamaño adecuado para los mapas de bits proporcionados con esta función. Obtenga el tamaño, cree los mapas de bits y, a continuación, establézcalos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

## <a name="cmenusetmenuiteminfo"></a><a name="setmenuiteminfo"></a>CMenu::SetMenuItemInfo

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
Consulte la descripción `SetMenuItemInfo` de *lpmii* en el Windows SDK.

*fByPos*<br/>
Consulte la descripción `SetMenuItemInfo` de *fByPosition* en el Windows SDK.

### <a name="remarks"></a>Observaciones

Esta función ajusta [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow), que se describe en el Windows SDK.

## <a name="cmenutrackpopupmenu"></a><a name="trackpopupmenu"></a>CMenu::TrackPopupMenu

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
Especifica los indicadores de posición de pantalla y posición del ratón. Consulte [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) para obtener una lista de los indicadores disponibles.

*X*<br/>
Especifica la posición horizontal en las coordenadas de pantalla del menú emergente. Dependiendo del valor del parámetro *nFlags,* el menú se puede alinear a la izquierda, a la derecha o centrado en relación con esta posición.

*y y*<br/>
Especifica la posición vertical en las coordenadas de pantalla de la parte superior del menú de la pantalla.

*pWnd*<br/>
Identifica la ventana que posee el menú emergente. Este parámetro no puede ser NULL, incluso si se especifica el TPM_NONOTIFY marca. Esta ventana recibe todos los mensajes WM_COMMAND del menú. En las versiones 3.1 y posteriores de `TrackPopupMenu` Windows, la ventana no recibe mensajes WM_COMMAND hasta que se devuelve. En Windows 3.0, la ventana `TrackPopupMenu` recibe WM_COMMAND mensajes antes de las devoluciones.

*lpRect*<br/>
ignorado.

### <a name="return-value"></a>Valor devuelto

Este método devuelve el resultado de llamar a [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Un menú emergente flotante puede aparecer en cualquier lugar de la pantalla.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

## <a name="cmenutrackpopupmenuex"></a><a name="trackpopupmenuex"></a>CMenu::TrackPopupMenuEx

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

*X*<br/>
Especifica la posición horizontal en las coordenadas de pantalla del menú emergente.

*y y*<br/>
Especifica la posición vertical en las coordenadas de pantalla de la parte superior del menú de la pantalla.

*pWnd*<br/>
Un puntero a la ventana que posee el menú emergente y recibe los mensajes del menú creado. Esta ventana puede ser cualquier ventana de la aplicación actual, pero no puede ser NULL. Si especifica TPM_NONOTIFY en el parámetro *fuFlags,* la función no envía ningún mensaje a *pWnd*. La función debe devolver para la ventana señalada por *pWnd* para recibir el mensaje WM_COMMAND.

*lptpm*<br/>
Puntero a una estructura [TPMPARAMS](/windows/win32/api/winuser/ns-winuser-tpmparams) que especifica un área de la pantalla que el menú no debe superponerse. Este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si especifica TPM_RETURNCMD en el parámetro *fuFlags,* el valor devuelto es el identificador de elemento de menú del elemento seleccionado por el usuario. Si el usuario cancela el menú sin realizar una selección, o si se produce un error, el valor devuelto es 0.

Si no especifica TPM_RETURNCMD en el parámetro *fuFlags,* el valor devuelto es distinto de cero si la función se realiza correctamente y 0 si se produce un error. Para obtener información de error extendida, llame a [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Observaciones

Un menú emergente flotante puede aparecer en cualquier lugar de la pantalla. Para obtener más información sobre el control de errores al crear el menú emergente, consulte [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

## <a name="see-also"></a>Consulte también

[EJEMPLO de MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)
