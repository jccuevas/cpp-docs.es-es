---
title: "CMFCToolBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBar class"
ms.assetid: e7679c01-fb94-44c0-98c6-3af955292fb5
caps.latest.revision: 48
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 50
---
# CMFCToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCToolBar` se parece a [CToolBar Class](../../mfc/reference/ctoolbar-class.md), pero proporciona compatibilidad adicional para las características de la interfaz de usuario.  Se incluyen las barras de herramientas planas, barras de herramientas con imágenes activo, iconos grandes, los botones de buscapersonas, barras de herramientas bloquean, los controles rebar, el texto en imágenes, imágenes de fondo, y las barras de herramientas con fichas.  La clase de `CMFCToolBar` también contiene compatibilidad integrada para la personalización de usuario de barras de herramientas y menús, arrastrar y colocar entre las barras de herramientas y menús, botones del cuadro combinado, los botones del cuadro de edición, los selectores de colores, y los botones de consolidación.  
  
## Sintaxis  
  
```  
class CMFCToolBar : public CMFCBaseToolBar  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCToolBar::CMFCToolBar`|Constructor predeterminado.|  
|`CMFCToolBar::~CMFCToolBar`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBar::AddBasicCommand](../Topic/CMFCToolBar::AddBasicCommand.md)|Agrega un comando de menú a la lista de comandos que se muestra cuando un usuario abre un menú.|  
|[CMFCToolBar::AddCommandUsage](../Topic/CMFCToolBar::AddCommandUsage.md)|Incrementa en uno el contador que está asociado al comando especificado.|  
|[CMFCToolBar::AddToolBarForImageCollection](../Topic/CMFCToolBar::AddToolBarForImageCollection.md)|Agregar imágenes de los recursos de interfaz de usuario a la colección de imágenes en la aplicación.|  
|[CMFCToolBar::AdjustLayout](../Topic/CMFCToolBar::AdjustLayout.md)|Actualiza el tamaño y la posición de una barra de herramientas.  \(Reemplaza [CBasePane::AdjustLayout](../Topic/CBasePane::AdjustLayout.md)\).|  
|[CMFCToolBar::AdjustSize](../Topic/CMFCToolBar::AdjustSize.md)|Actualiza el tamaño de la barra de herramientas.|  
|[CMFCToolBar::AllowChangeTextLabels](../Topic/CMFCToolBar::AllowChangeTextLabels.md)|Especifica si las etiquetas de texto se pueden mostrar en imágenes de los botones de la barra de herramientas.|  
|[CMFCToolBar::AreTextLabels](../Topic/CMFCToolBar::AreTextLabels.md)|Especifica si las etiquetas de texto en imágenes se muestran actualmente en los botones de la barra de herramientas.|  
|[CMFCToolBar::AutoGrayInactiveImages](../Topic/CMFCToolBar::AutoGrayInactiveImages.md)|Habilita o deshabilita la generación automática de imágenes de botón inactivas.|  
|[CMFCToolBar::ButtonToIndex](../Topic/CMFCToolBar::ButtonToIndex.md)|devuelve el índice de un objeto especificado de [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md) en esta barra de herramientas.|  
|[CMFCToolBar::CalcFixedLayout](../Topic/CMFCToolBar::CalcFixedLayout.md)|calcula el tamaño horizontal de la barra de herramientas.  \(Reemplaza [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md).\)|  
|[CMFCToolBar::CalcSize](../Topic/CMFCToolBar::CalcSize.md)|Llamado por el marco como parte del proceso de cálculo de diseño.  \(Reemplaza [CPane::CalcSize](../Topic/CPane::CalcSize.md).\)|  
|[CMFCToolBar::CanHandleSiblings](../Topic/CMFCToolBar::CanHandleSiblings.md)|Determina si colocan la barra de herramientas y su elemento relacionado en el mismo panel.|  
|[CMFCToolBar::CleanUpImages](../Topic/CMFCToolBar::CleanUpImages.md)|Libera los recursos del sistema asignados para las imágenes de la barra de herramientas.|  
|[CMFCToolBar::CleanUpLockedImages](../Topic/CMFCToolBar::CleanUpLockedImages.md)|Libera los recursos del sistema asignados para las imágenes compilaciones de la barra de herramientas.|  
|[CMFCToolBar::CanBeClosed](../Topic/CMFCToolBar::CanBeClosed.md)|especifica si un usuario puede cerrar la barra de herramientas.  \(Reemplaza [CBasePane::CanBeClosed](../Topic/CBasePane::CanBeClosed.md).\)|  
|[CMFCToolBar::CanBeRestored](../Topic/CMFCToolBar::CanBeRestored.md)|Determina si el sistema puede restaurar una barra de herramientas a su estado original después de la personalización.|  
|[CMFCToolBar::CanFocus](../Topic/CMFCToolBar::CanFocus.md)|Especifica si el panel puede recibir el foco.  \(Reemplaza [CBasePane::CanFocus](../Topic/CBasePane::CanFocus.md).\)|  
|[CMFCToolBar::CanHandleSiblings](../Topic/CMFCToolBar::CanHandleSiblings.md)|Determina si colocan la barra de herramientas y su elemento relacionado en el mismo panel.|  
|[CMFCToolBar::CommandToIndex](../Topic/CMFCToolBar::CommandToIndex.md)|Devuelve el índice del botón en la barra de herramientas con un identificador especificada de comando|  
|[CMFCToolBar::Create](../Topic/CMFCToolBar::Create.md)|Crea un objeto `CMFCToolBar`.|  
|[CMFCToolBar::CreateEx](../Topic/CMFCToolBar::CreateEx.md)|Crea un objeto de `CMFCToolBar` que utilice más opciones de estilo, como iconos grandes.|  
|[CMFCToolBar::Deactivate](../Topic/CMFCToolBar::Deactivate.md)|desactiva la barra de herramientas.|  
|[CMFCToolBar::EnableCustomizeButton](../Topic/CMFCToolBar::EnableCustomizeButton.md)|Habilita o deshabilita el botón de **agregue o quite los botones** que aparece al final de la barra de herramientas.|  
|[CMFCToolBar::EnableDocking](../Topic/CMFCToolBar::EnableDocking.md)|Habilita el acoplamiento del panel al cuadro principal.  \(Reemplaza [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md).\)|  
|[CMFCToolBar::EnableLargeIcons](../Topic/CMFCToolBar::EnableLargeIcons.md)|Habilita o deshabilita iconos grandes en los botones de la barra de herramientas.|  
|[CMFCToolBar::EnableQuickCustomization](../Topic/CMFCToolBar::EnableQuickCustomization.md)|Habilita o deshabilita la personalización rápida de barras de herramientas para que el usuario puede presionar la tecla de **Alt** y arrastrar un botón a una nueva ubicación.|  
|[CMFCToolBar::EnableReflections](../Topic/CMFCToolBar::EnableReflections.md)|Habilita o deshabilita la reflexión del comando.|  
|[CMFCToolBar::EnableTextLabels](../Topic/CMFCToolBar::EnableTextLabels.md)|Habilita o deshabilita las etiquetas de texto en imágenes de botón de la barra de herramientas.|  
|[CMFCToolBar::FromHandlePermanent](../Topic/CMFCToolBar::FromHandlePermanent.md)|Recupera un puntero al objeto de `CMFCToolBar` que contiene el identificador de ventana especificado.|  
|[CMFCToolBar::GetAllButtons](../Topic/CMFCToolBar::GetAllButtons.md)|Devuelve una lista de solo lectura de botones de una barra de herramientas.|  
|[CMFCToolBar::GetAllToolbars](../Topic/CMFCToolBar::GetAllToolbars.md)|Devuelve una lista de solo lectura de todas las barras de herramientas en la aplicación.|  
|[CMFCToolBar::GetBasicCommands](../Topic/CMFCToolBar::GetBasicCommands.md)|Devuelve una lista de solo lectura de los comandos básicos definido en la aplicación.|  
|[CMFCToolBar::GetButton](../Topic/CMFCToolBar::GetButton.md)|Devuelve un puntero al objeto de `CMFCToolBarButton` que tiene un índice especificado del botón de la barra de herramientas.|  
|[CMFCToolBar::GetButtonInfo](../Topic/CMFCToolBar::GetButtonInfo.md)|Devuelve el identificador de comando, el estilo, y el índice del botón en el índice especificado.|  
|[CMFCToolBar::GetButtonSize](../Topic/CMFCToolBar::GetButtonSize.md)|Devuelve las dimensiones de cada botón de la barra de herramientas.|  
|[CMFCToolBar::GetButtonStyle](../Topic/CMFCToolBar::GetButtonStyle.md)|Devuelve el estilo actual del botón de la barra de herramientas que se encuentra en el índice especificado.|  
|[CMFCToolBar::GetButtonText](../Topic/CMFCToolBar::GetButtonText.md)|Devuelve la etiqueta de texto de un botón que tiene el índice especificado.|  
|[CMFCToolBar::GetColdImages](../Topic/CMFCToolBar::GetColdImages.md)|Devuelve un puntero a la colección de imágenes en frío del botón de la barra de herramientas en la aplicación.|  
|[CMFCToolBar::GetColumnWidth](../Topic/CMFCToolBar::GetColumnWidth.md)|devuelve el ancho de los botones de la barra de herramientas.|  
|[CMFCToolBar::GetCommandButtons](../Topic/CMFCToolBar::GetCommandButtons.md)|Devuelve una lista de botones que tiene el identificador especificado de comando de todas las barras de herramientas en la aplicación.|  
|[CMFCToolBar::GetCount](../Topic/CMFCToolBar::GetCount.md)|Devuelve el número de botones y separadores en la barra de herramientas.|  
|[CMFCToolBar::GetCustomizeButton](../Topic/CMFCToolBar::GetCustomizeButton.md)|Recupera un puntero al objeto de `CMFCCustomizeButton` que está asociado a la barra de herramientas.|  
|[CMFCToolBar::GetDefaultImage](../Topic/CMFCToolBar::GetDefaultImage.md)|Devuelve el índice de la imagen predeterminada para un botón de la barra de herramientas con un identificador especificada de comando|  
|[CMFCToolBar::GetDisabledImages](../Topic/CMFCToolBar::GetDisabledImages.md)|Devuelve un puntero a la colección de imágenes que se utilizan para los botones de la barra de herramientas deshabilitados en la aplicación.|  
|[CMFCToolBar::GetDisabledMenuImages](../Topic/CMFCToolBar::GetDisabledMenuImages.md)|Devuelve un puntero a la colección de imágenes que se utilizan para los botones de menú deshabilitados en la aplicación.|  
|[CMFCToolBar::GetDroppedDownMenu](../Topic/CMFCToolBar::GetDroppedDownMenu.md)|Recupera un puntero al objeto de botón de menú que muestra actualmente el submenú.|  
|[CMFCToolBar::GetGrayDisabledButtons](../Topic/CMFCToolBar::GetGrayDisabledButtons.md)|Especifica si las imágenes de botones deshabilitados son versiones atenuadas de las imágenes de botón estándar, o tomado de la colección de imágenes de botón deshabilitadas.|  
|[CMFCToolBar::GetHighlightedButton](../Topic/CMFCToolBar::GetHighlightedButton.md)|Devuelve un puntero al botón de la barra de herramientas que está actualmente resaltado.|  
|[CMFCToolBar::GetHotBorder](../Topic/CMFCToolBar::GetHotBorder.md)|determina si los botones de la barra de herramientas caluroso\-están seguidos.|  
|[CMFCToolBar::GetHotTextColor](../Topic/CMFCToolBar::GetHotTextColor.md)|Devuelve el color del texto de los botones de la barra de herramientas resaltado.|  
|[CMFCToolBar::GetHwndLastFocus](../Topic/CMFCToolBar::GetHwndLastFocus.md)|Devuelve un identificador a la ventana que tiene el foco de entrada justo antes de que realizó la barra de herramientas.|  
|[CMFCToolBar::GetIgnoreSetText](../Topic/CMFCToolBar::GetIgnoreSetText.md)|Especifica si las llamadas a las etiquetas específicas de botón se omitirán.|  
|[CMFCToolBar::GetImageSize](../Topic/CMFCToolBar::GetImageSize.md)|Devuelve el tamaño actual de las imágenes de botón de la barra de herramientas.|  
|[CMFCToolBar::GetImages](../Topic/CMFCToolBar::GetImages.md)|Devuelve un puntero a la colección de imágenes de botón predeterminado en la aplicación.|  
|[CMFCToolBar::GetImagesOffset](../Topic/CMFCToolBar::GetImagesOffset.md)|Devuelve la diferencia de índice utilizado para buscar las imágenes de los botones de la barra de herramientas de esta barra de herramientas de la lista global de imágenes de botón de la barra de herramientas.|  
|[CMFCToolBar::GetInvalidateItemRect](../Topic/CMFCToolBar::GetInvalidateItemRect.md)|Recupera la región del área de cliente que se debe volver a dibujar para el botón en el índice especificado.|  
|[CMFCToolBar::GetItemID](../Topic/CMFCToolBar::GetItemID.md)|Devuelve el identificador de comando del botón de la barra de herramientas en el índice especificado.|  
|[CMFCToolBar::GetItemRect](../Topic/CMFCToolBar::GetItemRect.md)|Devuelve el rectángulo delimitador del botón en el índice especificado.|  
|[CMFCToolBar::GetLargeColdImages](../Topic/CMFCToolBar::GetLargeColdImages.md)|Devuelve un puntero a la colección de imágenes en frío del botón de la barra de herramientas en la aplicación.|  
|[CMFCToolBar::GetLargeDisabledImages](../Topic/CMFCToolBar::GetLargeDisabledImages.md)|Devuelve un puntero a la colección de imágenes deshabilitadas del botón de la barra de herramientas en la aplicación.|  
|[CMFCToolBar::GetLargeImages](../Topic/CMFCToolBar::GetLargeImages.md)|Devuelve un puntero a la colección de imágenes del botón de la barra de herramientas en la aplicación.|  
|[CMFCToolBar::GetLockedColdImages](../Topic/CMFCToolBar::GetLockedColdImages.md)|Devuelve un puntero a la colección de imágenes en frío bloqueadas en la barra de herramientas.|  
|[CMFCToolBar::GetLockedDisabledImages](../Topic/CMFCToolBar::GetLockedDisabledImages.md)|Devuelve un puntero a la colección de imágenes deshabilitadas bloqueadas en la barra de herramientas.|  
|[CMFCToolBar::GetLockedImages](../Topic/CMFCToolBar::GetLockedImages.md)|Devuelve un puntero a la colección de imágenes de botón bloqueadas en la barra de herramientas.|  
|[CMFCToolBar::GetLockedImageSize](../Topic/CMFCToolBar::GetLockedImageSize.md)|Devuelve el tamaño predeterminado de imágenes compilaciones de la barra de herramientas.|  
|[CMFCToolBar::GetLockedMenuImages](../Topic/CMFCToolBar::GetLockedMenuImages.md)|Devuelve un puntero a la colección de imágenes bloqueadas en el menú de barras de herramientas en la barra de herramientas.|  
|[CMFCToolBar::GetMenuButtonSize](../Topic/CMFCToolBar::GetMenuButtonSize.md)|Devuelve el tamaño de botones de menú en la aplicación.|  
|[CMFCToolBar::GetMenuImageSize](../Topic/CMFCToolBar::GetMenuImageSize.md)|Devuelve el tamaño de las imágenes de botón de menú en la aplicación.|  
|[CMFCToolBar::GetMenuImages](../Topic/CMFCToolBar::GetMenuImages.md)|Devuelve un puntero a la colección de imágenes de botón de menú de la aplicación.|  
|[CMFCToolBar::GetOrigButtons](../Topic/CMFCToolBar::GetOrigButtons.md)|recupera la colección de botones no\-personalizados de la barra de herramientas.|  
|[CMFCToolBar::GetOrigResetButtons](../Topic/CMFCToolBar::GetOrigResetButtons.md)|recupera la colección de botones de reinicio no\-personalizados de la barra de herramientas.|  
|[CMFCToolBar::GetResourceID](../Topic/CMFCToolBar::GetResourceID.md)|recupera el Id. de recurso de la barra de herramientas.|  
|[CMFCToolBar::GetRouteCommandsViaFrame](../Topic/CMFCToolBar::GetRouteCommandsViaFrame.md)|determina que el objeto, el cuadro primario o el propietario, envía los comandos a la barra de herramientas.|  
|[CMFCToolBar::GetRowHeight](../Topic/CMFCToolBar::GetRowHeight.md)|devuelve el alto de botones de la barra de herramientas.|  
|[CMFCToolBar::GetShowTooltips](../Topic/CMFCToolBar::GetShowTooltips.md)|Especifica si la información sobre herramientas se muestran para los botones de la barra de herramientas.|  
|[CMFCToolBar::GetSiblingToolBar](../Topic/CMFCToolBar::GetSiblingToolBar.md)|Recupera el elemento relacionado de la barra de herramientas.|  
|[CMFCToolBar::GetUserImages](../Topic/CMFCToolBar::GetUserImages.md)|Devuelve un puntero a la colección de imágenes definido por el usuario del botón de la barra de herramientas en la aplicación.|  
|[CMFCToolBar::HitTest](../Topic/CMFCToolBar::HitTest.md)|Devuelve el índice del botón de la barra de herramientas que se encuentra en la posición especificada.|  
|[CMFCToolBar::InsertButton](../Topic/CMFCToolBar::InsertButton.md)|inserta un botón en la barra de herramientas.|  
|[CMFCToolBar::InsertSeparator](../Topic/CMFCToolBar::InsertSeparator.md)|Inserta un separador de la barra de herramientas.|  
|[CMFCToolBar::InvalidateButton](../Topic/CMFCToolBar::InvalidateButton.md)|Reemplaza el área cliente del botón de la barra de herramientas que existe en el índice especificado.|  
|[CMFCToolBar::IsAddRemoveQuickCustomize](../Topic/CMFCToolBar::IsAddRemoveQuickCustomize.md)|Determina si un usuario puede agregar o quitar botones de la barra de herramientas mediante la opción de menú de **Personalizar** .|  
|[CMFCToolBar::IsAltCustomizeMode](../Topic/CMFCToolBar::IsAltCustomizeMode.md)|Especifica si *la personalización rápida* se utiliza para agregar un botón.|  
|[CMFCToolBar::IsAutoGrayInactiveImages](../Topic/CMFCToolBar::IsAutoGrayInactiveImages.md)|Especifica si la generación automática de imágenes de botón \(no resaltado\) inactivas está habilitada.|  
|[CMFCToolBar::IsBasicCommand](../Topic/CMFCToolBar::IsBasicCommand.md)|determina si un comando está en la lista de comandos básicos.|  
|[CMFCToolBar::IsButtonExtraSizeAvailable](../Topic/CMFCToolBar::IsButtonExtraSizeAvailable.md)|Determina si la barra de herramientas puede mostrar botones que tienen bordes extendidos.|  
|[CMFCToolBar::IsButtonHighlighted](../Topic/CMFCToolBar::IsButtonHighlighted.md)|Determina si un botón en la barra de herramientas está resaltado.|  
|[CMFCToolBar::IsCommandPermitted](../Topic/CMFCToolBar::IsCommandPermitted.md)|determina si permiten a un comando.|  
|[CMFCToolBar::IsCommandRarelyUsed](../Topic/CMFCToolBar::IsCommandRarelyUsed.md)|Determina si se utiliza un comando raramente \(vea [CMFCToolBar::SetCommandUsageOptions](../Topic/CMFCToolBar::SetCommandUsageOptions.md)\).|  
|[CMFCToolBar::IsCustomizeMode](../Topic/CMFCToolBar::IsCustomizeMode.md)|Especifica si el marco de la barra de herramientas está en modo de personalización.|  
|[CMFCToolBar::IsDragButton](../Topic/CMFCToolBar::IsDragButton.md)|Determina si se arrastra un botón de la barra de herramientas.|  
|[CMFCToolBar::IsExistCustomizeButton](../Topic/CMFCToolBar::IsExistCustomizeButton.md)|determina si la barra de herramientas contiene el botón de **Personalizar** .|  
|[CMFCToolBar::IsFloating](../Topic/CMFCToolBar::IsFloating.md)|Determina si la barra de herramientas flota.|  
|[CMFCToolBar::IsLargeIcons](../Topic/CMFCToolBar::IsLargeIcons.md)|Especifica si las barras de herramientas en la aplicación muestran actualmente iconos grandes.|  
|[CMFCToolBar::IsLastCommandFromButton](../Topic/CMFCToolBar::IsLastCommandFromButton.md)|Determina si se suministra el comando recientemente ejecutado el botón de la barra de herramientas especificado.|  
|[CMFCToolBar::IsLocked](../Topic/CMFCToolBar::IsLocked.md)|determina si la barra de herramientas está bloqueada.|  
|[CMFCToolBar::IsOneRowWithSibling](../Topic/CMFCToolBar::IsOneRowWithSibling.md)|Determina si la barra de herramientas y la barra de herramientas relacionado están colocados en la misma fila.|  
|[CMFCToolBar::IsUserDefined](../Topic/CMFCToolBar::IsUserDefined.md)|Especifica si la barra de herramientas está definido por el usuario.|  
|[CMFCToolBar::LoadBitmap](../Topic/CMFCToolBar::LoadBitmap.md)|Carga las imágenes de la barra de herramientas de recursos de la aplicación.|  
|[CMFCToolBar::LoadBitmapEx](../Topic/CMFCToolBar::LoadBitmapEx.md)|Carga las imágenes de la barra de herramientas de recursos de la aplicación.  incluye imágenes grandes.|  
|[CMFCToolBar::LoadParameters](../Topic/CMFCToolBar::LoadParameters.md)|Carga opciones de barras de herramientas globales del Registro de Windows.|  
|[CMFCToolBar::LoadState](../Topic/CMFCToolBar::LoadState.md)|Carga información de estado de la barra de herramientas del Registro de Windows.  \(Reemplaza [CPane::LoadState](../Topic/CPane::LoadState.md).\)|  
|[CMFCToolBar::LoadToolBar](../Topic/CMFCToolBar::LoadToolBar.md)|carga la barra de herramientas de recursos de la aplicación.|  
|[CMFCToolBar::LoadToolBarEx](../Topic/CMFCToolBar::LoadToolBarEx.md)|Carga la barra de herramientas de recursos de la aplicación mediante la clase de `CMFCToolBarInfo` para que la aplicación para utilizar imágenes grandes.|  
|[CMFCToolBar::OnChangeHot](../Topic/CMFCToolBar::OnChangeHot.md)|Llamado por el marco cuando un usuario selecciona un botón de la barra de herramientas.|  
|[CMFCToolBar::OnFillBackground](../Topic/CMFCToolBar::OnFillBackground.md)|Llamado por el marco de [CBasePane::DoPaint](../Topic/CBasePane::DoPaint.md) para rellenar el fondo de la barra de herramientas.|  
|[CMFCToolBar::OnReset](../Topic/CMFCToolBar::OnReset.md)|restablece la barra de herramientas a su estado original.|  
|[CMFCToolBar::OnSetAccData](../Topic/CMFCToolBar::OnSetAccData.md)|\(Reemplaza [CBasePane::OnSetAccData](../Topic/CBasePane::OnSetAccData.md).\)|  
|[CMFCToolBar::OnSetDefaultButtonText](../Topic/CMFCToolBar::OnSetDefaultButtonText.md)|Restablece el texto de un botón de la barra de herramientas a su estado predeterminado.|  
|`CMFCToolBar::OnUpdateCmdUI`|Utilizado de forma interna.|  
|[CMFCToolBar::RemoveAllButtons](../Topic/CMFCToolBar::RemoveAllButtons.md)|quita todos los botones de la barra de herramientas.|  
|[CMFCToolBar::RemoveButton](../Topic/CMFCToolBar::RemoveButton.md)|quita el botón con el índice especificado de la barra de herramientas.|  
|[CMFCToolBar::RemoveStateFromRegistry](../Topic/CMFCToolBar::RemoveStateFromRegistry.md)|Elimina la información de estado de la barra de herramientas del Registro de Windows.|  
|[CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)|reemplaza un botón de la barra de herramientas con otro botón de la barra de herramientas.|  
|[CMFCToolBar::ResetAll](../Topic/CMFCToolBar::ResetAll.md)|restablece todas las barras de herramientas a sus estados originales.|  
|[CMFCToolBar::ResetAllImages](../Topic/CMFCToolBar::ResetAllImages.md)|borra todas las colecciones de la imagen de la barra de herramientas en la aplicación.|  
|[CMFCToolBar::RestoreOriginalState](../Topic/CMFCToolBar::RestoreOriginalState.md)|Restaura el estado original de una barra de herramientas.|  
|[CMFCToolBar::SaveState](../Topic/CMFCToolBar::SaveState.md)|Guarda información de estado para la barra de herramientas en el Registro de Windows.  \(Reemplaza [CPane::SaveState](../Topic/CPane::SaveState.md).\)|  
|`CMFCToolBar::Serialize`|\(Reemplaza `CBasePane::Serialize`.\)|  
|[CMFCToolBar::SetBasicCommands](../Topic/CMFCToolBar::SetBasicCommands.md)|Establece la lista de comandos que se muestra cuando un usuario abre un menú.|  
|[CMFCToolBar::SetButtonInfo](../Topic/CMFCToolBar::SetButtonInfo.md)|Establece el identificador de comando, el estilo, y el identificador de la imagen de un botón de la barra de herramientas.|  
|[CMFCToolBar::SetButtonStyle](../Topic/CMFCToolBar::SetButtonStyle.md)|Establece el estilo de botón de la barra de herramientas en el índice especificado.|  
|[CMFCToolBar::SetButtonText](../Topic/CMFCToolBar::SetButtonText.md)|Establece el etiqueta de texto de un botón de la barra de herramientas.|  
|[CMFCToolBar::SetButtons](../Topic/CMFCToolBar::SetButtons.md)|Establece los botones de la barra de herramientas.|  
|[CMFCToolBar::SetCommandUsageOptions](../Topic/CMFCToolBar::SetCommandUsageOptions.md)|Especifica cuándo los comandos raramente utilizados no aparecen en el menú de la aplicación.|  
|[CMFCToolBar::SetCustomizeMode](../Topic/CMFCToolBar::SetCustomizeMode.md)|Habilita o deshabilita el modo de personalización para todas las barras de herramientas en la aplicación.|  
|[CMFCToolBar::SetGrayDisabledButtons](../Topic/CMFCToolBar::SetGrayDisabledButtons.md)|Especifica si los botones deshabilitados en la barra de herramientas están deshabilitados o si las imágenes deshabilitadas se utilizan para los botones deshabilitados.|  
|[CMFCToolBar::SetHeight](../Topic/CMFCToolBar::SetHeight.md)|establece el alto de la barra de herramientas.|  
|[CMFCToolBar::SetHotBorder](../Topic/CMFCToolBar::SetHotBorder.md)|especifica si los botones de la barra de herramientas caluroso\-están seguidos.|  
|[CMFCToolBar::SetHotTextColor](../Topic/CMFCToolBar::SetHotTextColor.md)|Establece el color del texto para los botones de la barra de herramientas activo.|  
|[CMFCToolBar::SetLargeIcons](../Topic/CMFCToolBar::SetLargeIcons.md)|Especifica si los botones de la barra de herramientas muestra iconos grandes.|  
|[CMFCToolBar::SetLockedSizes](../Topic/CMFCToolBar::SetLockedSizes.md)|Establece los tamaños de botones bloqueados y las imágenes bloqueadas en la barra de herramientas.|  
|[CMFCToolBar::SetMenuSizes](../Topic/CMFCToolBar::SetMenuSizes.md)|Establece el tamaño de los botones de menú de barras de herramientas y de las imágenes.|  
|[CMFCToolBar::SetNonPermittedCommands](../Topic/CMFCToolBar::SetNonPermittedCommands.md)|establece la lista de comandos que no se puede ejecutar por el usuario.|  
|[CMFCToolBar::SetOneRowWithSibling](../Topic/CMFCToolBar::SetOneRowWithSibling.md)|posiciones la barra de herramientas y su elemento relacionado respecto a la misma fila.|  
|[CMFCToolBar::SetPermament](../Topic/CMFCToolBar::SetPermament.md)|especifica si un usuario puede cerrar la barra de herramientas.|  
|[CMFCToolBar::SetRouteCommandsViaFrame](../Topic/CMFCToolBar::SetRouteCommandsViaFrame.md)|Especifica si el marco primario o el propietario envía comandos a la barra de herramientas.|  
|[CMFCToolBar::SetShowTooltips](../Topic/CMFCToolBar::SetShowTooltips.md)|Especifica si el marco muestra información sobre herramientas.|  
|[CMFCToolBar::SetSiblingToolBar](../Topic/CMFCToolBar::SetSiblingToolBar.md)|Especifica el elemento relacionado de la barra de herramientas.|  
|[CMFCToolBar::SetSizes](../Topic/CMFCToolBar::SetSizes.md)|Especifica los tamaños de botones y las imágenes en todas las barras de herramientas.|  
|[CMFCToolBar::SetToolBarBtnText](../Topic/CMFCToolBar::SetToolBarBtnText.md)|Especifica las propiedades de un botón en la barra de herramientas.|  
|[CMFCToolBar::SetTwoRowsWithSibling](../Topic/CMFCToolBar::SetTwoRowsWithSibling.md)|Posiciones la barra de herramientas y su elemento relacionado respecto a filas independientes.|  
|[CMFCToolBar::SetUserImages](../Topic/CMFCToolBar::SetUserImages.md)|establece la colección de imágenes definido por el usuario en la aplicación.|  
|[CMFCToolBar::StretchPane](../Topic/CMFCToolBar::StretchPane.md)|Expande la barra de herramientas vertical u horizontalmente. \(Reemplaza [CBasePane::StretchPane](../Topic/CBasePane::StretchPane.md).\)|  
|[CMFCToolBar::TranslateChar](../Topic/CMFCToolBar::TranslateChar.md)|Ejecuta un comando del botón si la clave especificada corresponde a un método abreviado de teclado válido.|  
|[CMFCToolBar::UpdateButton](../Topic/CMFCToolBar::UpdateButton.md)|Actualiza el estado del botón especificado.|  
|[CMFCToolBar::WrapToolBar](../Topic/CMFCToolBar::WrapToolBar.md)|Coloca los botones de la barra de herramientas de nuevo dentro de las dimensiones especificadas.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBar::AllowShowOnList](../Topic/CMFCToolBar::AllowShowOnList.md)|Determina si la barra de herramientas se muestra en la lista del panel de **barras de herramientas** del cuadro de diálogo de **Personalizar** .|  
|[CMFCToolBar::CalcMaxButtonHeight](../Topic/CMFCToolBar::CalcMaxButtonHeight.md)|calcula el alto máximo de un botón en la barra de herramientas.|  
|[CMFCToolBar::DoPaint](../Topic/CMFCToolBar::DoPaint.md)|Redibuja una barra de herramientas.|  
|[CMFCToolBar::DrawButton](../Topic/CMFCToolBar::DrawButton.md)|Redibuja un botón de la barra de herramientas.|  
|[CMFCToolBar::DrawSeparator](../Topic/CMFCToolBar::DrawSeparator.md)|Redibuja un separador de una barra de herramientas.|  
|[CMFCToolBar::OnUserToolTip](../Topic/CMFCToolBar::OnUserToolTip.md)|Llamado por el marco cuando la información sobre herramientas de un botón está a punto de ser mostrada.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBar::m\_bDontScaleImages](../Topic/CMFCToolBar::m_bDontScaleImages.md)|Especifica si escalar o no las imágenes de la barra de herramientas de alto modo de PPP.|  
|[CMFCToolBar::m\_dblLargeImageRatio](../Topic/CMFCToolBar::m_dblLargeImageRatio.md)|Especifica la relación entre la dimensión \(alto o ancho\) de imágenes grandes y la dimensión de las imágenes normales.|  
  
## Comentarios  
 Para especificar un objeto de `CMFCToolBar` en la aplicación, siga estos pasos:  
  
1.  Agregue un objeto de `CMFCToolBar` a la ventana de marco principal.  
  
2.  Cuando se procesa el mensaje de `WM_CREATE` para la ventana de marco principal, llame a [CMFCToolBar::Create](../Topic/CMFCToolBar::Create.md) o [CMFCToolBar::CreateEx](../Topic/CMFCToolBar::CreateEx.md) para crear la barra de herramientas y especificar su estilo.  
  
3.  Llamada [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md) para especificar el estilo de acoplamiento.  
  
 Para insertar un botón especial, como un cuadro combinado o una barra de herramientas desplegable, reserva un botón ficticio en el recurso primario, y reemplace el botón ficticio en tiempo de ejecución mediante [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md).  Para obtener más información, vea [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md).  
  
 `CMFCToolBar` es la clase base para las clases [CMFCMenuBar Class](../../mfc/reference/cmfcmenubar-class.md), [CMFCPopupMenuBar \(clase\)](../../mfc/reference/cmfcpopupmenubar-class.md), y [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)de la biblioteca MFC.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCToolBar` .  El ejemplo muestra cómo establecer el texto de la etiqueta de ventana de la barra de herramientas, establecer los bordes, establecer el estilo del panel, y habilitar el botón de **agregue o quite los botones** que aparece al final de la barra de herramientas.  Este fragmento de código es parte de [Ejemplo de demostración de IE](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo#6](../../mfc/reference/codesnippet/CPP/cmfctoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo#8](../../mfc/reference/codesnippet/CPP/cmfctoolbar-class_2.cpp)]  
  
## Requisitos  
 **encabezado:** afxtoolbar.h  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCMenuBar Class](../../mfc/reference/cmfcmenubar-class.md)   
 [CMFCPopupMenuBar \(clase\)](../../mfc/reference/cmfcpopupmenubar-class.md)   
 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)