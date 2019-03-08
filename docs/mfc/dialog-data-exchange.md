---
title: Intercambio de datos de cuadro de diálogo
ms.date: 11/19/2018
helpviewer_keywords:
- initializing dialog boxes
- canceling data exchange
- dialog box data, retrieving
- DDX (dialog data exchange), data exchange mechanism
- dialog boxes [MFC], initializing
- dialog boxes [MFC], retrieving user input using DDX
- dialog box data
- dialog boxes [MFC], data exchange
- CDataExchange class [MFC], using DDX
- DoDataExchange method [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- transferring dialog box data
- DDX (dialog data exchange), canceling
- UpdateData method [MFC]
- retrieving dialog box data [MFC]
ms.assetid: 4675f63b-41d2-45ed-b6c3-235ad8ab924b
ms.openlocfilehash: 338630aef358d9490461179288d5c45a2d3b821c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302325"
---
# <a name="dialog-data-exchange"></a>Intercambio de datos de cuadro de diálogo

Si utiliza el mecanismo DDX, se establecen los valores iniciales del cuadro de diálogo variables de miembro del objeto, normalmente, en su `OnInitDialog` controlador o el constructor del cuadro de diálogo. Inmediatamente antes de que aparezca el cuadro de diálogo, mecanismo DDX del marco de trabajo transfiere los valores de las variables de miembro para los controles en el cuadro de diálogo, donde aparecen cuando el propio cuadro de diálogo aparezca en respuesta a `DoModal` o `Create`. La implementación predeterminada de `OnInitDialog` en `CDialog` llamadas la `UpdateData` función miembro de clase `CWnd` para inicializar los controles en el cuadro de diálogo.

El mismo mecanismo transfiere los valores de los controles a las variables miembro cuando el usuario hace clic en el botón Aceptar (o cuando llame a la `UpdateData` función miembro con el argumento **TRUE**). El mecanismo de validación de datos de cuadro de diálogo valida los elementos de datos para el que especifica las reglas de validación.

La ilustración siguiente muestra el intercambio de datos de cuadro de diálogo.

![Intercambio de datos de cuadro de diálogo](../mfc/media/vc379d1.gif "intercambio de datos de cuadro de diálogo") <br/>
Intercambio de datos de cuadro de diálogo

`UpdateData` funciona en ambas direcciones, según lo especificado por el **BOOL** parámetro pasado a él. Para llevar a cabo el intercambio, `UpdateData` configura un `CDataExchange` objeto y llama a la invalidación de la clase de cuadro de diálogo `CDialog`del `DoDataExchange` función miembro. `DoDataExchange` toma un argumento de tipo `CDataExchange`. El `CDataExchange` objeto pasa a `UpdateData` representa el contexto del intercambio, definiendo dicha información como la dirección del intercambio.

Cuando usted (o un asistente de código) invalidar `DoDataExchange`, especifique una llamada a una función DDX por miembro de datos (control). Cada función DDX sabe cómo intercambiar datos en ambas direcciones según el contexto proporcionado por el `CDataExchange` argumento pasado a su `DoDataExchange` por `UpdateData`.

MFC proporciona muchas funciones DDX para distintos tipos de exchange. El ejemplo siguiente se muestra un `DoDataExchange` invalidación en las DDX dos funciones y una función DDV se denominan:

[!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/cpp/dialog-data-exchange_1.cpp)]

El `DDX_` y `DDV_` líneas son una asignación de datos. Las funciones DDX y DDV de ejemplo que se muestran son para un control de casilla de verificación y un control de cuadro de edición, respectivamente.

Si el usuario cancela el cuadro de diálogo modal, el `OnCancel` función miembro termina el cuadro de diálogo y `DoModal` devuelve el valor **IDCANCEL**. En ese caso, no se intercambian datos entre el cuadro de diálogo y el objeto de cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Intercambio y validación de datos de cuadros de diálogo](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Validación de datos de cuadro de diálogo](../mfc/dialog-data-validation.md)
