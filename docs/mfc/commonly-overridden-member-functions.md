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
ms.openlocfilehash: 7d4fc9005ff368ef6a83252e8cf0b2005ecf2cef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619666"
---
# <a name="commonly-overridden-member-functions"></a>Funciones miembro que se reemplazan con frecuencia

En la tabla siguiente se enumeran las funciones miembro más probables que se van a invalidar en la `CDialog` clase derivada de.

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>Funciones miembro que se reemplazan normalmente de la clase CDialog

|Función de miembro|Mensaje al que responde|Propósito de la invalidación|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|Inicializa los controles del cuadro de diálogo.|
|`OnOK`|**BN_CLICKED** para el botón **IDOK**|Responder cuando el usuario haga clic en el botón Aceptar.|
|`OnCancel`|**BN_CLICKED** para el botón **IDCANCEL**|Responder cuando el usuario haga clic en el botón Cancelar.|

`OnInitDialog`, `OnOK` y `OnCancel` son funciones virtuales. Para invalidarlos, se declara una función de reemplazo en la clase de cuadro de diálogo derivada mediante el [Asistente para clases MFC](reference/mfc-class-wizard.md).

`OnInitDialog`se llama justo antes de que se muestre el cuadro de diálogo. Debe llamar al controlador predeterminado `OnInitDialog` desde su invalidación, normalmente como la primera acción del controlador. De forma predeterminada, `OnInitDialog` devuelve **true** para indicar que el foco se debe establecer en el primer control del cuadro de diálogo.

`OnOK`normalmente se invalida para los cuadros de diálogo no modales pero no modales. Si invalida este controlador para un cuadro de diálogo modal, llame a la versión de la clase base desde su invalidación, para asegurarse de que `EndDialog` se llama a, o llame a `EndDialog` sí mismo.

`OnCancel`normalmente se invalida en los cuadros de diálogo no modales.

Para obtener más información acerca de estas funciones miembro, vea la clase [CDialog](reference/cdialog-class.md) en la *referencia de MFC* y la explicación sobre [Cómo trabajar con cuadros de diálogo en MFC](life-cycle-of-a-dialog-box.md).

## <a name="see-also"></a>Consulte también

[Cuadros de diálogo](dialog-boxes.md)<br/>
[Funciones miembro que se agregan con frecuencia](commonly-added-member-functions.md)
