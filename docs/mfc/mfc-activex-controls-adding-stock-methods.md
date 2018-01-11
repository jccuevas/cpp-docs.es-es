---
title: "Controles ActiveX MFC: Agregar métodos estándar | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2531f84974626fcdb364df67b12f27d61e75a62a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>Controles ActiveX MFC: Agregar métodos estándar
Un método estándar difiere de un método personalizado en que ya está implementado por la clase [COleControl](../mfc/reference/colecontrol-class.md). Por ejemplo, `COleControl` contiene una función miembro predefinida que admite el método de actualización para el control. La entrada de asignación de envío para este método estándar es **DISP_STOCKFUNC_REFRESH**.  
  
 `COleControl`admite dos métodos estándar: DoClick y Refresh. La actualización es invocada por el usuario del control para actualizar inmediatamente la apariencia del control; DoClick se invoca para que se activen haga clic en del control eventos.  
  
|Método|Entrada del mapa de envíos|Comentario|  
|------------|------------------------|-------------|  
|`DoClick`|**(DE DISP_STOCKPROP_DOCLICK)**|Se desencadena un evento Click.|  
|**Actualizar**|**(DE DISP_STOCKPROP_REFRESH)**|La apariencia del control se actualiza inmediatamente.|  
  
##  <a name="_core_adding_a_stock_method_using_classwizard"></a>Agregar un método estándar mediante el Asistente para agregar métodos  
 Agregar un método estándar es sencillo con el [Asistente para agregar métodos](../ide/add-method-wizard.md). El siguiente procedimiento muestra cómo agregar el método de actualización para un control creado mediante el Asistente para controles de ActiveX de MFC.  
  
#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Para agregar el método de actualización estándar mediante el Asistente para agregar métodos  
  
1.  Cargue el proyecto del control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca del control.  
  
3.  Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar método**.  
  
     Se abrirá al Asistente para agregar métodos.  
  
5.  En el **nombre del método** cuadro, haga clic en **actualizar**.  
  
6.  Haga clic en **Finalizar**.  
  
##  <a name="_core_classwizard_changes_for_stock_methods"></a>Agregar método asistente cambia para métodos estándar  
 Dado que el método estándar Refresh es compatible con la clase del control base, el **Asistente para agregar métodos** no cambia la declaración de clase del control de ninguna manera. Agrega una entrada para el método al mapa de envíos del control y a su. Este archivo IDL. Se agrega la siguiente línea al mapa de envíos del control, situado en su implementación (. Archivo CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]  
  
 Esto hace que el método de actualización estén disponibles para los usuarios del control.  
  
 La siguiente línea se agrega al control. Este archivo IDL:  
  
 [!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]  
  
 Esta línea asigna el método de actualización de un número de Id. específico.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

