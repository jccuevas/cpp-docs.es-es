---
title: "Usar controles comunes en un cuadro de di&#225;logo | Microsoft Docs"
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
  - "controles comunes [C++], en cuadros de diálogo"
  - "controles de cuadro de diálogo [C++], controles comunes"
  - "controles comunes de Windows [C++], en cuadros de diálogo"
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar controles comunes en un cuadro de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los controles comunes de Windows se pueden utilizar en [cuadros de diálogo](../mfc/dialog-boxes.md), forman las vistas, vistas de registro, y cualquier otra ventana basada en una plantilla de cuadro de diálogo.  El procedimiento siguiente, con los cambios leves, funcionará para formularios también.  
  
## Procedimientos  
  
#### Para utilizar un control común en un cuadro de diálogo  
  
1.  Coloque el control en la plantilla [mediante el editor de cuadros de diálogo](../mfc/using-the-dialog-editor-to-add-controls.md)de diálogo.  
  
2.  Agregue a la clase de diálogo una variable miembro que representa el control.  En el cuadro de diálogo de **Agregar variable de miembro** , **Control variable** comprobado y asegúrese de que **Control** está seleccionado para **category**.  
  
3.  Si este control común es proporcionando entrada programar, declare a la variable miembro adicional en la clase de diálogo para controlar esos valores de entrada.  
  
    > [!NOTE]
    >  Puede agregar a estas variables miembro mediante el menú contextual en la vista de clases \(vea [Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md)\).  
  
4.  En [OnInitDialog](../Topic/CDialog::OnInitDialog.md) para la clase de cuadro de diálogo, fije las condiciones iniciales para el control común.  Mediante la variable miembro creada en el paso anterior, use las funciones miembro para establecer valor inicial y otros valores.  Vea las descripciones siguientes de los controles de los detalles en valores.  
  
     También puede utilizar [diálogo de intercambio de datos](../mfc/dialog-data-exchange-and-validation.md) \(DDX\) para inicializar los controles en un cuadro de diálogo.  
  
5.  En los controladores de los controles en el cuadro de diálogo, utilice la variable miembro para manipular el control.  Vea las descripciones siguientes de los controles de los detalles en métodos.  
  
    > [!NOTE]
    >  La variable miembro existirá sólo mientras el cuadro de diálogo propio.  No podrá ver el control por valores de entrada una vez cerrado el cuadro de diálogo.  Para trabajar con valores de entrada de un control común, reemplace `OnOK` en la clase de diálogo.  En la invalidación, vea control por valores de entrada y almacene los valores de las variables miembro de la clase de diálogo.  
  
    > [!NOTE]
    >  También puede utilizar el cuadro de diálogo de intercambio de datos para establecer o recuperar valores de los controles en un cuadro de diálogo.  
  
## Comentarios  
 La adición de algunos controles comunes a un cuadro de diálogo hará que el cuadro de diálogo a ya no funciona.  Hace referencia a [Adding Controls to a Dialog Causes the Dialog to No Longer Function](../mfc/adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function.md) para obtener más información sobre cómo administrar esta situación.  
  
## ¿Qué desea hacer?  
  
-   [Agregue controles a un cuadro de diálogo a mano en lugar con el editor de cuadros de diálogo](../mfc/adding-controls-by-hand.md)  
  
-   [Derive mi control desde uno de los controles comunes estándar de Windows](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [Utilice un control común como una ventana secundaria](../mfc/using-a-common-control-as-a-child-window.md)  
  
-   [Reciba los mensajes de notificación de un control](../mfc/receiving-notification-from-common-controls.md)  
  
-   [Utilice el cuadro de diálogo de intercambio de datos \(DDX\)](../mfc/dialog-data-exchange-and-validation.md)  
  
## Vea también  
 [Crear y usar controles](../mfc/making-and-using-controls.md)   
 [Controles](../mfc/controls-mfc.md)