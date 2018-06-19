---
title: Usar CSpinButtonCtrl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CSpinButtonCtrl
dev_langs:
- C++
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03b1e83977c1d75070e8878dfdcc53c7afca7a86
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384405"
---
# <a name="using-cspinbuttonctrl"></a>Usar CSpinButtonCtrl
El *botón de número* control (también conocido como un *flechas* control) proporciona un par de flechas que un usuario puede hacer clic para ajustar un valor. Este valor se conoce como el *posición actual*. La posición permanece dentro del intervalo del botón de número. Cuando el usuario hace clic en la flecha hacia arriba, la posición se mueve hacia el valor máximo; y cuando el usuario hace clic en la flecha hacia abajo, la posición se mueve hacia el valor mínimo.  
  
 El control de botón de número se representa en MFC mediante la [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) clase.  
  
> [!NOTE]
>  De forma predeterminada, el intervalo para el botón de número tiene el máximo establecido en cero (0) y el mínimo establecido en 100. Dado que el valor máximo es menor que el valor mínimo, al hacer clic en la flecha arriba reduce la posición y al hacer clic en la flecha hacia abajo aumenta lo. Use [CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) para ajustar estos valores.  
  
 Por lo general, se muestra la posición actual en un control complementario. El control complementario se conoce como el *ventana relacionada*. Para ver una ilustración de un control de botón de número, vea [sobre controles de flechas](http://msdn.microsoft.com/library/windows/desktop/bb759889) del SDK de Windows.  
  
 Para crear un control de número y una ventana de amigo de control de edición, en Visual Studio, en primer lugar arrastre un control de edición en el cuadro de diálogo o ventana y, a continuación, arrastre un control de número. Seleccione el control de número y establezca su **automática amigo** y **establecer amigo entero** propiedades a **True**. Establecer el **alineación** propiedad; **Derecha alinear** es más habitual. Con esta configuración, el control de edición se establece como la ventana relacionada porque precede directamente el control de edición en el orden de tabulación. El control de edición muestra enteros y el control de número se incrusta en el lado derecho del control de edición. Si lo desea, puede establecer el intervalo válido de control de número mediante la [CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) método. No hay controladores de eventos necesarios para la comunicación entre el control de número y la ventana relacionada porque intercambian datos directamente. Si utiliza un control de número para otros propósitos, por ejemplo, para desplazarse a través de una secuencia de windows o los cuadros de diálogo, a continuación, agregar un controlador para el `UDN_DELTAPOS` el mensaje y realizar la acción personalizada no existe.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Estilos de botón de cuadro de número](../mfc/spin-button-styles.md)  
  
-   [Funciones miembro del botón de número](../mfc/spin-button-member-functions.md)  
  
## <a name="see-also"></a>Vea también  
 [Controles](../mfc/controls-mfc.md)

