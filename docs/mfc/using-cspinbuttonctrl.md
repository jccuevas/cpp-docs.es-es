---
title: "Usar CSpinButtonCtrl | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSpinButtonCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSpinButtonCtrl (clase), utilizar"
  - "control de botón de número"
  - "controles de flechas"
  - "controles de flechas, control de botón de número"
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar CSpinButtonCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*El control de botón de número* \(también conocido como control giratorio\) proporciona un par de flechas que un usuario puede hacer clic para ajustar un valor.  Este valor se conoce como *la posición actual*.  La posición permanece dentro del intervalo del botón de número.  Cuando el usuario hace clic en la flecha arriba, la posición avanza hacia el máximo; y cuando el usuario hace clic en la flecha abajo, la posición avanza hacia el mínimo.  
  
 El control de botón de número se representa en MFC por la clase de [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) .  
  
> [!NOTE]
>  De forma predeterminada, el intervalo para el botón de número tiene el máximo establecido en cero \(0\) y el mínimo establecido en 100.  Dado que el valor máximo es menor que el valor mínimo, haciendo clic en la flecha arriba reduce la posición y haciendo clic en la flecha abajo la aumenta.  Uso [CSpinButtonCtrl::SetRange](../Topic/CSpinButtonCtrl::SetRange.md) de ajustar estos valores.  
  
 Normalmente, la posición actual se muestra en un control complementarias.  El control complementaria se conoce como *ventana de relacionada*.  Para obtener un ejemplo de un control de botón de número, vea [Acerca de los Controles arriba\-abajo](http://msdn.microsoft.com/library/windows/desktop/bb759889) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 Para crear un control de número y una ventana de relacionada del control de edición, en Visual Studio, primero arrastre un control de edición al cuadro de diálogo o la ventana, y luego arrastre un control de número.  Seleccione el control de número y establezca sus propiedades de **Relacionada auto** y de **Establezca el entero de relacionada** a **VERDADERO**.  También establezca la propiedad de **Alineación** ; **Alineación a la derecha** es el más típico.  Con esta configuración, el control de edición se establece como ventana de relacionada porque precede directamente el control de edición en el orden de tabulación.  Los enteros del control de edición y el control de número se inserta en el lado derecho del control de edición.  Opcionalmente, puede establecer el intervalo válido del control de número utilizando el método de [CSpinButtonCtrl::SetRange](../Topic/CSpinButtonCtrl::SetRange.md) .  No se requiere ningún controladores de eventos comunicarse entre el control de número y la ventana de relacionada porque se intercambian datos directamente.  Si utiliza un control de número para algún otro propósito, por ejemplo, a la página con una secuencia de ventanas o cuadros de diálogo, agregue un controlador para el mensaje de `UDN_DELTAPOS` y realice la acción personalizada allí.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Estilos de botón de cuadro de número](../mfc/spin-button-styles.md)  
  
-   [Funciones miembro del botón de número](../mfc/spin-button-member-functions.md)  
  
## Vea también  
 [Controles](../mfc/controls-mfc.md)