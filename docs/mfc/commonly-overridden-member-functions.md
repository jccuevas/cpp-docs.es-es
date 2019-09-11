---
title: Funciones miembro que se reemplazan con frecuencia
ms.date: 09/06/2019
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
ms.openlocfilehash: f63dd6079b96181305f3207d4a1ef823df8d8ba4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907688"
---
# <a name="commonly-overridden-member-functions"></a>Funciones miembro que se reemplazan con frecuencia

En la tabla siguiente se enumeran las funciones miembro más probables `CDialog`que se van a invalidar en la clase derivada de.

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Funciones miembro que se reemplazan normalmente de la clase CDialog

|Función miembro|Mensaje al que responde|Propósito de la invalidación|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|Inicializa los controles del cuadro de diálogo.|
|`OnOK`|**BN_CLICKED** para el botón **IDOK**|Responder cuando el usuario haga clic en el botón Aceptar.|
|`OnCancel`|**BN_CLICKED** para el botón **IDCANCEL**|Responder cuando el usuario haga clic en el botón Cancelar.|

`OnInitDialog`, `OnOK` y`OnCancel` son funciones virtuales. Para invalidarlos, se declara una función de reemplazo en la clase de cuadro de diálogo derivada mediante el [Asistente para clases MFC](reference/mfc-class-wizard.md).

`OnInitDialog`se llama justo antes de que se muestre el cuadro de diálogo. Debe llamar al controlador predeterminado `OnInitDialog` desde su invalidación, normalmente como la primera acción del controlador. De forma predeterminada `OnInitDialog` , devuelve **true** para indicar que el foco se debe establecer en el primer control del cuadro de diálogo.

`OnOK`normalmente se invalida para los cuadros de diálogo no modales pero no modales. Si invalida este controlador para un cuadro de diálogo modal, llame a la versión de la clase base desde su invalidación `EndDialog` , para asegurarse de que `EndDialog` se llama a, o llame a sí mismo.

`OnCancel`normalmente se invalida en los cuadros de diálogo no modales.

Para obtener más información sobre estas funciones miembro, vea la clase [CDialog](../mfc/reference/cdialog-class.md) en la *referencia de MFC* y la explicación sobre el [ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md).

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Funciones miembro que se agregan con frecuencia](../mfc/commonly-added-member-functions.md)
