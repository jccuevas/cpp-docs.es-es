---
title: CMenu (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMenu
dev_langs:
- C++
helpviewer_keywords:
- HMENU
- menus, class
- menus, base class
- menus, creating
- menus, managing
- CMenu class
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
caps.latest.revision: 22
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
ms.openlocfilehash: dcd353bf0be5d23c1782347f54b16a875ed190ed
ms.lasthandoff: 02/24/2017

---
# <a name="cmenu-class"></a>CMenu (clase)
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
|[CMenu:: AppendMenu](#appendmenu)|Agrega un nuevo elemento al final de este menú.|  
|[CMenu::Attach](#attach)|Asocia un identificador de menú de Windows para un `CMenu` objeto.|  
|[CMenu::CheckMenuItem](#checkmenuitem)|Coloca una marca de verificación junto a o quita una marca de verificación de un elemento de menú en el menú emergente.|  
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|Coloca un botón de radio situado junto a un elemento de menú y quita el botón de opción de todos los demás elementos de menú en el grupo.|  
|[CMenu::CreateMenu](#createmenu)|Crea un menú vacío y lo asocia a un `CMenu` objeto.|  
|[CMenu::CreatePopupMenu](#createpopupmenu)|Crea un menú emergente vacío y lo asocia a un `CMenu` objeto.|  
|[CMenu:: DeleteMenu](#deletemenu)|Elimina un elemento especificado en el menú. Si el elemento de menú tiene un menú emergente asociado, destruye el identificador del menú emergente y libera la memoria utilizada por él.|  
|[CMenu::DeleteTempMap](#deletetempmap)|Elimina cualquier temporal `CMenu` objetos creados por el `FromHandle` función miembro.|  
|[CMenu::DestroyMenu](#destroymenu)|Destruye el menú asociado a un `CMenu` de objetos y libera la memoria que ocupaba el menú.|  
|[CMenu::Detach](#detach)|Desasocia un identificador de menú de Windows desde un `CMenu` de objetos y devuelve el identificador.|  
|[CMenu::DrawItem](#drawitem)|Llamado por el marco cuando un aspecto visual de los cambios de un menú dibujado por el propietario.|  
|[EnableMenuItem](#enablemenuitem)|Habilita, deshabilita o atenúa (grises) un elemento de menú.|  
|[CMenu::FromHandle](#fromhandle)|Devuelve un puntero a un `CMenu` objeto, dados un identificador de menú de Windows.|  
|[CMenu::GetDefaultItem](#getdefaultitem)|Determina el elemento de menú predeterminado en el menú especificado.|  
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|Recupera el identificador de contexto de ayuda asociado al menú.|  
|[CMenu::GetMenuInfo](#getmenuinfo)|Recupera información sobre un menú específico.|  
|[CMenu::GetMenuItemCount](#getmenuitemcount)|Determina el número de elementos de un menú emergente o de nivel superior.|  
|[CMenu::GetMenuItemID](#getmenuitemid)|Obtiene el identificador del elemento de menú para un elemento de menú que se encuentra en la posición especificada.|  
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|Recupera información sobre un elemento de menú.|  
|[CMenu::GetMenuState](#getmenustate)|Devuelve el estado del elemento de menú especificado o el número de elementos de un menú emergente.|  
|[CMenu::GetMenuString](#getmenustring)|Recupera la etiqueta del elemento de menú especificado.|  
|[CMenu::GetSafeHmenu](#getsafehmenu)|Devuelve el `m_hMenu` contenido en este `CMenu` objeto.|  
|[CMenu::GetSubMenu](#getsubmenu)|Recupera un puntero a un menú emergente.|  
|[CMenu::InsertMenu](#insertmenu)|Inserta un nuevo elemento de menú en la posición especificada, bajando otros elementos del menú.|  
|[CMenu::InsertMenuItem](#insertmenuitem)|Inserta un nuevo elemento de menú en la posición especificada en un menú.|  
|[CMenu::LoadMenu](#loadmenu)|Carga un recurso de menú desde el archivo ejecutable y lo adjunta a un `CMenu` objeto.|  
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|Carga un menú de una plantilla de menú en la memoria y lo adjunta a un `CMenu` objeto.|  
|[CMenu::MeasureItem](#measureitem)|Llamado por el marco de trabajo para determinar las dimensiones de menú cuando se crea un menú dibujado por el propietario.|  
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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMenu::operator HMENU](#operator_hmenu)|Recupera el identificador del objeto de menú.|  
|[CMenu::operator! =](#operator_neq)|Determina si dos objetos de menú no son iguales.|  
|[CMenu::operator ==](#operator_eq_eq)|Determina si dos objetos de menú son iguales.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMenu::m_hMenu](#m_hmenu)|Especifica el identificador del menú de Windows asociado a la `CMenu` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Proporciona funciones miembro para crear, seguimiento, actualizar y destruir un menú.  
  
 Crear un `CMenu` objeto en el marco de pila como una variable local, a continuación, llamar a `CMenu`de las funciones miembro para manipular el nuevo menú según sea necesario. A continuación, llame a [CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu) establecer el menú en una ventana, seguido inmediatamente por una llamada a la `CMenu` del objeto [separar](#detach) función miembro. El `CWnd::SetMenu` establece el menú Ventana en el menú nuevo, hace que la ventana se vuelva a dibujar para reflejar el cambio de menú y pasa también la propiedad del menú en la ventana de función miembro. La llamada a **separar** desasocia la `HMENU` desde el `CMenu` lo objeto, que, cuando local `CMenu` variable sale del ámbito, el `CMenu` destructor de objeto no intenta destruir un menú ya no posee. El menú se destruye automáticamente cuando se destruye la ventana.  
  
 Puede usar el [LoadMenuIndirect](#loadmenuindirect) para crear un menú de una plantilla en memoria, pero un menú creado desde un recurso mediante una llamada a función miembro [LoadMenu](#loadmenu) resulta más fácil de mantener, y el propio recurso de menú se puede crear y modificar mediante el editor de menús.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenu`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-nameappendmenua--cmenuappendmenu"></a><a name="appendmenu"></a>CMenu:: AppendMenu  
 Agrega un nuevo elemento al final de un menú.  
  
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
 `nFlags`  
 Especifica información sobre el estado del nuevo elemento de menú cuando se agrega al menú. Consta de uno o varios de los valores enumerados en la sección Comentarios.  
  
 `nIDNewItem`  
 Especifica el identificador de comando del elemento de menú nuevo o, si `nFlags` está establecido en **MF_POPUP**, el identificador de menú ( `HMENU`) de un menú emergente. El `nIDNewItem` parámetro se omite (no es necesario) si `nFlags` está establecido en **MF_SEPARATOR**.  
  
 `lpszNewItem`  
 Especifica el contenido del nuevo elemento de menú. El `nFlags` parámetro se usa para interpretar `lpszNewItem` de la siguiente manera:  
  
|nFlags|Interpretación de lpszNewItem|  
|------------|-----------------------------------|  
|`MF_OWNERDRAW`|Contiene un valor de 32 bits proporcionada por la aplicación que la aplicación puede usar para mantener datos adicionales asociados con el elemento de menú. Este valor de 32 bits está disponible para la aplicación cuando procesa `WM_MEASUREITEM` y `WM_DRAWITEM` mensajes. El valor se almacena en el **itemData** miembro de la estructura proporcionada con los mensajes.|  
|**MF_STRING**|Contiene un puntero a una cadena terminada en null. Se trata de la interpretación predeterminada.|  
|**MF_SEPARATOR**|El `lpszNewItem` parámetro se omite (no es necesario).|  
  
 *pBmp*  
 Apunta a un `CBitmap` objeto que se usará como el elemento de menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 La aplicación puede especificar el estado del elemento de menú estableciendo valores en `nFlags`. Cuando `nIDNewItem` especifica un menú emergente, se convierte en parte del menú al que se anexa. Si se destruye dicho menú, también se destruirá el menú anexado. Se debería desasociar un menú anexado un `CMenu` objeto para evitar el conflicto. Tenga en cuenta que **MF_STRING** y `MF_OWNERDRAW` no son válidos para la versión de mapa de bits de `AppendMenu`.  
  
 La lista siguiente describe los indicadores que se pueden establecer en `nFlags`:  
  
- **MF_CHECKED** actúa como un botón de alternancia con **MF_UNCHECKED** para colocar la marca de verificación predeterminada junto al elemento. Cuando la aplicación proporciona los mapas de bits de la marca de verificación (consulte la [SetMenuItemBitmaps](#setmenuitembitmaps) función miembro), se muestra el mapa de bits "marca de verificación en".  
  
- **MF_UNCHECKED** actúa como un botón de alternancia con **MF_CHECKED** para quitar una marca de verificación junto al elemento. Cuando la aplicación proporciona los mapas de bits de la marca de verificación (consulte la `SetMenuItemBitmaps` función miembro), se muestra el mapa de bits de "marca de verificación de desactivar".  
  
- **MF_DISABLED** deshabilita el elemento de menú para que no se puede seleccionar, pero no lo dim.  
  
- `MF_ENABLED`Habilita el elemento de menú para que se pueden seleccionar y restaura su estado atenuado.  
  
- **MF_GRAYED** deshabilita el elemento de menú para que se atenúa y no se pueden seleccionar.  
  
- **MF_MENUBARBREAK** coloca el elemento en una nueva línea en un menú estático o en una nueva columna en los menús emergentes. Una línea divisoria vertical separará la nueva columna de menú emergente de la columna antigua.  
  
- **MF_MENUBREAK** coloca el elemento en una nueva línea en un menú estático o en una nueva columna en los menús emergentes. No se coloca ninguna línea divisoria entre las columnas.  
  
- `MF_OWNERDRAW`Especifica que el elemento es un elemento dibujado por el propietario. Cuando el menú aparece por primera vez, la ventana que posee el menú recibe una `WM_MEASUREITEM` mensaje, que recupera el alto y ancho del elemento de menú. El `WM_DRAWITEM` mensaje es enviado cada vez que el propietario debe actualizar el aspecto visual del elemento de menú. Esta opción no es válida para un elemento de menú de nivel superior.  
  
- **MF_POPUP** especifica que el elemento de menú tiene un menú emergente asociado a él. El parámetro ID especifica un identificador de un menú emergente que desea asociar con el elemento. Se utiliza para agregar un menú emergente de nivel superior o un menú emergente jerárquico a un elemento del menú emergente.  
  
- **MF_SEPARATOR** dibuja una línea de división horizontal. Sólo puede utilizarse en un menú emergente. Esta línea no aparecen atenuada, deshabilitada o resaltada. Se omiten los otros parámetros.  
  
- **MF_STRING** especifica que el elemento de menú es una cadena de caracteres.  
  
 Cada uno de los siguientes grupos muestra indicadores que se excluyen mutuamente y no pueden utilizarse juntos:  
  
- **MF_DISABLED**, `MF_ENABLED`, y **MF_GRAYED**  
  
- **MF_STRING**, `MF_OWNERDRAW`, **MF_SEPARATOR**y la versión de mapa de bits  
  
- **MF_MENUBARBREAK** y **MF_MENUBREAK**  
  
- **MF_CHECKED** y **MF_UNCHECKED**  
  
 Cuando un menú que reside en una ventana se cambia (o no se muestra la ventana), la aplicación debe llamar a [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::CreateMenu](#createmenu).  
  
##  <a name="a-nameattacha--cmenuattach"></a><a name="attach"></a>CMenu::Attach  
 Asocia un menú de Windows existente a un `CMenu` objeto.  
  
```  
BOOL Attach(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 `hMenu`  
 Especifica un identificador de un menú de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 No se debería llamar a esta función si un menú ya está asociado a la `CMenu` objeto. El identificador del menú se almacena en el `m_hMenu` miembro de datos.  
  
 Si el menú que desea manipular ya está asociado a una ventana, puede usar el [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu) función para obtener un identificador del menú.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[21 NVC_MFCWindowing](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="a-namecheckmenuitema--cmenucheckmenuitem"></a><a name="checkmenuitem"></a>CMenu::CheckMenuItem  
 Agrega marcas de verificación o quita las marcas de verificación de los elementos de menú en el menú emergente.  
  
```  
UINT CheckMenuItem(
    UINT nIDCheckItem,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDCheckItem`  
 Especifica el elemento de menú se activa, según lo determinado por `nCheck`.  
  
 `nCheck`  
 Especifica cómo comprobar el elemento de menú y cómo determinar la posición del elemento en el menú. El `nCheck` parámetro puede ser una combinación de **MF_CHECKED** o **MF_UNCHECKED** con **MF_BYPOSITION** o **MF_BYCOMMAND** marcas. Estas marcas se pueden combinar mediante el operador OR bit a bit. Tienen los significados siguientes:  
  
- **MF_BYCOMMAND** especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado.  
  
- **MF_BYPOSITION** especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.  
  
- **MF_CHECKED** actúa como un botón de alternancia con **MF_UNCHECKED** para colocar la marca de verificación predeterminada junto al elemento.  
  
- **MF_UNCHECKED** actúa como un botón de alternancia con **MF_CHECKED** para quitar una marca de verificación junto al elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 El estado anterior del elemento: **MF_CHECKED** o **MF_UNCHECKED**, o 0xFFFFFFFF si no existe el elemento de menú.  
  
### <a name="remarks"></a>Comentarios  
 El `nIDCheckItem` parámetro especifica el elemento que desea modificar.  
  
 El `nIDCheckItem` parámetro puede identificar un elemento de menú emergente, así como un elemento de menú. Se necesita ningún paso especial para comprobar un elemento de menú emergente. No se puede proteger los elementos de menú de nivel superior. Un elemento de menú emergente debe comprobarse por posición, puesto que no tiene un identificador de elemento de menú asociado.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::GetMenuState](#getmenustate).  
  
##  <a name="a-namecheckmenuradioitema--cmenucheckmenuradioitem"></a><a name="checkmenuradioitem"></a>CMenu::CheckMenuRadioItem  
 Comprueba un elemento de menú especificado y lo convierte en un elemento de radio.  
  
```  
BOOL CheckMenuRadioItem(
    UINT nIDFirst,  
    UINT nIDLast,  
    UINT nIDItem,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDFirst`  
 Especifica (como un identificador o el desplazamiento, dependiendo del valor de `nFlags`) el primer elemento de menú en el grupo de botones de radio.  
  
 `nIDLast`  
 Especifica (como un identificador o el desplazamiento, dependiendo del valor de `nFlags`) el último elemento de menú en el grupo de botones de radio.  
  
 `nIDItem`  
 Especifica (como un identificador o el desplazamiento, dependiendo del valor de `nFlags`) del elemento en el grupo que se comprobará con un botón de radio.  
  
 `nFlags`  
 Especifica la interpretación de `nIDFirst`, `nIDLast`, y `nIDItem` de la siguiente manera:  
  
|nFlags|Interpretación|  
|------------|--------------------|  
|**MF_BYCOMMAND**|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el predeterminado si no **MF_BYCOMMAND** ni **MF_BYPOSITION** se establece.|  
|**MF_BYPOSITION**|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.|  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; en caso contrario 0  
  
### <a name="remarks"></a>Comentarios  
 Al mismo tiempo, la función desactiva todos los otros elementos de menú en el grupo asociado y borra la marca de tipo de elemento de la opción para esos elementos. Se muestra el elemento marcado con un mapa de bits de botón (o viñeta) de radio en lugar de un mapa de bits de marca de verificación.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [ON_COMMAND_RANGE](http://msdn.microsoft.com/library/c52719fc-dd6e-48c9-af79-383f48d608e0).  
  
##  <a name="a-namecmenua--cmenucmenu"></a><a name="cmenu"></a>CMenu::CMenu  
 Crea un menú vacío y lo asocia a un `CMenu` objeto.  
  
```  
CMenu();
```  
  
### <a name="remarks"></a>Comentarios  
 El menú no se crea hasta que llame a una de las funciones de miembro create o carga de **CMenu:**  
  
- [CreateMenu](#createmenu)  
  
- [CreatePopupMenu](#createpopupmenu)  
  
- [LoadMenu](#loadmenu)  
  
- [LoadMenuIndirect](#loadmenuindirect)  
  
- [Adjuntar](#attach)  
  
##  <a name="a-namecreatemenua--cmenucreatemenu"></a><a name="createmenu"></a>CMenu::CreateMenu  
 Crea un menú y lo adjunta a la `CMenu` objeto.  
  
```  
BOOL CreateMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el menú se creó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El menú inicialmente está vacío. Se pueden agregar elementos de menú mediante el uso de la `AppendMenu` o `InsertMenu` función miembro.  
  
 Si el menú está asignado a una ventana, se destruye automáticamente cuando se destruye la ventana.  
  
 Antes de salir, la aplicación deberá liberar recursos del sistema asociados a un menú si el menú no está asignado a una ventana. Una aplicación libera un menú llamando a la [DestroyMenu](#destroymenu) función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#22;](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]  
  
##  <a name="a-namecreatepopupmenua--cmenucreatepopupmenu"></a><a name="createpopupmenu"></a>CMenu::CreatePopupMenu  
 Crea un menú emergente y lo adjunta a la `CMenu` objeto.  
  
```  
BOOL CreatePopupMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se creó correctamente el menú emergente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El menú inicialmente está vacío. Se pueden agregar elementos de menú mediante el uso de la `AppendMenu` o `InsertMenu` función miembro. La aplicación puede agregar el menú emergente a un menú existente o un menú emergente. El `TrackPopupMenu` función miembro puede utilizarse para mostrar este menú como menú emergente flotante y realizar un seguimiento de las selecciones en el menú emergente.  
  
 Si el menú está asignado a una ventana, se destruye automáticamente cuando se destruye la ventana. Si el menú se agrega a un menú existente, se destruye automáticamente cuando se destruye dicho menú.  
  
 Antes de salir, la aplicación deberá liberar recursos del sistema asociados con un menú emergente si el menú no está asignado a una ventana. Una aplicación libera un menú llamando a la [DestroyMenu](#destroymenu) función miembro.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::CreateMenu](#createmenu).  
  
##  <a name="a-namedeletemenua--cmenudeletemenu"></a><a name="deletemenu"></a>CMenu:: DeleteMenu  
 Elimina un elemento en el menú.  
  
```  
BOOL DeleteMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPosition`  
 Especifica el elemento de menú que se va a eliminar, según lo determinado por `nFlags`.  
  
 `nFlags`  
 Se usa para interpretar `nPosition` de la siguiente manera:  
  
|nFlags|Interpretación de nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el predeterminado si no **MF_BYCOMMAND** ni **MF_BYPOSITION** se establece.|  
|**MF_BYPOSITION**|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.|  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el elemento de menú tiene un menú emergente asociado, `DeleteMenu` destruye el identificador del menú emergente y libera la memoria utilizada por el menú emergente.  
  
 Cuando un menú que reside en una ventana se cambia (o no se muestra la ventana), la aplicación debe llamar a [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).  
  
##  <a name="a-namedeletetempmapa--cmenudeletetempmap"></a><a name="deletetempmap"></a>CMenu::DeleteTempMap  
 Llama de forma automática el `CWinApp` controlador de tiempo de inactividad, elimina cualquier temporal `CMenu` objetos creados por la [FromHandle](#fromhandle) función miembro.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>Comentarios  
 `DeleteTempMap`Desasocia el objeto de menú de Windows asociado a un temporal `CMenu` objeto antes de eliminar el `CMenu` objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[23 de NVC_MFCWindowing #](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]  
  
##  <a name="a-namedestroymenua--cmenudestroymenu"></a><a name="destroymenu"></a>CMenu::DestroyMenu  
 Destruye el menú y los recursos de Windows que se han utilizado.  
  
```  
BOOL DestroyMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se destruye el menú; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El menú se separa de la `CMenu` objeto antes de ser destruido. Windows `DestroyMenu` función es invocada automáticamente el `CMenu` destructor.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::CreateMenu](#createmenu).  
  
##  <a name="a-namedetacha--cmenudetach"></a><a name="detach"></a>CMenu::Detach  
 Desasocia un menú de Windows desde un `CMenu` de objetos y devuelve el identificador.  
  
```  
HMENU Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de tipo `HMENU`, a un menú de Windows, si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 El `m_hMenu` miembro de datos está establecido en **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[21 NVC_MFCWindowing](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="a-namedrawitema--cmenudrawitem"></a><a name="drawitem"></a>CMenu::DrawItem  
 Llamado por el marco cuando un aspecto visual de los cambios de un menú dibujado por el propietario.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDrawItemStruct`  
 Un puntero a un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) estructura que contiene información sobre el tipo de dibujo necesario.  
  
### <a name="remarks"></a>Comentarios  
 El `itemAction` miembro de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que se realiza. Reemplace esta función miembro para implementar un dibujados por el propietario del dibujo `CMenu` objeto. La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para el contexto de presentación proporcionado en `lpDrawItemStruct` antes de la finalización de esta función miembro.  
  
 Consulte [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) para obtener una descripción de la `DRAWITEMSTRUCT` estructura.  
  
### <a name="example"></a>Ejemplo  
 El código siguiente es de MFC [CTRLTEST](../../visual-cpp-samples.md) ejemplo:  
  
 [!code-cpp[NVC_MFCWindowing&#24;](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]  
  
##  <a name="a-nameenablemenuitema--cmenuenablemenuitem"></a><a name="enablemenuitem"></a>EnableMenuItem  
 Habilita, deshabilita o un elemento de menú, se atenúa.  
  
```  
UINT EnableMenuItem(
    UINT nIDEnableItem,  
    UINT nEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 *nIDEnableItem*  
 Especifica el elemento de menú que está habilitada, según lo determinado por `nEnable`. Este parámetro puede especificar elementos de menú emergente, así como elementos de menú estándar.  
  
 `nEnable`  
 Especifica la acción que se realizará. Puede ser una combinación de **MF_DISABLED**, `MF_ENABLED`, o **MF_GRAYED**, con **MF_BYCOMMAND** o **MF_BYPOSITION**. Estos valores pueden combinarse mediante el operador OR bit a bit. Estos valores tienen los significados siguientes:  
  
- **MF_BYCOMMAND** especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado.  
  
- **MF_BYPOSITION** especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.  
  
- **MF_DISABLED** deshabilita el elemento de menú para que no se puede seleccionar, pero no lo dim.  
  
- `MF_ENABLED`Habilita el elemento de menú para que se pueden seleccionar y restaura su estado atenuado.  
  
- **MF_GRAYED** deshabilita el elemento de menú para que se atenúa y no se pueden seleccionar.  
  
### <a name="return-value"></a>Valor devuelto  
 Estado anterior ( **MF_DISABLED**, `MF_ENABLED`, o **MF_GRAYED**) o –&1; si no es válido.  
  
### <a name="remarks"></a>Comentarios  
 El [CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu), y [LoadMenuIndirect](#loadmenuindirect) funciones miembro también pueden establecer el estado (habilitado, deshabilitado o atenuado) de un elemento de menú.  
  
 Mediante la **MF_BYPOSITION** valor requiere una aplicación para usar el valor correcto `CMenu`. Si el `CMenu` del menú se usa la barra, depende de un elemento de menú de nivel superior (un elemento en la barra de menús). Para establecer el estado de un elemento en un menú emergente de elementos emergente o anidado por posición, una aplicación debe especificar el `CMenu` del menú emergente.  
  
 Cuando se especifica una aplicación el **MF_BYCOMMAND** marca, Windows comprueba todos los elementos de menú emergente que pertenecen a la `CMenu`; por lo tanto, a menos que existen elementos de menú duplicados, usando el `CMenu` del menú barra es suficiente.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#25;](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]  
  
##  <a name="a-namefromhandlea--cmenufromhandle"></a><a name="fromhandle"></a>CMenu::FromHandle  
 Devuelve un puntero a un `CMenu` objeto, dados un identificador de Windows a un menú.  
  
```  
static CMenu* PASCAL FromHandle(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 `hMenu`  
 Identificador de Windows de un menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CMenu` que puede ser temporal o permanente.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CMenu` objeto no está asociado al objeto de menú de Windows, un archivo temporal `CMenu` objeto creado y conectado.  
  
 Este temporal `CMenu` objeto solo es válido hasta la próxima vez que la aplicación tiene el tiempo de inactividad en el bucle de eventos, en qué momento se eliminan todos los objetos temporales.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::CreateMenu](#createmenu).  
  
##  <a name="a-namegetdefaultitema--cmenugetdefaultitem"></a><a name="getdefaultitem"></a>CMenu::GetDefaultItem  
 Determina el elemento de menú predeterminado en el menú especificado.  
  
```  
UINT GetDefaultItem(
    UINT gmdiFlags,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 *gmdiFlags*  
 Valor que especifica cómo la función busca elementos de menú. Este parámetro puede ser ninguno, uno o una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|**GMDI_GOINTOPOPUPS**|Especifica que, si el elemento predeterminado es uno que se abre un submenú, la función Buscar de forma recursiva en el submenú correspondiente. Si el submenú no tiene ningún elemento de forma predeterminada, el valor devuelto identifica el elemento que se abre el submenú.<br /><br /> De forma predeterminada, la función devuelve el primer elemento de forma predeterminada en el menú especificado, independientemente de si es un elemento que se abre un submenú.|  
|**GMDI_USEDISABLED**|Especifica que la función es devolver un elemento predeterminado, incluso si está deshabilitado.<br /><br /> De forma predeterminada, la función omite los elementos deshabilitados o no accesible.|  
  
 `fByPos`  
 Valor que especifica si se debe recuperar el identificador del elemento de menú o su posición. Si este parámetro es **FALSE**, se devuelve el identificador. De lo contrario, se devuelve la posición.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es el identificador o la posición del elemento de menú. Si se produce un error en la función, el valor devuelto es - 1.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento de la función de Win32 [GetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647976), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="a-namegetmenucontexthelpida--cmenugetmenucontexthelpid"></a><a name="getmenucontexthelpid"></a>CMenu::GetMenuContextHelpId  
 Recupera el identificador asociado a la Ayuda contextual `CMenu`.  
  
```  
DWORD GetMenuContextHelpId() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador asociado actualmente a la Ayuda contextual `CMenu` si existe; de lo contrario, cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="a-namegetmenuinfoa--cmenugetmenuinfo"></a><a name="getmenuinfo"></a>CMenu::GetMenuInfo  
 Recupera información de un menú.  
  
```  
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpcmi`  
 Un puntero a un [MENUINFO](http://msdn.microsoft.com/library/windows/desktop/ms647575) estructura que contiene información sobre el menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es distinto de cero; de lo contrario, el valor devuelto es cero.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar información sobre el menú.  
  
##  <a name="a-namegetmenuitemcounta--cmenugetmenuitemcount"></a><a name="getmenuitemcount"></a>CMenu::GetMenuItemCount  
 Determina el número de elementos de un menú emergente o de nivel superior.  
  
```  
UINT GetMenuItemCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en el menú si la función se realiza correctamente; de lo contrario,-1.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).  
  
##  <a name="a-namegetmenuitemida--cmenugetmenuitemid"></a><a name="getmenuitemid"></a>CMenu::GetMenuItemID  
 Obtiene el identificador de elemento de menú para un elemento de menú situado en la posición definida por `nPos`.  
  
```  
UINT GetMenuItemID(int nPos) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 Especifica la posición (basado en cero) del elemento de menú cuyo identificador se está recuperando.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del elemento para el elemento especificado en un menú emergente, si la función se realiza correctamente. Si el elemento especificado es un menú emergente (en lugar de un elemento en el menú emergente), el valor devuelto será –&1;. Si `nPos` corresponde a una **separador** elemento de menú, el valor devuelto es 0.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="a-namegetmenuiteminfoa--cmenugetmenuiteminfo"></a><a name="getmenuiteminfo"></a>CMenu::GetMenuItemInfo  
 Recupera información sobre un elemento de menú.  
  
```  
BOOL GetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `uItem`  
 Identificador o la posición del elemento de menú para obtener información acerca de. El significado de este parámetro depende del valor de `ByPos`.  
  
 `lpMenuItemInfo`  
 Un puntero a un [MENUITEMINFO](http://msdn.microsoft.com/library/windows/desktop/ms647578), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)], que contiene información sobre el menú.  
  
 `fByPos`  
 Valor que especifica el significado de `nIDItem`. De forma predeterminada, `ByPos` es **FALSE**, lo que indica que uItem es un identificador de elemento de menú. Si `ByPos` no está establecido en **FALSE**, indica una posición del elemento de menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es distinto de cero. Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, utilice la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento de la de la función de Win32 [GetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms647980), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Tenga en cuenta que en la implementación de MFC de `GetMenuItemInfo`, no se usa un identificador de un menú.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_MFCWindowing #](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]  
  
##  <a name="a-namegetmenustatea--cmenugetmenustate"></a><a name="getmenustate"></a>CMenu::GetMenuState  
 Devuelve el estado del elemento de menú especificado o el número de elementos de un menú emergente.  
  
```  
UINT GetMenuState(
    UINT nID,  
    UINT nFlags) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 Especifica el identificador del elemento de menú, según lo determinado por `nFlags`.  
  
 `nFlags`  
 Especifica la naturaleza de `nID`. Puede ser uno de los siguientes valores:  
  
- **MF_BYCOMMAND** especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el valor predeterminado.  
  
- **MF_BYPOSITION** especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor 0xFFFFFFFF si el elemento especificado no existe. Si *nId* identifica un menú emergente, el byte de orden superior contiene el número de elementos en el menú emergente y el byte de orden inferior contiene los indicadores de menú asociados con el menú emergente. De lo contrario, el valor devuelto es una máscara (o booleano) de los valores de la lista siguiente (esta máscara describe el estado del menú de elemento que *nId* identifica):  
  
- **MF_CHECKED** actúa como un botón de alternancia con **MF_UNCHECKED** para colocar la marca de verificación predeterminada junto al elemento. Cuando la aplicación proporciona los mapas de bits de la marca de verificación (consulte la `SetMenuItemBitmaps` función miembro), se muestra el mapa de bits "marca de verificación en".  
  
- **MF_DISABLED** deshabilita el elemento de menú para que no se puede seleccionar, pero no lo dim.  
  
- `MF_ENABLED`Habilita el elemento de menú para que se pueden seleccionar y restaura su estado atenuado. Tenga en cuenta que el valor de esta constante es 0; una aplicación no debe probar en 0 para el error cuando se utiliza este valor.  
  
- **MF_GRAYED** deshabilita el elemento de menú para que se atenúa y no se pueden seleccionar.  
  
- **MF_MENUBARBREAK** coloca el elemento en una nueva línea en un menú estático o en una nueva columna en los menús emergentes. Una línea divisoria vertical separará la nueva columna de menú emergente de la columna antigua.  
  
- **MF_MENUBREAK** coloca el elemento en una nueva línea en un menú estático o en una nueva columna en los menús emergentes. No se coloca ninguna línea divisoria entre las columnas.  
  
- **MF_SEPARATOR** dibuja una línea de división horizontal. Sólo puede utilizarse en un menú emergente. Esta línea no aparecen atenuada, deshabilitada o resaltada. Se omiten los otros parámetros.  
  
- **MF_UNCHECKED** actúa como un botón de alternancia con **MF_CHECKED** para quitar una marca de verificación junto al elemento. Cuando la aplicación proporciona los mapas de bits de la marca de verificación (consulte la `SetMenuItemBitmaps` función miembro), se muestra el mapa de bits de "marca de verificación de desactivar". Tenga en cuenta que el valor de esta constante es 0; una aplicación no debe probar en 0 para el error cuando se utiliza este valor.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing Nº&27;](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]  
  
##  <a name="a-namegetmenustringa--cmenugetmenustring"></a><a name="getmenustring"></a>CMenu::GetMenuString  
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
 `nIDItem`  
 Especifica el identificador entero del elemento de menú o el desplazamiento del elemento de menú en el menú, dependiendo del valor de `nFlags`.  
  
 `lpString`  
 Señala al búfer que va a recibir la etiqueta.  
  
 `rString`  
 Una referencia a un `CString` objeto que va a recibir la cadena copiada de menú.  
  
 `nMaxCount`  
 Especifica la longitud máxima (en caracteres) de la etiqueta que se va a copiar. Si la etiqueta es mayor que el máximo especificado en `nMaxCount`, se truncan los caracteres adicionales.  
  
 `nFlags`  
 Especifica la interpretación de la `nIDItem` parámetro. Puede ser uno de los siguientes valores:  
  
|nFlags|Interpretación de nIDItem|  
|------------|-------------------------------|  
|**MF_BYCOMMAND**|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el predeterminado si no **MF_BYCOMMAND** ni **MF_BYPOSITION** se establece.|  
|**MF_BYPOSITION**|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.|  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica el número real de caracteres copiados en el búfer, no incluido el terminador null.  
  
### <a name="remarks"></a>Comentarios  
 El `nMaxCount` parámetro debe ser mayor que el número de caracteres de la etiqueta para acomodar el carácter null que finaliza una cadena de uno.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="a-namegetsafehmenua--cmenugetsafehmenu"></a><a name="getsafehmenu"></a>CMenu::GetSafeHmenu  
 Devuelve el `HMENU` contenido en este `CMenu` objeto, o un **NULL** `CMenu` puntero.  
  
```  
HMENU GetSafeHmenu() const;  
```  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::LoadMenu](#loadmenu).  
  
##  <a name="a-namegetsubmenua--cmenugetsubmenu"></a><a name="getsubmenu"></a>CMenu::GetSubMenu  
 Recupera el `CMenu` objeto de un menú emergente.  
  
```  
CMenu* GetSubMenu(int nPos) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 Especifica la posición del menú emergente contenido en el menú. Valores de posición comienzan en 0 para el primer elemento de menú. No se puede usar el identificador del menú emergente en esta función.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CMenu` cuyos `m_hMenu` miembro contiene un identificador del menú emergente si ya existe un menú emergente en la posición especificada; en caso contrario **NULL**. Si un `CMenu` objeto no existe, se creará uno temporal. El `CMenu` no se debe almacenar el puntero devuelto.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::TrackPopupMenu](#trackpopupmenu).  
  
##  <a name="a-nameinsertmenua--cmenuinsertmenu"></a><a name="insertmenu"></a>CMenu::InsertMenu  
 Inserta un nuevo elemento de menú en la posición especificada por `nPosition` y mueve otros elementos del menú desplegable.  
  
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
 `nPosition`  
 Especifica el elemento de menú antes de que el nuevo elemento de menú es va a insertar. El `nFlags` parámetro se puede utilizar para interpretar `nPosition` de las maneras siguientes:  
  
|nFlags|Interpretación de nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el predeterminado si no **MF_BYCOMMAND** ni **MF_BYPOSITION** se establece.|  
|**MF_BYPOSITION**|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0. Si `nPosition` es -1, el nuevo elemento de menú se anexa al final del menú.|  
  
 `nFlags`  
 Especifica cómo `nPosition` se interpreta y se especifica información sobre el estado del nuevo elemento de menú cuando se agrega al menú. Para obtener una lista de las marcas que se pueden establecer, consulte el [AppendMenu](#appendmenu) función miembro. Para especificar más de un valor, utilice el operador OR bit a bit para combinarlos con el **MF_BYCOMMAND** o **MF_BYPOSITION** marca.  
  
 `nIDNewItem`  
 Especifica el identificador de comando del elemento de menú nuevo o, si `nFlags` está establecido en **MF_POPUP**, el identificador de menú ( `HMENU`) del menú emergente. El `nIDNewItem` parámetro se omite (no es necesario) si `nFlags` está establecido en **MF_SEPARATOR**.  
  
 `lpszNewItem`  
 Especifica el contenido del nuevo elemento de menú. `nFlags`se puede utilizar para interpretar `lpszNewItem` de las maneras siguientes:  
  
|nFlags|Interpretación de lpszNewItem|  
|------------|-----------------------------------|  
|`MF_OWNERDRAW`|Contiene un valor de 32 bits proporcionada por la aplicación que la aplicación puede usar para mantener datos adicionales asociados con el elemento de menú. Este valor de 32 bits está disponible para la aplicación en la **itemData** miembro de la estructura proporcionada por el [WM_MEASUREITEM](http://msdn.microsoft.com/library/windows/desktop/bb775925) y [WM_DRAWITEM](http://msdn.microsoft.com/library/windows/desktop/bb775923) mensajes. Estos mensajes se envían cuando el elemento de menú se muestra inicialmente o se cambia.|  
|**MF_STRING**|Contiene un puntero largo a una cadena terminada en null. Se trata de la interpretación predeterminada.|  
|**MF_SEPARATOR**|El `lpszNewItem` parámetro se omite (no es necesario).|  
  
 *pBmp*  
 Apunta a un `CBitmap` objeto que se usará como el elemento de menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 La aplicación puede especificar el estado del elemento de menú estableciendo valores en `nFlags`.  
  
 Cuando un menú que reside en una ventana se cambia (o no se muestra la ventana), la aplicación debe llamar a `CWnd::DrawMenuBar`.  
  
 Cuando `nIDNewItem` especifica un menú emergente, se convierte en parte del menú en el que se inserta. Si se destruye dicho menú, también se destruirá el menú insertado. Se debería desasociar un menú insertado un `CMenu` objeto para evitar el conflicto.  
  
 Si el activo se maximiza la ventana secundaria MDI (interfaz) de varios documentos y una aplicación inserta un menú emergente en el menú de la aplicación MDI llamando a esta función y especificando el **MF_BYPOSITION** marca, el menú es insertar una posición más hacia la izquierda de lo esperado. Esto sucede porque el menú Control de la ventana secundaria MDI activa se inserta en la primera posición de la barra de menús de la ventana de marco MDI. Para colocar el menú correctamente, la aplicación debe agregar 1 al valor de posición que se utilizará en caso contrario. Una aplicación puede utilizar el **WM_MDIGETACTIVE** mensaje para determinar si está maximizada la ventana secundaria activa actualmente.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#28;](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]  
  
##  <a name="a-nameinsertmenuitema--cmenuinsertmenuitem"></a><a name="insertmenuitem"></a>CMenu::InsertMenuItem  
 Inserta un nuevo elemento de menú en la posición especificada en un menú.  
  
```  
BOOL InsertMenuItem(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `uItem`  
 Consulte la descripción de `uItem` en [InsertMenuItem](http://msdn.microsoft.com/library/windows/desktop/ms647988) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `lpMenuItemInfo`  
 Consulte la descripción de `lpmii` en **InsertMenuItem** en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `fByPos`  
 Consulte la descripción de `fByPosition` en **InsertMenuItem** en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Esta función contiene [InsertMenuItem](http://msdn.microsoft.com/library/windows/desktop/ms647988), descrita en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameloadmenua--cmenuloadmenu"></a><a name="loadmenu"></a>CMenu::LoadMenu  
 Carga un recurso de menú de archivo ejecutable de la aplicación y lo adjunta a la `CMenu` objeto.  
  
```  
BOOL LoadMenu(LPCTSTR lpszResourceName);  
BOOL LoadMenu(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszResourceName`  
 Apunta a una cadena terminada en null que contiene el nombre del recurso de menú cargar.  
  
 `nIDResource`  
 Especifica el identificador del menú del recurso de menú cargar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el recurso de menú se ha cargado correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Antes de salir, la aplicación deberá liberar recursos del sistema asociados a un menú si el menú no está asignado a una ventana. Una aplicación libera un menú llamando a la [DestroyMenu](#destroymenu) función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#29;](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]  
  
##  <a name="a-nameloadmenuindirecta--cmenuloadmenuindirect"></a><a name="loadmenuindirect"></a>CMenu::LoadMenuIndirect  
 Carga un recurso desde una plantilla de menú en la memoria y lo adjunta a la `CMenu` objeto.  
  
```  
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpMenuTemplate*  
 Señala a una plantilla de menú (que es una sola [MENUITEMTEMPLATEHEADER](http://msdn.microsoft.com/library/windows/desktop/ms647583) estructura y una colección de uno o varios [MENUITEMTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms647581) estructuras). Para obtener más información sobre estas dos estructuras, vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el recurso de menú se ha cargado correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Una plantilla de menú es un encabezado seguido de una colección de uno o varios [MENUITEMTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms647581) estructuras, cada uno de los cuales puede contener uno o más elementos de menú y menús emergentes.  
  
 El número de versión debe ser 0.  
  
 El **mtOption** deben incluir indicadores **MF_END** para el último elemento en una lista emergente y para el último elemento de la lista principal. Consulte la `AppendMenu` la función miembro de otros indicadores. El **mtId** miembro se debe omitir desde el **MENUITEMTEMPLATE** estructura cuando **MF_POPUP** se especifica en **mtOption**.  
  
 El espacio asignado para el **MENUITEMTEMPLATE** estructura debe ser lo suficientemente grande como para **mtString** para contener el nombre del elemento de menú como una cadena terminada en null.  
  
 Antes de salir, la aplicación deberá liberar recursos del sistema asociados a un menú si el menú no está asignado a una ventana. Una aplicación libera un menú llamando a la [DestroyMenu](#destroymenu) función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing Nº&30;](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]  
  
##  <a name="a-namemhmenua--cmenumhmenu"></a><a name="m_hmenu"></a>CMenu::m_hMenu  
 Especifica la `HMENU` identificador del menú Windows conectado a la `CMenu` objeto.  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::LoadMenu](#loadmenu).  
  
##  <a name="a-namemeasureitema--cmenumeasureitem"></a><a name="measureitem"></a>CMenu::MeasureItem  
 Lo llama el marco de trabajo cuando se crea un menú con el estilo de dibujo del propietario.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMeasureItemStruct`  
 Un puntero a un `MEASUREITEMSTRUCT` estructura.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro y rellene el `MEASUREITEMSTRUCT` estructura para informar a Windows de dimensiones del menú.  
  
 Consulte [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) para obtener una descripción de la `MEASUREITEMSTRUCT` estructura.  
  
### <a name="example"></a>Ejemplo  
 El código siguiente es de MFC [CTRLTEST](../../visual-cpp-samples.md) ejemplo:  
  
 [!code-cpp[NVC_MFCWindowing&#31;](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]  
  
##  <a name="a-namemodifymenua--cmenumodifymenu"></a><a name="modifymenu"></a>CMenu::ModifyMenu  
 Cambia un elemento de menú existente en la posición especificada por `nPosition`.  
  
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
 `nPosition`  
 Especifica el elemento de menú que se va a cambiar. El `nFlags` parámetro se puede utilizar para interpretar `nPosition` de las maneras siguientes:  
  
|nFlags|Interpretación de nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el predeterminado si no **MF_BYCOMMAND** ni **MF_BYPOSITION** se establece.|  
|**MF_BYPOSITION**|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.|  
  
 `nFlags`  
 Especifica cómo `nPosition` se interpreta y se proporciona información acerca de los cambios que se realizan en el elemento de menú. Para obtener una lista de marcas que se pueden establecer, consulte el [AppendMenu](#appendmenu) función miembro.  
  
 `nIDNewItem`  
 Especifica el identificador de comando del elemento de menú modificado o, si `nFlags` está establecido en **MF_POPUP**, el identificador de menú ( `HMENU`) de un menú emergente. El `nIDNewItem` parámetro se omite (no es necesario) si `nFlags` está establecido en **MF_SEPARATOR**.  
  
 `lpszNewItem`  
 Especifica el contenido del nuevo elemento de menú. El `nFlags` parámetro se puede utilizar para interpretar `lpszNewItem` de las maneras siguientes:  
  
|nFlags|Interpretación de lpszNewItem|  
|------------|-----------------------------------|  
|`MF_OWNERDRAW`|Contiene un valor de 32 bits proporcionada por la aplicación que la aplicación puede usar para mantener datos adicionales asociados con el elemento de menú. Este valor de 32 bits está disponible para la aplicación cuando procesa **MF_MEASUREITEM** y **MF_DRAWITEM**.|  
|**MF_STRING**|Contiene un puntero largo a una cadena terminada en null o en una `CString`.|  
|**MF_SEPARATOR**|El `lpszNewItem` parámetro se omite (no es necesario).|  
  
 *pBmp*  
 Apunta a un `CBitmap` objeto que se usará como el elemento de menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 La aplicación especifica el nuevo estado del elemento de menú estableciendo valores en `nFlags`. Si esta función reemplaza un menú emergente asociado al elemento de menú, destruye el menú emergente antiguo y libera la memoria utilizada por el menú emergente.  
  
 Cuando `nIDNewItem` especifica un menú emergente, se convierte en parte del menú en el que se inserta. Si se destruye dicho menú, también se destruirá el menú insertado. Se debería desasociar un menú insertado un `CMenu` objeto para evitar el conflicto.  
  
 Cuando un menú que reside en una ventana se cambia (o no se muestra la ventana), la aplicación debe llamar a `CWnd::DrawMenuBar`. Para cambiar los atributos de los elementos de menú existentes, es mucho más rápido utilizar el `CheckMenuItem` y `EnableMenuItem` funciones miembro.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="a-nameoperatorhmenua--cmenuoperator-hmenu"></a><a name="operator_hmenu"></a>CMenu::operator HMENU  
 Utilice este operador para recuperar el identificador de la `CMenu` objeto.  
  
```  
operator HMENU() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el identificador de la `CMenu` objeto; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar el controlador para llamar directamente a las API de Windows.  
  
##  <a name="a-nameoperatorneqa--cmenuoperator-"></a><a name="operator_neq"></a>CMenu::operator! =  
 Determina si dos menús lógicamente no son iguales.  
  
```  
BOOL operator!=(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `menu`  
 Un `CMenu` objeto para la comparación.  
  
### <a name="remarks"></a>Comentarios  
 Comprueba si un objeto de menú en el lado izquierdo no es igual a un objeto de menú en el lado derecho.  
  
##  <a name="a-nameoperatoreqeqa--cmenuoperator-"></a><a name="operator_eq_eq"></a>CMenu::operator ==  
 Determina si dos menús son lógicamente iguales.  
  
```  
BOOL operator==(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `menu`  
 Un `CMenu` objeto para la comparación.  
  
### <a name="remarks"></a>Comentarios  
 Comprueba si un objeto de menú en el lado izquierdo es igual (en términos de la `HMENU` valor) a un objeto de menú en el lado derecho.  
  
##  <a name="a-nameremovemenua--cmenuremovemenu"></a><a name="removemenu"></a>CMenu::RemoveMenu  
 Elimina un elemento de menú con un menú emergente asociado en el menú.  
  
```  
BOOL RemoveMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPosition`  
 Especifica el elemento de menú que se va a quitar. El `nFlags` parámetro se puede utilizar para interpretar `nPosition` de las maneras siguientes:  
  
|nFlags|Interpretación de nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el predeterminado si no **MF_BYCOMMAND** ni **MF_BYPOSITION** se establece.|  
|**MF_BYPOSITION**|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.|  
  
 `nFlags`  
 Especifica cómo `nPosition` se interpreta.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 No destruye el identificador de un menú emergente, por lo que se puede reutilizar el menú. Antes de llamar a esta función, la aplicación puede llamar a la `GetSubMenu` función miembro para recuperar el elemento emergente `CMenu` objeto para su reutilización.  
  
 Cuando un menú que reside en una ventana se cambia (o no se muestra la ventana), la aplicación debe llamar a `CWnd::DrawMenuBar`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="a-namesetdefaultitema--cmenusetdefaultitem"></a><a name="setdefaultitem"></a>CMenu::SetDefaultItem  
 Establece el elemento de menú predeterminado para el menú especificado.  
  
```  
BOOL SetDefaultItem(
    UINT uItem,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `uItem`  
 Identificador o la posición del nuevo elemento de menú predeterminado o - 1 para ningún elemento predeterminado. El significado de este parámetro depende del valor de `fByPos`.  
  
 `fByPos`  
 Valor que especifica el significado de `uItem`. Si este parámetro es **FALSE**, `uItem` es un identificador de elemento de menú. De lo contrario, es una posición de elemento de menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es distinto de cero. Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, utilice la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento de la función de Win32 [SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="a-namesetmenucontexthelpida--cmenusetmenucontexthelpid"></a><a name="setmenucontexthelpid"></a>CMenu::SetMenuContextHelpId  
 Asocia un identificador de contexto de ayuda con `CMenu`.  
  
```  
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwContextHelpId`  
 Id. de ayuda contextual para asociar `CMenu`.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; en caso contrario 0  
  
### <a name="remarks"></a>Comentarios  
 Todos los elementos en el menú compartan este identificador, no es posible adjuntar un identificador de contexto de ayuda a los elementos de menú individuales.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="a-namesetmenuinfoa--cmenusetmenuinfo"></a><a name="setmenuinfo"></a>CMenu::SetMenuInfo  
 Establece la información de un menú.  
  
```  
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpcmi`  
 Un puntero a un [MENUINFO](http://msdn.microsoft.com/library/windows/desktop/ms647575) estructura que contiene información sobre el menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es distinto de cero; de lo contrario, el valor devuelto es cero.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para definir información específica sobre el menú.  
  
##  <a name="a-namesetmenuitembitmapsa--cmenusetmenuitembitmaps"></a><a name="setmenuitembitmaps"></a>CMenu::SetMenuItemBitmaps  
 Los mapas de bits especificado se asocia con un elemento de menú.  
  
```  
BOOL SetMenuItemBitmaps(
    UINT nPosition,  
    UINT nFlags,  
    const CBitmap* pBmpUnchecked,  
    const CBitmap* pBmpChecked);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPosition`  
 Especifica el elemento de menú que se va a cambiar. El `nFlags` parámetro se puede utilizar para interpretar `nPosition` de las maneras siguientes:  
  
|nFlags|Interpretación de nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Especifica que el parámetro proporciona el identificador de comando del elemento de menú existente. Este es el predeterminado si no **MF_BYCOMMAND** ni **MF_BYPOSITION** se establece.|  
|**MF_BYPOSITION**|Especifica que el parámetro indica la posición del elemento de menú existente. Es el primer elemento en la posición 0.|  
  
 `nFlags`  
 Especifica cómo `nPosition` se interpreta.  
  
 `pBmpUnchecked`  
 Especifica el mapa de bits que se utilizará para los elementos de menú que no estén protegidos.  
  
 `pBmpChecked`  
 Especifica el mapa de bits que se utilizará para los elementos de menú que se comprueban.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el elemento de menú está activada o desactivada, Windows muestra el mapa de bits correspondiente situada junto al elemento de menú.  
  
 Si el valor `pBmpUnchecked` o `pBmpChecked` es **NULL**, a continuación, Windows no muestra nada al lado del elemento de menú para el atributo correspondiente. Si ambos parámetros son **NULL**, Windows utiliza la marca de verificación de forma predeterminada, cuando el elemento está activado y quita la marca de verificación cuando el elemento está desactivado.  
  
 Cuando se destruye el menú, no se destruyen estos mapas de bits; la aplicación debe destruir.  
  
 Windows **GetMenuCheckMarkDimensions** función recupera las dimensiones de la marca de verificación predeterminado usado para los elementos de menú. La aplicación utiliza estos valores para determinar el tamaño adecuado de los mapas de bits que se suministra con esta función. Obtener el tamaño, crear los mapas de bits y, a continuación, establecerlos.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#32;](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing Nº&33;](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]  
  
##  <a name="a-namesetmenuiteminfoa--cmenusetmenuiteminfo"></a><a name="setmenuiteminfo"></a>CMenu::SetMenuItemInfo  
 Cambia la información sobre un elemento de menú.  
  
```  
BOOL SetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `uItem`  
 Consulte la descripción de `uItem` en [SetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms648001) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `lpMenuItemInfo`  
 Consulte la descripción de `lpmii` en **SetMenuItemInfo** en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `fByPos`  
 Consulte la descripción de `fByPosition` en **SetMenuItemInfo** en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Esta función contiene [SetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms648001), descrita en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nametrackpopupmenua--cmenutrackpopupmenu"></a><a name="trackpopupmenu"></a>CMenu::TrackPopupMenu  
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
 `nFlags`  
 Especifica los marcadores de posición de la pantalla y la posición del mouse. Consulte [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) para obtener una lista de los indicadores disponibles.  
  
 *x*  
 Especifica la posición horizontal, en coordenadas de pantalla del menú emergente. Dependiendo del valor de la `nFlags` parámetro, el menú puede ser alineado a la izquierda, alineado a la derecha o centrada con respecto a esta posición.  
  
 *y*  
 Especifica la posición vertical, en coordenadas de pantalla de la parte superior del menú en la pantalla.  
  
 `pWnd`  
 Identifica la ventana que posee el menú emergente. Este parámetro no puede ser **NULL**, incluso si la **TPM_NONOTIFY** se especifica la marca. Esta ventana recibe todos **WM_COMMAND** mensajes en el menú. En las versiones 3.1 y versiones posteriores de Windows, la ventana de recepción no **WM_COMMAND** mensajes hasta que `TrackPopupMenu` devuelve. En Windows 3.0, la ventana recibe **WM_COMMAND** mensajes antes de `TrackPopupMenu` devuelve.  
  
 `lpRect`  
 ignorado.  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve el resultado de llamar al método [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Un menú emergente flotante puede aparecer en cualquier parte en la pantalla.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#34;](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]  
  
##  <a name="a-nametrackpopupmenuexa--cmenutrackpopupmenuex"></a><a name="trackpopupmenuex"></a>CMenu::TrackPopupMenuEx  
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
 `fuFlags`  
 Especifica diversas funciones para el menú extendido. Para obtener una lista de todos los valores y su significado, consulte [TrackPopupMenuEx](http://msdn.microsoft.com/library/windows/desktop/ms648003).  
  
 *x*  
 Especifica la posición horizontal, en coordenadas de pantalla del menú emergente.  
  
 *y*  
 Especifica la posición vertical, en coordenadas de pantalla de la parte superior del menú en la pantalla.  
  
 `pWnd`  
 Puntero a la ventana propietaria del menú emergente y recibir los mensajes en el menú creado. Esta ventana puede ser cualquiera de las ventanas de la aplicación actual pero no puede ser **NULL**. Si especifica **TPM_NONOTIFY** en el `fuFlags` parámetro, la función no enviará mensajes a `pWnd`. La función debe devolver para la ventana señalada `pWnd` para recibir el **WM_COMMAND** mensaje.  
  
 *lptpm*  
 Puntero a un [TPMPARAMS](http://msdn.microsoft.com/library/windows/desktop/ms647586) estructura que especifica el área de la pantalla, el menú no debe superponerse. Este parámetro puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Si especifica **TPM_RETURNCMD** en el `fuFlags` parámetro, el valor devuelto es el identificador del elemento de menú del elemento seleccionado por el usuario. Si el usuario cancela el menú sin realizar una selección, o si se produce un error, el valor devuelto es 0.  
  
 Si no se especifica **TPM_RETURNCMD** en el `fuFlags` parámetro, el valor devuelto es distinto de cero si la función se realiza correctamente y 0 si se produce un error. Para obtener información de error extendida, llame a [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Comentarios  
 Un menú emergente flotante puede aparecer en cualquier parte en la pantalla. Para obtener más información sobre cómo controlar los errores al crear el menú emergente, vea [TrackPopupMenuEx](http://msdn.microsoft.com/library/windows/desktop/ms648003).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC CTRLTEST](../../visual-cpp-samples.md)   
 [Ejemplo de MFC DYNAMENU](../../visual-cpp-samples.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)

