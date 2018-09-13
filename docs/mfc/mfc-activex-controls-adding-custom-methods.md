---
title: 'Controles ActiveX MFC: Agregar métodos personalizados | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f0d52f3dec2967cc7a8d859e1f6845fe93c6fd6
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45534890"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>Controles ActiveX MFC: Agregar métodos personalizados
Métodos personalizados se diferencian de los métodos estándar en que no están implementadas por `COleControl`. Debe proporcionar la implementación para cada método personalizado que agregue al control.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).  
  
 Usuario de un control ActiveX puede llamar a un método personalizado en cualquier momento para realizar acciones específicas del control. La entrada de asignación de envío para los métodos personalizados es la forma DISP_FUNCTION.  
  
##  <a name="_core_adding_a_custom_method_with_classwizard"></a> Agregar un método personalizado con el Asistente para agregar métodos  
 El siguiente procedimiento muestra cómo agregar el método personalizado PtInCircle al código de esqueleto de un control ActiveX. PtInCircle determina si las coordenadas que se pasa al control son dentro o fuera del círculo. También se puede usar este mismo procedimiento para agregar otros métodos personalizados. Sustituya el nombre del método personalizado y sus parámetros de los parámetros y el nombre del método PtInCircle.  
  
> [!NOTE]
>  Este ejemplo se usa el `InCircle` función desde el artículo de eventos. Para obtener más información sobre esta función, vea el artículo [controles ActiveX MFC: agregar eventos personalizados a un ActiveX Control](../mfc/mfc-activex-controls-adding-custom-events.md).  
  
#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Para agregar el método personalizado PtInCircle mediante el Asistente para agregar métodos  
  
1.  Cargar el proyecto del control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca del control.  
  
3.  Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar método**.  
  
     Se abrirá al Asistente para agregar método.  
  
5.  En el **nombre del método** , escriba *PtInCircle*.  
  
6.  En el **nombre interno** cuadro, escriba el nombre de la función interna del método o utilice el valor predeterminado (en este caso, *PtInCircle*).  
  
7.  En el **Return Type** cuadro, haga clic en **VARIANT_BOOL** para el tipo de valor devuelto del método.  
  
8.  Mediante el **tipo de parámetro** y **nombre del parámetro** controles, agregue un parámetro denominado *xCoord* (tipo *OLE_XPOS_PIXELS*).  
  
9. Mediante el **tipo de parámetro** y **nombre del parámetro** controles, agregue un parámetro denominado *yCoord* (tipo *OLE_YPOS_PIXELS*).  
  
10. Haga clic en **Finalizar**.  
  
##  <a name="_core_classwizard_changes_for_custom_methods"></a> Agregar método cambios del Asistente para métodos personalizados  
 Cuando se agrega un método personalizado, el Asistente para agregar métodos realiza algunos cambios en los archivos de encabezado (. (H) e implementación (. Archivos CPP). Se agrega la línea siguiente a la declaración de mapa de envío en el archivo de encabezado (. H) archivo de:  
  
 [!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]  
  
 Este código declara un controlador de método de envío denominado `PtInCircle`. Se puede llamar a esta función por el usuario de control mediante el nombre externo `PtInCircle`.  
  
 La siguiente línea se agrega al control. Archivo IDL:  
  
 [!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]  
  
 Esta línea asigna el `PtInCircle` método un número de Id. específico, la posición del método en la lista de métodos y propiedades del Asistente para agregar métodos. Porque se ha utilizado el Asistente para agregar métodos para agregar el método personalizado, la entrada para el se agregó automáticamente al proyecto. Archivo IDL.  
  
 Además, la línea siguiente, se encuentra en la implementación (. Archivo CPP) de la clase de control, se agrega al mapa de envíos del control:  
  
 [!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]  
  
 La macro DISP_FUNCTION asigna el método `PtInCircle` en función de controlador del control, `PtInCircle`, declara el tipo de valor devuelto sea **VARIANT_BOOL**y declara dos parámetros de tipo **VTS_XPOS_PIXELS** y **VTS_YPOSPIXELS** que se pasarán al `PtInCircle`.  
  
 Por último, el Asistente para agregar métodos agrega la función auxiliar `CSampleCtrl::PtInCircle` a la parte inferior de la implementación del control (. Archivo CPP). Para `PtInCircle` para que funcione como se indicó anteriormente, debe modificarlo como sigue:  
  
 [!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Iconos de la Vista de clases y del Examinador de objetos](/visualstudio/ide/class-view-and-object-browser-icons)

