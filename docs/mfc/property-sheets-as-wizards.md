---
title: Hojas de propiedades como asistentes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 634359763f24e02987664fe3de1094e3e7fec64c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="property-sheets-as-wizards"></a>Hojas de propiedades como asistentes
Una característica clave de una hoja de propiedades del asistente es que el desplazamiento viene definido con los botones siguiente o finalizar, Atrás y Cancelar en lugar de fichas. Debe llamar a [CPropertySheet:: SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode) antes de llamar a [CPropertySheet:: DoModal](../mfc/reference/cpropertysheet-class.md#domodal) en el objeto de hoja de propiedades para aprovechar esta característica.  
  
 El usuario recibe el mismo [notificaciones CPropertyPage:: OnSetActive](../mfc/reference/cpropertypage-class.md#onsetactive) y [CPropertyPage:: OnKillActive](../mfc/reference/cpropertypage-class.md#onkillactive) notificaciones mientras se desplaza de una página a otra página. Botones siguiente y finalizar son controles mutuamente excluyentes; es decir, solo uno de ellos se mostrarán a la vez. En la primera página, debe habilitarse el botón siguiente. Si el usuario está en la última página, debe habilitarse el botón Finalizar. Esto no sirve automáticamente por el marco de trabajo. Tiene que llamar a [CPropertySheet:: SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons) en la última página para lograr esto.  
  
 Para mostrar todos los botones de manera predeterminada, es necesario mostrar el botón Finalizar y mover el botón siguiente. A continuación, mueva el botón Atrás para que se mantiene su posición relativa en el botón siguiente.  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)

