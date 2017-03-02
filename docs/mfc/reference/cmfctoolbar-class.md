---
title: Clase CMFCToolBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBar
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBar class
ms.assetid: e7679c01-fb94-44c0-98c6-3af955292fb5
caps.latest.revision: 48
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
ms.openlocfilehash: a34997b4b68ddcc8f42869466f17d67f32141d7c
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbar-class"></a>Clase CMFCToolBar
El `CMFCToolBar` clase es similar a [CToolBar (clase)](../../mfc/reference/ctoolbar-class.md), pero proporciona compatibilidad adicional para las características de la interfaz de usuario. Se incluyen las barras de herramientas planas, las barras de herramientas con imágenes activas, los iconos grandes, los botones de buscapersonas, las barras de herramientas bloqueadas, los controles rebar, el texto en imágenes, las imágenes de fondo y las barras de herramientas con pestañas. La clase `CMFCToolBar` también contiene compatibilidad integrada para la personalización de usuario de barras de herramientas y menús, arrastrar y colocar entre las barras de herramientas y menús, botones del cuadro combinado, botones del cuadro de edición, selectores de colores y botones acumulados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCToolBar : public CMFCBaseToolBar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCToolBar::CMFCToolBar`|Constructor predeterminado.|  
|`CMFCToolBar::~CMFCToolBar`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBar::AddBasicCommand](#addbasiccommand)|Agrega un comando de menú a la lista de comandos que siempre se muestran cuando un usuario abre un menú.|  
|[CMFCToolBar::AddCommandUsage](#addcommandusage)|Se incrementa en uno el contador que está asociado al comando especificado.|  
|[CMFCToolBar::AddToolBarForImageCollection](#addtoolbarforimagecollection)|Agrega imágenes de los recursos de la interfaz de usuario a la colección de imágenes en la aplicación.|  
|[CMFCToolBar::AdjustLayout](#adjustlayout)|Vuelve a calcular el tamaño y la posición de una barra de herramientas. (Invalida [CBasePane::AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout)).|  
|[CMFCToolBar::AdjustSize](#adjustsize)|Vuelve a calcular el tamaño de la barra de herramientas.|  
|[CMFCToolBar::AllowChangeTextLabels](#allowchangetextlabels)|Especifica si se pueden mostrar etiquetas de texto en imágenes en los botones de barra de herramientas.|  
|[CMFCToolBar::AreTextLabels](#aretextlabels)|Especifica si las etiquetas de texto en imágenes se muestran actualmente en los botones de barra de herramientas.|  
|[CMFCToolBar::AutoGrayInactiveImages](#autograyinactiveimages)|Habilita o deshabilita la generación automática de imágenes de botón inactiva.|  
|[CMFCToolBar::ButtonToIndex](#buttontoindex)|Devuelve el índice de un objeto [CMFCToolBarButton clase](../../mfc/reference/cmfctoolbarbutton-class.md) objeto en esta barra de herramientas.|  
|[CMFCToolBar::CalcFixedLayout](#calcfixedlayout)|Calcula el tamaño horizontal de la barra de herramientas. (Invalida [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCToolBar::CalcSize](#calcsize)|Llamado por el marco como parte del proceso de cálculo de diseño. (Invalida [CPane::CalcSize](../../mfc/reference/cpane-class.md#calcsize).)|  
|[CMFCToolBar::CanHandleSiblings](#canhandlesiblings)|Determina si la barra de herramientas y sus elementos relacionados están colocados en el mismo panel.|  
|[CMFCToolBar::CleanUpImages](#cleanupimages)|Libera los recursos de sistema asignados para las imágenes de la barra de herramientas.|  
|[CMFCToolBar::CleanUpLockedImages](#cleanuplockedimages)|Libera los recursos de sistema asignados para las imágenes bloqueadas de la barra de herramientas.|  
|[CMFCToolBar::CanBeClosed](#canbeclosed)|Especifica si un usuario puede cerrar la barra de herramientas. (Invalida [CBasePane::CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed).)|  
|[CMFCToolBar::CanBeRestored](#canberestored)|Determina si el sistema puede restaurar una barra de herramientas a su estado original después de la personalización.|  
|[CMFCToolBar::CanFocus](#canfocus)|Especifica si el panel puede recibir el foco. (Invalida [CBasePane::CanFocus](../../mfc/reference/cbasepane-class.md#canfocus).)|  
|[CMFCToolBar::CanHandleSiblings](#canhandlesiblings)|Determina si la barra de herramientas y sus elementos relacionados están colocados en el mismo panel.|  
|[CMFCToolBar::CommandToIndex](#commandtoindex)|Devuelve el índice del botón en la barra de herramientas con un identificador de comando especificado.|  
|[CMFCToolBar::Create](#create)|Crea un objeto `CMFCToolBar`.|  
|[CMFCToolBar::CreateEx](#createex)|Crea un `CMFCToolBar` objeto que utiliza otras opciones de estilo, como iconos grandes.|  
|[CMFCToolBar::Deactivate](#deactivate)|Desactiva la barra de herramientas.|  
|[CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton)|Habilita o deshabilita la **agregar o quitar botones** botón que aparece en el extremo de la barra de herramientas.|  
|[CMFCToolBar::EnableDocking](#enabledocking)|Habilita el acoplamiento del panel al marco principal. (Invalida [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|  
|[CMFCToolBar::EnableLargeIcons](#enablelargeicons)|Habilita o deshabilita los iconos grandes en los botones de barra de herramientas.|  
|[CMFCToolBar::EnableQuickCustomization](#enablequickcustomization)|Habilita o deshabilita la personalización rápida de las barras de herramientas para que el usuario puede presionar el **Alt** clave y arrastre un botón hasta una nueva ubicación.|  
|[CMFCToolBar::EnableReflections](#enablereflections)|Habilita o deshabilita la reflexión de comando.|  
|[CMFCToolBar::EnableTextLabels](#enabletextlabels)|Habilita o deshabilita las etiquetas de texto en imágenes de botón de barra de herramientas.|  
|[CMFCToolBar::FromHandlePermanent](#fromhandlepermanent)|Recupera un puntero a la `CMFCToolBar` objeto que contiene el identificador de ventana especificado.|  
|[CMFCToolBar::GetAllButtons](#getallbuttons)|Devuelve una lista de solo lectura de botones en una barra de herramientas.|  
|[CMFCToolBar::GetAllToolbars](#getalltoolbars)|Devuelve una lista de solo lectura de todas las barras de herramientas en la aplicación.|  
|[CMFCToolBar::GetBasicCommands](#getbasiccommands)|Devuelve una lista de solo lectura de los comandos básicos definidos en la aplicación.|  
|[CMFCToolBar::GetButton](#getbutton)|Devuelve un puntero a la `CMFCToolBarButton` objeto que tiene un índice de botón de barra de herramientas especificada.|  
|[CMFCToolBar::GetButtonInfo](#getbuttoninfo)|Devuelve el identificador de comando, el estilo y el índice de la imagen del botón en un índice especificado.|  
|[CMFCToolBar::GetButtonSize](#getbuttonsize)|Devuelve las dimensiones de cada botón en la barra de herramientas.|  
|[CMFCToolBar::GetButtonStyle](#getbuttonstyle)|Devuelve el estilo actual del botón de barra de herramientas que se encuentra en el índice especificado.|  
|[CMFCToolBar::GetButtonText](#getbuttontext)|Devuelve la etiqueta de texto de un botón que tiene un índice especificado.|  
|[CMFCToolBar::GetColdImages](#getcoldimages)|Devuelve un puntero a la colección de imágenes de botón de barra de herramientas frío en la aplicación.|  
|[CMFCToolBar::GetColumnWidth](#getcolumnwidth)|Devuelve el ancho de los botones de barra de herramientas.|  
|[CMFCToolBar::GetCommandButtons](#getcommandbuttons)|Devuelve una lista de botones que tienen un identificador de comando especificado de todas las barras de herramientas en la aplicación.|  
|[CMFCToolBar::GetCount](#getcount)|Devuelve el número de botones y separadores en la barra de herramientas.|  
|[CMFCToolBar::GetCustomizeButton](#getcustomizebutton)|Recupera un puntero a la `CMFCCustomizeButton` objeto asociado con la barra de herramientas.|  
|[CMFCToolBar::GetDefaultImage](#getdefaultimage)|Devuelve el índice de la imagen predeterminada para un botón de barra de herramientas con un identificador de comando especificado.|  
|[CMFCToolBar::GetDisabledImages](#getdisabledimages)|Devuelve un puntero a la colección de imágenes que se utilizan para los botones de barras de herramientas de la aplicación.|  
|[CMFCToolBar::GetDisabledMenuImages](#getdisabledmenuimages)|Devuelve un puntero a la colección de imágenes que se utilizan para los botones de menú deshabilitado en la aplicación.|  
|[CMFCToolBar::GetDroppedDownMenu](#getdroppeddownmenu)|Recupera un puntero al objeto de botón de menú que se muestra actualmente su submenú.|  
|[CMFCToolBar::GetGrayDisabledButtons](#getgraydisabledbuttons)|Especifica si las imágenes de los botones deshabilitados están atenuadas versiones de las imágenes de botón normal, o tomado de la colección de imágenes de botón deshabilitado.|  
|[CMFCToolBar::GetHighlightedButton](#gethighlightedbutton)|Devuelve un puntero al botón de barra de herramientas seleccionada actualmente.|  
|[CMFCToolBar::GetHotBorder](#gethotborder)|Determina si los botones de barra de herramientas son el seguimiento.|  
|[CMFCToolBar::GetHotTextColor](#gethottextcolor)|Devuelve el color del texto de los botones de barra de herramientas resaltados.|  
|[CMFCToolBar::GetHwndLastFocus](#gethwndlastfocus)|Devuelve un identificador a la ventana que tenía el foco de entrada, justo antes de la barra de herramientas.|  
|[CMFCToolBar::GetIgnoreSetText](#getignoresettext)|Especifica si se omiten las llamadas para establecer las etiquetas de los botones.|  
|[CMFCToolBar::GetImageSize](#getimagesize)|Devuelve el tamaño actual de imágenes de botón de barra de herramientas.|  
|[CMFCToolBar::GetImages](#getimages)|Devuelve un puntero a la colección de forma predeterminada, las imágenes de botón en la aplicación.|  
|[CMFCToolBar::GetImagesOffset](#getimagesoffset)|Devuelve el desplazamiento del índice utilizado para buscar imágenes de los botones de la barra de herramientas para esta barra de herramientas en la lista global de imágenes de botón de barra de herramientas.|  
|[CMFCToolBar::GetInvalidateItemRect](#getinvalidateitemrect)|Recupera la región del área de cliente que debe volver a dibujar el botón en el índice especificado.|  
|[CMFCToolBar::GetItemID](#getitemid)|Devuelve el identificador de comando del botón de barra de herramientas en un índice especificado.|  
|[CMFCToolBar::GetItemRect](#getitemrect)|Devuelve el rectángulo delimitador del botón en un índice especificado.|  
|[CMFCToolBar::GetLargeColdImages](#getlargecoldimages)|Devuelve un puntero a la colección de imágenes de botón de barra de herramientas frío en la aplicación.|  
|[CMFCToolBar::GetLargeDisabledImages](#getlargedisabledimages)|Devuelve un puntero a la colección de imágenes de botón de barra de herramientas deshabilitado en la aplicación.|  
|[CMFCToolBar::GetLargeImages](#getlargeimages)|Devuelve un puntero a la colección de imágenes de botón de barra de herramientas en la aplicación.|  
|[CMFCToolBar::GetLockedColdImages](#getlockedcoldimages)|Devuelve un puntero a la colección de imágenes frías bloqueadas en la barra de herramientas.|  
|[CMFCToolBar::GetLockedDisabledImages](#getlockeddisabledimages)|Devuelve un puntero a la colección de imágenes deshabilitadas bloqueadas en la barra de herramientas.|  
|[CMFCToolBar::GetLockedImages](#getlockedimages)|Devuelve un puntero a la colección de imágenes de botón bloqueado en la barra de herramientas.|  
|[CMFCToolBar::GetLockedImageSize](#getlockedimagesize)|Devuelve el tamaño predeterminado de las imágenes bloqueadas de la barra de herramientas.|  
|[CMFCToolBar::GetLockedMenuImages](#getlockedmenuimages)|Devuelve un puntero a la colección de la barra de herramientas bloqueado imágenes de menú en la barra de herramientas.|  
|[CMFCToolBar::GetMenuButtonSize](#getmenubuttonsize)|Devuelve el tamaño de los botones de menú en la aplicación.|  
|[CMFCToolBar::GetMenuImageSize](#getmenuimagesize)|Devuelve el tamaño de imágenes de botón de menú de la aplicación.|  
|[CMFCToolBar::GetMenuImages](#getmenuimages)|Devuelve un puntero a la colección de imágenes de botón de menú de la aplicación.|  
|[CMFCToolBar::GetOrigButtons](#getorigbuttons)|Recupera la colección de botones no personalizada de la barra de herramientas.|  
|[CMFCToolBar::GetOrigResetButtons](#getorigresetbuttons)|Recupera la colección de botones de reinicio no personalizada de la barra de herramientas.|  
|[CMFCToolBar::GetResourceID](#getresourceid)|Recupera el identificador de recurso de la barra de herramientas.|  
|[CMFCToolBar::GetRouteCommandsViaFrame](#getroutecommandsviaframe)|Determina qué objeto, el marco primario o el propietario, envía comandos a la barra de herramientas.|  
|[CMFCToolBar::GetRowHeight](#getrowheight)|Devuelve el alto de los botones de barra de herramientas.|  
|[CMFCToolBar::GetShowTooltips](#getshowtooltips)|Especifica si se muestra información sobre herramientas para los botones de barra de herramientas.|  
|[CMFCToolBar::GetSiblingToolBar](#getsiblingtoolbar)|Recupera al elemento relacionado de la barra de herramientas.|  
|[CMFCToolBar::GetUserImages](#getuserimages)|Devuelve un puntero a la colección de imágenes de botón de barra de herramientas definidas por el usuario en la aplicación.|  
|[CMFCToolBar::HitTest](#hittest)|Devuelve el índice del botón de barra de herramientas que se encuentra en la posición especificada.|  
|[CMFCToolBar::InsertButton](#insertbutton)|Inserta un botón en la barra de herramientas.|  
|[CMFCToolBar::InsertSeparator](#insertseparator)|Inserta un separador en la barra de herramientas.|  
|[CMFCToolBar::InvalidateButton](#invalidatebutton)|Invalida el área cliente del botón de barra de herramientas que existe en el índice proporcionado.|  
|[CMFCToolBar::IsAddRemoveQuickCustomize](#isaddremovequickcustomize)|Determina si un usuario puede agregar o quitar botones de barra de herramientas mediante el **personalizar** opción de menú.|  
|[CMFCToolBar::IsAltCustomizeMode](#isaltcustomizemode)|Especifica si *personalización rápida* se usa para arrastrar un botón.|  
|[CMFCToolBar::IsAutoGrayInactiveImages](#isautograyinactiveimages)|Especifica si está habilitada la generación automática de imágenes de los botones inactivo (no resaltado).|  
|[CMFCToolBar::IsBasicCommand](#isbasiccommand)|Determina si es un comando en la lista de comandos básicos.|  
|[CMFCToolBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Determina si la barra de herramientas puede mostrar botones que se han extendido bordes.|  
|[CMFCToolBar::IsButtonHighlighted](#isbuttonhighlighted)|Determina si está resaltado en la barra de herramientas un botón.|  
|[CMFCToolBar::IsCommandPermitted](#iscommandpermitted)|Determina si se permite un comando.|  
|[CMFCToolBar::IsCommandRarelyUsed](#iscommandrarelyused)|Determina si un comando se usa rara vez (consulte [CMFCToolBar::SetCommandUsageOptions](#setcommandusageoptions)).|  
|[CMFCToolBar::IsCustomizeMode](#iscustomizemode)|Especifica si el marco de la barra de herramientas está en modo de personalización.|  
|[CMFCToolBar::IsDragButton](#isdragbutton)|Determina si se arrastra un botón de barra de herramientas.|  
|[CMFCToolBar::IsExistCustomizeButton](#isexistcustomizebutton)|Determina si la barra de herramientas contiene el **personalizar** botón.|  
|[CMFCToolBar::IsFloating](#isfloating)|Determina si la barra de herramientas es flotante.|  
|[CMFCToolBar::IsLargeIcons](#islargeicons)|Especifica si las barras de herramientas en la aplicación actualmente mostrarán iconos grandes.|  
|[CMFCToolBar::IsLastCommandFromButton](#islastcommandfrombutton)|Determina si se ejecuta el último comando se envió desde el botón de barra de herramientas especificada.|  
|[CMFCToolBar::IsLocked](#islocked)|Determina si la barra de herramientas está bloqueado.|  
|[CMFCToolBar::IsOneRowWithSibling](#isonerowwithsibling)|Determina si la barra de herramientas y la barra de herramientas del mismo nivel se colocan en la misma fila.|  
|[CMFCToolBar::IsUserDefined](#isuserdefined)|Especifica si la barra de herramientas está definido por el usuario.|  
|[CMFCToolBar::LoadBitmap](#loadbitmap)|Carga las imágenes de la barra de herramientas desde los recursos de la aplicación.|  
|[CMFCToolBar::LoadBitmapEx](#loadbitmapex)|Carga las imágenes de la barra de herramientas desde los recursos de la aplicación. Incluye imágenes de gran tamaño.|  
|[CMFCToolBar::LoadParameters](#loadparameters)|Carga las opciones de la barra de herramientas global del registro de Windows.|  
|[CMFCToolBar::LoadState](#loadstate)|Carga la información de estado de la barra de herramientas desde el registro de Windows. (Invalida [CPane::LoadState](../../mfc/reference/cpane-class.md#loadstate).)|  
|[CMFCToolBar::LoadToolBar](#loadtoolbar)|Carga la barra de herramientas de recursos de aplicación.|  
|[CMFCToolBar::LoadToolBarEx](#loadtoolbarex)|Carga de la barra de herramientas de recursos de aplicación mediante la `CMFCToolBarInfo` clase auxiliar para habilitar la aplicación para usar imágenes de gran tamaño.|  
|[CMFCToolBar::OnChangeHot](#onchangehot)|Llamado por el marco cuando un usuario selecciona un botón en la barra de herramientas.|  
|[CMFCToolBar::OnFillBackground](#onfillbackground)|Llamado por el marco de [CBasePane::DoPaint](../../mfc/reference/cbasepane-class.md#dopaint) para rellenar el fondo de la barra de herramientas.|  
|[CMFCToolBar::OnReset](#onreset)|Restaura la barra de herramientas a su estado original.|  
|[CMFCToolBar::OnSetAccData](#onsetaccdata)|(Invalida [CBasePane::OnSetAccData](../../mfc/reference/cbasepane-class.md#onsetaccdata).)|  
|[CMFCToolBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|Restaura el texto de un botón de barra de herramientas a su estado predeterminado.|  
|`CMFCToolBar::OnUpdateCmdUI`|Se utiliza internamente.|  
|[CMFCToolBar::RemoveAllButtons](#removeallbuttons)|Quita todos los botones de la barra de herramientas.|  
|[CMFCToolBar::RemoveButton](#removebutton)|Quita el botón con el índice especificado de la barra de herramientas.|  
|[CMFCToolBar::RemoveStateFromRegistry](#removestatefromregistry)|Elimina la información de estado de la barra de herramientas del registro de Windows.|  
|[CMFCToolBar::ReplaceButton](#replacebutton)|Reemplaza un botón de barra de herramientas con otro botón de barra de herramientas.|  
|[CMFCToolBar::ResetAll](#resetall)|Restaura todas las barras de herramientas a su estado original.|  
|[CMFCToolBar::ResetAllImages](#resetallimages)|Borra todas las colecciones de imagen de barra de herramientas de la aplicación.|  
|[CMFCToolBar::RestoreOriginalState](#restoreoriginalstate)|Restaura el estado original de una barra de herramientas.|  
|[CMFCToolBar::SaveState](#savestate)|Guarda la información de estado de la barra de herramientas en el registro de Windows. (Invalida [CPane::SaveState](../../mfc/reference/cpane-class.md#savestate).)|  
|`CMFCToolBar::Serialize`|(Invalida `CBasePane::Serialize`).|  
|[CMFCToolBar::SetBasicCommands](#setbasiccommands)|Establece la lista de comandos que siempre se muestran cuando un usuario abre un menú.|  
|[CMFCToolBar::SetButtonInfo](#setbuttoninfo)|Establece el identificador de comando, el estilo y el Id. de imagen de un botón de barra de herramientas.|  
|[CMFCToolBar::SetButtonStyle](#setbuttonstyle)|Establece el estilo del botón de barra de herramientas en el índice especificado.|  
|[CMFCToolBar::SetButtonText](#setbuttontext)|Establece la etiqueta de texto de un botón de barra de herramientas.|  
|[CMFCToolBar::SetButtons](#setbuttons)|Establece los botones de la barra de herramientas.|  
|[CMFCToolBar::SetCommandUsageOptions](#setcommandusageoptions)|Especifica cuándo comandos poco usados no aparecen en el menú de la aplicación.|  
|[CMFCToolBar::SetCustomizeMode](#setcustomizemode)|Habilita o deshabilita el modo de personalización para todas las barras de herramientas en la aplicación.|  
|[CMFCToolBar::SetGrayDisabledButtons](#setgraydisabledbuttons)|Especifica si se atenúan los botones deshabilitados en la barra de herramientas o si se usan imágenes deshabilitadas para los botones deshabilitados.|  
|[CMFCToolBar::SetHeight](#setheight)|Establece el alto de la barra de herramientas.|  
|[CMFCToolBar::SetHotBorder](#sethotborder)|Especifica si los botones de barra de herramientas de seguimiento.|  
|[CMFCToolBar::SetHotTextColor](#sethottextcolor)|Establece el color del texto de los botones de barra de herramientas de acceso rápido.|  
|[CMFCToolBar::SetLargeIcons](#setlargeicons)|Especifica si los botones de barra de herramientas muestran iconos grandes.|  
|[CMFCToolBar::SetLockedSizes](#setlockedsizes)|Establece los tamaños de los botones de bloqueadas y bloqueadas imágenes en la barra de herramientas.|  
|[CMFCToolBar::SetMenuSizes](#setmenusizes)|Establece el tamaño de sus imágenes y botones de menú de la barra de herramientas.|  
|[CMFCToolBar::SetNonPermittedCommands](#setnonpermittedcommands)|Establece la lista de comandos que no se puede ejecutar por el usuario.|  
|[CMFCToolBar::SetOneRowWithSibling](#setonerowwithsibling)|Coloca la barra de herramientas y del mismo nivel en la misma fila.|  
|[CMFCToolBar::SetPermament](#setpermament)|Especifica si un usuario puede cerrar la barra de herramientas.|  
|[CMFCToolBar::SetRouteCommandsViaFrame](#setroutecommandsviaframe)|Especifica si el marco primario o el propietario envía comandos a la barra de herramientas.|  
|[CMFCToolBar::SetShowTooltips](#setshowtooltips)|Especifica si el marco de trabajo muestra información sobre herramientas.|  
|[CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar)|Especifica al elemento relacionado de la barra de herramientas.|  
|[CMFCToolBar::SetSizes](#setsizes)|Especifica los tamaños de los botones y las imágenes en todas las barras de herramientas.|  
|[CMFCToolBar::SetToolBarBtnText](#settoolbarbtntext)|Especifica las propiedades de un botón en la barra de herramientas.|  
|[CMFCToolBar::SetTwoRowsWithSibling](#settworowswithsibling)|Coloca la barra de herramientas y su hermano en filas independientes.|  
|[CMFCToolBar::SetUserImages](#setuserimages)|Establece la colección de imágenes definido por el usuario en la aplicación.|  
|[CMFCToolBar::StretchPane](#stretchpane)|Expande la barra de herramientas vertical u horizontalmente. (Invalida [CBasePane::StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane).)|  
|[CMFCToolBar::TranslateChar](#translatechar)|Ejecuta un comando de botón si el código de clave especificado corresponde a un método abreviado de teclado válido.|  
|[CMFCToolBar::UpdateButton](#updatebutton)|Actualiza el estado del botón especificado.|  
|[CMFCToolBar::WrapToolBar](#wraptoolbar)|Cambia la posición de los botones de barra de herramientas dentro de las dimensiones dadas.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBar::AllowShowOnList](#allowshowonlist)|Determina si la barra de herramientas se muestra en la lista en la **las barras de herramientas** panel de la **personalizar** cuadro de diálogo.|  
|[CMFCToolBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|Calcula el alto máximo de un botón en la barra de herramientas.|  
|[CMFCToolBar::DoPaint](#dopaint)|Vuelve a dibujar una barra de herramientas.|  
|[CMFCToolBar::DrawButton](#drawbutton)|Vuelve a dibujar un botón de barra de herramientas.|  
|[CMFCToolBar::DrawSeparator](#drawseparator)|Vuelve a dibujar un separador de barra de herramientas.|  
|[CMFCToolBar::OnUserToolTip](#onusertooltip)|Llamado por el marco cuando la información sobre herramientas para un botón que se va a mostrar.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBar::m_bDontScaleImages](#m_bdontscaleimages)|Especifica si se debe escalar o imágenes de barra de herramientas no en modo de PPP alta.|  
|[CMFCToolBar::m_dblLargeImageRatio](#m_dbllargeimageratio)|Especifica la proporción entre la dimensión (alto o ancho) de imágenes de gran tamaño y la dimensión de las imágenes normales.|  
  
## <a name="remarks"></a>Comentarios  
 Para incorporar un `CMFCToolBar` de objeto en la aplicación, siga estos pasos:  
  
1.  Agregar un `CMFCToolBar` objeto en la ventana de marco principal.  
  
2.  Cuando se procesa la `WM_CREATE` de mensajes para la ventana de marco principal, llame a [CMFCToolBar::Create](#create) o [CMFCToolBar::CreateEx](#createex) para crear la barra de herramientas y especifique su estilo.  
  
3.  Llame a [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking) para especificar el estilo de acoplamiento.  
  
 Para insertar un botón especial, como un cuadro combinado o lista desplegable barra de herramientas, reservar un botón ficticio en el recurso primario y reemplazar el botón ficticio en tiempo de ejecución mediante [CMFCToolBar::ReplaceButton](#replacebutton). Para obtener más información, consulte [Tutorial: poner controles en barras de herramientas de](../walkthrough-putting-controls-on-toolbars.md).  
  
 `CMFCToolBar`es la clase base para las clases de biblioteca MFC [CMFCMenuBar clase](../../mfc/reference/cmfcmenubar-class.md), [CMFCPopupMenuBar clase](../../mfc/reference/cmfcpopupmenubar-class.md), y [CMFCDropDownToolBar clase](../../mfc/reference/cmfcdropdowntoolbar-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCToolBar` clase. En el ejemplo se muestra cómo establecer el texto de la etiqueta de la ventana de la barra de herramientas, los bordes, establecer el estilo del panel y habilitar la **agregar o quitar botones** botón que aparece en el extremo de la barra de herramientas. Este fragmento de código forma parte de la [ejemplo de demostración de IE](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo Nº&6;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo Nº&8;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_2.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtoolbar.h  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 `CMFCToolBar`  
  
##  <a name="a-nameaddbasiccommanda--cmfctoolbaraddbasiccommand"></a><a name="addbasiccommand"></a>CMFCToolBar::AddBasicCommand  
 Agrega un comando de menú a la lista de comandos que siempre se muestran cuando un usuario abre un menú.  
  
```  
static void __stdcall AddBasicCommand(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 Especifica el comando para agregar.  
  
### <a name="remarks"></a>Comentarios  
 Un comando básico siempre se muestra cuando se abre el menú. Este método es significativo cuando el usuario decide ver los comandos usados recientemente.  
  
 Utilice la [CMFCToolBar::SetBasicCommands](#setbasiccommands) para establecer la lista de comandos que siempre se muestran cuando un usuario abre un menú. Utilice la [CMFCToolBar::GetBasicCommands](#getbasiccommands) método para recuperar la lista de comandos básicos que se utiliza la aplicación.  
  
##  <a name="a-nameaddcommandusagea--cmfctoolbaraddcommandusage"></a><a name="addcommandusage"></a>CMFCToolBar::AddCommandUsage  
 Se incrementa en uno el contador que está asociado al comando especificado.  
  
```  
static void __stdcall AddCommandUsage(UINT uiCommand);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCommand`  
 Especifica el contador de comando que se va a incrementar.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando el usuario selecciona un elemento de menú.  
  
 El marco de trabajo usa los contadores para mostrar recientemente utilizar elementos de menú de comandos.  
  
 Este método incrementa el contador de comando mediante el uso de la [CMFCCmdUsageCount::AddCmd](../../mfc/reference/cmfccmdusagecount-class.md#addcmd) método.  
  
##  <a name="a-nameaddtoolbarforimagecollectiona--cmfctoolbaraddtoolbarforimagecollection"></a><a name="addtoolbarforimagecollection"></a>CMFCToolBar::AddToolBarForImageCollection  
 Agrega imágenes de los recursos de la interfaz de usuario a la colección de imágenes en la aplicación.  
  
```  
static BOOL __stdcall AddToolBarForImageCollection(
    UINT uiResID,  
    UINT uiBmpResID=0,  
    UINT uiColdResID=0,  
    UINT uiMenuResID=0,  
    UINT uiDisabledResID=0,  
    UINT uiMenuDisabledResID=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiResID`  
 Id. de recurso de una barra de herramientas con imágenes de carga.  
  
 [in] `uiBmpResID`  
 Identificador de recurso de un mapa de bits con imágenes de la barra de herramientas.  
  
 [in] `uiColdResID`  
 Identificador de recurso de un mapa de bits con imágenes de la barra de herramientas "frío".  
  
 [in] `uiMenuResID`  
 Identificador de recurso de un mapa de bits con imágenes de menú.  
  
 [in] `uiDisabledResID`  
 Identificador de recurso de un mapa de bits con imágenes de barras de herramientas.  
  
 [in] `uiMenuDisabledResID`  
 Identificador de recurso de un mapa de bits con imágenes de menú deshabilitado.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método tiene éxito; `FALSE` si `uiResID` o `uiBmpResID` no especifica los recursos válidos o se produce otro error.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para cargar un mapa de bits con imágenes de la barra de herramientas y agregarlo a la colección de imágenes de la barra de herramientas. Este método crea un objeto temporal de la barra de herramientas y las llamadas [CMFCToolBar::LoadToolBar](#loadtoolbar).  
  
##  <a name="a-nameadjustlayouta--cmfctoolbaradjustlayout"></a><a name="adjustlayout"></a>CMFCToolBar::AdjustLayout  
 Vuelve a calcular el tamaño y la posición de una barra de herramientas.  
  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método cuando se ha creado la barra de herramientas para volver a calcular su tamaño y posición.  
  
 El marco de trabajo llama a este método cada vez que se debe cambiar el diseño de la barra de herramientas. Por ejemplo, el diseño debe cambiar cuando el usuario mueve a otra barra de control, cambia el tamaño de una ventana de la aplicación o personaliza la barra de herramientas.  
  
 Invalide este método para proporcionar su propio diseño dinámico en clases que derivan de `CMFCToolbar`.  
  
##  <a name="a-nameadjustsizea--cmfctoolbaradjustsize"></a><a name="adjustsize"></a>CMFCToolBar::AdjustSize  
 Vuelve a calcular el tamaño de la barra de herramientas.  
  
```  
void AdjustSize();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método asegura que la barra de herramientas se ajusta a los límites del marco primario. Este método no hace nada si la barra de herramientas no tiene ningún marco primario.  
  
 El [CMFCToolBar::AdjustLayout](#adjustlayout) método llama a este método para volver a calcular el tamaño, si el elemento primario de la barra de herramientas no es un `CMFCReBar` objeto.  
  
##  <a name="a-nameallowchangetextlabelsa--cmfctoolbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCToolBar::AllowChangeTextLabels  
 Especifica si se pueden mostrar etiquetas de texto en imágenes en los botones de barra de herramientas.  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se permite mostrar etiquetas de texto debajo de imágenes. de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Se llama a este método mediante el cuadro de diálogo de personalización para determinar si se habilita un **Mostrar etiquetas de texto** casilla de verificación en la **las barras de herramientas** página de la barra de herramientas seleccionado.  
  
 La implementación predeterminada devuelve `TRUE`.  
  
 Invalide este método en un objeto derivado de `CMFCToolBar` y devolver `FALSE` cuando no desea que el usuario decida si se muestran las etiquetas de texto en los botones de barra de herramientas en las imágenes.  
  
##  <a name="a-nameallowshowonlista--cmfctoolbarallowshowonlist"></a><a name="allowshowonlist"></a>CMFCToolBar::AllowShowOnList  
 Determina si la barra de herramientas se muestra en la lista de barras de herramientas en el **las barras de herramientas** panel de la **personalizar** cuadro de diálogo.  
  
```  
virtual BOOL AllowShowOnList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el objeto de barra de herramientas se puede mostrar en el cuadro de lista en la página de personalización de la barra de herramientas; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo para determinar si la lista en la página de personalización de la barra de herramientas debe incluir un determinado objeto derivado de `CMFCToolBar`.  
  
 La implementación predeterminada siempre devuelve `TRUE`. Invalide este método si no desea que una barra de herramientas aparecen en la lista de barras de herramientas en el cuadro de diálogo de personalización.  
  
##  <a name="a-namearetextlabelsa--cmfctoolbararetextlabels"></a><a name="aretextlabels"></a>CMFCToolBar::AreTextLabels  
 Especifica si las etiquetas de texto en imágenes se muestran actualmente en los botones de barra de herramientas.  
  
```  
BOOL AreTextLabels() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si los botones de barra de herramientas Mostrar etiquetas de texto debajo de imágenes. de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice [CMFCToolBar::EnableTextLabels](#enabletextlabels) para especificar si se muestra el texto. El valor predeterminado es `FALSE`. Llame a [CMFCToolBar::AllowChangeTextLabels](#allowchangetextlabels) para especificar si el usuario puede cambiar esta configuración en el cuadro de diálogo de personalización.  
  
##  <a name="a-nameautograyinactiveimagesa--cmfctoolbarautograyinactiveimages"></a><a name="autograyinactiveimages"></a>CMFCToolBar::AutoGrayInactiveImages  
 Habilita o deshabilita la generación automática de imágenes de botón inactiva.  
  
```  
static void AutoGrayInactiveImages(
    BOOL bEnable=TRUE,  
    int nGrayImagePercentage=0,  
    BOOL bRedrawAllToolbars=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Un valor booleano que especifica si se va a atenuar imágenes inactivas. Si este parámetro es `TRUE`, imágenes inactivas aparecen atenuadas. De lo contrario, imágenes inactivas no aparecen atenuadas.  
  
 [in] `nGrayImagePercentage`  
 Especifica el porcentaje de luminancia para imágenes inactivas. Si `bEnable` es `FALSE`, este valor se omite.  
  
 [in] `bRedrawAllToolbars`  
 Un valor booleano que especifica si se va a dibujar las barras de herramientas en la aplicación. Si este parámetro es `TRUE`, este método vuelve a dibujar las barras de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Si `bEnable` es `TRUE`, el marco de trabajo usa `nGrayImagePercentage` para generar imágenes inactivas de las imágenes normales. De lo contrario, debe proporcionar el conjunto de imágenes inactivas mediante el [CMFCToolBar::GetColdImages](#getcoldimages) método. De forma predeterminada, esta opción está deshabilitada.  
  
 Para obtener más información acerca de la `nGrayImagePercentage` parámetro, consulte [CMFCToolBarImages::GrayImages](../../mfc/reference/cmfctoolbarimages-class.md#grayimages).  
  
##  <a name="a-namebuttontoindexa--cmfctoolbarbuttontoindex"></a><a name="buttontoindex"></a>CMFCToolBar::ButtonToIndex  
 Devuelve el índice de un objeto [CMFCToolBarButton clase](../../mfc/reference/cmfctoolbarbutton-class.md) objeto en esta barra de herramientas.  
  
```  
int ButtonToIndex(const CMFCToolBarButton* pButton) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Un puntero al objeto de botón de barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de `pButton` en la lista interna de botones de barra de herramientas; o -1 si el botón especificado no está en esta barra de herramientas.  
  
##  <a name="a-namecalcfixedlayouta--cmfctoolbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCToolBar::CalcFixedLayout  
 Calcula el tamaño horizontal de la barra de herramientas.  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bStretch`  
 `TRUE`Para ajustar el tamaño del marco primario a la barra de herramientas.  
  
 [in] `bHorz`  
 `TRUE`para orientar la barra de herramientas horizontal; `FALSE` para orientar la barra de herramientas verticalmente.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` objeto que especifica el tamaño de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Este método calcula el tamaño de la barra de herramientas mediante el `CMFCToolBar::CalcLayout` método. Pasa el `LM_STRETCH` marca la `dwMode` parámetro si `bStretch` es `TRUE`. Pasa el `LM_HORZ` marca si `bHorz` es `TRUE`.  
  
 Vea el ejemplo VisualStudioDemo para obtener un ejemplo que utiliza este método.  
  
##  <a name="a-namecalcmaxbuttonheighta--cmfctoolbarcalcmaxbuttonheight"></a><a name="calcmaxbuttonheight"></a>CMFCToolBar::CalcMaxButtonHeight  
 Calcula el alto máximo de botones de la barra de herramientas.  
  
```  
virtual int CalcMaxButtonHeight();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto máximo de botones.  
  
### <a name="remarks"></a>Comentarios  
 Este método calcula el alto máximo entre todos los botones de barra de herramientas de la barra de herramientas. El alto puede variar dependiendo de factores como el estado de acoplamiento de barra de herramientas actual.  
  
 Invalide este método en una clase derivada de `CMFCToolBar` para proporcionar su propio cálculo de alto.  
  
##  <a name="a-namecalcsizea--cmfctoolbarcalcsize"></a><a name="calcsize"></a>CMFCToolBar::CalcSize  
 Llamado por el marco como parte del proceso de cálculo de diseño.  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bVertDock`  
 `TRUE`para especificar que la barra de herramientas está acoplado verticalmente; `FALSE` para especificar que la barra de herramientas está acoplado horizontalmente.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` objeto que especifica el tamaño total de los botones de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Este método tiene en cuenta los atributos que afectan al tamaño de cada botón, como el área de la etiqueta de texto y el tamaño del borde.  
  
 Si la barra de herramientas contiene botones, este método devuelve el tamaño de un solo botón reservado mediante el [CMFCToolBar::GetButtonSize](#getbuttonsize) método.  
  
##  <a name="a-namecanbecloseda--cmfctoolbarcanbeclosed"></a><a name="canbeclosed"></a>CMFCToolBar::CanBeClosed  
 Especifica si un usuario puede cerrar la barra de herramientas.  
  
```  
virtual BOOL CanBeClosed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de herramientas puede ser cerrada por el usuario; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para determinar si el usuario puede cerrar una barra de herramientas. Si el método devuelve `TRUE`, el marco de trabajo permite que el comando SC_CLOSE en el menú de sistema de la barra de herramientas y el usuario puede cerrar la barra de herramientas mediante una casilla de verificación en la lista de barras de herramientas en el cuadro de diálogo de personalización.  
  
 La implementación predeterminada devuelve `TRUE`. Invalide este método en una clase derivada de `CMFCToolBar` para hacer que los objetos de la barra de herramientas que no se puede cerrar por el usuario.  
  
##  <a name="a-namecanberestoreda--cmfctoolbarcanberestored"></a><a name="canberestored"></a>CMFCToolBar::CanBeRestored  
 Determina si el sistema puede restaurar una barra de herramientas a su estado original después de la personalización.  
  
```  
virtual BOOL CanBeRestored() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de herramientas se puede restaurar desde los recursos de la aplicación; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para determinar si se puede devolver una barra de herramientas a su estado original después de la personalización. Se carga el estado original de los recursos de aplicación.  
  
 Si `CanBeRestored` devuelve `TRUE`, **las barras de herramientas** página del cuadro de diálogo de personalización permite la **restablecer** botón de la barra de herramientas seleccionado.  
  
 La implementación predeterminada devuelve `TRUE` si el identificador de recurso original de la barra de herramientas cuando se cargó es distinto de cero. Normalmente, no se puede restaurar solo definido por el usuario las barras de herramientas.  
  
 Puede invalidar el `CanBeRestored` método para personalizar este comportamiento en las clases derivadas.  
  
##  <a name="a-namecanfocusa--cmfctoolbarcanfocus"></a><a name="canfocus"></a>CMFCToolBar::CanFocus  
 Especifica si el panel puede recibir el foco.  
  
```  
virtual BOOL CanFocus() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método reemplaza la implementación de la clase base, [CBasePane::CanFocus](../../mfc/reference/cbasepane-class.md#canfocus), porque los objetos de la barra de herramientas no pueden recibir el foco.  
  
##  <a name="a-namecanhandlesiblingsa--cmfctoolbarcanhandlesiblings"></a><a name="canhandlesiblings"></a>CMFCToolBar::CanHandleSiblings  
 Determina si la barra de herramientas y sus elementos relacionados están colocados en el mismo panel.  
  
```  
BOOL CanHandleSiblings();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si la barra de herramientas tiene un elemento relacionado y la barra de herramientas y su elemento relacionado se colocan en el mismo panel; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El método CMFCCustomizeButton::CreatePopupMenu interno llama a este método para determinar cómo mostrar la **personalizar** menú emergente. Si este método devuelve `TRUE`, el marco de trabajo muestra el **mostrar botones en una fila** o **mostrar botones en dos filas** botones.  
  
 Normalmente no tiene que utilizar este método. Para habilitar la **personalizar** botón que aparece en la barra de herramientas, llamada la [CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton) método. Para habilitar la **mostrar botones en una fila** o **mostrar botones en dos filas** botones, llame a [CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar).  
  
##  <a name="a-namecleanupimagesa--cmfctoolbarcleanupimages"></a><a name="cleanupimages"></a>CMFCToolBar::CleanUpImages  
 Libera los recursos de sistema asignados para las imágenes de la barra de herramientas.  
  
```  
static void CMFCToolBar::CleanUpImages();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se cierra una aplicación.  
  
##  <a name="a-namecleanuplockedimagesa--cmfctoolbarcleanuplockedimages"></a><a name="cleanuplockedimages"></a>CMFCToolBar::CleanUpLockedImages  
 Libera los recursos de sistema asignados para las imágenes bloqueadas de la barra de herramientas.  
  
```  
void CleanUpLockedImages();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método cuando cambia el estilo visual de la aplicación. Vea el ejemplo VisualStudioDemo para obtener un ejemplo que utiliza este método.  
  
##  <a name="a-namecommandtoindexa--cmfctoolbarcommandtoindex"></a><a name="commandtoindex"></a>CMFCToolBar::CommandToIndex  
 Devuelve el índice del botón en la barra de herramientas con un identificador de comando especificado.  
  
```  
int CommandToIndex(
    UINT nIDFind,  
    int iIndexFirst=0) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIDFind`  
 Especifica el identificador del comando.  
  
 [in] `iIndexFirst`  
 Especifica el índice inicial a comenzar.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del botón de barra de herramientas, si el método se realizó correctamente; -1 si no hay ningún botón con el identificador especificado.  
  
### <a name="remarks"></a>Comentarios  
 Un `CMFCToolBar` objeto mantiene una lista interna de los botones de la barra de herramientas. Llame a esta función para recuperar el índice de un botón en la lista proporcionada el identificador de comando del botón.  
  
 Si `iIndex` es mayor que 0, este método omite cualquier botón de la barra de herramientas que tiene un índice menor que `iIndex`.  
  
##  <a name="a-namecreatea--cmfctoolbarcreate"></a><a name="create"></a>CMFCToolBar::Create  
 Crea un objeto `CMFCToolBar`.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT nID=AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParentWnd`  
 Puntero a la ventana primaria de la barra de herramientas.  
  
 [in] `dwStyle`  
 El estilo de barra de herramientas. Consulte [Control de barra de herramientas y estilos de botón](http://msdn.microsoft.com/library/windows/desktop/bb760439) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para la lista de estilos.  
  
 [in] `nID`  
 El identificador de la ventana secundaria de la barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea una barra de controles y lo adjunta a la barra de herramientas. Crea la barra de controles con el `TBSTYLE_FLAT` estilo. Llame a [CMFCToolBar::CreateEx](#createex) si desea que un estilo de barra de control diferente.  
  
##  <a name="a-namecreateexa--cmfctoolbarcreateex"></a><a name="createex"></a>CMFCToolBar::CreateEx  
 Crea un `CMFCToolBar` objeto que utiliza otras opciones de estilo, como iconos grandes.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle=TBSTYLE_FLAT,  
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,  
    CRect rcBorders=CRect(1,
    1,
    1,
    1),  
    UINT nID=AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParentWnd`  
 Puntero a la ventana primaria de la barra de herramientas.  
  
 [in] `dwCtrlStyle`  
 Estilos adicionales para crear el objeto de barra de control incrustado.  
  
 [in] `dwStyle`  
 El estilo de barra de herramientas. Consulte [Control de barra de herramientas y estilos de botón](http://msdn.microsoft.com/library/windows/desktop/bb760439) para obtener una lista de estilos apropiados.  
  
 [in] `rcBorders`  
 Un `CRect` objeto que especifica el ancho de los bordes de ventana de la barra de herramientas.  
  
 [in] `nID`  
 El identificador de la ventana secundaria de la barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si este método se realiza correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea una barra de controles y lo adjunta a la barra de herramientas.  
  
 Llamar a este método en lugar de [CMFCToolBar::Create](#create) cuando desee proporcionar estilos específicos. Por ejemplo, establecer `dwCtrlStyle` a `TBSTYLE_FLAT | TBSTYLE_TRANSPARENT` para crear una barra de herramientas que se parece a las barras de herramientas que usan Internet Explorer 4.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `CreateEx` método de la `CMFCToolBar` clase. Este fragmento de código forma parte de la [ejemplo de demostración de IE](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo Nº&6;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo&#7;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_3.cpp)]  
  
##  <a name="a-namedeactivatea--cmfctoolbardeactivate"></a><a name="deactivate"></a>CMFCToolBar::Deactivate  
 Desactiva la barra de herramientas.  
  
```  
virtual void Deactivate();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método desactiva la barra de herramientas quitando el foco en el botón de barra de herramientas resaltados. El marco de trabajo llama a este método cuando pierde el foco de la barra de herramientas o se destruye.  
  
##  <a name="a-namedopainta--cmfctoolbardopaint"></a><a name="dopaint"></a>CMFCToolBar::DoPaint  
 Vuelve a dibujar una barra de herramientas.  
  
```  
virtual void DoPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se debe dibujar una parte de la barra de herramientas.  
  
 Invalide este método para personalizar la apariencia de un objeto derivado de `CMFCToolBar`.  
  
##  <a name="a-namedrawbuttona--cmfctoolbardrawbutton"></a><a name="drawbutton"></a>CMFCToolBar::DrawButton  
 Vuelve a dibujar un botón de barra de herramientas.  
  
```  
virtual BOOL DrawButton(
    CDC* pDC,  
    CMFCToolBarButton* pButton,  
    CMFCToolBarImages* pImages,  
    BOOL bHighlighted,  
    BOOL bDrawDisabledImages);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pButton`  
 Puntero a un botón que se va a dibujar.  
  
 [in] `pImages`  
 Puntero a las imágenes de la barra de herramientas.  
  
 [in] `bHighlighted`  
 `TRUE`Si el botón está resaltado; de lo contrario, `FALSE`.  
  
 [in] `bDrawDisabledImages`  
 `TRUE`Si los botones deshabilitados aparecen atenuados; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el botón volver a dibujar; `FALSE` si el botón está oculto.  
  
### <a name="remarks"></a>Comentarios  
 El [CMFCToolBar::DrawButton](#drawbutton) método llama a este método cuando se debe dibujar un botón de barra de herramientas.  
  
 Invalide este método si desea personalizar el aspecto de botones en la barra de herramientas.  
  
##  <a name="a-namedrawseparatora--cmfctoolbardrawseparator"></a><a name="drawseparator"></a>CMFCToolBar::DrawSeparator  
 Vuelve a dibujar un separador de barra de herramientas.  
  
```  
virtual void DrawSeparator(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 El rectángulo delimitador de la ubicación donde se dibuja el separador, en píxeles.  
  
 [in] `bHorz`  
 `TRUE`Si el separador es horizontal, `FALSE` si el separador es vertical.  
  
### <a name="remarks"></a>Comentarios  
 [CMFCToolBar::DoPaint](#dopaint) llama a este método para cada [CMFCToolBar::DrawSeparator](#drawseparator) objeto que tiene el `TBBS_SEPARATOR` estilo, en lugar de llamar [CMFCToolBar::DrawButton](#drawbutton) para esos botones.  
  
 Invalide este método en una clase derivada de [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) para personalizar la apariencia de los separadores de la barra de herramientas. La implementación predeterminada llama [CMFCVisualManager::OnDrawSeparator](../../mfc/reference/cmfcvisualmanager-class.md#ondrawseparator) para dibujar un separador cuyo aspecto viene determinado por el administrador visual actual.  
  
##  <a name="a-nameenablecustomizebuttona--cmfctoolbarenablecustomizebutton"></a><a name="enablecustomizebutton"></a>CMFCToolBar::EnableCustomizeButton  
 Habilita o deshabilita el botón Personalizar que aparece en la barra de herramientas.  
  
```  
void EnableCustomizeButton(
    BOOL bEnable,  
    int iCustomizeCmd,  
    const CString& strCustomizeText,  
    BOOL bQuickCustomize=TRUE);

 
void EnableCustomizeButton(
    BOOL bEnable,  
    int iCustomizeCmd,  
    UINT uiCustomizeTextResId,  
    BOOL bQuickCustomize=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Habilita o deshabilita el botón Personalizar.  
  
 [in] `iCustomizeCmd`  
 El identificador de comando del botón Personalizar.  
  
 [in] `strCustomizeText`  
 La etiqueta de texto del botón Personalizar.  
  
 [in] `uiCustomizeTextResId`  
 El identificador de la cadena de recurso de la etiqueta del botón Personalizar.  
  
 [in] `bQuickCustomize`  
 Habilita o deshabilita la **agregar o quitar botones** opción en el menú que se despliega en el botón.  
  
### <a name="remarks"></a>Comentarios  
 Si `iCustomizeCmd` es -1, la muestra de framework Personalizar botón cuando varios botones de barra de herramientas no caben en el área de la barra de herramientas. La flecha muestra una doble hacia la izquierda de un botón o botón de contenido adicional, lo que indica que hay más botones.  
  
 Si `iCustomizeCmd` especifica un identificador de comando válido, y `bEnable` es `TRUE`, siempre se muestra el botón Personalizar. El botón tiene una pequeña flecha abajo y abre un menú que contiene un comando. Este comando utiliza la etiqueta de texto especificada por `strCustomizeText`. Si `bQuickCustomize` también es `TRUE`, el menú muestra el **agregar o quitar botones** opción.  
  
 El marco de trabajo agrega dinámicamente al menú los botones que no caben en el área de la barra de herramientas antes que el elemento especificado por `iCustomizeCmd`. Se muestra el botón de contenido adicional situado junto a la flecha hacia abajo.  
  
##  <a name="a-nameenabledockinga--cmfctoolbarenabledocking"></a><a name="enabledocking"></a>CMFCToolBar::EnableDocking  
 Habilita el acoplamiento del panel al marco principal.  
  
```  
virtual void EnableDocking(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwAlignment`  
 Especifica la alineación de acoplamiento para habilitar.  
  
### <a name="remarks"></a>Comentarios  
 Este método extiende la implementación de la clase base, [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking), estableciendo la `CBasePane::m_dwControlBarStyle` miembro de datos `AFX_CBRS_FLOAT`. Este método pasa `dwAlignment` a la implementación de la clase base.  
  
##  <a name="a-nameenablelargeiconsa--cmfctoolbarenablelargeicons"></a><a name="enablelargeicons"></a>CMFCToolBar::EnableLargeIcons  
 Habilita o deshabilita los iconos grandes en los botones de barra de herramientas.  
  
```  
void EnableLargeIcons(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar iconos grandes, `FALSE` para deshabilitar iconos grandes.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, se habilitan los iconos grandes.  
  
##  <a name="a-nameenablequickcustomizationa--cmfctoolbarenablequickcustomization"></a><a name="enablequickcustomization"></a>CMFCToolBar::EnableQuickCustomization  
 Habilita o deshabilita la personalización rápida de las barras de herramientas para que el usuario puede presionar el **Alt** clave y arrastre un botón hasta una nueva ubicación.  
  
```  
static void EnableQuickCustomization(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar la personalización rápida, `FALSE` para deshabilitar la personalización rápida.  
  
##  <a name="a-nameenablereflectionsa--cmfctoolbarenablereflections"></a><a name="enablereflections"></a>CMFCToolBar::EnableReflections  
 Habilita o deshabilita la reflexión de comando.  
  
```  
void EnableReflections(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar la reflexión de comando; `FALSE` para deshabilitar el reflejo de comando.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para habilitar la reflexión de comando para los botones de barra de herramientas que contienen controles incrustados, como cuadros combinados.  
  
 Para obtener más información acerca de la reflexión de comando, consulte [TN062: reflexión de mensajes para controles de Windows](../../mfc/tn062-message-reflection-for-windows-controls.md).  
  
##  <a name="a-nameenabletextlabelsa--cmfctoolbarenabletextlabels"></a><a name="enabletextlabels"></a>CMFCToolBar::EnableTextLabels  
 Habilita o deshabilita las etiquetas de texto en imágenes de botón de barra de herramientas.  
  
```  
void EnableTextLabels(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bEnable`  
 `TRUE`Si aparecen las etiquetas de texto en imágenes de botón de barra de herramientas; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si están habilitadas las etiquetas de texto, se amplían todos los botones de la barra de herramientas para proporcionar espacio para las etiquetas que se mostrará en las imágenes. El cuadro de diálogo de personalización tiene un **Mostrar etiqueta de texto** casilla de verificación en la **las barras de herramientas** página. Cuando el usuario selecciona una barra de herramientas y activa esta opción, el marco llama a `EnableTextLabels` para la barra de herramientas seleccionado. Puede deshabilitar la casilla de verificación para un objeto derivado de [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) devolviendo `FALSE` de [CMFCToolBar::AllowChangeTextLabels](#allowchangetextlabels) .  
  
##  <a name="a-namefromhandlepermanenta--cmfctoolbarfromhandlepermanent"></a><a name="fromhandlepermanent"></a>CMFCToolBar::FromHandlePermanent  
 Recupera un puntero a la `CMFCToolBar` objeto que contiene el identificador de ventana especificado.  
  
```  
static CMFCToolBar* __stdcall FromHandlePermanent(HWND hwnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hwnd`  
 Para buscar el identificador de ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CMFCToolBar` objeto que contiene el identificador de ventana determinado o `NULL` si no existe la correspondiente `CMFCToolBar` objeto existe.  
  
### <a name="remarks"></a>Comentarios  
 Este método compartido examina cada barra de herramientas de la aplicación para la `CMFCToolBar` objeto que contiene el identificador de ventana especificado.  
  
##  <a name="a-namegetallbuttonsa--cmfctoolbargetallbuttons"></a><a name="getallbuttons"></a>CMFCToolBar::GetAllButtons  
 Devuelve una lista de solo lectura de botones en una barra de herramientas.  
  
```  
const CObList& GetAllButtons() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia constante a una [clase CObList](../../mfc/reference/coblist-class.md) , que contiene una colección de [CMFCToolBarButton clase](../../mfc/reference/cmfctoolbarbutton-class.md) objetos.  
  
##  <a name="a-namegetalltoolbarsa--cmfctoolbargetalltoolbars"></a><a name="getalltoolbars"></a>CMFCToolBar::GetAllToolbars  
 Devuelve una lista de solo lectura de todas las barras de herramientas en la aplicación.  
  
```  
static const CObList& GetAllToolbars();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Const hacen referencia a un [clase CObList](../../mfc/reference/coblist-class.md) objeto que contiene una colección de `CMFCToolBar` objetos.  
  
##  <a name="a-namegetbasiccommandsa--cmfctoolbargetbasiccommands"></a><a name="getbasiccommands"></a>CMFCToolBar::GetBasicCommands  
 Devuelve una lista de solo lectura de los comandos básicos definidos en la aplicación.  
  
```  
static const CList<UINT,UINT>& GetBasicCommands();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Const hacen referencia a un [CList (clase)](../../mfc/reference/clist-class.md) objeto que contiene una colección de comandos básicos.  
  
### <a name="remarks"></a>Comentarios  
 Agregar comandos básicos mediante una llamada a [CMFCToolBar::AddBasicCommand](#addbasiccommand) o [CMFCToolBar::SetBasicCommands](#setbasiccommands).  
  
##  <a name="a-namegetbuttona--cmfctoolbargetbutton"></a><a name="getbutton"></a>CMFCToolBar::GetButton  
 Devuelve un puntero a la [CMFCToolBarButton clase](../../mfc/reference/cmfctoolbarbutton-class.md) objeto en un índice especificado.  
  
```  
CMFCToolBarButton* GetButton(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
 Especifica el índice del botón para devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al botón de barra de herramientas, si existe; o `NULL` si no hay ningún botón de este tipo.  
  
##  <a name="a-namegetbuttoninfoa--cmfctoolbargetbuttoninfo"></a><a name="getbuttoninfo"></a>CMFCToolBar::GetButtonInfo  
 Devuelve el identificador de comando, el estilo y el índice de la imagen del botón en un índice especificado.  
  
```  
void GetButtonInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& iImage) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice del botón en la lista de botones de la barra de herramientas.  
  
 [out] `nID`  
 El identificador de un botón de comando.  
  
 [out] `nStyle`  
 El estilo del botón.  
  
 [out] `iImage`  
 El índice de la imagen del botón.  
  
### <a name="remarks"></a>Comentarios  
 El `GetButtonInfo` método busca un botón de barra de herramientas en el índice especificado y recupera el índice de comandos de identificador, el estilo y la imagen del botón.  
  
 Si el botón situado en el índice especificado no existe, el marco de trabajo establece `nID` y `nStyle` en 0, y `iImage` en -1 cuando el método devuelve.  
  
##  <a name="a-namegetbuttonsizea--cmfctoolbargetbuttonsize"></a><a name="getbuttonsize"></a>CMFCToolBar::GetButtonSize  
 Devuelve las dimensiones de cada botón en la barra de herramientas.  
  
```  
CSize GetButtonSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [clase CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que especifica las dimensiones de cada botón en la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Llame a [CMFCToolBar::SetSizes](#setsizes) o [CMFCToolBar::SetLockedSizes](#setlockedsizes) para establecer las dimensiones de cada botón en la barra de herramientas.  
  
##  <a name="a-namegetbuttonstylea--cmfctoolbargetbuttonstyle"></a><a name="getbuttonstyle"></a>CMFCToolBar::GetButtonStyle  
 Devuelve el estilo actual del botón de barra de herramientas que se encuentra en el índice especificado.  
  
```  
UINT GetButtonStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice de un botón de barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que especifica el estilo del botón de barra de herramientas. . Consulte [estilos de Control de barra de herramientas](../../mfc/reference/toolbar-control-styles.md) para obtener una lista de los estilos posibles.  
  
### <a name="remarks"></a>Comentarios  
 Llame a [CMFCToolBar::SetButtonStyle](#setbuttonstyle) para establecer el estilo de un botón de barra de herramientas  
  
##  <a name="a-namegetbuttontexta--cmfctoolbargetbuttontext"></a><a name="getbuttontext"></a>CMFCToolBar::GetButtonText  
 Devuelve la etiqueta de texto de un botón que tiene un índice especificado.  
  
```  
CString GetButtonText(int nIndex) const;  
  
void GetButtonText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 El índice de un botón de barra de herramientas.  
  
 [out] `rString`  
 El texto de la etiqueta del botón de barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 El texto de la etiqueta del botón de barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Llame a [CMFCToolBar::SetButtonText](#setbuttontext) o [CMFCToolBar::SetToolBarBtnText](#settoolbarbtntext) para establecer la etiqueta de texto.  
  
##  <a name="a-namegetcoldimagesa--cmfctoolbargetcoldimages"></a><a name="getcoldimages"></a>CMFCToolBar::GetColdImages  
 Devuelve un puntero a la colección de imágenes de botón de barra de herramientas frío en la aplicación.  
  
```  
static CMFCToolBarImages* GetColdImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la colección de imágenes de botón de barra de herramientas frío.  
  
### <a name="remarks"></a>Comentarios  
 Imágenes frías son los que se utilizan cuando el usuario no está interactuando con los botones de barra de herramientas. Llame a [CMFCToolBar::LoadBitmapEx](#loadbitmapex) o [CMFCToolBar::LoadBitmap](#loadbitmap) para cargar las imágenes en frías.  
  
##  <a name="a-namegetcolumnwidtha--cmfctoolbargetcolumnwidth"></a><a name="getcolumnwidth"></a>CMFCToolBar::GetColumnWidth  
 Devuelve el ancho de los botones de barra de herramientas.  
  
```  
virtual int GetColumnWidth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que especifica el ancho de los botones de barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para calcular el diseño de la barra de herramientas. Invalide este método en una clase derivada para especificar un ancho de columna diferente de la barra de herramientas.  
  
##  <a name="a-namegetcommandbuttonsa--cmfctoolbargetcommandbuttons"></a><a name="getcommandbuttons"></a>CMFCToolBar::GetCommandButtons  
 Devuelve una lista de botones que tienen un identificador de comando especificado de todas las barras de herramientas en la aplicación.  
  
```  
static int GetCommandButtons(
    UINT uiCmd,  
    CObList& listButtons);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando de los botones.  
  
 [out] `listButtons`  
 Una referencia a un [clase CObList](../../mfc/reference/coblist-class.md) objeto que recibe la lista de botones de barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de botones que tienen el identificador de comando especificado.  
  
##  <a name="a-namegetcounta--cmfctoolbargetcount"></a><a name="getcount"></a>CMFCToolBar::GetCount  
 Devuelve el número de botones y separadores en la barra de herramientas.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de botones y separadores en la barra de herramientas.  
  
##  <a name="a-namegetcustomizebuttona--cmfctoolbargetcustomizebutton"></a><a name="getcustomizebutton"></a>CMFCToolBar::GetCustomizeButton  
 Recupera un puntero a la `CMFCCustomizeButton` objeto asociado con la barra de herramientas.  
  
```  
CMFCCustomizeButton* GetCustomizeButton();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CMFCCustomizeButton` objeto asociado con la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Este método recupera el **personalizar** botón que aparece al final de la barra de herramientas. Utilice la [CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton) método para agregar el **personalizar** botón a la barra de herramientas.  
  
 Puede llamar a la [CMFCToolBar::IsExistCustomizeButton](#isexistcustomizebutton) método para determinar si la barra de herramientas contiene válido `CMFCCustomizeButton` objeto.  
  
##  <a name="a-namegetdefaultimagea--cmfctoolbargetdefaultimage"></a><a name="getdefaultimage"></a>CMFCToolBar::GetDefaultImage  
 Devuelve el índice de la imagen predeterminada para un botón de barra de herramientas con un identificador de comando especificado.  
  
```  
static int GetDefaultImage(UINT uiID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiID`  
 Especifica el identificador de comando del botón.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de la imagen de la barra de herramientas en la lista de imágenes compartida.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método compartido para recuperar el índice de la imagen predeterminada para un botón de barra de herramientas con el identificador de comando especificado. El valor devuelto es un índice en la colección de imágenes de botón de barra de herramientas para todas las barras de herramientas en la aplicación compartida. Llame a la [CMFCToolBar::GetImages](#getimages) método para obtener un puntero a esta colección.  
  
##  <a name="a-namegetdisabledimagesa--cmfctoolbargetdisabledimages"></a><a name="getdisabledimages"></a>CMFCToolBar::GetDisabledImages  
 Devuelve un puntero a la colección de imágenes que se utilizan para los botones de barras de herramientas de la aplicación.  
  
```  
static CMFCToolBarImages* __stdcall GetDisabledImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la colección de imágenes de botones de barras de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Cargar imágenes de botones de barras de herramientas mediante el [CMFCToolBarEditBoxButton clase](../../mfc/reference/cmfctoolbareditboxbutton-class.md) y [CMFCToolBar::LoadBitmap](#loadbitmap) métodos.  
  
##  <a name="a-namegetdisabledmenuimagesa--cmfctoolbargetdisabledmenuimages"></a><a name="getdisabledmenuimages"></a>CMFCToolBar::GetDisabledMenuImages  
 Devuelve un puntero a la colección de imágenes que se utilizan para los botones de menú deshabilitado en la aplicación.  
  
```  
static CMFCToolBarImages* __stdcall GetDisabledMenuImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la colección de imágenes de menú deshabilitado.  
  
### <a name="remarks"></a>Comentarios  
 Cargar las imágenes deshabilitadas mediante el [CMFCToolBarEditBoxButton clase](../../mfc/reference/cmfctoolbareditboxbutton-class.md) método.  
  
##  <a name="a-namegetdroppeddownmenua--cmfctoolbargetdroppeddownmenu"></a><a name="getdroppeddownmenu"></a>CMFCToolBar::GetDroppedDownMenu  
 Recupera un puntero al objeto de botón de menú que se muestra actualmente su submenú.  
  
```  
CMFCToolBarMenuButton* GetDroppedDownMenu(int* pIndex = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `pIndex`  
 Recibe el índice del botón en la colección de botones de barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto de botón de menú que muestra su submenú o `NULL` si ningún menú muestra su submenú.  
  
### <a name="remarks"></a>Comentarios  
 Si devuelve este método no `NULL` valor y `pIndex` no `NULL`, el valor indicado por `pIndex` se establece en el índice del botón de menú de la colección de botones de barra de herramientas.  
  
##  <a name="a-namegetgraydisabledbuttonsa--cmfctoolbargetgraydisabledbuttons"></a><a name="getgraydisabledbuttons"></a>CMFCToolBar::GetGrayDisabledButtons  
 Especifica si las imágenes de los botones deshabilitados están atenuadas versiones de las imágenes de botón normal, o tomado de la colección de imágenes de botón deshabilitado.  
  
```  
BOOL GetGrayDisabledButtons() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`para atenuar las imágenes de los botones deshabilitados; `FALSE`obtener imágenes de la colección de imágenes deshabilitadas.  
  
### <a name="remarks"></a>Comentarios  
 Utilice [CMFCToolBar::SetGrayDisabledButtons](#setgraydisabledbuttons) para cambiar entre imágenes atenuadas y las imágenes de la colección de imágenes deshabilitadas.  
  
##  <a name="a-namegethighlightedbuttona--cmfctoolbargethighlightedbutton"></a><a name="gethighlightedbutton"></a>CMFCToolBar::GetHighlightedButton  
 Devuelve un puntero al botón de barra de herramientas seleccionada actualmente.  
  
```  
CMFCToolBarButton* GetHighlightedButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un objeto de botón de barra de herramientas; o `NULL` si no hay ningún botón está resaltado.  
  
### <a name="remarks"></a>Comentarios  
 Si tiene el foco de teclado, se resalta un botón de barra de herramientas. También se resalta un botón de barra de herramientas si los botones de barra de herramientas de seguimiento en esta aplicación (para obtener más información, consulte [CMFCToolBar::GetHotBorder](#gethotborder) y [CMFCToolBar::SetHotBorder](#sethotborder)) y cuando ningún botón de barra de herramientas que apunta el mouse o el elemento de menú tiene el foco de teclado.  
  
##  <a name="a-namegethotbordera--cmfctoolbargethotborder"></a><a name="gethotborder"></a>CMFCToolBar::GetHotBorder  
 Determina si los botones de barra de herramientas son *seguimiento*. Si un botón es el seguimiento, se resalta cuando el mouse pasa sobre ella.  
  
```  
BOOL GetHotBorder() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si los botones de barra de herramientas de seguimiento; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, los botones de barra de herramientas son el seguimiento.  
  
##  <a name="a-namegethottextcolora--cmfctoolbargethottextcolor"></a><a name="gethottextcolor"></a>CMFCToolBar::GetHotTextColor  
 Devuelve el color del texto de los botones de barra de herramientas resaltados.  
  
```  
static COLORREF GetHotTextColor();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que representa el color de resaltado de texto actual.  
  
### <a name="remarks"></a>Comentarios  
 Llame a [CMFCToolBar::SetHotTextColor](#sethottextcolor) para establecer un nuevo color de texto para los botones de barra de herramientas resaltados.  
  
##  <a name="a-namegethwndlastfocusa--cmfctoolbargethwndlastfocus"></a><a name="gethwndlastfocus"></a>CMFCToolBar::GetHwndLastFocus  
 Devuelve un identificador a la ventana que tenía el foco de entrada, justo antes de la barra de herramientas.  
  
```  
HWND GetHwndLastFocus() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador de ventana que no se derive de [CMFCBaseToolBar clase](../../mfc/reference/cmfcbasetoolbar-class.md), que anteriormente tenía el foco de entrada o `NULL` si no hay ninguna ventana.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un `CMFCToolBar` control recibe el foco de entrada, que almacena un identificador de ventana que perdió el foco para que pueda restaurar posteriormente.  
  
##  <a name="a-namegetignoresettexta--cmfctoolbargetignoresettext"></a><a name="getignoresettext"></a>CMFCToolBar::GetIgnoreSetText  
 Especifica si se omiten las llamadas para establecer las etiquetas de los botones.  
  
```  
BOOL GetIgnoreSetText() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se omiten las llamadas para establecer las etiquetas de botón; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetimagesa--cmfctoolbargetimages"></a><a name="getimages"></a>CMFCToolBar::GetImages  
 Devuelve un puntero a la colección de forma predeterminada, las imágenes de botón en la aplicación.  
  
```  
static CMFCToolBarImages* GetImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [CMFCToolBarImages clase](../../mfc/reference/cmfctoolbarimages-class.md) objeto que contiene la colección de imágenes predeterminado para todas las barras de herramientas en la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Este método compartido proporciona acceso a la colección de forma predeterminada, todas las imágenes de la barra de herramientas de la aplicación. Llame a la [CMFCToolBar::LoadBitmap](#loadbitmap) para agregar imágenes a la colección.  
  
##  <a name="a-namegetimagesizea--cmfctoolbargetimagesize"></a><a name="getimagesize"></a>CMFCToolBar::GetImageSize  
 Devuelve el tamaño actual de imágenes de botón de barra de herramientas.  
  
```  
CSize GetImageSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [clase CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que representa el tamaño actual de imágenes de botón de barra de herramientas.  
  
##  <a name="a-namegetimagesoffseta--cmfctoolbargetimagesoffset"></a><a name="getimagesoffset"></a>CMFCToolBar::GetImagesOffset  
 Devuelve el desplazamiento del índice utilizado para buscar imágenes de los botones de la barra de herramientas para esta barra de herramientas en la lista global de imágenes de botón de barra de herramientas.  
  
```  
int GetImagesOffset() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El desplazamiento del índice de las imágenes de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Todas las imágenes de barra de herramientas predeterminada se almacenan en la plantilla global [CMFCToolBarImages clase](../../mfc/reference/cmfctoolbarimages-class.md) lista. Las imágenes para cada botón en la barra de herramientas se almacenan consecutivamente en esa lista. Para calcular el índice de la imagen, agregue el índice del botón en la barra de herramientas para el desplazamiento del principio de la lista de imágenes para ese botón de barra de herramientas.  
  
 Llame a [CMFCToolBar::ButtonToIndex](#buttontoindex) para obtener el índice de un botón de barra de herramientas recibe un puntero al botón.  
  
 Llame a [CMFCToolBar::GetImages](#getimages) para obtener un puntero a la colección de imágenes de la barra de herramientas.  
  
##  <a name="a-namegetinvalidateitemrecta--cmfctoolbargetinvalidateitemrect"></a><a name="getinvalidateitemrect"></a>CMFCToolBar::GetInvalidateItemRect  
 Recupera la región del área de cliente que debe volver a dibujar el botón en el índice especificado.  
  
```  
virtual void GetInvalidateItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 El índice del botón para el que se va a recuperar el área de cliente.  
  
 [out] `lpRect`  
 Un puntero a un `RECT` objeto que recibe la región del área de cliente.  
  
### <a name="remarks"></a>Comentarios  
 El `lpRect` parámetro no debe ser `NULL`. Si no existe ningún botón en el índice proporcionado, `lpRect` recibe un `RECT` objeto que se inicializa en cero.  
  
##  <a name="a-namegetitemida--cmfctoolbargetitemid"></a><a name="getitemid"></a>CMFCToolBar::GetItemID  
 Devuelve el identificador de comando del botón de barra de herramientas en un índice especificado.  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice del botón de barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de comando del botón de barra de herramientas; o bien, cero si no existe el botón con el índice especificado.  
  
##  <a name="a-namegetitemrecta--cmfctoolbargetitemrect"></a><a name="getitemrect"></a>CMFCToolBar::GetItemRect  
 Devuelve el rectángulo delimitador del botón en un índice especificado.  
  
```  
virtual void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice de un botón de barra de herramientas.  
  
 [out] `lpRect`  
 Un puntero a `CRect` objeto que recibe las coordenadas de la imagen del rectángulo delimitador.  
  
### <a name="remarks"></a>Comentarios  
 El `CRect` objeto al que `lpRect` puntos se establece en 0 si no existe un botón en el índice especificado.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `GetItemRect` método de la `CMFCToolBar` clase. Este fragmento de código forma parte de la [ejemplo de demostración de IE](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo Nº&6;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo&#9;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_4.cpp)]  
  
##  <a name="a-namegetlargecoldimagesa--cmfctoolbargetlargecoldimages"></a><a name="getlargecoldimages"></a>CMFCToolBar::GetLargeColdImages  
 Devuelve un puntero a la colección de imágenes de botón de barra de herramientas frío en la aplicación.  
  
```  
static CMFCToolBarImages* GetLargeColdImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la colección de imágenes frías grandes.  
  
### <a name="remarks"></a>Comentarios  
 Imágenes frías son los que se utilizan cuando el usuario no está interactuando con los botones de barra de herramientas. Llame a [CMFCToolBar::LoadBitmapEx](#loadbitmapex) para cargar las imágenes grandes frías.  
  
##  <a name="a-namegetlargedisabledimagesa--cmfctoolbargetlargedisabledimages"></a><a name="getlargedisabledimages"></a>CMFCToolBar::GetLargeDisabledImages  
 Devuelve un puntero a la colección de imágenes de botón de barra de herramientas deshabilitado en la aplicación.  
  
```  
static CMFCToolBarImages* GetLargeDisabledImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la colección de imágenes de botón de barra de herramientas deshabilitado.  
  
### <a name="remarks"></a>Comentarios  
 Imágenes de gran tamaño son versiones grandes de las imágenes de botón normal de la barra de herramientas. Llame a [CMFCToolBar::LoadBitmapEx](#loadbitmapex) o [CMFCToolBar::LoadBitmap](#loadbitmap) para cargar las imágenes grandes.  
  
##  <a name="a-namegetlargeimagesa--cmfctoolbargetlargeimages"></a><a name="getlargeimages"></a>CMFCToolBar::GetLargeImages  
 Devuelve un puntero a la colección de imágenes de botón de barra de herramientas en la aplicación.  
  
```  
static CMFCToolBarImages* GetLargeImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la colección de imágenes de botón de barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Imágenes de gran tamaño son versiones grandes de las imágenes de botón normal de la barra de herramientas. Llame a [CMFCToolBar::LoadBitmapEx](#loadbitmapex) para cargar las imágenes grandes.  
  
##  <a name="a-namegetlockedcoldimagesa--cmfctoolbargetlockedcoldimages"></a><a name="getlockedcoldimages"></a>CMFCToolBar::GetLockedColdImages  
 Devuelve un puntero a la colección de imágenes frías bloqueadas en la barra de herramientas.  
  
```  
CMFCToolBarImages* GetLockedColdImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la colección de imágenes frías bloqueadas, o `NULL` si la barra de herramientas no está bloqueado.  
  
### <a name="remarks"></a>Comentarios  
 Las imágenes bloqueadas son versiones de las imágenes de botón normal de la barra de herramientas que el marco de trabajo que se utiliza cuando el usuario no puede personalizar la barra de herramientas. Imágenes frías son los que se utilizan cuando el usuario no está interactuando con los botones de barra de herramientas.  
  
 Este método devuelve `NULL` si la barra de herramientas no está bloqueado. Este método también genera un error de aserción en compilaciones de depuración si la barra de herramientas no está bloqueado. Para obtener más información acerca de las barras de herramientas bloqueadas, consulte [CMFCToolBar::IsLocked](#islocked).  
  
 Llame a la [CMFCToolBar::LoadBitmapEx](#loadbitmapex) para cargar las imágenes bloqueadas frías.  
  
##  <a name="a-namegetlockeddisabledimagesa--cmfctoolbargetlockeddisabledimages"></a><a name="getlockeddisabledimages"></a>CMFCToolBar::GetLockedDisabledImages  
 Devuelve un puntero a la colección de imágenes deshabilitadas bloqueadas en la barra de herramientas.  
  
```  
CMFCToolBarImages* GetLockedDisabledImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la colección de imágenes deshabilitadas bloqueadas, o `NULL` si la barra de herramientas no está bloqueado.  
  
### <a name="remarks"></a>Comentarios  
 Las imágenes bloqueadas son versiones de las imágenes de botón normal de la barra de herramientas que el marco de trabajo que se utiliza cuando el usuario no puede personalizar la barra de herramientas. Imágenes deshabilitadas son las que el marco de trabajo se usa cuando el botón tiene el `TBBS_DISABLED` estilo.  
  
 Este método devuelve `NULL` si la barra de herramientas no está bloqueado. Este método también genera un error de aserción en compilaciones de depuración si la barra de herramientas no está bloqueado. Para obtener más información acerca de las barras de herramientas bloqueadas, consulte [CMFCToolBar::IsLocked](#islocked).  
  
 Llame a la [CMFCToolBar::LoadBitmapEx](#loadbitmapex) para cargar el bloqueado deshabilitado imágenes.  
  
##  <a name="a-namegetlockedimagesa--cmfctoolbargetlockedimages"></a><a name="getlockedimages"></a>CMFCToolBar::GetLockedImages  
 Devuelve un puntero a la colección de imágenes de botón bloqueado en la barra de herramientas.  
  
```  
CMFCToolBarImages* GetLockedImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la colección de imágenes de botón de barra de herramientas bloqueadas, o `NULL` si la barra de herramientas no está bloqueado.  
  
### <a name="remarks"></a>Comentarios  
 Las imágenes bloqueadas son versiones de las imágenes de botón normal de la barra de herramientas que el marco de trabajo que se utiliza cuando el usuario no puede personalizar la barra de herramientas.  
  
 Este método devuelve `NULL` si la barra de herramientas no está bloqueado. Este método también genera un error de aserción en compilaciones de depuración si la barra de herramientas no está bloqueado. Para obtener más información acerca de las barras de herramientas bloqueadas, consulte [CMFCToolBar::IsLocked](#islocked).  
  
##  <a name="a-namegetlockedimagesizea--cmfctoolbargetlockedimagesize"></a><a name="getlockedimagesize"></a>CMFCToolBar::GetLockedImageSize  
 Devuelve el tamaño predeterminado de las imágenes bloqueadas de la barra de herramientas.  
  
```  
CSize GetLockedImageSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` estructura que especifica el tamaño de las imágenes bloqueadas de la barra de herramientas o una cadena vacía `CSize` estructura si la barra de herramientas no está bloqueado.  
  
### <a name="remarks"></a>Comentarios  
 Las imágenes bloqueadas son versiones de las imágenes de botón normal de la barra de herramientas que el marco de trabajo que se utiliza cuando el usuario no puede personalizar la barra de herramientas.  
  
 Este método devuelve un `CSize` estructura con ancho cero y un alto cero si la barra de herramientas no está bloqueado. Este método también genera un error de aserción en compilaciones de depuración si la barra de herramientas no está bloqueado. Para obtener más información acerca de las barras de herramientas bloqueadas, consulte [CMFCToolBar::IsLocked](#islocked).  
  
 Llame a la [CMFCToolBar::SetLockedSizes](#setlockedsizes) método para especificar el tamaño de la imagen bloqueada.  
  
##  <a name="a-namegetlockedmenuimagesa--cmfctoolbargetlockedmenuimages"></a><a name="getlockedmenuimages"></a>CMFCToolBar::GetLockedMenuImages  
 Devuelve un puntero a la colección de la barra de herramientas bloqueado imágenes de menú en la barra de herramientas.  
  
```  
CMFCToolBarImages* GetLockedMenuImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la colección de imágenes de menú de barra de herramientas bloqueadas, o `NULL` si la barra de herramientas no está bloqueado.  
  
### <a name="remarks"></a>Comentarios  
 Las imágenes bloqueadas son versiones de las imágenes de menú normal de la barra de herramientas que el marco de trabajo que se utiliza cuando el usuario no puede personalizar la barra de herramientas.  
  
 Este método devuelve `NULL` si la barra de herramientas no está bloqueado. Este método también genera un error de aserción en compilaciones de depuración si la barra de herramientas no está bloqueado. Para obtener más información acerca de las barras de herramientas bloqueadas, consulte [CMFCToolBar::IsLocked](#islocked).  
  
 Llame a la [CMFCToolBar::LoadBitmapEx](#loadbitmapex) para cargar las imágenes de menú bloqueado.  
  
##  <a name="a-namegetmenubuttonsizea--cmfctoolbargetmenubuttonsize"></a><a name="getmenubuttonsize"></a>CMFCToolBar::GetMenuButtonSize  
 Devuelve el tamaño de los botones de menú en la aplicación.  
  
```  
static CSize GetMenuButtonSize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` objeto que representa el tamaño de los botones de menú, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de los botones de menú de barras de herramientas se mantiene como una variable global y se puede recuperar este método estático.  
  
 Llame a [CMFCToolBar::SetMenuSizes](#setmenusizes) para establecer esta variable global.  
  
##  <a name="a-namegetmenuimagesa--cmfctoolbargetmenuimages"></a><a name="getmenuimages"></a>CMFCToolBar::GetMenuImages  
 Devuelve un puntero a la colección de imágenes de botón de menú de la aplicación.  
  
```  
static CMFCToolBarImages* GetMenuImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la colección de imágenes de menú.  
  
### <a name="remarks"></a>Comentarios  
 Llame a la [CMFCToolBar::LoadBitmapEx](#loadbitmapex) para cargar las imágenes de menú.  
  
 Llame a la [CMFCToolBar::SetMenuSizes](#setmenusizes) para establecer el tamaño de los botones y las imágenes.  
  
##  <a name="a-namegetmenuimagesizea--cmfctoolbargetmenuimagesize"></a><a name="getmenuimagesize"></a>CMFCToolBar::GetMenuImageSize  
 Devuelve el tamaño de imágenes de botón de menú de la aplicación.  
  
```  
static CSize GetMenuImageSize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` objeto que representa el tamaño de las imágenes de menú.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve el tamaño de imágenes en los botones de menú de barra de herramientas que se mantienen como una variable global. Llame a [CMFCToolBar::SetMenuSizes](#setmenusizes) para establecer esta variable global.  
  
##  <a name="a-namegetorigbuttonsa--cmfctoolbargetorigbuttons"></a><a name="getorigbuttons"></a>CMFCToolBar::GetOrigButtons  
 Recupera la colección de botones no personalizada de la barra de herramientas.  
  
```  
const CObList& GetOrigButtons() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la lista de botones no personalizada de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo crea una copia de los botones de barra de herramientas antes de que son personalizados por el usuario. El [CMFCToolBar::SetButtons](#setbuttons) método agrega una copia de cada botón en la matriz proporcionada a la lista de botones original. El [CMFCToolBar::RestoreOriginalState](#restoreoriginalstate) método restaura el estado original de la barra de herramientas mediante la carga del archivo de recursos.  
  
 Para establecer la lista de botones originales de la barra de herramientas, llame a la [CMFCToolBar::SetOrigButtons](#setorigbuttons) método.  
  
##  <a name="a-namegetorigresetbuttonsa--cmfctoolbargetorigresetbuttons"></a><a name="getorigresetbuttons"></a>CMFCToolBar::GetOrigResetButtons  
 Recupera la colección de botones de reinicio no personalizada de la barra de herramientas.  
  
```  
const CObList& GetOrigResetButtons() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la lista de botones de reinicio no personalizada de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario hace clic en el **restablecer** botón durante el modo de personalización, el marco de trabajo usa este método para restaurar los botones que se quitaron de la barra de herramientas.  
  
 El [CMFCToolBar::SetButtons](#setbuttons) método agrega una copia de cada botón de barra de herramientas a la lista de botones de restablecimiento original después de llamar a la [CMFCToolBar::OnReset](#onreset) método. Puede invalidar el [CMFCToolBar::OnReset](#onreset) método para personalizar el aspecto de botones después el usuario presiona el **restablecer** botón.  
  
##  <a name="a-namegetresourceida--cmfctoolbargetresourceid"></a><a name="getresourceid"></a>CMFCToolBar::GetResourceID  
 Recupera el identificador de recurso de la barra de herramientas.  
  
```  
UINT GetResourceID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de recurso de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Llame a la [CMFCToolBar::LoadToolBarEx](#loadtoolbarex) para establecer el identificador de recurso de la barra de herramientas.  
  
##  <a name="a-namegetroutecommandsviaframea--cmfctoolbargetroutecommandsviaframe"></a><a name="getroutecommandsviaframe"></a>CMFCToolBar::GetRouteCommandsViaFrame  
 Determina qué objeto, el marco primario o el propietario, envía comandos a la barra de herramientas.  
  
```  
BOOL GetRouteCommandsViaFrame();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el marco primario envía comandos a la barra de herramientas; 0 si el propietario envía comandos a la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco primario envía comandos a la barra de herramientas. Llame a [CMFCToolBar::SetRouteCommandsViaFrame](#setroutecommandsviaframe) para cambiar este comportamiento.  
  
 Si este método devuelve un valor distinto de cero, puede recuperar un puntero al objeto de marco principal mediante la `CMFCToolBar::GetCommandTarget` método. Vea el ejemplo VisualStudioDemo para obtener un ejemplo que utiliza este método.  
  
##  <a name="a-namegetrowheighta--cmfctoolbargetrowheight"></a><a name="getrowheight"></a>CMFCToolBar::GetRowHeight  
 Devuelve el alto de los botones de barra de herramientas.  
  
```  
virtual int GetRowHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto de los botones de barra de herramientas, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para calcular el diseño de la barra de herramientas. Invalide este método en una clase derivada para especificar un alto diferente de la barra de herramientas.  
  
##  <a name="a-namegetshowtooltipsa--cmfctoolbargetshowtooltips"></a><a name="getshowtooltips"></a>CMFCToolBar::GetShowTooltips  
 Especifica si se muestra información sobre herramientas para los botones de barra de herramientas.  
  
```  
static BOOL GetShowTooltips();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se muestra información sobre herramientas para botones de barra de herramientas; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada se muestra información sobre herramientas. Puede cambiar este indicador estático mediante una llamada a [CMFCToolBar::SetShowTooltips](#setshowtooltips).  
  
##  <a name="a-namegetsiblingtoolbara--cmfctoolbargetsiblingtoolbar"></a><a name="getsiblingtoolbar"></a>CMFCToolBar::GetSiblingToolBar  
 Recupera al elemento relacionado de la barra de herramientas.  
  
```  
CMFCToolBar* GetSiblingToolBar();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la barra de herramientas del mismo nivel.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre cómo habilitar la **mostrar botones en una fila** y **mostrar botones en dos filas** botones, vea [CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar).  
  
##  <a name="a-namegetuserimagesa--cmfctoolbargetuserimages"></a><a name="getuserimages"></a>CMFCToolBar::GetUserImages  
 Devuelve un puntero a la colección de imágenes de botón de barra de herramientas definidas por el usuario en la aplicación.  
  
```  
static CMFCToolBarImages* GetUserImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la colección de imágenes de botón de barra de herramientas definidas por el usuario para todas las barras de herramientas en la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Llame a la [CMFCToolBar::SetUserImages](#setuserimages) para establecer la colección de imágenes definido por el usuario en la aplicación.  
  
##  <a name="a-namehittesta--cmfctoolbarhittest"></a><a name="hittest"></a>CMFCToolBar::HitTest  
 Devuelve el índice del botón de barra de herramientas que se encuentra en la posición especificada.  
  
```  
virtual int HitTest(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 El punto de prueba, en coordenadas de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del botón que se encuentra en la posición especificada, o -1 si no hay ningún botón de este tipo o el botón es un separador.  
  
##  <a name="a-nameinsertbuttona--cmfctoolbarinsertbutton"></a><a name="insertbutton"></a>CMFCToolBar::InsertButton  
 Inserta un botón en la barra de herramientas.  
  
```  
virtual int InsertButton(
    const CMFCToolBarButton& button,  
    INT_PTR iInsertAt=-1);

 
virtual int InsertButton(
    CMFCToolBarButton* pButton,  
    int iInsertAt=-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `button`  
 Especifica el botón Insertar.  
  
 [in] `iInsertAt`  
 Especifica la posición de base cero para insertar en el botón.  
  
### <a name="return-value"></a>Valor devuelto  
 La posición donde se insertó el botón o -1 si un error se produce.  
  
### <a name="remarks"></a>Comentarios  
 Si `iInsertAt` es -1, este método agrega el botón al final de la lista de botones de barra de herramientas.  
  
 Llame a la [CMFCToolBar::InsertSeparator](#insertseparator) método para insertar un separador en la barra de herramientas.  
  
##  <a name="a-nameinsertseparatora--cmfctoolbarinsertseparator"></a><a name="insertseparator"></a>CMFCToolBar::InsertSeparator  
 Inserta un separador en la barra de herramientas.  
  
```  
virtual int InsertSeparator(INT_PTR iInsertAt=-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iInsertAt`  
 Especifica la posición de base cero para insertar separador en. Este parámetro debe ser mayor que 0.  
  
### <a name="return-value"></a>Valor devuelto  
 La posición donde se insertó el separador o -1 si un error se produce.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para insertar un separador entre los dos botones existentes. Si `iInsertAt` es -1, este método agrega el separador al final de la lista de botones de barra de herramientas.  
  
 No puede utilizar este método para agregar un separador a una barra de herramientas vacía.  
  
 Llame a la [CMFCToolBar::InsertButton](#insertbutton) método para insertar un botón en la barra de herramientas.  
  
##  <a name="a-nameinvalidatebuttona--cmfctoolbarinvalidatebutton"></a><a name="invalidatebutton"></a>CMFCToolBar::InvalidateButton  
 Invalida el área cliente del botón de barra de herramientas que existe en el índice proporcionado.  
  
```  
CMFCToolBarButton* InvalidateButton(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Índice de base cero del botón de la barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CMFCToolBarButton` objeto que existe en el índice proporcionado o `NULL` si no existe el objeto existe.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se actualiza el área de cliente que está asociado con un botón de barra de herramientas. Llama a la [CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect) método con el rectángulo de cliente de la `CMFCToolBarButton` objeto que existe en el índice proporcionado.  
  
##  <a name="a-nameisaddremovequickcustomizea--cmfctoolbarisaddremovequickcustomize"></a><a name="isaddremovequickcustomize"></a>CMFCToolBar::IsAddRemoveQuickCustomize  
 Determina si un usuario puede agregar o quitar botones de barra de herramientas mediante el **personalizar** opción de menú.  
  
```  
BOOL IsAddRemoveQuickCustomize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si un usuario puede utilizar el **personalizar** opción de menú para modificar la barra de herramientas; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisaltcustomizemodea--cmfctoolbarisaltcustomizemode"></a><a name="isaltcustomizemode"></a>CMFCToolBar::IsAltCustomizeMode  
 Especifica si *personalización rápida* se usa para arrastrar un botón. Cuando se habilita la personalización rápida, un usuario puede presione y mantenga presionada la tecla Alt y arrastre un botón hasta una nueva ubicación.  
  
```  
static BOOL __stdcall IsAltCustomizeMode();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se utiliza la personalización rápida a arrastrar un botón; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisautograyinactiveimagesa--cmfctoolbarisautograyinactiveimages"></a><a name="isautograyinactiveimages"></a>CMFCToolBar::IsAutoGrayInactiveImages  
 Especifica si está habilitada la generación automática de imágenes de los botones inactivo (no resaltado).  
  
```  
static BOOL IsAutoGrayInactiveImages();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si está habilitada la opción de dim automáticamente imágenes inactivas; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Puede habilitar o deshabilitar la atenuación automática de imágenes inactivas mediante una llamada a [CMFCToolBar::AutoGrayInactiveImages](#autograyinactiveimages).  
  
##  <a name="a-nameisbasiccommanda--cmfctoolbarisbasiccommand"></a><a name="isbasiccommand"></a>CMFCToolBar::IsBasicCommand  
 Determina si es un comando en la lista de comandos básicos.  
  
```  
static BOOL IsBasicCommand(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 Especifica el comando para comprobar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el comando especificado pertenece a la lista de comandos básicos; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método estático determina si el comando especificado por `uiCmd` pertenece a la lista global de los comandos básicos. Puede cambiar la lista de comandos básicas mediante una llamada a [CMFCToolBar::AddBasicCommand](#addbasiccommand) o [CMFCToolBar::SetBasicCommands](#setbasiccommands).  
  
##  <a name="a-nameisbuttonextrasizeavailablea--cmfctoolbarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFCToolBar::IsButtonExtraSizeAvailable  
 Determina si la barra de herramientas puede mostrar botones que se han extendido bordes.  
  
```  
virtual BOOL IsButtonExtraSizeAvailable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si puede mostrar la barra botones con el tamaño de borde adicionales; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve el objeto de barra de herramientas `TRUE` si puede mostrar botones que se han extendido bordes. Un botón de barra de herramientas llama a este método cuando controla la [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd) notificación y establecerá su indicador de tamaño de borde adicionales interno en consecuencia. Este indicador interno puede recuperarse más adelante llamando a [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).  
  
 Invalide este método en una clase derivada de `CMFCToolBar` y devolver `TRUE` si puede mostrar los botones de barra de herramientas con el tamaño del borde adicional y devolver la barra de `FALSE` en caso contrario. La implementación predeterminada devuelve `TRUE`.  
  
##  <a name="a-nameisbuttonhighlighteda--cmfctoolbarisbuttonhighlighted"></a><a name="isbuttonhighlighted"></a>CMFCToolBar::IsButtonHighlighted  
 Determina si se resalta el botón especificado.  
  
```  
BOOL IsButtonHighlighted(int iButton) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iButton`  
 Especifica el índice de un botón de barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se resalta el botón especificado; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameiscommandpermitteda--cmfctoolbariscommandpermitted"></a><a name="iscommandpermitted"></a>CMFCToolBar::IsCommandPermitted  
 Determina si se permite un comando.  
  
```  
static BOOL IsCommandPermitted(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 Especifica el comando para comprobar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se permite el comando especificado; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método estático determina si el comando especificado por `uiCmd` pertenece a la lista global de comandos no permitida.  
  
 Puede cambiar la lista de comandos no permitida llamando [CMFCToolBar::SetNonPermittedCommands](#setnonpermittedcommands).  
  
##  <a name="a-nameiscommandrarelyuseda--cmfctoolbariscommandrarelyused"></a><a name="iscommandrarelyused"></a>CMFCToolBar::IsCommandRarelyUsed  
 Determina si un comando rara vez se usa.  
  
```  
static BOOL IsCommandRarelyUsed(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 Especifica el comando para comprobar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el comando especificado se utiliza muy poco; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El `IsCommandRarelyUsed` método devuelve `FALSE` cuando se producen uno o más de las condiciones siguientes:  
  
-   El comando especificado pertenece a la lista de comandos básicos  
  
-   El comando especificado no es uno de los comandos estándares  
  
-   El marco de trabajo está en modo de personalización  
  
-   La lista de comandos básicas está vacía  
  
-   Más del 20% de las llamadas de comando son llamadas al comando especificado.  
  
##  <a name="a-nameiscustomizemodea--cmfctoolbariscustomizemode"></a><a name="iscustomizemode"></a>CMFCToolBar::IsCustomizeMode  
 Especifica si el marco de la barra de herramientas está en modo de personalización.  
  
```  
static BOOL IsCustomizeMode();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el marco de trabajo está en modo de personalización; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Puede alternar el modo de personalización mediante una llamada a [CMFCToolBar::SetCustomizeMode](#setcustomizemode).  
  
 El marco de trabajo cambia el modo cuando el usuario invoca el cuadro de diálogo de personalización ( [CMFCToolBarsCustomizeDialog clase](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)).  
  
##  <a name="a-nameisdragbuttona--cmfctoolbarisdragbutton"></a><a name="isdragbutton"></a>CMFCToolBar::IsDragButton  
 Determina si se arrastra un botón de barra de herramientas.  
  
```  
BOOL IsDragButton(const CMFCToolBarButton* pButton) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Puntero a un botón de barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se arrastra el botón especificado; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisexistcustomizebuttona--cmfctoolbarisexistcustomizebutton"></a><a name="isexistcustomizebutton"></a>CMFCToolBar::IsExistCustomizeButton  
 Determina si la barra de herramientas contiene el **personalizar** botón.  
  
```  
BOOL IsExistCustomizeButton();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de herramientas contiene el **personalizar** botón; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si este método devuelve `TRUE`, [CMFCToolBar::GetCustomizeButton](#getcustomizebutton) método devuelve un puntero a la **personalizar** botón que aparece al final de la barra de herramientas.  
  
 Utilice la [CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton) método para agregar el **personalizar** botón a la barra de herramientas.  
  
##  <a name="a-nameisfloatinga--cmfctoolbarisfloating"></a><a name="isfloating"></a>CMFCToolBar::IsFloating  
 Determina si la barra de herramientas es flotante.  
  
```  
virtual BOOL IsFloating() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de herramientas es flotante; de lo contrario, `FALSE`.  
  
##  <a name="a-nameislargeiconsa--cmfctoolbarislargeicons"></a><a name="islargeicons"></a>CMFCToolBar::IsLargeIcons  
 Especifica si las barras de herramientas en la aplicación actualmente mostrarán iconos grandes.  
  
```  
static BOOL IsLargeIcons();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la aplicación utiliza iconos grandes; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llame a [CMFCToolBar::SetLargeIcons](#setlargeicons) para alternar entre iconos grandes y los iconos normales.  
  
 El marco de trabajo cambia automáticamente el modo cuando el usuario alterna la **iconos grandes** casilla de verificación en la **opciones** página de la **personalización** cuadro de diálogo.  
  
##  <a name="a-nameislastcommandfrombuttona--cmfctoolbarislastcommandfrombutton"></a><a name="islastcommandfrombutton"></a>CMFCToolBar::IsLastCommandFromButton  
 Determina si se ejecuta el último comando se envió desde el botón de barra de herramientas especificada.  
  
```  
static BOOL IsLastCommandFromButton(CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Puntero al botón.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se envió el último comando del botón que `pButton` especifica; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método obtiene un puntero a un [estructura MSG](../../mfc/reference/msg-structure1.md) llamando a `CWnd::GetCurrentMessage`. A continuación, compara la `HWND` del botón con el `MSG::lParam` y `MSG::hwnd` miembros para determinar si el botón fue el origen del comando.  
  
##  <a name="a-nameislockeda--cmfctoolbarislocked"></a><a name="islocked"></a>CMFCToolBar::IsLocked  
 Determina si la barra de herramientas está bloqueado.  
  
```  
BOOL IsLocked() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de herramientas está bloqueado; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve `TRUE` cuando el usuario no puede realizar las tareas de personalización, como cambiar la posición de los botones de barra de herramientas.  
  
 Barras de herramientas bloqueadas utilizar listas de imágenes distintas. Para obtener más información acerca de estas listas de imágenes, consulte [CMFCToolBar::LoadBitmapEx](#loadbitmapex).  
  
##  <a name="a-nameisonerowwithsiblinga--cmfctoolbarisonerowwithsibling"></a><a name="isonerowwithsibling"></a>CMFCToolBar::IsOneRowWithSibling  
 Determina si la barra de herramientas y la barra de herramientas del mismo nivel se colocan en la misma fila.  
  
```  
BOOL IsOneRowWithSibling();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de herramientas y del mismo nivel se colocan en la misma fila. de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El [CMFCCustomizeButton::CreatePopupMenu](http://msdn.microsoft.com/en-us/e501083e-f78e-4d8d-900c-40bd6e2bb7f8) método llama a este método para determinar cómo mostrar la **personalizar** menú emergente. Si este método devuelve `TRUE`, el marco de trabajo muestra el **mostrar botones en una fila** botón. De lo contrario, el marco de trabajo muestra el **mostrar botones en dos filas** botón.  
  
 Normalmente no tiene que utilizar este método. Para habilitar la **mostrar botones en una fila** o **mostrar botones en dos filas** botones, llame a [CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar).  
  
##  <a name="a-nameisresourcechangeda--cmfctoolbarisresourcechanged"></a><a name="isresourcechanged"></a>CMFCToolBar::IsResourceChanged  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsResourceChanged() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameissiblinga--cmfctoolbarissibling"></a><a name="issibling"></a>CMFCToolBar::IsSibling  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsSibling();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisuserdefineda--cmfctoolbarisuserdefined"></a><a name="isuserdefined"></a>CMFCToolBar::IsUserDefined  
 Especifica si la barra de herramientas está definido por el usuario.  
  
```  
BOOL IsUserDefined() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de herramientas creada por el usuario; de lo contrario, `FALSE`.  
  
##  <a name="a-nameloadbitmapa--cmfctoolbarloadbitmap"></a><a name="loadbitmap"></a>CMFCToolBar::LoadBitmap  
 Carga las imágenes de la barra de herramientas desde los recursos de la aplicación.  
  
```  
virtual BOOL LoadBitmap(
    UINT uiResID,  
    UINT uiColdResID=0,  
    UINT uiMenuResID=0,  
    BOOL bLocked=FALSE,  
    UINT uiDisabledResID=0,  
    UINT uiMenuDisabledResID=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de barra de herramientas activa.  
  
 [in] `uiColdResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de barra de herramientas inactiva.  
  
 [in] `uiMenuResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de menú regular.  
  
 [in] `bLocked`  
 `TRUE`Para bloquear la barra de herramientas; de lo contrario, `FALSE`.  
  
 [in] `uiDisabledResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de barra de herramientas deshabilitada.  
  
 [in] `uiMenuDisabledResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de menú deshabilitado.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El [CMFCToolBar::LoadToolBarEx](#loadtoolbarex) método llama a este método para cargar las imágenes que están asociadas a la barra de herramientas. Invalide este método para realizar la carga personalizada de recursos de imagen.  
  
 Llame al método `LoadBitmapEx` para cargar imágenes adicionales después de crear la barra de herramientas.  
  
##  <a name="a-nameloadbitmapexa--cmfctoolbarloadbitmapex"></a><a name="loadbitmapex"></a>CMFCToolBar::LoadBitmapEx  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL LoadBitmapEx(
    CMFCToolBarInfo& params,  
    BOOL bLocked = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `params`  
 [in] `bLocked`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameloadlargeiconsstatea--cmfctoolbarloadlargeiconsstate"></a><a name="loadlargeiconsstate"></a>CMFCToolBar::LoadLargeIconsState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BOOL __stdcall LoadLargeIconsState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameloadparametersa--cmfctoolbarloadparameters"></a><a name="loadparameters"></a>CMFCToolBar::LoadParameters  
 Carga las opciones de la barra de herramientas global del registro de Windows.  
  
```  
static BOOL LoadParameters(LPCTSTR lpszProfileName=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Especifica la ruta de acceso relativa de la clave del registro de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método carga parámetros globales, como el tipo de animación de menús, el estilo de sombra de menú y si desea mostrar iconos grandes en el registro de Windows.  
  
 El [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate) método llama a este método como parte del proceso de inicialización de la aplicación.  
  
##  <a name="a-nameloadstatea--cmfctoolbarloadstate"></a><a name="loadstate"></a>CMFCToolBar::LoadState  
 Carga la información de estado de la barra de herramientas desde el registro de Windows.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Especifica la ruta de acceso relativa de la clave del registro de Windows.  
  
 [in] `nIndex`  
 Especifica el identificador del control de la barra de herramientas.  
  
 [in] `uiID`  
 Especifica el identificador de recurso de la barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método como parte del proceso de inicialización de la aplicación. Para obtener más información, consulte [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate).  
  
##  <a name="a-nameloadtoolbara--cmfctoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CMFCToolBar::LoadToolBar  
 Carga la barra de herramientas de recursos de aplicación.  
  
```  
virtual BOOL LoadToolBar(
    UINT uiResID,  
    UINT uiColdResID=0,  
    UINT uiMenuResID=0,  
    BOOL bLocked=FALSE,  
    UINT uiDisabledResID=0,  
    UINT uiMenuDisabledResID=0,  
    UINT uiHotResID=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiResID`  
 El identificador de recurso de la barra de herramientas.  
  
 [in] `uiColdResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de barra de herramientas inactiva.  
  
 [in] `uiMenuResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de menú regular.  
  
 [in] `bLocked`  
 Un valor booleano que especifica si la barra de herramientas está bloqueado o no. Si este parámetro es `TRUE`, la barra de herramientas está bloqueado. De lo contrario, la barra de herramientas no está bloqueado.  
  
 [in] `uiDisabledResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de barra de herramientas deshabilitada.  
  
 [in] `uiMenuDisabledResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de menú deshabilitado.  
  
 [in] `uiHotResID`  
 El identificador de recurso del mapa de bits que hace referencia a las imágenes de barra de herramientas activa.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método durante la inicialización para cargar las imágenes que están asociadas a la barra de herramientas.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `LoadToolBar` método en la `CMFCToolBar` clase. Este fragmento de código forma parte de la [ejemplo de demostración de IE](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo Nº&6;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo&#7;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_3.cpp)]  
  
##  <a name="a-nameloadtoolbarexa--cmfctoolbarloadtoolbarex"></a><a name="loadtoolbarex"></a>CMFCToolBar::LoadToolBarEx  
 Carga de la barra de herramientas de recursos de aplicación mediante la `CMFCToolBarInfo` clase auxiliar para habilitar la aplicación para usar imágenes de gran tamaño.  
  
```  
virtual BOOL LoadToolBarEx(
    UINT uiToolbarResID,  
    CMFCToolBarInfo& params,  
    BOOL bLocked=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiToolbarResID`  
 El identificador de recurso de la barra de herramientas.  
  
 [in] `params`  
 Una referencia a un `CMFCToolBarInfo` objeto que contiene los identificadores de recursos para las imágenes de la barra de herramientas.  
  
 [in] `bLocked`  
 Un valor booleano que especifica si la barra de herramientas está bloqueado o no. Si este parámetro es `TRUE`, la barra de herramientas está bloqueado. De lo contrario, la barra de herramientas no está bloqueado.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para cargar imágenes de barra de herramientas de los recursos de aplicación.  
  
##  <a name="a-namemdbllargeimageratioa--cmfctoolbarmdbllargeimageratio"></a><a name="m_dbllargeimageratio"></a>CMFCToolBar::m_dblLargeImageRatio  
 Especifica la proporción entre la dimensión (alto o ancho) de imágenes de gran tamaño y la dimensión de las imágenes normales.  
  
```  
AFX_IMPORT_DATA static double m_dblLargeImageRatio;  
```  
  
### <a name="remarks"></a>Comentarios  
 La proporción predeterminada es 2. Puede cambiar este valor para hacer las imágenes de la barra de herramientas mayor o menor.  
  
 El marco de trabajo usa a este miembro de datos cuando no se especifica un conjunto de imágenes de gran tamaño. Por ejemplo, si se proporciona solo el conjunto de imágenes pequeñas con tamaño de 16 x 16 y desea que las imágenes de grandes tamaño de 24 x 24, establecer a este miembro de datos a 1.5.  
  
##  <a name="a-namenextmenua--cmfctoolbarnextmenu"></a><a name="nextmenu"></a>CMFCToolBar::NextMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL NextMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonbeforeremovebuttona--cmfctoolbaronbeforeremovebutton"></a><a name="onbeforeremovebutton"></a>CMFCToolBar::OnBeforeRemoveButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnBeforeRemoveButton(
    CMFCToolBarButton* pButton,  
    DROPEFFECT dropEffect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Sin usar.  
  
 [in] `dropEffect`  
 Sin usar.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonchangehota--cmfctoolbaronchangehot"></a><a name="onchangehot"></a>CMFCToolBar::OnChangeHot  
 Llamado por el marco cuando un usuario selecciona un botón en la barra de herramientas.  
  
```  
virtual void OnChangeHot(int iHot);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iHot`  
 Especifica el índice del botón de barra de herramientas que está seleccionado; o -1 si no se selecciona ningún botón de barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para que el usuario selecciona un botón de una barra de herramientas de procesamiento de notificaciones.  
  
##  <a name="a-nameonchangevisualmanagera--cmfctoolbaronchangevisualmanager"></a><a name="onchangevisualmanager"></a>CMFCToolBar::OnChangeVisualManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnChangeVisualManager();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonfillbackgrounda--cmfctoolbaronfillbackground"></a><a name="onfillbackground"></a>CMFCToolBar::OnFillBackground  
 Llamado por el marco de [CBasePane::DoPaint](../../mfc/reference/cbasepane-class.md#dopaint) para rellenar el fondo de la barra de herramientas.  
  
```  
virtual void OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 [CMFCToolBar::DoPaint](#dopaint) llama a este método cuando se ha rellenado el fondo de una barra de herramientas. La implementación predeterminada no hace nada.  
  
 Invalide este método para dibujar el fondo personalizado en las clases derivadas.  
  
##  <a name="a-nameonglobalfontschangeda--cmfctoolbaronglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBar::OnGlobalFontsChanged  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonreseta--cmfctoolbaronreset"></a><a name="onreset"></a>CMFCToolBar::OnReset  
 Restaura la barra de herramientas a su estado original.  
  
```  
virtual void OnReset();
```  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para controlar la notificación acerca de un restablecimiento de la barra de herramientas.  
  
 La implementación predeterminada no hace nada. Invalidar `OnReset` en una clase derivada de `CMFCToolBar` cuando la barra de herramientas tiene botones ficticio que se deben reemplazar cuando la barra de herramientas vuelve a su estado original.  
  
##  <a name="a-nameonsetaccdataa--cmfctoolbaronsetaccdata"></a><a name="onsetaccdata"></a>CMFCToolBar::OnSetAccData  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnSetAccData(long lVal);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lVal`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonsetdefaultbuttontexta--cmfctoolbaronsetdefaultbuttontext"></a><a name="onsetdefaultbuttontext"></a>CMFCToolBar::OnSetDefaultButtonText  
 Restaura el texto de un botón de barra de herramientas a su estado predeterminado.  
  
```  
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Señala un botón, cuyo texto se va a establecer.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`texto Siel se restauró correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para las notificaciones del proceso que se está cambiando el texto de un botón de barra de herramientas a su valor predeterminado.  
  
 La implementación predeterminada carga el texto de un botón de los recursos de aplicación.  
  
##  <a name="a-nameonusertooltipa--cmfctoolbaronusertooltip"></a><a name="onusertooltip"></a>CMFCToolBar::OnUserToolTip  
 Llamado por el marco cuando la información sobre herramientas para un botón que se va a mostrar.  
  
```  
virtual BOOL OnUserToolTip(
    CMFCToolBarButton* pButton,  
    CString& strTTText) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Señala un botón de barra de herramientas para el que es mostrar una información sobre herramientas.  
  
 [out] `strTTText`  
 Una referencia a `CString` objeto que recibe el texto de la información sobre herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si `strTTText` se rellena con el texto de información sobre herramientas; en caso contrario `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando la información sobre herramientas para un botón de barra de herramientas que se va a mostrar. Si `OnUserToolTip` devuelve `TRUE`, el marco de trabajo muestra información sobre herramientas que contiene el texto devuelto por `OnUserToolTip` en `strTTText`. De lo contrario, la información sobre herramientas contiene el texto del botón.  
  
 Reemplazar `OnUserToolTip` para personalizar la información sobre herramientas de botones de barra de herramientas. La implementación predeterminada llama [CMFCToolBar::OnUserToolTip](#onusertooltip) para obtener el texto de información sobre herramientas.  
  
##  <a name="a-nameprevmenua--cmfctoolbarprevmenu"></a><a name="prevmenu"></a>CMFCToolBar::PrevMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PrevMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameprocesscommanda--cmfctoolbarprocesscommand"></a><a name="processcommand"></a>CMFCToolBar::ProcessCommand  
 Publicaciones en un `WM_COMMAND` mensaje en la ventana propietaria de la barra de herramientas.  
  
```  
BOOL ProcessCommand(CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Puntero a un botón en la barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Este método siempre debe devolver `TRUE`. MFC utiliza `FALSE` internamente los valores.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía una `WM_COMMAND` mensaje en la ventana propietaria de la barra de herramientas llamando a [CWnd::PostMessage](../../mfc/reference/cwnd-class.md#postmessage) y pasando el identificador de comando del botón especificado como el `wParam` parámetro.  
  
 Utilice la [ON_COMMAND](http://msdn.microsoft.com/library/f24f8bda-2cf4-49d5-aa3d-6f2e6bb003f2) macro para asignar el `WM_COMMAND` mensaje a una función miembro.  
  
##  <a name="a-nameremoveallbuttonsa--cmfctoolbarremoveallbuttons"></a><a name="removeallbuttons"></a>CMFCToolBar::RemoveAllButtons  
 Quita todos los botones y los separadores de la barra de herramientas.  
  
```  
virtual void RemoveAllButtons();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se vuelve a crear o se destruye una barra de herramientas.  
  
##  <a name="a-nameremovebuttona--cmfctoolbarremovebutton"></a><a name="removebutton"></a>CMFCToolBar::RemoveButton  
 Quita el botón que tiene el índice especificado de la barra de herramientas.  
  
```  
virtual BOOL RemoveButton(int iIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
 Especifica el índice basado en cero del botón que se va a quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método tiene éxito, o `FALSE` si el índice especificado no es válido o el índice hace referencia a la **personalizar** botón.  
  
### <a name="remarks"></a>Comentarios  
 Este método actualiza los atributos adicionales de la barra de herramientas que se ven afectados por la eliminación del botón. Por ejemplo, este método quita los separadores de la barra de herramientas y vuelve a generar la tabla de teclas de método abreviado.  
  
 Para obtener más información acerca de la **personalizar** botón, consulte [CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton).  
  
##  <a name="a-nameremovestatefromregistrya--cmfctoolbarremovestatefromregistry"></a><a name="removestatefromregistry"></a>CMFCToolBar::RemoveStateFromRegistry  
 Elimina la información de estado de la barra de herramientas del registro de Windows.  
  
```  
virtual BOOL RemoveStateFromRegistry(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Especifica la clave del registro donde se encuentra la información de estado.  
  
 [in] `nIndex`  
 El identificador del control de la barra de herramientas.  
  
 [in] `uiID`  
 El identificador de recurso de la barra de herramientas. Si este parámetro es -1, este método utiliza el [CWnd::GetDlgCtrlID](../../mfc/reference/cwnd-class.md#getdlgctrlid) método para recuperar el identificador de recurso.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se elimina una barra de herramientas definidas por el usuario.  
  
 Invalide este método si almacena información de estado adicional en el registro de Windows.  
  
##  <a name="a-namereplacebuttona--cmfctoolbarreplacebutton"></a><a name="replacebutton"></a>CMFCToolBar::ReplaceButton  
 Reemplaza un botón de barra de herramientas con otro botón de barra de herramientas.  
  
```  
int ReplaceButton(
    UINT uiCmd,  
    const CMFCToolBarButton& button,  
    BOOL bAll=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando del botón para reemplazar.  
  
 [in] `button`  
 Una referencia a la `CMFCToolBarButton` para insertar.  
  
 [in] `bAll`  
 Un valor booleano que especifica si se reemplazarán todos los botones con el identificador de comando especificado por `uiCmd`. Si este parámetro es `TRUE`, se reemplazan todos los botones que tienen el identificador de comando especificado. De lo contrario, se reemplaza el primer botón.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de botones que se reemplazan. Este método devuelve 0 si no existe un botón con el identificador de comando especificado en la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método cuando desee agregar botones de barra de herramientas que no se puede cargar desde recursos. Puede crear un botón de marcador de posición en tiempo de diseño y reemplazar ese botón con un botón personalizado al inicializar la barra de herramientas. Vea el ejemplo VisualStudioDemo para obtener un ejemplo que utiliza este método.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `ReplaceButton` método en la `CMFCToolBar` clase. Este fragmento de código forma parte de la [ejemplo de demostración de IE](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo Nº&6;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo&#10;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_5.cpp)]  
  
##  <a name="a-nameresetalla--cmfctoolbarresetall"></a><a name="resetall"></a>CMFCToolBar::ResetAll  
 Restaura todas las barras de herramientas a su estado original.  
  
```  
static void __stdcall ResetAll();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a la [CMFCToolBar::RestoreOriginalState](#restoreoriginalstate) método de cada barra de herramientas en la aplicación que se puede restaurar. Usa el [CMFCToolBar::CanBeRestored](#canberestored) método para determinar si se puede restaurar una barra de herramientas.  
  
##  <a name="a-nameresetallimagesa--cmfctoolbarresetallimages"></a><a name="resetallimages"></a>CMFCToolBar::ResetAllImages  
 Borra todas las colecciones de imagen de barra de herramientas de la aplicación.  
  
```  
static void __stdcall ResetAllImages();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método borra las colecciones de imágenes que inicializan el [CMFCToolBar::LoadToolBar](#loadtoolbar) y [CMFCToolBar::LoadBitmap](#loadbitmap) métodos.  
  
##  <a name="a-nameresetimagesa--cmfctoolbarresetimages"></a><a name="resetimages"></a>CMFCToolBar::ResetImages  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ResetImages();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namerestorefocusa--cmfctoolbarrestorefocus"></a><a name="restorefocus"></a>CMFCToolBar::RestoreFocus  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void RestoreFocus();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namerestoreoriginalstatea--cmfctoolbarrestoreoriginalstate"></a><a name="restoreoriginalstate"></a>CMFCToolBar::RestoreOriginalState  
 Restaura el estado original de una barra de herramientas.  
  
```  
virtual BOOL RestoreOriginalState();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es `TRUE` si el método se realiza correctamente éxito, o `FALSE` si se produce un error en el método o la barra de herramientas está definida por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 Este método carga la barra de herramientas del archivo de recursos mediante la [CMFCToolBar::LoadToolBar](#loadtoolbar) método.  
  
 El marco de trabajo llama a este método cuando el usuario elige el **Restablecer todo** situado en el **las barras de herramientas** página del cuadro de diálogo de personalización.  
  
##  <a name="a-namesaveparametersa--cmfctoolbarsaveparameters"></a><a name="saveparameters"></a>CMFCToolBar::SaveParameters  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BOOL __stdcall SaveParameters(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesavestatea--cmfctoolbarsavestate"></a><a name="savestate"></a>CMFCToolBar::SaveState  
 Guarda la información de estado de la barra de herramientas en el registro de Windows.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Especifica la ruta de acceso relativa de la clave del registro de Windows.  
  
 [in] `nIndex`  
 El identificador del control de la barra de herramientas.  
  
 [in] `uiID`  
 El identificador de recurso de la barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando guarda el estado de la aplicación en el registro. Para obtener más información, consulte [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).  
  
##  <a name="a-namesetbasiccommandsa--cmfctoolbarsetbasiccommands"></a><a name="setbasiccommands"></a>CMFCToolBar::SetBasicCommands  
 Establece la lista de comandos que siempre se muestran cuando un usuario abre un menú.  
  
```  
static void __stdcall SetBasicCommands(CList<UINT,UINT>& lstCommands);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lstCommands`  
 Una referencia a un `CList` objeto que contiene una colección de comandos.  
  
### <a name="remarks"></a>Comentarios  
 Un comando básico siempre se muestra cuando se abre el menú. Este método es significativo cuando el usuario decide ver los comandos usados recientemente.  
  
 Utilice la [CMFCToolBar::AddBasicCommand](#addbasiccommand) para agregar un comando a la lista de comandos básicos. Utilice la [CMFCToolBar::GetBasicCommands](#getbasiccommands) método para recuperar la lista de comandos básicos que se utiliza la aplicación.  
  
 Vea el ejemplo del explorador para obtener un ejemplo que utiliza este método.  
  
##  <a name="a-namesetbuttoninfoa--cmfctoolbarsetbuttoninfo"></a><a name="setbuttoninfo"></a>CMFCToolBar::SetButtonInfo  
 Establece el identificador de comando, el estilo y el Id. de imagen de un botón de barra de herramientas.  
  
```  
void SetButtonInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int iImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Índice de base cero del botón cuyas propiedades se establecen.  
  
 [in] `nID`  
 El identificador de comando del botón.  
  
 [in] `nStyle`  
 El estilo del botón. Consulte [estilos de Control de barra de herramientas](../../mfc/reference/toolbar-control-styles.md) la lista de estilos de botón de barra de herramientas disponibles.  
  
 [in] `iImage`  
 El índice de base cero de imagen del botón (es decir, el índice de la colección de imágenes de la barra de herramientas).  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para establecer las propiedades de un botón de barra de herramientas.  
  
 En compilaciones de depuración, este método genera un error de aserción si el índice especificado por `nIndex` no es válido.  
  
 Llame a la [CMFCToolBar::SetButtonStyle](#setbuttonstyle) para establecer sólo el estilo del botón.  
  
##  <a name="a-namesetbuttonsa--cmfctoolbarsetbuttons"></a><a name="setbuttons"></a>CMFCToolBar::SetButtons  
 Establece los botones de la barra de herramientas.  
  
```  
virtual BOOL SetButtons(
    const UINT* lpIDArray,  
    int nIDCount,  
    BOOL bRemapImages=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpIDArray`  
 Puntero a la matriz de identificadores de comando de los botones para insertar.  
  
 [in] `nIDCount`  
 El número de elementos de `lpIDArray`.  
  
 [in] `bRemapImages`  
 Un valor booleano que especifica si se va a asociar las imágenes de botón existentes con los botones insertados. Si este parámetro es `TRUE`, se reasignan las imágenes.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para quitar los botones existentes de una barra de herramientas e insertar una colección de nuevos botones.  
  
 Este método agrega la **personalizar** botón a la barra de herramientas y lo envía el `AFX_WM_RESETTOOLBAR` mensaje en la ventana principal de la barra de herramientas. Para obtener más información acerca de la **personalizar** botón, consulte [CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton).  
  
##  <a name="a-namesetbuttonstylea--cmfctoolbarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CMFCToolBar::SetButtonStyle  
 Establece el estilo del botón de barra de herramientas en el índice especificado.  
  
```  
virtual void SetButtonStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Índice de base cero del botón de barra de herramientas cuyo estilo que se va a establecer.  
  
 [in] `nStyle`  
 El estilo del botón. Consulte [estilos de Control de barra de herramientas](../../mfc/reference/toolbar-control-styles.md) la lista de estilos de botón de barra de herramientas disponibles.  
  
### <a name="remarks"></a>Comentarios  
 Este método quita el `TBBS_PRESSED` estilo si `nStyle` es `TBBS_DISABLED` porque el usuario no puede hacer clic en un botón deshabilitado.  
  
##  <a name="a-namesetbuttontexta--cmfctoolbarsetbuttontext"></a><a name="setbuttontext"></a>CMFCToolBar::SetButtonText  
 Establece la etiqueta de texto de un botón de barra de herramientas.  
  
```  
BOOL SetButtonText(
    int nIndex,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 El índice del botón de barra de herramientas.  
  
 [in] `lpszText`  
 La etiqueta de texto del botón de barra de herramientas. Debe ser no - `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método tiene éxito; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve `FALSE` si el índice proporcionado no hace referencia a un botón de barra de herramientas válido.  
  
##  <a name="a-namesetcommandusageoptionsa--cmfctoolbarsetcommandusageoptions"></a><a name="setcommandusageoptions"></a>CMFCToolBar::SetCommandUsageOptions  
 Especifica cuándo comandos poco usados no aparecen en el menú de la aplicación.  
  
```  
static BOOL SetCommandUsageOptions(
    UINT nStartCount,  
    UINT nMinUsagePercentage=5);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nStartCount`  
 Especifica el número de veces que los comandos se debe ejecutar antes de que el marco de trabajo muestra los comandos básicos y usados recientemente.  
  
 [in] `nMinUsagePercentage`  
 El porcentaje de veces que se debe ejecutar un comando para que se considere un comando usados recientemente.  
  
### <a name="return-value"></a>Valor devuelto  
 `FALSE`Si `nMinUsagePercentage` es igual a o mayor que 100; en caso contrario, `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para personalizar el algoritmo que aparecen las usa framework para determinar los elementos de menú utilizados recientemente y cómo básicos. Para obtener más información acerca de los comandos básicos, consulte [CMFCToolBar::AddBasicCommand](#addbasiccommand).  
  
 Esta clase usa el `CMFCCmdUsageCount` clase para realizar un seguimiento del recuento de uso de comandos. Para obtener más información acerca de esta clase, vea [CMFCCmdUsageCount clase](../../mfc/reference/cmfccmdusagecount-class.md).  
  
##  <a name="a-namesetcustomizemodea--cmfctoolbarsetcustomizemode"></a><a name="setcustomizemode"></a>CMFCToolBar::SetCustomizeMode  
 Habilita o deshabilita el modo de personalización para todas las barras de herramientas en la aplicación.  
  
```  
static BOOL __stdcall SetCustomizeMode(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 Un valor booleano que especifica si desea habilitar o deshabilitar el modo de personalización. Establezca este parámetro en `TRUE` para habilitar el modo de personalización o `FALSE` para deshabilitarlo.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si llama a este método cambia el modo de personalización; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método ajusta el diseño de y vuelve a dibujar cada barra de herramientas en la aplicación. Llame a la [CMFCToolBar::IsCustomizeMode](#iscustomizemode) método para determinar si la aplicación está en modo de personalización  
  
##  <a name="a-namesetgraydisabledbuttonsa--cmfctoolbarsetgraydisabledbuttons"></a><a name="setgraydisabledbuttons"></a>CMFCToolBar::SetGrayDisabledButtons  
 Especifica si se atenúan los botones disponibles en la barra de herramientas, o si se utilizan imágenes de botón disponible.  
  
```  
void SetGrayDisabledButtons(BOOL bGrayDisabledButtons);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bGrayDisabledButtons`  
 Un valor booleano que especifica cómo mostrar botones disponibles. Si este parámetro es `TRUE`, el marco de trabajo atenúa los botones. De lo contrario, el marco de trabajo utiliza la colección de imágenes disponibles para el botón.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, los botones disponibles aparecen atenuados.  
  
##  <a name="a-namesetheighta--cmfctoolbarsetheight"></a><a name="setheight"></a>CMFCToolBar::SetHeight  
 Establece el alto de la barra de herramientas.  
  
```  
void SetHeight(int cyHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `cyHeight`  
 El alto de la barra de herramientas, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Este método vuelve a dibujar la barra de herramientas cuando establece el alto.  
  
##  <a name="a-namesethelpmodea--cmfctoolbarsethelpmode"></a><a name="sethelpmode"></a>CMFCToolBar::SetHelpMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall SetHelpMode(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bOn`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesethota--cmfctoolbarsethot"></a><a name="sethot"></a>CMFCToolBar::SetHot  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL SetHot(CMFCToolBarButton* pMenuButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMenuButton`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesethotbordera--cmfctoolbarsethotborder"></a><a name="sethotborder"></a>CMFCToolBar::SetHotBorder  
 Especifica si los botones de barra de herramientas de seguimiento.  
  
```  
void SetHotBorder(BOOL bShowHotBorder);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShowHotBorder`  
 Un valor booleano que especifica si los botones de barra de herramientas de seguimiento en caliente. Si este parámetro es `TRUE`, la barra de herramientas hot-pistas de sus botones. De lo contrario, la barra de herramientas no caliente seguimiento sus botones.  
  
### <a name="remarks"></a>Comentarios  
 Si un botón es el seguimiento, el marco de trabajo resalta el botón cuando el mouse pasa sobre ella. De forma predeterminada, cada barra de herramientas hot-pistas de sus botones.  
  
 Llame a la [CMFCToolBar::GetHotBorder](#gethotborder) método para determinar si las pistas caliente de barra de herramientas sus botones.  
  
##  <a name="a-namesethottextcolora--cmfctoolbarsethottextcolor"></a><a name="sethottextcolor"></a>CMFCToolBar::SetHotTextColor  
 Establece el color del texto de los botones de barra de herramientas de acceso rápido.  
  
```  
static void SetHotTextColor(COLORREF clrText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `clrText`  
 Especifica el color del texto de los botones de barra de herramientas que son el seguimiento.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de los botones de barra de herramientas de seguimiento, consulte [CMFCToolBar::GetHotBorder](#gethotborder) y [CMFCToolBar::SetHotBorder](#sethotborder).  
  
##  <a name="a-namesetignoresettexta--cmfctoolbarsetignoresettext"></a><a name="setignoresettext"></a>CMFCToolBar::SetIgnoreSetText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetIgnoreSetText(BOOL bValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bValue`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetlargeiconsa--cmfctoolbarsetlargeicons"></a><a name="setlargeicons"></a>CMFCToolBar::SetLargeIcons  
 Especifica si los botones de barra de herramientas muestran iconos grandes.  
  
```  
static void SetLargeIcons(BOOL bLargeIcons=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bLargeIcons`  
 Un valor booleano que especifica qué iconos que se utilizan. Si este parámetro es `TRUE`, el marco de trabajo muestra iconos grandes. De lo contrario, el marco de trabajo muestra los iconos normales.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando el usuario cambia el estado de la **iconos grandes** casilla de verificación en la **opciones** ficha de la **personalizar** cuadro de diálogo. Este método cambia el tamaño de todas las barras de herramientas en la aplicación.  
  
 De forma predeterminada, el marco de trabajo muestra iconos regulares.  
  
 Para obtener más información acerca de la **personalizar** cuadro de diálogo, vea [CMFCToolBarsCustomizeDialog clase](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
##  <a name="a-namesetlockedsizesa--cmfctoolbarsetlockedsizes"></a><a name="setlockedsizes"></a>CMFCToolBar::SetLockedSizes  
 Establece los tamaños de los botones de bloqueadas y bloqueadas imágenes en la barra de herramientas.  
  
```  
void SetLockedSizes(
    SIZE sizeButton,  
    SIZE sizeImage,  
    BOOL bDontScale = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `sizeButton`  
 Especifica el tamaño de los botones de barra de herramientas bloqueadas.  
  
 [in] `sizeImage`  
 Especifica el tamaño de las imágenes bloqueadas de la barra de herramientas.  
  
 `bDontScale`  
 Especifica si a escala o no bloqueado imágenes de la barra de herramientas en el modo de PPP alta.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño predeterminado de los botones de bloqueadas es 23 x 22 píxeles. El tamaño predeterminado de las imágenes bloqueadas es 16 x 15 píxeles.  
  
 Llame a la [CMFCToolBar::GetLockedImageSize](#getlockedimagesize) bloqueado de método para recuperar el tamaño de imágenes. Llame a la [CMFCToolBar::GetButtonSize](#getbuttonsize) bloqueado de método para recuperar el tamaño de los botones de barra de herramientas.  
  
##  <a name="a-namesetmaskmodea--cmfctoolbarsetmaskmode"></a><a name="setmaskmode"></a>CMFCToolBar::SetMaskMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetMaskMode(BOOL bMasked);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMasked`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetmenusizesa--cmfctoolbarsetmenusizes"></a><a name="setmenusizes"></a>CMFCToolBar::SetMenuSizes  
 Establece el tamaño de sus imágenes y botones de menú de la barra de herramientas.  
  
```  
static void __stdcall SetMenuSizes(
    SIZE sizeButton,  
    SIZE sizeImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `sizeButton`  
 Especifica el tamaño de los botones de barra de herramientas, en píxeles.  
  
 [in] `sizeImage`  
 Especifica el tamaño de las imágenes de la barra de herramientas, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, los botones de menú y sus imágenes tienen un tamaño definido.  
  
 Llame a la [CMFCToolBar::GetMenuButtonSize](#getmenubuttonsize) método para determinar el tamaño de los botones de menú y el [CMFCToolBar::GetMenuImageSize](#getmenuimagesize) método para determinar el tamaño de imágenes de botón de menú.  
  
 Consulte los ejemplos de IEDemo y MSMoneyDemo para obtener ejemplos que utilizan este método.  
  
##  <a name="a-namesetnonpermittedcommandsa--cmfctoolbarsetnonpermittedcommands"></a><a name="setnonpermittedcommands"></a>CMFCToolBar::SetNonPermittedCommands  
 Establece la lista de comandos que no se puede ejecutar por el usuario.  
  
```  
static void SetNonPermittedCommands(CList<UINT,UINT>& lstCommands);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lstCommands`  
 Una referencia a un `CList` objeto que contiene los comandos que no se puede ejecutar por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para evitar que el usuario seleccione determinados comandos. Por ejemplo, puede evitar que el usuario seleccione ciertos comandos por razones de seguridad. Consulte los ejemplos de MDITabsDemo y MenuSubSet para obtener ejemplos que utilizan este método.  
  
 Este método borra la lista anterior de comandos no permitida. De forma predeterminada, la lista de comandos no permitida está vacía.  
  
##  <a name="a-namesetonerowwithsiblinga--cmfctoolbarsetonerowwithsibling"></a><a name="setonerowwithsibling"></a>CMFCToolBar::SetOneRowWithSibling  
 Coloca la barra de herramientas y del mismo nivel en la misma fila.  
  
```  
void SetOneRowWithSibling();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando el usuario hace clic en el **mostrar botones en una fila** botón.  
  
 Llame a la [CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar) método para habilitar el **mostrar botones en una fila** o **mostrar botones en dos filas** botones. Si se llama a [CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar) para esta barra de herramientas, la barra de herramientas del mismo nivel se mueve a la fila de esta barra de herramientas. De lo contrario, esta barra de herramientas se mueve a la fila del mismo nivel.  
  
 El marco llama el [CMFCToolBar::SetTwoRowsWithSibling](#settworowswithsibling) método cuando el usuario hace clic en el **mostrar botones en dos filas** botón.  
  
##  <a name="a-namesetorigbuttonsa--cmfctoolbarsetorigbuttons"></a><a name="setorigbuttons"></a>CMFCToolBar::SetOrigButtons  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetOrigButtons(const CObList& lstOrigButtons);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lstOrigButtons`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetpermamenta--cmfctoolbarsetpermament"></a><a name="setpermament"></a>CMFCToolBar::SetPermament  
 Especifica si un usuario puede cerrar la barra de herramientas.  
  
```  
void SetPermament(BOOL bPermament=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bPermament`  
 Un valor booleano que especifica si un usuario puede cerrar la barra de herramientas. Si este parámetro es `TRUE`, un usuario no puede cerrar la barra de herramientas. De lo contrario, un usuario puede cerrar la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, un usuario puede cerrar cada barra de herramientas.  
  
 Llame a la [CMFCToolBar::CanBeClosed](#canbeclosed) método para determinar si un usuario puede cerrar la barra de herramientas.  
  
##  <a name="a-namesetroutecommandsviaframea--cmfctoolbarsetroutecommandsviaframe"></a><a name="setroutecommandsviaframe"></a>CMFCToolBar::SetRouteCommandsViaFrame  
 Especifica si el marco primario o el propietario envía comandos a la barra de herramientas.  
  
```  
void SetRouteCommandsViaFrame(BOOL bValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bValue`  
 Si este parámetro es `TRUE`, el marco primario envía comandos a la barra de herramientas. De lo contrario, el propietario envía comandos a la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco primario envía comandos a la barra de herramientas. Llame a la [CMFCToolBar::GetRouteCommandsViaFrame](#getroutecommandsviaframe) método para determinar si el marco primario o el propietario envía comandos a la barra de herramientas.  
  
##  <a name="a-namesetshowtooltipsa--cmfctoolbarsetshowtooltips"></a><a name="setshowtooltips"></a>CMFCToolBar::SetShowTooltips  
 Especifica si el marco de trabajo muestra información sobre herramientas.  
  
```  
static void SetShowTooltips(BOOL bValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bValue`  
 Si este parámetro es `TRUE`, el marco de trabajo muestra información sobre herramientas. De lo contrario, el marco de trabajo oculta la información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco de trabajo muestra información sobre herramientas.  
  
 Llame a la [CMFCToolBar::GetShowTooltips](#getshowtooltips) método para determinar si el marco de trabajo muestra información sobre herramientas.  
  
##  <a name="a-namesetsiblingtoolbara--cmfctoolbarsetsiblingtoolbar"></a><a name="setsiblingtoolbar"></a>CMFCToolBar::SetSiblingToolBar  
 Especifica al elemento relacionado de la barra de herramientas.  
  
```  
void SetSiblingToolBar(CMFCToolBar* pBrotherToolbar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBrotherToolbar`  
 Puntero a la barra de herramientas del mismo nivel.  
  
### <a name="remarks"></a>Comentarios  
 Este método permite la **mostrar botones en una fila** o **mostrar botones en dos filas** botones que se muestran cuando el usuario muestra el **personalizar** menú emergente. Llamar a este método cuando desee permitir al usuario especificar si las barras de herramientas relacionados aparecen en la misma fila o en filas diferentes.  
  
 Llamar a este método después de habilitar la **personalizar** botón que aparece en la barra de herramientas. Para habilitar la **personalizar** botón, llame a la [CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton) método.  
  
 Para recuperar el elemento relacionado de una barra de herramientas, llame a [CMFCToolBar::GetSiblingToolBar](#getsiblingtoolbar).  
  
##  <a name="a-namesetsizesa--cmfctoolbarsetsizes"></a><a name="setsizes"></a>CMFCToolBar::SetSizes  
 Especifica los tamaños de los botones y las imágenes en todas las barras de herramientas.  
  
```  
static void __stdcall SetSizes(
    SIZE sizeButton,  
    SIZE sizeImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `sizeButton`  
 El tamaño de los botones de barra de herramientas, en píxeles.  
  
 [in] `sizeImage`  
 El tamaño de las imágenes de los botones de barra de herramientas, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño predeterminado de los botones de barra de herramientas es 23 x 22 píxeles. El tamaño predeterminado de imágenes de botón de barra de herramientas es 16 x 15 píxeles.  
  
 Llame a la [CMFCToolBar::GetImageSize](#getimagesize) método para recuperar el tamaño de imágenes de botón de barra de herramientas. Llame a la [CMFCToolBar::GetButtonSize](#getbuttonsize) método para recuperar el tamaño de los botones de barra de herramientas.  
  
##  <a name="a-namesettoolbarbtntexta--cmfctoolbarsettoolbarbtntext"></a><a name="settoolbarbtntext"></a>CMFCToolBar::SetToolBarBtnText  
 Especifica las propiedades de un botón en la barra de herramientas.  
  
```  
void SetToolBarBtnText(
    UINT nBtnIndex,  
    LPCTSTR szText=NULL,  
    BOOL bShowText=TRUE,  
    BOOL bShowImage=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nBtnIndex`  
 Índice de base cero del botón de barra de herramientas de la lista de botones de barra de herramientas.  
  
 [in] `szText`  
 Especifica la etiqueta de texto del botón de barra de herramientas.  
  
 [in] `bShowText`  
 Si este parámetro es `TRUE`, el marco de trabajo muestra la etiqueta de texto. De lo contrario, el marco de trabajo oculta la etiqueta de texto.  
  
 [in] `bShowImage`  
 Si este parámetro es `TRUE`, el marco de trabajo muestra la imagen del botón de barra de herramientas. De lo contrario, el marco de trabajo oculta la imagen del botón de barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco de trabajo muestra las imágenes de los botones de barra de herramientas, pero no muestra la etiqueta de texto de los botones de barra de herramientas.  
  
 En compilaciones de depuración, este método genera un error de aserción si `nBtnIndex` no hace referencia a una barra de herramientas válido botón o barra de herramientas es un separador.  
  
##  <a name="a-namesettworowswithsiblinga--cmfctoolbarsettworowswithsibling"></a><a name="settworowswithsibling"></a>CMFCToolBar::SetTwoRowsWithSibling  
 Coloca la barra de herramientas y su hermano en filas independientes.  
  
```  
void SetTwoRowsWithSibling();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando el usuario hace clic en el **mostrar botones en dos filas** botón.  
  
 Llame a la [CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar) método para habilitar el **mostrar botones en una fila** o **mostrar botones en dos filas** botones. Si se llama a [CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar) para esta barra de herramientas, la barra de herramientas del mismo nivel se mueve a una fila independiente. De lo contrario, esta barra de herramientas se mueve a una fila independiente.  
  
 El marco llama el [CMFCToolBar::SetOneRowWithSibling](#setonerowwithsibling) método cuando el usuario hace clic en el **mostrar botones en una fila** botón.  
  
##  <a name="a-namesetuserimagesa--cmfctoolbarsetuserimages"></a><a name="setuserimages"></a>CMFCToolBar::SetUserImages  
 Establece la colección de imágenes definido por el usuario en la aplicación.  
  
```  
static BOOL SetUserImages(CMFCToolBarImages* pUserImages);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pUserImages`  
 Puntero a la colección de imágenes definido por el usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método tiene éxito; de lo contrario, 0 si especificado `CMFCToolBarImages` objeto no es válido o tiene un tamaño de imagen difiere del tamaño de la imagen predeterminada de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo utiliza imágenes definidas por el usuario para dibujar los botones de barra de herramientas que son personalizados por el usuario. La lista de imágenes especificada por `pUserImages` se comparte entre todas las barras de herramientas en la aplicación.  
  
 Este método genera un error de aserción en compilaciones de depuración si especificado `CMFCToolBarImages` objeto no es válido o tiene un tamaño de imagen difiere del tamaño de la imagen predeterminada de la barra de herramientas.  
  
 Los ejemplos de OutlookDemo ToolTipDemo y VisualStudioDemo utilizan este método para establecer la colección global de imágenes definido por el usuario. Carga el archivo que se denomina UserImages.bmp, que se encuentra en el directorio de trabajo de la aplicación.  
  
 Llame a la [CMFCToolBar::GetUserImages](#getuserimages) método para recuperar la colección de imágenes definido por el usuario en la aplicación.  
  
##  <a name="a-namestretchpanea--cmfctoolbarstretchpane"></a><a name="stretchpane"></a>CMFCToolBar::StretchPane  
 Expande la barra de herramientas horizontal o verticalmente y cambia de posición los botones si es necesario.  
  
```  
virtual CSize StretchPane(
    int nLength,  
    BOOL bVert);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nLength`  
 La cantidad, en píxeles, por el que se va a expandir el panel.  
  
 [in] `bVert`  
 Si `TRUE`, se expande el panel verticalmente. Si `FALSE`, se ajusta el panel horizontalmente.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` objeto que especifica el tamaño del área de cliente de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [CMFCToolBar::WrapToolBar](#wraptoolbar) para volver a colocar los botones de la barra de herramientas estirada.  
  
 El valor devuelto se determina mediante una llamada a [CMFCToolBar::CalcSize](#calcsize).  
  
##  <a name="a-nametranslatechara--cmfctoolbartranslatechar"></a><a name="translatechar"></a>CMFCToolBar::TranslateChar  
 Ejecuta un comando de botón si el código de clave especificado corresponde a un método abreviado de teclado válido.  
  
```  
virtual BOOL TranslateChar(UINT nChar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nChar`  
 Especifica un código de tecla virtual. Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h  
  
### <a name="return-value"></a>Valor devuelto  
 `FALSE`Si el código de clave especificado es no imprimible o no corresponde a un método abreviado de teclado válido; `TRUE` si el código de clave especificado corresponde a una opción de menú desplegable; en caso contrario, el valor devuelto de [CMFCToolBar::ProcessCommand](#processcommand).  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se presiona una tecla junto con la tecla Alt.  
  
##  <a name="a-nameupdatebuttona--cmfctoolbarupdatebutton"></a><a name="updatebutton"></a>CMFCToolBar::UpdateButton  
 Actualiza el estado del botón especificado.  
  
```  
void UpdateButton(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice basado en cero del botón Actualizar.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namewraptoolbara--cmfctoolbarwraptoolbar"></a><a name="wraptoolbar"></a>CMFCToolBar::WrapToolBar  
 Cambia la posición de los botones de barra de herramientas dentro de las dimensiones dadas.  
  
```  
int WrapToolBar(
    int nWidth,  
    int nHeight = 32767,  
    CDC* pDC = NULL,  
    int nColumnWidth = -1,  
    int nRowHeight = -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nWidth`  
 Ancho máximo de la barra de herramientas.  
  
 [in] `nHeight`  
 Alto máximo de la barra de herramientas. No se utiliza si la barra de herramientas es flotante.  
  
 [in] `pDC`  
 Puntero a un contexto de dispositivo. Si es NULL, se utiliza el contexto de dispositivo para la barra de herramientas.  
  
 [in] `nColumnWidth`  
 Ancho del botón. Si-1, se utiliza el ancho actual.  
  
 [in] m`nRowHeight`  
 Alto del botón. Si-1, se utiliza el alto actual.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de filas de botones de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Este método recoloca botones dentro de la barra de herramientas, ajuste los botones para filas adicionales si es necesario.  
  
##  <a name="a-namembdontscaleimagesa--cmfctoolbarmbdontscaleimages"></a><a name="m_bdontscaleimages"></a>CMFCToolBar::m_bDontScaleImages  
 Especifica si se debe o no escalar imágenes de la barra de herramientas en el modo de PPP alta.  
  
```  
AFX_IMPORT_DATA static BOOL m_bDontScaleImages;  
```  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)   
 [Clase CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)   
 [Clase de CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [Tutorial: Poner controles en barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)




