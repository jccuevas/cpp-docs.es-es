---
title: Recuperación de datos desde el objeto de cuadro de diálogo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8b221bd97d9ee943e19b043bcc9be6aba0fa1672
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929600"
---
# <a name="retrieving-data-from-the-dialog-object"></a>Recuperar datos del objeto de cuadro de diálogo
El marco de trabajo proporciona una manera sencilla para inicializar los valores de los controles en un cuadro de diálogo y para recuperar los valores de los controles. El enfoque más laborioso manual es llamar a funciones como la `SetDlgItemText` y `GetDlgItemText` funciones miembro de clase `CWnd`, que se aplican a las ventanas de control. Con estas funciones, tener acceso a cada control individualmente para establecer u obtener su valor, llamar a funciones como `SetWindowText` y `GetWindowText`. Enfoque del marco de trabajo automatiza la inicialización y la recuperación.  
  
 Intercambio de datos de cuadros de diálogo (DDX) permite intercambiar datos entre los controles en el cuadro de diálogo cuadro y las variables miembro del objeto de cuadro de diálogo más fácilmente. Este intercambio funciona en ambas direcciones. Para inicializar los controles en el cuadro de diálogo, puede establecer los valores de miembros de datos en el objeto de cuadro de diálogo y el marco de trabajo transferirá los valores a los controles antes de que se muestre el cuadro de diálogo. A continuación, puede en cualquier momento actualizar a los miembros de datos de cuadro de diálogo con los datos introducidos por el usuario. En ese momento, puede usar los datos, se hace referencia a las variables de miembro de datos.  
  
 También puede organizar para los valores de los controles de cuadro de diálogo que se debe validar automáticamente con la validación de datos de cuadro de diálogo (DDV).  
  
 DDX y DDV se explican con más detalle en [intercambio de datos de cuadros de diálogo y validación](../mfc/dialog-data-exchange-and-validation.md).  
  
 Para un cuadro de diálogo modal, puede recuperar los datos que el usuario escribió al `DoModal` devuelve IDOK pero antes del cuadro de diálogo se destruye el objeto. Para un cuadro de diálogo no modal, puede recuperar datos del objeto de cuadro de diálogo en cualquier momento mediante una llamada a `UpdateData` con el argumento **TRUE** y, a continuación, obtener acceso a variables de miembro de clase de cuadro de diálogo. Este tema se explica con más detalle en [intercambio de datos de cuadros de diálogo y validación](../mfc/dialog-data-exchange-and-validation.md).  
  
## <a name="see-also"></a>Vea también  
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

