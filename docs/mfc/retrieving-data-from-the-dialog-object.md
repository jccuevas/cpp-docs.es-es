---
title: Recuperar datos del objeto de cuadro de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], retrieving user data
- dialog box data [MFC]
- data [MFC], retrieving
- GetDlgItemText method [MFC]
- SetDlgItemText method [MFC]
- SetWindowText method [MFC]
- dialog box data [MFC], retrieving
- retrieving data [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- dialog box controls [MFC], initializing values
- DDX (dialog data exchange) [MFC]
- MFC dialog boxes [MFC], retrieving user input
- data retrieval [MFC], dialog boxes
- data [MFC], dialog boxes
- DDX (dialog data exchange) [MFC], about DDX
- DDX (dialog data exchange) [MFC], retrieving data from Dialog object
- GetWindowText method [MFC]
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
ms.openlocfilehash: 903d76a1e672d05a3c093e528f7153562df8e3e5
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685566"
---
# <a name="retrieving-data-from-the-dialog-object"></a>Recuperar datos del objeto de cuadro de diálogo

El marco de trabajo proporciona una manera sencilla de inicializar los valores de los controles en un cuadro de diálogo y de recuperar los valores de los controles. El enfoque manual más laborioso es llamar a funciones como las funciones miembro `SetDlgItemText` y `GetDlgItemText` de la clase `CWnd`, que se aplican a las ventanas de control. Con estas funciones, se tiene acceso a cada control individualmente para establecer u obtener su valor, llamando a funciones como `SetWindowText` y `GetWindowText`. El enfoque del marco automatiza la inicialización y la recuperación.

Intercambio de datos de cuadros de diálogo (DDX) permite intercambiar datos entre los controles del cuadro de diálogo y las variables de miembro del objeto de cuadro de diálogo más fácilmente. Este intercambio funciona de ambas maneras. Para inicializar los controles en el cuadro de diálogo, puede establecer los valores de los miembros de datos en el objeto de diálogo y el marco de trabajo transferirá los valores a los controles antes de que se muestre el cuadro de diálogo. A continuación, puede actualizar los miembros de datos del cuadro de diálogo con los datos especificados por el usuario en cualquier momento. En ese momento, puede usar los datos haciendo referencia a las variables de miembro de datos.

También puede organizar los valores de los controles de cuadro de diálogo que se van a validar automáticamente con la validación de datos de cuadro de diálogo (DDV).

DDX y DDV se explican con más detalle en [intercambio y validación de datos de cuadro de diálogo](../mfc/dialog-data-exchange-and-validation.md).

En un cuadro de diálogo modal, puede recuperar los datos especificados por el usuario cuando `DoModal` devuelve IDOK, pero antes de que se destruya el objeto de cuadro de diálogo. En el caso de un cuadro de diálogo no modal, puede recuperar datos del objeto de cuadro de diálogo en cualquier momento llamando a `UpdateData` con el argumento **true** y, a continuación, tener acceso a las variables de miembro de clase de cuadro de diálogo. Este tema se describe con más detalle en [intercambio y validación de datos de cuadro de diálogo](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Vea también

[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)
