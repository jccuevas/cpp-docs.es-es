---
title: Funciones miembro que se reemplazan con frecuencia
ms.date: 11/04/2016
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
ms.openlocfilehash: 26a1527dbdac4b2a9deb57fb13481f8d2f9cb5b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152038"
---
# <a name="commonly-overridden-member-functions"></a>Funciones miembro que se reemplazan con frecuencia

En la tabla siguiente se enumera más probable es que las funciones miembro para invalidar en su `CDialog`-clase derivada.

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Se reemplazan con frecuencia las funciones miembro de clase CDialog

|Función miembro|Mensaje al que responde|Propósito de la invalidación|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|Inicializar los controles del cuadro de diálogo.|
|`OnOK`|**BN_CLICKED** botón **IDOK**|Responder cuando el usuario hace clic en el botón Aceptar.|
|`OnCancel`|**BN_CLICKED** botón **IDCANCEL**|Responder cuando el usuario hace clic en el botón Cancelar.|

`OnInitDialog`, `OnOK`, y `OnCancel` son funciones virtuales. Para reemplazarlos, declare una función de reemplazo en la clase de cuadro de diálogo derivada mediante la [ventana propiedades](/visualstudio/ide/reference/properties-window).

`OnInitDialog` se llama justo antes de que se muestra el cuadro de diálogo. Debe llamar a la predeterminada `OnInitDialog` controlador desde el reemplazo, normalmente como la primera acción en el controlador. De forma predeterminada, `OnInitDialog` devuelve **TRUE** para indicar que se debe establecer el foco al primer control en el cuadro de diálogo.

`OnOK` Normalmente, se invalida para cuadros de diálogo no modal, pero no modal. Si invalida este controlador para un cuadro de diálogo modal, llame a la versión de la clase base desde el reemplazo, para asegurarse de que `EndDialog` se llama, o llamar a `EndDialog` usted mismo.

`OnCancel` Normalmente, se invalida para cuadros de diálogo no modal.

Para obtener más información acerca de estas funciones miembro, vea la clase [CDialog](../mfc/reference/cdialog-class.md) en el *referencia de MFC* y la descripción en [ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md).

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Funciones miembro que se agregan con frecuencia](../mfc/commonly-added-member-functions.md)
