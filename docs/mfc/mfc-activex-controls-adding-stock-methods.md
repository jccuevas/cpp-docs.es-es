---
title: 'Controles ActiveX MFC: Agregar métodos estándar | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 604a095ab26abf4953d56786e00461cabd07e579
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45534955"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>Controles ActiveX MFC: Agregar métodos estándar
Un método estándar difiere de un método personalizado en que ya está implementado por la clase [COleControl](../mfc/reference/colecontrol-class.md). Por ejemplo, `COleControl` contiene una función miembro predefinida que admite el método de actualización para el control. La entrada de asignación de envío para este método estándar es DISP_STOCKFUNC_REFRESH.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).  
  
 `COleControl` admite dos métodos estándar: DoClick y actualización. Se invoca la actualización por el usuario del control para actualizar inmediatamente la apariencia del control; DoClick se invoca para desencadenar haga clic en del control eventos.  
  
|Método|Entrada del mapa de envíos|Comentario|  
|------------|------------------------|-------------|  
|`DoClick`|**(DE DISP_STOCKPROP_DOCLICK)**|Se desencadena un evento Click.|  
|`Refresh`|**(DE DISP_STOCKPROP_REFRESH)**|Se actualiza inmediatamente la apariencia del control.|  
  
##  <a name="_core_adding_a_stock_method_using_classwizard"></a> Agregar un método estándar mediante el Asistente para agregar métodos  
 Agregar un método estándar es sencillo mediante la [Asistente para agregar métodos](../ide/add-method-wizard.md). El siguiente procedimiento muestra cómo agregar el método de actualización a un control creado mediante el Asistente para controles de ActiveX de MFC.  
  
#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Para agregar el método de actualización estándar mediante el Asistente para agregar métodos  
  
1.  Cargue el proyecto del control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca del control.  
  
3.  Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar método**.  
  
     Se abrirá al Asistente para agregar método.  
  
5.  En el **nombre del método** cuadro, haga clic en **actualizar**.  
  
6.  Haga clic en **Finalizar**.  
  
##  <a name="_core_classwizard_changes_for_stock_methods"></a> Agregar método cambios del Asistente para métodos estándar  
 Dado que el método de actualización es compatible con la clase del control base, el **Asistente para agregar métodos** no cambia la declaración de clase del control de ninguna manera. Agrega una entrada para el método al mapa de envíos del control y a su. Archivo IDL. Se agrega la siguiente línea al mapa de envíos del control, ubicado en su implementación (. Archivo CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]  
  
 Esto hace que el método de actualización disponible para los usuarios del control.  
  
 La siguiente línea se agrega al control. Archivo IDL:  
  
 [!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]  
  
 Esta línea asigna el método de actualización de un número de Id. específico.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

