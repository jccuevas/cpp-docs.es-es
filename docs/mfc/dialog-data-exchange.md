---
title: "Intercambio de datos de cuadros de diálogo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 35f280228d523c7401e2a90ca395a79a9c87cd51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-data-exchange"></a>Intercambio de datos de cuadro de diálogo
Si utiliza el mecanismo DDX, se establecen los valores iniciales del cuadro de diálogo variables de miembro del objeto, por lo general en su `OnInitDialog` controlador o el constructor del cuadro de diálogo. Inmediatamente antes de que se muestre el cuadro de diálogo, mecanismo DDX del marco de trabajo transfiere los valores de las variables de miembro para los controles en el cuadro de diálogo, donde aparecen cuando el propio cuadro de diálogo aparezca en respuesta a `DoModal` o **crear** . La implementación predeterminada de `OnInitDialog` en `CDialog` llamadas el `UpdateData` función miembro de clase `CWnd` para inicializar los controles en el cuadro de diálogo.  
  
 El mismo mecanismo transfiere valores desde los controles a las variables miembro cuando el usuario hace clic en el botón Aceptar (o cada vez que se llama a la `UpdateData` función miembro con el argumento **TRUE**). El mecanismo de validación de datos de cuadro de diálogo valida cualquier elemento de datos para el que especifica las reglas de validación.  
  
 La ilustración siguiente muestra el intercambio de datos de cuadros de diálogo.  
  
 ![Intercambio de datos de cuadro de diálogo](../mfc/media/vc379d1.gif "vc379d1")  
Intercambio de datos de cuadro de diálogo  
  
 `UpdateData`funciona en ambas direcciones, según lo especificado por el **BOOL** parámetro se pasa a él. Para llevar a cabo el intercambio, `UpdateData` configura un `CDataExchange` objeto y llamadas a la invalidación de la clase de cuadro de diálogo `CDialog`del `DoDataExchange` función miembro. `DoDataExchange`toma un argumento de tipo `CDataExchange`. El `CDataExchange` objeto pasa a `UpdateData` representa el contexto del intercambio, definiendo dicha información como la dirección del intercambio.  
  
 Cuando usted (o un Asistente para código) reemplaza `DoDataExchange`, especificar una llamada a una función DDX por miembro de datos (control). Cada función DDX sabe cómo intercambiar datos en ambas direcciones basados en el contexto proporcionado por el `CDataExchange` argumento pasado a la `DoDataExchange` por `UpdateData`.  
  
 MFC proporciona muchas funciones DDX para distintos tipos de exchange. El ejemplo siguiente muestra un `DoDataExchange` invalidación en qué DDX dos funciones y una función DDV se denominan:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/cpp/dialog-data-exchange_1.cpp)]  
  
 El `DDX_` y `DDV_` líneas son una asignación de datos. Las funciones DDX y DDV de ejemplo que se muestran son para un control de casilla de verificación y un control de cuadro de edición, respectivamente.  
  
 Si el usuario cancela el cuadro de diálogo modal, el `OnCancel` función miembro termina el cuadro de diálogo y `DoModal` devuelve el valor **IDCANCEL**. En ese caso, no se intercambian datos entre el cuadro de diálogo y el objeto de cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Datos de cuadro de diálogo intercambio y validación](../mfc/dialog-data-exchange-and-validation.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)   
 [Validación de datos de cuadro de diálogo](../mfc/dialog-data-validation.md)

