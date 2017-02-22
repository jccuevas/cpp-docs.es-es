---
title: "Controles ActiveX MFC: Agregar m&#233;todos est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DoClick (método)"
  - "controles ActiveX en MFC, métodos"
  - "controles ActiveX en MFC, métodos estándar"
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Controles ActiveX MFC: Agregar m&#233;todos est&#225;ndar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un método común diferencia de un método personalizado en que es implementado por la clase [COleControl](../mfc/reference/colecontrol-class.md).  Por ejemplo, `COleControl` contiene una función predefinida de miembro que admite el método update del control.  La entrada de asignación de envío para este método común es **DISP\_STOCKFUNC\_REFRESH**.  
  
 `COleControl` admite dos métodos comunes: DoClick y actualización.  Actualización es invocado por el usuario del control inmediatamente para actualizar el aspecto del control; DoClick se invoca para desencadenar el evento Click del control.  
  
|Método|Entrada de asignación de envío|Comment|  
|------------|------------------------------------|-------------|  
|`DoClick`|**DISP\_STOCKPROP\_DOCLICK \(\)**|Desencadena un evento Click.|  
|**Actualizar**|**DISP\_STOCKPROP\_REFRESH \(\)**|Inmediatamente actualiza la apariencia del control.|  
  
##  <a name="_core_adding_a_stock_method_using_classwizard"></a> Agregue un método común Con el asistente para agregar métodos  
 Agregar un método común es sencilla mediante [Asistente para agregar métodos](../ide/add-method-wizard.md).  El procedimiento siguiente muestra cómo agregar el método update a un control creado mediante el asistente para controles ActiveX MFC.  
  
#### Para agregar almacene el método de actualización mediante el asistente para agregar métodos  
  
1.  Cargue el proyecto de control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca de controles.  
  
3.  Haga clic con el botón secundario en el nodo de la interfaz del control \(el segundo nodo el nodo de biblioteca\) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar método**.  
  
     Se abrirá el asistente para agregar métodos.  
  
5.  En el cuadro de **Nombre del método** , haga clic en **Actuali&&zar**.  
  
6.  Haga clic en **Finalizar**.  
  
##  <a name="_core_classwizard_changes_for_stock_methods"></a> Agregue los cambios del asistente de método para métodos comunes  
 Dado que almacene el método update se admite en la clase base de controles, **Asistente para agregar métodos** no cambia la declaración de clase del control de cualquier forma.  Agrega una entrada para el método en el envío de control asignado y su archivo de .IDL.  La siguiente línea se agrega al mapa de envío del control, ubicado en el archivo de implementación \(.CPP\):  
  
 [!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-methods_1.cpp)]  
  
 Esto crea actualizar el método disponible para los usuarios del control.  
  
 La siguiente línea se agrega al archivo de .IDL de control:  
  
 [!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-methods_2.idl)]  
  
 Esta línea asigna a método de actualización al número de identificación concreto.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)