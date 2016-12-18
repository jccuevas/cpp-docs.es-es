---
title: "Controles ActiveX MFC: Agregar m&#233;todos personalizados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX en MFC, métodos"
  - "PtInCircle (método personalizado)"
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controles ActiveX MFC: Agregar m&#233;todos personalizados
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los métodos personalizados difieren de los métodos comunes en que no implementa ya por `COleControl`.  Debe proporcionar la implementación para cada método personalizado que agregue al control.  
  
 Un usuario del control ActiveX puede llamar a un método personalizado en cualquier momento para realizar acciones CONTROL\- concretos.  La entrada de asignación de envío para los métodos personalizados tiene el formato `DISP_FUNCTION`.  
  
##  <a name="_core_adding_a_custom_method_with_classwizard"></a> Agregue un método personalizado Con el asistente para agregar métodos  
 El procedimiento siguiente muestra cómo agregar el método personalizado PtInCircle un código estructural del control ActiveX.  PtInCircle determina dentro de si las coordenadas pasadas al control se o fuera del círculo.  Este mismo procedimiento también se puede utilizar para agregar otros métodos personalizados.  Sustituya el nombre de método y los parámetros para el nombre y los parámetros del método de PtInCircle.  
  
> [!NOTE]
>  Este ejemplo utiliza la función de `InCircle` de los eventos de caso.  Para obtener más información sobre esta función, vea el artículo [Controles ActiveX de MFC: Agregar eventos personalizados a un control ActiveX](../mfc/mfc-activex-controls-adding-custom-events.md).  
  
#### Para agregar el método personalizado de PtInCircle mediante el asistente para agregar métodos  
  
1.  Cargue el proyecto de control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca de controles.  
  
3.  Haga clic con el botón secundario en el nodo de la interfaz del control \(el segundo nodo el nodo de biblioteca\) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar método**.  
  
     Se abrirá el asistente para agregar métodos.  
  
5.  En el cuadro de **Nombre del método** , `PtInCircle`escrito.  
  
6.  En el cuadro de **Nombre interno** , escriba el nombre de la función interna de método o use el valor predeterminado \(en este caso, `PtInCircle`\).  
  
7.  En el cuadro de **Tipo devuelto** , haga clic en **VARIANT\_BOOL** para el tipo de valor devuelto del método.  
  
8.  Mediante los controles de **Tipo de parámetro** y de **Nombre del parámetro** , agregue un parámetro denominado `xCoord` \(tipo **OLE\_XPOS\_PIXELS**\).  
  
9. Mediante los controles de **Tipo de parámetro** y de **Nombre del parámetro** , agregue un parámetro denominado `yCoord` \(tipo **OLE\_YPOS\_PIXELS**\).  
  
10. Haga clic en **Finalizar**.  
  
##  <a name="_core_classwizard_changes_for_custom_methods"></a> Agregue los cambios del asistente de método para métodos personalizados  
 Cuando se agrega un método personalizado, el asistente para agregar realiza algunos cambios en el encabezado de la clase control \(. H\) y archivos de implementación \(.CPP\).  La siguiente línea se agrega a la declaración del mapa de distribución en el encabezado de la clase control \(. H\) archivo:  
  
 [!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-methods_1.h)]  
  
 Este código declara un método `PtInCircle`denominado controlador de envío.  Esta función se puede llamar el usuario del control mediante el nombre externo PtInCircle.  
  
 La siguiente línea se agrega al archivo de .IDL de control:  
  
 [!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-methods_2.idl)]  
  
 Esta línea asigna al método de PtInCircle el número de identificación concreto, la posición de los métodos del asistente para agregar métodos y la lista de propiedades.  Dado que utilizaban el asistente para agregar métodos para agregar el método personalizado, la entrada para él se agregó automáticamente al archivo de .IDL del proyecto.  
  
 Además, la línea siguiente, ubicada en el archivo de implementación \(.CPP\) de la clase de control, se agrega al envío de control asignado:  
  
 [!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-methods_3.cpp)]  
  
 La macro de `DISP_FUNCTION` asigna el método PtInCircle a la función de controlador de control, `PtInCircle`, declara el tipo de valor devuelto para ser **VARIANT\_BOOL**, y declara dos parámetros de **VTS\_XPOS\_PIXELS** escrito y de **VTS\_YPOSPIXELS** que se pasarán a `PtInCircle`.  
  
 Finalmente, el asistente para agregar agrega la función `CSampleCtrl::PtInCircle` de código auxiliar al archivo de implementación del control \(.CPP\).  Para que `PtInCircle` funcione como se indicó anteriormente, debe modificarse como sigue:  
  
 [!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-methods_4.cpp)]  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Iconos de la Vista de clases y del Examinador de objetos](../Topic/Class%20View%20and%20Object%20Browser%20Icons.md)