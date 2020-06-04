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
ms.openlocfilehash: 9a0199577ea46520c2eadc308812de8a1ce4b514
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "71685806"
---
# <a name="dialog-data-exchange"></a>Intercambio de datos de cuadro de diálogo

Si utiliza el mecanismo DDX, establezca los valores iniciales de las variables miembro del objeto de cuadro de diálogo, normalmente en el controlador de `OnInitDialog` o en el constructor del cuadro de diálogo. Inmediatamente antes de que se muestre el cuadro de diálogo, el mecanismo DDX del marco de trabajo transfiere los valores de las variables miembro a los controles del cuadro de diálogo, donde aparecen cuando el propio cuadro de diálogo aparece en respuesta a `DoModal` o `Create`. La implementación predeterminada de `OnInitDialog` en `CDialog` llama a la función miembro `UpdateData` de la clase `CWnd` para inicializar los controles en el cuadro de diálogo.

El mismo mecanismo transfiere los valores de los controles a las variables miembro cuando el usuario hace clic en el botón Aceptar (o cada vez que se llama a la función miembro `UpdateData` con el argumento **true**). El mecanismo de validación de datos de cuadro de diálogo valida los elementos de datos para los que especificó reglas de validación.

En la ilustración siguiente se muestra el intercambio de datos de cuadro de diálogo.

![Intercambio de datos de cuadros de diálogo](../mfc/media/vc379d1.gif "Intercambio de datos de cuadro de diálogo") <br/>
Intercambio de datos de cuadro de diálogo

`UpdateData` funciona en ambas direcciones, tal y como se especifica en el parámetro **bool** que se le ha pasado. Para llevar a cabo el intercambio, `UpdateData` configura un objeto `CDataExchange` y llama a la invalidación de la clase de cuadro de diálogo de la función miembro `DoDataExchange` de `CDialog`. `DoDataExchange` toma un argumento de tipo `CDataExchange`. El `CDataExchange` objeto pasado a `UpdateData` representa el contexto del intercambio, que define dicha información como la dirección del intercambio.

Cuando el usuario (o un asistente para código) invalide `DoDataExchange`, se especifica una llamada a una función DDX por cada miembro de datos (control). Cada función DDX sabe cómo intercambiar los datos en ambas direcciones en función del contexto proporcionado por el `CDataExchange` argumento que se pasa a su `DoDataExchange` mediante `UpdateData`.

MFC proporciona muchas funciones DDX para diferentes tipos de intercambio. En el ejemplo siguiente se muestra una invalidación de `DoDataExchange` en la que se llama a dos funciones DDX y una función DDV:

[!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/cpp/dialog-data-exchange_1.cpp)]

Las líneas `DDX_` y `DDV_` son un mapa de datos. Las funciones DDX y DDV de ejemplo mostradas son para un control de casilla y un control de cuadro de edición, respectivamente.

Si el usuario cancela un cuadro de diálogo modal, la función miembro `OnCancel` finaliza el cuadro de diálogo y `DoModal` devuelve el valor **IDCANCEL**. En ese caso, no se intercambian datos entre el cuadro de diálogo y el objeto de diálogo.

## <a name="see-also"></a>Vea también

[Intercambio y validación de datos de cuadros de diálogo](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Validación de datos de cuadro de diálogo](../mfc/dialog-data-validation.md)
