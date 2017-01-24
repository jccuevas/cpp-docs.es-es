---
title: "CToolBarCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CToolBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBarCtrl class"
  - "información sobre herramientas [C++], notificaciones"
  - "controles de barra de herramientas [MFC], CToolBarCtrl class"
  - "Windows common controls [C++], CToolBarCtrl"
ms.assetid: 8f2f8ad2-05d7-4975-8715-3f2eed795248
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CToolBarCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad de controles comunes de la barra de herramientas de Windows.  
  
## Sintaxis  
  
```  
class CToolBarCtrl : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CToolBarCtrl::CToolBarCtrl](../Topic/CToolBarCtrl::CToolBarCtrl.md)|Crea un objeto `CToolBarCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CToolBarCtrl::AddBitmap](../Topic/CToolBarCtrl::AddBitmap.md)|Agrega una o varias imágenes de botón bitmap en la lista de imágenes de botón disponibles para un control toolbar.|  
|[CToolBarCtrl::AddButtons](../Topic/CToolBarCtrl::AddButtons.md)|Agregue uno o varios botones a un control toolbar.|  
|[CToolBarCtrl::AddString](../Topic/CToolBarCtrl::AddString.md)|Agrega una nueva cadena, como Id. de recurso, a la lista de la barra de herramientas de cadenas.|  
|[CToolBarCtrl::AddStrings](../Topic/CToolBarCtrl::AddStrings.md)|Agrega una nueva cadena o cadenas, pasadas como un puntero a un búfer de cadenas nulo\-separadas, a la lista de la barra de herramientas de cadenas.|  
|[CToolBarCtrl::AutoSize](../Topic/CToolBarCtrl::AutoSize.md)|Cambia el tamaño de un control toolbar.|  
|[CToolBarCtrl::ChangeBitmap](../Topic/CToolBarCtrl::ChangeBitmap.md)|Cambia el mapa de bits para un botón del control toolbar actual.|  
|[CToolBarCtrl::CheckButton](../Topic/CToolBarCtrl::CheckButton.md)|Las comprobaciones o desactive un botón determinado en un control toolbar.|  
|[CToolBarCtrl::CommandToIndex](../Topic/CToolBarCtrl::CommandToIndex.md)|Recupera el índice de base cero del botón asociado al identificador de comandos especificado.|  
|[CToolBarCtrl::Create](../Topic/CToolBarCtrl::Create.md)|Crea un control de barra de herramientas y lo asocia a un objeto de `CToolBarCtrl` .|  
|[CToolBarCtrl::CreateEx](../Topic/CToolBarCtrl::CreateEx.md)|Crea un control toolbar con Windows especificado extendidas estilos y lo asocia a un objeto de `CToolBarCtrl` .|  
|[CToolBarCtrl::Customize](../Topic/CToolBarCtrl::Customize.md)|Muestra el cuadro de diálogo de la barra de herramientas de personalizar.|  
|[CToolBarCtrl::DeleteButton](../Topic/CToolBarCtrl::DeleteButton.md)|Elimina un botón del control de barra de herramientas.|  
|[CToolBarCtrl::EnableButton](../Topic/CToolBarCtrl::EnableButton.md)|Habilita o deshabilita el botón especificado en un control toolbar.|  
|[CToolBarCtrl::GetAnchorHighlight](../Topic/CToolBarCtrl::GetAnchorHighlight.md)|Recupera la configuración de resaltado de delimitación de una barra de herramientas.|  
|[CToolBarCtrl::GetBitmap](../Topic/CToolBarCtrl::GetBitmap.md)|Recupera el índice del mapa de bits asociado con un botón de una barra de herramientas.|  
|[CToolBarCtrl::GetBitmapFlags](../Topic/CToolBarCtrl::GetBitmapFlags.md)|Obtiene los indicadores asociado al mapa de bits de la barra de herramientas.|  
|[CToolBarCtrl::GetButton](../Topic/CToolBarCtrl::GetButton.md)|Recupera información sobre el botón especificado en un control toolbar.|  
|[CToolBarCtrl::GetButtonCount](../Topic/CToolBarCtrl::GetButtonCount.md)|recupera un recuento de los botones actualmente en el control de barra de herramientas.|  
|[CToolBarCtrl::GetButtonInfo](../Topic/CToolBarCtrl::GetButtonInfo.md)|Recupera información para un botón de una barra de herramientas.|  
|[CToolBarCtrl::GetButtonSize](../Topic/CToolBarCtrl::GetButtonSize.md)|recupera el ancho y el alto actuales de botones de la barra de herramientas, en píxeles.|  
|[CToolBarCtrl::GetColorScheme](../Topic/CToolBarCtrl::GetColorScheme.md)|Recupera la combinación de colores del control toolbar actual.|  
|[CToolBarCtrl::GetDisabledImageList](../Topic/CToolBarCtrl::GetDisabledImageList.md)|Recupera la imagen mostrada que un control toolbar utiliza para mostrar los botones deshabilitados.|  
|[CToolBarCtrl::GetDropTarget](../Topic/CToolBarCtrl::GetDropTarget.md)|Recupera la interfaz de [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) para un control toolbar.|  
|[CToolBarCtrl::GetExtendedStyle](../Topic/CToolBarCtrl::GetExtendedStyle.md)|Recupera los estilos extendidos para un control toolbar.|  
|[CToolBarCtrl::GetHotImageList](../Topic/CToolBarCtrl::GetHotImageList.md)|Recupera la imagen mostrada que un control toolbar utiliza para mostrar los botones “activo”.  Un botón activo aparece resaltada cuando el puntero del mouse está encima de él.|  
|[CToolBarCtrl::GetHotItem](../Topic/CToolBarCtrl::GetHotItem.md)|Recupera el índice de caso muy actual en una barra de herramientas.|  
|[CToolBarCtrl::GetImageList](../Topic/CToolBarCtrl::GetImageList.md)|Recupera la imagen mostrada que un control toolbar utiliza para mostrar botones en su estado predeterminado.|  
|[CToolBarCtrl::GetInsertMark](../Topic/CToolBarCtrl::GetInsertMark.md)|recupera la marca de inserción actual para la barra de herramientas.|  
|[CToolBarCtrl::GetInsertMarkColor](../Topic/CToolBarCtrl::GetInsertMarkColor.md)|Recupera el color utilizado para dibujar la marca de inserción para la barra de herramientas.|  
|[CToolBarCtrl::GetItemRect](../Topic/CToolBarCtrl::GetItemRect.md)|Recupera el rectángulo delimitador de un botón en un control toolbar.|  
|[CToolBarCtrl::GetMaxSize](../Topic/CToolBarCtrl::GetMaxSize.md)|Recupera el tamaño total de los botones y separadores visible en la barra de herramientas.|  
|[CToolBarCtrl::GetMaxTextRows](../Topic/CToolBarCtrl::GetMaxTextRows.md)|Recupera el número máximo de filas de texto que aparecen en un botón de la barra de herramientas.|  
|[CToolBarCtrl::GetMetrics](../Topic/CToolBarCtrl::GetMetrics.md)|Recupera las métricas de un control toolbar.|  
|[CToolBarCtrl::GetPadding](../Topic/CToolBarCtrl::GetPadding.md)|Recupera el relleno horizontal y vertical del control toolbar actual.|  
|[CToolBarCtrl::GetPressedImageList](../Topic/CToolBarCtrl::GetPressedImageList.md)|Recupera la imagen mostrada que el control toolbar actual utiliza para representar los botones en el estado presionado.|  
|[CToolBarCtrl::GetRect](../Topic/CToolBarCtrl::GetRect.md)|recupera el rectángulo delimitador para un botón de la barra de herramientas especificado.|  
|[CToolBarCtrl::GetRows](../Topic/CToolBarCtrl::GetRows.md)|Recupera el número de filas de botones mostrados actualmente en la barra de herramientas.|  
|[CToolBarCtrl::GetState](../Topic/CToolBarCtrl::GetState.md)|Recupera información sobre el estado del botón especificado en un control de barra de herramientas, por ejemplo si está habilitado, presionado, o comprobado.|  
|[CToolBarCtrl::GetString](../Topic/CToolBarCtrl::GetString.md)|recupera una cadena de la barra de herramientas.|  
|[CToolBarCtrl::GetStyle](../Topic/CToolBarCtrl::GetStyle.md)|Recupera los estilos actualmente en uso para un control toolbar.|  
|[CToolBarCtrl::GetToolTips](../Topic/CToolBarCtrl::GetToolTips.md)|Recupera el identificador del control de información sobre herramientas, si existe, asociado al control de barra de herramientas.|  
|[CToolBarCtrl::HideButton](../Topic/CToolBarCtrl::HideButton.md)|Oculta o muestra el botón especificado en un control toolbar.|  
|[CToolBarCtrl::HitTest](../Topic/CToolBarCtrl::HitTest.md)|Determina si un punto está en un control toolbar.|  
|[CToolBarCtrl::Indeterminate](../Topic/CToolBarCtrl::Indeterminate.md)|Establece o borrar el estado \(deshabilitada\) indeterminado de botón especificado en un control toolbar.|  
|[CToolBarCtrl::InsertButton](../Topic/CToolBarCtrl::InsertButton.md)|Inserta un botón en un control toolbar.|  
|[CToolBarCtrl::InsertMarkHitTest](../Topic/CToolBarCtrl::InsertMarkHitTest.md)|Recupera información de marca de inserción de un punto en una barra de herramientas.|  
|[CToolBarCtrl::IsButtonChecked](../Topic/CToolBarCtrl::IsButtonChecked.md)|Indica si el botón especificado en un control de barra de herramientas está activado.|  
|[CToolBarCtrl::IsButtonEnabled](../Topic/CToolBarCtrl::IsButtonEnabled.md)|Indica si el botón especificado en un control de barra de herramientas está habilitado.|  
|[CToolBarCtrl::IsButtonHidden](../Topic/CToolBarCtrl::IsButtonHidden.md)|Indica si el botón especificado en un control de barra de herramientas está oculto.|  
|[CToolBarCtrl::IsButtonHighlighted](../Topic/CToolBarCtrl::IsButtonHighlighted.md)|Comprueba el estado del resaltado del botón de la barra de herramientas.|  
|[CToolBarCtrl::IsButtonIndeterminate](../Topic/CToolBarCtrl::IsButtonIndeterminate.md)|Indica si el estado del botón especificado en un control toolbar es indeterminado \(gris\).|  
|[CToolBarCtrl::IsButtonPressed](../Topic/CToolBarCtrl::IsButtonPressed.md)|Indica si el botón especificado en un control de barra de herramientas está presionado.|  
|[CToolBarCtrl::LoadImages](../Topic/CToolBarCtrl::LoadImages.md)|Mapas de bits de las cargas de la lista de imágenes de un control toolbar.|  
|[CToolBarCtrl::MapAccelerator](../Topic/CToolBarCtrl::MapAccelerator.md)|Asigna un carácter de aceleradores a un botón de la barra de herramientas.|  
|[CToolBarCtrl::MarkButton](../Topic/CToolBarCtrl::MarkButton.md)|Establece el estado del resaltado de un botón determinado en un control toolbar.|  
|[CToolBarCtrl::MoveButton](../Topic/CToolBarCtrl::MoveButton.md)|mueve un botón a partir de un índice a otro.|  
|[CToolBarCtrl::PressButton](../Topic/CToolBarCtrl::PressButton.md)|Presione o libere el botón especificado en un control toolbar.|  
|[CToolBarCtrl::ReplaceBitmap](../Topic/CToolBarCtrl::ReplaceBitmap.md)|Reemplaza el mapa de bits existente en el control de barra de herramientas actual a un nuevo mapa de bits.|  
|[CToolBarCtrl::RestoreState](../Topic/CToolBarCtrl::RestoreState.md)|Restaura el estado de control toolbar.|  
|[CToolBarCtrl::SaveState](../Topic/CToolBarCtrl::SaveState.md)|Guarda el estado de control toolbar.|  
|[CToolBarCtrl::SetAnchorHighlight](../Topic/CToolBarCtrl::SetAnchorHighlight.md)|Establece la configuración de resaltado de delimitación de una barra de herramientas.|  
|[CToolBarCtrl::SetBitmapSize](../Topic/CToolBarCtrl::SetBitmapSize.md)|Establece el tamaño de las imágenes trazadas un mapa de bits que se van a un control toolbar.|  
|[CToolBarCtrl::SetButtonInfo](../Topic/CToolBarCtrl::SetButtonInfo.md)|establece la información para un botón existente en una barra de herramientas.|  
|[CToolBarCtrl::SetButtonSize](../Topic/CToolBarCtrl::SetButtonSize.md)|Establece el tamaño de los botones que se van a un control toolbar.|  
|[CToolBarCtrl::SetButtonStructSize](../Topic/CToolBarCtrl::SetButtonStructSize.md)|Especifica el tamaño de la estructura de `TBBUTTON` .|  
|[CToolBarCtrl::SetButtonWidth](../Topic/CToolBarCtrl::SetButtonWidth.md)|Establece el ancho mínimos y máximos de botón en el control de barra de herramientas.|  
|[CToolBarCtrl::SetCmdID](../Topic/CToolBarCtrl::SetCmdID.md)|Establece el identificador de comandos se envía a la ventana propietaria cuando se presiona el botón especificado.|  
|[CToolBarCtrl::SetColorScheme](../Topic/CToolBarCtrl::SetColorScheme.md)|Establece la combinación de colores del control toolbar actual.|  
|[CToolBarCtrl::SetDisabledImageList](../Topic/CToolBarCtrl::SetDisabledImageList.md)|Establece la imagen mostrada que el control toolbar utilizará para mostrar los botones deshabilitados.|  
|[CToolBarCtrl::SetDrawTextFlags](../Topic/CToolBarCtrl::SetDrawTextFlags.md)|Establece los marcadores de la función [DrawText](http://msdn.microsoft.com/library/windows/desktop/dd162498), que de Win32 se utiliza para dibujar texto en el rectángulo especificado, formato según cómo se establecen los marcadores.|  
|[CToolBarCtrl::SetExtendedStyle](../Topic/CToolBarCtrl::SetExtendedStyle.md)|Establece los estilos extendidos para un control toolbar.|  
|[CToolBarCtrl::SetHotImageList](../Topic/CToolBarCtrl::SetHotImageList.md)|Establece la imagen mostrada que el control toolbar utilizará para mostrar botones “activo”.|  
|[CToolBarCtrl::SetHotItem](../Topic/CToolBarCtrl::SetHotItem.md)|Establece el caso muy actual en una barra de herramientas.|  
|[CToolBarCtrl::SetImageList](../Topic/CToolBarCtrl::SetImageList.md)|Establece la imagen mostrada que la barra de herramientas utilizará para mostrar botones que están en su estado predeterminado.|  
|[CToolBarCtrl::SetIndent](../Topic/CToolBarCtrl::SetIndent.md)|Establece la sangría para el primer botón en un control toolbar.|  
|[CToolBarCtrl::SetInsertMark](../Topic/CToolBarCtrl::SetInsertMark.md)|establece la marca de inserción actual para la barra de herramientas.|  
|[CToolBarCtrl::SetInsertMarkColor](../Topic/CToolBarCtrl::SetInsertMarkColor.md)|Establece el color utilizado para dibujar la marca de inserción para la barra de herramientas.|  
|[CToolBarCtrl::SetMaxTextRows](../Topic/CToolBarCtrl::SetMaxTextRows.md)|Establece el número máximo de filas de texto que aparecen en un botón de la barra de herramientas.|  
|[CToolBarCtrl::SetMetrics](../Topic/CToolBarCtrl::SetMetrics.md)|Establece las métricas de un control toolbar.|  
|[CToolBarCtrl::SetOwner](../Topic/CToolBarCtrl::SetOwner.md)|Establece la ventana para recibir mensajes de notificación de control toolbar.|  
|[CToolBarCtrl::SetPadding](../Topic/CToolBarCtrl::SetPadding.md)|Establece el relleno horizontal y vertical del control toolbar actual.|  
|[CToolBarCtrl::SetPressedImageList](../Topic/CToolBarCtrl::SetPressedImageList.md)|Establece la imagen mostrada que el control toolbar actual utiliza para representar los botones en el estado presionado.|  
|[CToolBarCtrl::SetRows](../Topic/CToolBarCtrl::SetRows.md)|Establece el número de filas de botones mostrados en la barra de herramientas.|  
|[CToolBarCtrl::SetState](../Topic/CToolBarCtrl::SetState.md)|Establece el estado del botón especificado en un control toolbar.|  
|[CToolBarCtrl::SetStyle](../Topic/CToolBarCtrl::SetStyle.md)|Establece los estilos de un control toolbar.|  
|[CToolBarCtrl::SetToolTips](../Topic/CToolBarCtrl::SetToolTips.md)|Asocia un control de información sobre herramientas al control de barra de herramientas.|  
|[CToolBarCtrl::SetWindowTheme](../Topic/CToolBarCtrl::SetWindowTheme.md)|Establece el estilo visual de un control toolbar.|  
  
## Comentarios  
 Este control \(y por consiguiente la clase de `CToolBarCtrl` \) sólo está disponible para los programas que se ejecutan en versión 3,51 de Windows 95 \/98 y Windows NT y posterior.  
  
 Un control común de la barra de herramientas de Windows es una ventana secundaria rectangular que contiene uno o varios botones.  Estos botones pueden mostrar una imagen de mapa de bits, una cadena, o ambas.  Cuando el usuario elige un botón, envía un mensaje de comando a la ventana propietaria de la barra de herramientas.  Normalmente, los botones de una barra de herramientas corresponden a los elementos del menú de la aplicación; proporcionan una manera más sencilla para que el usuario tiene acceso a los comandos de una aplicación.  
  
 los objetos de`CToolBarCtrl` contienen varias estructuras de datos internas importantes: una lista de mapas de bits del botón o una lista de imágenes, una lista de cadenas de la etiqueta del botón, y una lista de estructuras de `TBBUTTON` que asocie una imagen o una cadena con la posición, el estilo, estado, y el identificador de comando del botón.  Cada uno de los elementos de estas estructuras de datos se está haciendo referencia por un índice de base cero.  Antes de poder utilizar un objeto de `CToolBarCtrl` , debe configurar estas estructuras de datos.  La lista de cadenas sólo se puede utilizar para las etiquetas del botón; no se puede recuperar cadenas de la barra de herramientas.  
  
 Para utilizar un objeto de `CToolBarCtrl` , realizará normalmente estos pasos:  
  
1.  Cree el objeto de `CToolBarCtrl` .  
  
2.  Llame a [Crear](../Topic/CToolBarCtrl::Create.md) para crear el control común de la barra de herramientas de Windows y para adjuntarlo al objeto de `CToolBarCtrl` .  Indica el estilo de la barra de herramientas mediante estilos, como **TBSTYLE\_TRANSPARENT** de una barra de herramientas transparente o **TBSTYLE\_DROPDOWN** de una barra de herramientas que admita botones desplegables de estilo.  
  
3.  Identificar cómo desea los botones de la barra de herramientas muestra:  
  
    -   Para utilizar imágenes de mapa de bits en los botones, agregue los mapas de bits del botón en la barra de herramientas llamando a [AddBitmap](../Topic/CToolBarCtrl::AddBitmap.md).  
  
    -   Para utilizar imágenes mostradas de una imagen que aparece para los botones, especifique la imagen lista llamando a [SetImageList](../Topic/CToolBarCtrl::SetImageList.md), [SetHotImageList](../Topic/CToolBarCtrl::SetHotImageList.md), o [SetDisabledImageList](../Topic/CToolBarCtrl::SetDisabledImageList.md).  
  
    -   Para utilizar las etiquetas de la cadena en los botones, agregue las cadenas a la barra de herramientas llamando a [AddString](../Topic/CToolBarCtrl::AddString.md) y\/o [AddStrings](../Topic/CToolBarCtrl::AddStrings.md).  
  
4.  Agregue las estructuras del botón en la barra de herramientas llamando a [AddButtons](../Topic/CToolBarCtrl::AddButtons.md).  
  
5.  Si desea que la información sobre herramientas de un botón de la barra de herramientas en una ventana propietaria que no es `CFrameWnd`, deberá controlar los mensajes de **TTN\_NEEDTEXT** en la ventana propietaria de la barra de herramientas como se describe en [Administrar notificaciones de información sobre herramientas](../../mfc/handling-tool-tip-notifications.md).  Si la ventana primaria de la barra de herramientas es derivada de `CFrameWnd`, la información sobre herramientas se muestran sin ningún esfuerzo adicional de se porque `CFrameWnd` proporciona un controlador predeterminado.  
  
6.  Si desea que el usuario pueda personalizar la barra de herramientas, los mensajes de notificación de personalización de identificador en la ventana propietaria como se describe en [Administrar notificaciones de personalización](../../mfc/handling-customization-notifications.md).  
  
 Puede utilizar [SaveState](../Topic/CToolBarCtrl::SaveState.md) para guardar el estado actual de un control de barra de herramientas en el registro y [RestoreState](../Topic/CToolBarCtrl::RestoreState.md) para restaurar el estado basándose en la información anteriormente almacenada en el registro.  Además de guardar el estado de la barra de herramientas entre usos de la aplicación, aplicaciones almacenan normalmente el estado antes de que el usuario personalizar la barra de herramientas en caso de que el usuario desee después para restaurar la barra de herramientas a su estado original.  
  
## Compatibilidad con la versión 4,0 de Internet Explorer y Later  
 Para admitir la funcionalidad introducida en Internet Explorer, la versión 4,0 y posterior, MFC proporciona compatibilidad con la lista de imágenes y estilos transparente y planos para los controles de barra de herramientas.  
  
 Una barra de herramientas transparente permite al cliente en la barra de herramientas muestra a través de.  Para crear una barra de herramientas transparente, utilice estilos de **TBSTYLE\_FLAT** y de **TBSTYLE\_TRANSPARENT** .  Seguimiento activo de la característica transparente de las barras de herramientas; es decir, cuando el puntero del mouse se mueve sobre un botón activo en la barra de herramientas, cambia el aspecto del botón.  Las barras de herramientas creadas con solo el estilo de **TBSTYLE\_FLAT** contendrán los botones que no son transparentes.  
  
 Compatibilidad con la lista de imágenes ofrece a control mayor flexibilidad para el comportamiento predeterminado, imágenes activo, y las imágenes deshabilitadas.  Utilice [GetImageList](../Topic/CToolBarCtrl::GetImageList.md), [GetHotImageList](../Topic/CToolBarCtrl::GetHotImageList.md), y [GetDisabledImageList](../Topic/CToolBarCtrl::GetDisabledImageList.md) con la barra de herramientas transparente para manipular la imagen según el estado:  
  
 Para obtener más información sobre cómo utilizar `CToolBarCtrl`, vea [Controles](../../mfc/controls-mfc.md) y [Mediante CToolBarCtrl](../../mfc/using-ctoolbarctrl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolBarCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [ejemplo CMNCTRL1 de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo MFCIE de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CToolBar Class](../../mfc/reference/ctoolbar-class.md)