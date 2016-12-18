---
title: "CToolBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CToolBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mapas de bits [C++], button controls"
  - "botones [C++], MFC toolbars"
  - "control bars [C++], CToolBar class"
  - "CToolBar class"
  - "barras de herramientas [C++], CToolBar class"
  - "Windows common controls [C++], CToolBar class"
  - "Windows toolbar common controls [C++]"
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
caps.latest.revision: 26
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Barras de controles que tienen un rango de botones de mapas de bits y separadores opcionales.  
  
## Sintaxis  
  
```  
class CToolBar : public CControlBar  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CToolBar::CToolBar](../Topic/CToolBar::CToolBar.md)|Crea un objeto `CToolBar`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CToolBar::CommandToIndex](../Topic/CToolBar::CommandToIndex.md)|Devuelve el índice de un botón con la identificación especificada de comando|  
|[CToolBar::Create](../Topic/CToolBar::Create.md)|Crea la barra de herramientas de Windows y la agrega al objeto de `CToolBar` .|  
|[CToolBar::CreateEx](../Topic/CToolBar::CreateEx.md)|Crea un objeto de `CToolBar` con estilos adicionales para el objeto incrustado de `CToolBarCtrl` .|  
|[CToolBar::GetButtonInfo](../Topic/CToolBar::GetButtonInfo.md)|recupera el identificador, el estilo, y el número de la imagen de un botón.|  
|[CToolBar::GetButtonStyle](../Topic/CToolBar::GetButtonStyle.md)|recupera el estilo para un botón.|  
|[CToolBar::GetButtonText](../Topic/CToolBar::GetButtonText.md)|recupera el texto que aparecerá en un botón.|  
|[CToolBar::GetItemID](../Topic/CToolBar::GetItemID.md)|Devuelve el identificador de comando de un botón o un separador en el índice especificado.|  
|[CToolBar::GetItemRect](../Topic/CToolBar::GetItemRect.md)|Recupera el rectángulo de presentación para el elemento en el índice especificado.|  
|[CToolBar::GetToolBarCtrl](../Topic/CToolBar::GetToolBarCtrl.md)|Permite el acceso directo al control común subyacente.|  
|[CToolBar::LoadBitmap](../Topic/CToolBar::LoadBitmap.md)|Carga el mapa de bits que contiene imágenes de mapa de bits\-botón.|  
|[CToolBar::LoadToolBar](../Topic/CToolBar::LoadToolBar.md)|Carga un recurso de la barra de herramientas creado con el editor de recursos.|  
|[CToolBar::SetBitmap](../Topic/CToolBar::SetBitmap.md)|Establece una imagen de mapa de bits.|  
|[CToolBar::SetButtonInfo](../Topic/CToolBar::SetButtonInfo.md)|establece el identificador, el estilo, y el número de la imagen de un botón.|  
|[CToolBar::SetButtons](../Topic/CToolBar::SetButtons.md)|Establece estilos button y un índice de imágenes de botón dentro del mapa de bits.|  
|[CToolBar::SetButtonStyle](../Topic/CToolBar::SetButtonStyle.md)|Establece el estilo de un botón.|  
|[CToolBar::SetButtonText](../Topic/CToolBar::SetButtonText.md)|establece el texto que aparecerá en un botón.|  
|[CToolBar::SetHeight](../Topic/CToolBar::SetHeight.md)|establece el alto de la barra de herramientas.|  
|[CToolBar::SetSizes](../Topic/CToolBar::SetSizes.md)|Establece los tamaños de botones y de los mapas de bits.|  
  
## Comentarios  
 Los botones pueden actuar como los pulsadores, botones de casilla, o los botones de radio.  los objetos de`CToolBar` suelen ser miembros insertados de los objetos de la ventana de marco derivados de la clase [CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).  
  
 [CToolBar:: GetToolBarCtrl](../Topic/CToolBar::GetToolBarCtrl.md), una función miembro nueva a MFC 4,0, permite aprovechar las ventajas de la compatibilidad de controles comunes de Windows para la personalización y la funcionalidad adicional de la barra de herramientas.  las funciones miembro de`CToolBar` ofrecen la mayor parte de la funcionalidad de los controles comunes de Windows; sin embargo, cuando se llama a `GetToolBarCtrl`, puede proporcionar a barras de herramientas aún más de las características de Windows 95 \/98 barra de herramientas.  Cuando se llama a `GetToolBarCtrl`, devolverá una referencia a un objeto de `CToolBarCtrl` .  Vea [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) para obtener más información sobre el diseño de las barras de herramientas mediante controles comunes de Windows.  Para obtener más información general sobre los controles comunes, vea [Controles comunes](http://msdn.microsoft.com/library/windows/desktop/bb775493) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Visual C\+\+ proporciona dos métodos para crear una barra de herramientas.  Para crear un recurso de la barra de herramientas mediante el editor de recursos, siga estos pasos:  
  
1.  Cree un recurso de la barra de herramientas.  
  
2.  Cree el objeto de `CToolBar` .  
  
3.  Llame a la función de [Crear](../Topic/CToolBar::Create.md) \(o [CreateEx](../Topic/CToolBar::CreateEx.md)\) para crear la barra de herramientas de Windows y para adjuntarla al objeto de `CToolBar` .  
  
4.  Llamada [LoadToolBar](../Topic/CToolBar::LoadToolBar.md) para cargar el recurso de la barra de herramientas.  
  
 De lo contrario, siga estos pasos:  
  
1.  Cree el objeto de `CToolBar` .  
  
2.  Llame a la función de [Crear](../Topic/CToolBar::Create.md) \(o [CreateEx](../Topic/CToolBar::CreateEx.md)\) para crear la barra de herramientas de Windows y para adjuntarla al objeto de `CToolBar` .  
  
3.  Llame a [LoadBitmap](../Topic/CToolBar::LoadBitmap.md) para cargar el mapa de bits que contiene imágenes de botón de la barra de herramientas.  
  
4.  Llame a [SetButtons](../Topic/CToolBar::SetButtons.md) para establecer el estilo de botón y asociar cada botón con una imagen en el mapa de bits.  
  
 Todas las imágenes de botón en la barra de herramientas se toman en un mapa de bits, que debe contener una imagen de cada botón.  Todas las imágenes deben tener el mismo tamaño; el valor predeterminado es 16 píxeles de ancho y 15 píxeles de alto.  Las imágenes deben estar en paralelo en el mapa de bits.  
  
 La función de `SetButtons` contiene un puntero a una matriz de id. del control y un entero que especifica el número de elementos de la matriz.  La función asigna el identificador de cada botón al valor del elemento correspondiente de la matriz y asigna a cada botón un índice de la imagen, que especifica la posición de la imagen del botón en el mapa de bits.  si un elemento de matriz tiene el valor **ID\_SEPARATOR**, no se asigna ningún índice de la imagen.  
  
 El orden de las imágenes en el mapa de bits es normalmente el orden en el que se dibujan en la pantalla, pero puede utilizar la función de [SetButtonInfo](../Topic/CToolBar::SetButtonInfo.md) para cambiar la relación entre el orden de la imagen y el orden de dibujo.  
  
 Todos los botones de una barra de herramientas son el mismo tamaño.  El valor predeterminado es de 24 x 22 píxeles, de acuerdo con *las instrucciones de la interfaz de Windows para el diseño de software*.  Cualquier espacio adicional entre la imagen y las dimensiones del botón se utiliza para formar un borde alrededor de la imagen.  
  
 Cada botón con una imagen.  Se representan las diferentes estados y estilos de botón \(normal, arriba, siguiente, de deshabilitado, deshabilitado siguiente, e indeterminado\) de ese una imagen.  Aunque los mapas de bits pueden ser cualquier color, puede lograr los mejores resultados con imágenes negro y tonos de gris.  
  
> [!WARNING]
>  `CToolBar` admite mapas de bits con un máximo de 16 colores.  Cuando se carga una imagen en un editor de barras de herramientas, Visual Studio convierte automáticamente la imagen a 16 colores bitmap en caso necesario, y muestra un mensaje de advertencia si la imagen se ha convertido.  Si utiliza una imagen con más de 16 colores \(mediante un editor externo para editar la imagen\), la aplicación podría comportarse inesperado.  
  
 los botones de la barra de herramientas imitan los pulsadores de forma predeterminada.  Sin embargo, los botones de la barra de herramientas también pueden imitar botones o los botones de radio de la casilla.  Botones de casilla tienen tres estados: activada, desactivada, e indeterminado.  Los botones de radio sólo tienen dos estados: comprobado y borrado.  
  
 Para establecer un estilo de botón individual o de separador sin que señale a una matriz, llame a [GetButtonStyle](../Topic/CToolBar::GetButtonStyle.md) para recuperar el estilo, y llame a [SetButtonStyle](../Topic/CToolBar::SetButtonStyle.md) en lugar de `SetButtons`.  `SetButtonStyle` es muy útil cuando se desea cambiar el estilo de un botón en tiempo de ejecución.  
  
 Para asignar texto aparezca en un botón, llame a [GetButtonText](../Topic/CToolBar::GetButtonText.md) para recuperar el texto que aparezca en el botón, y llame a [SetButtonText](../Topic/CToolBar::SetButtonText.md) para establecer el texto.  
  
 Para crear un botón, una asignación de casilla el estilo **TBBS\_CHECKBOX** o utilizar la función miembro de `SetCheck` de un objeto de `CCmdUI` en un controlador de `ON_UPDATE_COMMAND_UI` .  La llamada `SetCheck` gira un mismo botón en un botón de la casilla.  Pase `SetCheck` un argumento de 0 para desactivado, 1 para activa, o 2 para indeterminado.  
  
 Para crear un botón de radio, llame a la función miembro de [SetRadio](../Topic/CCmdUI::SetRadio.md) de un objeto de [CCmdUI](../../mfc/reference/ccmdui-class.md) de un controlador de `ON_UPDATE_COMMAND_UI` .  Pase `SetRadio` un argumento de 0 para desactivado o cero para activarla.  Para proporcionar un grupo de radio mutuamente comportamiento exclusivo, debe tener los controladores de `ON_UPDATE_COMMAND_UI` para todos los botones en el grupo.  
  
 Para obtener más información sobre cómo utilizar `CToolBar`, vea el artículo [implementación de la barra de herramientas de MFC](../../mfc/mfc-toolbar-implementation.md) y [nota técnica 31: Barras de controles](../../mfc/tn031-control-bars.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CToolBar`  
  
## Requisitos  
 **encabezado:** afxext.h  
  
## Vea también  
 [ejemplo CTRLBARS de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo DLGCBR32 de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo DOCKTOOL de MFC](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl Class](../../mfc/reference/ctoolbarctrl-class.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [CToolBar::Create](../Topic/CToolBar::Create.md)   
 [CToolBar::LoadBitmap](../Topic/CToolBar::LoadBitmap.md)   
 [CToolBar::SetButtons](../Topic/CToolBar::SetButtons.md)   
 [CCmdUI::SetCheck](../Topic/CCmdUI::SetCheck.md)   
 [CCmdUI::SetRadio](../Topic/CCmdUI::SetRadio.md)