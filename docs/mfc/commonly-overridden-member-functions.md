---
title: Funciones miembro reemplazadas habitualmente | Documentos de Microsoft
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
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5aa3fb072ca882b03b9da96d54cdefbba5e59a68
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="commonly-overridden-member-functions"></a>Funciones miembro que se reemplazan con frecuencia
La tabla siguiente enumera el más probable es que las funciones miembro para invalidar en su `CDialog`-clase derivada.  
  
### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Las funciones miembro de clase CDialog se reemplazan con frecuencia  
  
|Función miembro|Mensaje al que responde|Propósito del reemplazo|  
|---------------------|----------------------------|-----------------------------|  
|`OnInitDialog`|**WM_INITDIALOG**|Inicializar los controles del cuadro de diálogo.|  
|`OnOK`|**BN_CLICKED** para botón **IDOK**|Responder cuando el usuario hace clic en el botón Aceptar.|  
|`OnCancel`|**BN_CLICKED** para botón **IDCANCEL**|Responder cuando el usuario hace clic en el botón Cancelar.|  
  
 `OnInitDialog`, `OnOK`, y `OnCancel` son funciones virtuales. Para reemplazarlos, declare una función de reemplazo en la clase de cuadro de diálogo derivada utilizando el [ventana propiedades](/visualstudio/ide/reference/properties-window).  
  
 `OnInitDialog`se llama justo antes de que se muestra el cuadro de diálogo. Se debe llamar a la opción predeterminada `OnInitDialog` controlador desde el reemplazo, normalmente como la primera acción en el controlador. De forma predeterminada, `OnInitDialog` devuelve **TRUE** para indicar que se debe establecer el foco al primer control en el cuadro de diálogo.  
  
 `OnOK`Normalmente se invalida para cuadros de diálogo no modales pero no modal. Si invalida este controlador para un cuadro de diálogo modal, llame a la versión de la clase base desde el reemplazo, para asegurarse de que `EndDialog` se llama, o llamar a `EndDialog` usted mismo.  
  
 `OnCancel`se reemplaza normalmente para cuadros de diálogo no modal.  
  
 Para obtener más información acerca de estas funciones miembro, vea la clase [CDialog](../mfc/reference/cdialog-class.md) en el *referencia de MFC* así como el análisis en [ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md).  
  
## <a name="see-also"></a>Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Funciones miembro que se agregan con frecuencia](../mfc/commonly-added-member-functions.md)
