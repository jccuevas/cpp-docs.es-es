---
title: "Controles ActiveX MFC: Agregar métodos personalizados | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2f79d4c5f7407e3de12ccf180a68b2b22e35bf10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>Controles ActiveX MFC: Agregar métodos personalizados
Métodos personalizados se diferencian de los métodos estándar en que no están implementadas por `COleControl`. Debe proporcionar la implementación para cada método personalizado que agregue al control.  
  
 Usuario de un control ActiveX puede llamar a un método personalizado en cualquier momento para realizar acciones específicas del control. La entrada de mapa de envíos para métodos personalizados tiene la forma `DISP_FUNCTION`.  
  
##  <a name="_core_adding_a_custom_method_with_classwizard"></a>Agregar un método personalizado con el Asistente para agregar métodos  
 El siguiente procedimiento muestra cómo agregar el método personalizado PtInCircle a la estructura de código de un control ActiveX. PtInCircle determina si las coordenadas que se pasan al control están dentro o fuera del círculo. También se puede utilizar este mismo procedimiento para agregar otros métodos personalizados. Sustituya el nombre de método personalizado y sus parámetros para el nombre del método PtInCircle y los parámetros.  
  
> [!NOTE]
>  Este ejemplo se utiliza la `InCircle` función del artículo eventos. Para obtener más información sobre esta función, vea el artículo [controles ActiveX de MFC: agregar eventos personalizados a un ActiveX Control](../mfc/mfc-activex-controls-adding-custom-events.md).  
  
#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Para agregar el método personalizado PtInCircle mediante el Asistente para agregar métodos  
  
1.  Cargar proyecto del control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca del control.  
  
3.  Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar método**.  
  
     Se abrirá al Asistente para agregar métodos.  
  
5.  En el **nombre del método** , escriba `PtInCircle`.  
  
6.  En el **nombre interno** cuadro, escriba el nombre de función interna del método o utilice el valor predeterminado (en este caso, `PtInCircle`).  
  
7.  En el **tipo de valor devuelto** cuadro, haga clic en **VARIANT_BOOL** para el tipo de valor devuelto del método.  
  
8.  Mediante el **tipo de parámetro** y **nombre de parámetro** controles, agregue un parámetro denominado `xCoord` (tipo **OLE_XPOS_PIXELS**).  
  
9. Mediante el **tipo de parámetro** y **nombre de parámetro** controles, agregue un parámetro denominado `yCoord` (tipo **OLE_YPOS_PIXELS**).  
  
10. Haga clic en **Finalizar**.  
  
##  <a name="_core_classwizard_changes_for_custom_methods"></a>Agregar método asistente cambia para métodos personalizados  
 Cuando se agrega un método personalizado, el Asistente para agregar métodos realiza algunos cambios en el encabezado de la clase de control (. (H) e implementación (. Archivos CPP). La siguiente línea se agrega a la declaración de mapa de envíos en el encabezado de la clase de control (. H) archivo:  
  
 [!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]  
  
 Este código declara un controlador de método de envío denominado `PtInCircle`. Esta función se puede llamar el usuario de control mediante el nombre externo PtInCircle.  
  
 La siguiente línea se agrega al control. Este archivo IDL:  
  
 [!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]  
  
 Esta línea asigna al método PtInCircle un número de identificador específico, la posición del método en la lista de métodos y propiedades del Asistente para agregar métodos. Dado que el Asistente para agregar métodos se utilizó para agregar el método personalizado, la entrada se agregó automáticamente para el proyecto. Este archivo IDL.  
  
 Además, la siguiente línea, se encuentra en la implementación (. Archivo CPP) de la clase de control, se agrega al mapa de envíos del control:  
  
 [!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]  
  
 El `DISP_FUNCTION` macro asigna el método PtInCircle a la función de controlador del control, `PtInCircle`, declara el tipo de valor devuelto sea **VARIANT_BOOL**y declara dos parámetros de tipo **VTS_XPOS_PIXELS** y **VTS_YPOSPIXELS** que se pasan a `PtInCircle`.  
  
 Por último, el Asistente para agregar métodos agrega la función auxiliar `CSampleCtrl::PtInCircle` a la parte inferior de la implementación del control (. Archivo CPP). Para `PtInCircle` para que funcione como se indicó anteriormente, deben modificarse los siguientes:  
  
 [!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Iconos de la Vista de clases y del Examinador de objetos](/visualstudio/ide/class-view-and-object-browser-icons)

