---
title: Hojas de propiedades como asistentes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 65aedc5dbeb8a740d5713983f66eefe693864937
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="property-sheets-as-wizards"></a>Hojas de propiedades como asistentes
Una característica clave de una hoja de propiedades del asistente es que el desplazamiento viene definido con los botones siguiente o finalizar, Atrás y Cancelar en lugar de fichas. Debe llamar a [CPropertySheet:: SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode) antes de llamar a [CPropertySheet:: DoModal](../mfc/reference/cpropertysheet-class.md#domodal) en el objeto de hoja de propiedades para aprovechar esta característica.  
  
 El usuario recibe el mismo [notificaciones CPropertyPage:: OnSetActive](../mfc/reference/cpropertypage-class.md#onsetactive) y [CPropertyPage:: OnKillActive](../mfc/reference/cpropertypage-class.md#onkillactive) notificaciones mientras se desplaza de una página a otra página. Botones siguiente y finalizar son controles mutuamente excluyentes; es decir, solo uno de ellos se mostrarán a la vez. En la primera página, debe habilitarse el botón siguiente. Si el usuario está en la última página, debe habilitarse el botón Finalizar. Esto no sirve automáticamente por el marco de trabajo. Tiene que llamar a [CPropertySheet:: SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons) en la última página para lograr esto.  
  
 Para mostrar todos los botones de manera predeterminada, es necesario mostrar el botón Finalizar y mover el botón siguiente. A continuación, mueva el botón Atrás para que se mantiene su posición relativa en el botón siguiente.  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)

