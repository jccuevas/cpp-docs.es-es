---
title: Ciclo de vida de un cuadro de diálogo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: faf204f05c03e742e0f491fb3991b56d3405ebc4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346186"
---
# <a name="life-cycle-of-a-dialog-box"></a>Ciclo de vida de un cuadro de diálogo
Durante el ciclo de vida de un cuadro de diálogo, el usuario invoca el cuadro de diálogo, normalmente dentro de un controlador de comandos que crea e inicializa el objeto de cuadro de diálogo, el usuario interactúa con el cuadro de diálogo y se cierra el cuadro de diálogo.  
  
 En cuadros de diálogo modales, el controlador recopila los datos que el usuario ha especificado una vez que se cierra el cuadro de diálogo. Puesto que el objeto de cuadro de diálogo existe después de su ventana de cuadro de diálogo se ha cerrado, simplemente puede utilizar las variables de miembro de la clase de cuadro de diálogo para extraer los datos.  
  
 Para los cuadros de diálogo no modal, a menudo puede extraer datos del objeto de cuadro de diálogo mientras el cuadro de diálogo sigue estando visible. En algún momento, se destruye el objeto de cuadro de diálogo; Cuando esto sucede depende de su código.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Crear y mostrar cuadros de diálogo](../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [Crear cuadros de diálogo modales](../mfc/creating-modal-dialog-boxes.md)  
  
-   [Crear cuadros de diálogo no modales](../mfc/creating-modeless-dialog-boxes.md)  
  
-   [Usar una plantilla de cuadro de diálogo en memoria](../mfc/using-a-dialog-template-in-memory.md)  
  
-   [Establecer el color de fondo del cuadro de diálogo](../mfc/setting-the-dialog-boxs-background-color.md)  
  
-   [Inicializar el cuadro de diálogo](../mfc/initializing-the-dialog-box.md)  
  
-   [Controlar mensajes de Windows en el cuadro de diálogo](../mfc/handling-windows-messages-in-your-dialog-box.md)  
  
-   [Recuperación de datos desde el objeto de cuadro de diálogo](../mfc/retrieving-data-from-the-dialog-object.md)  
  
-   [Cierre el cuadro de diálogo](../mfc/closing-the-dialog-box.md)  
  
-   [Destruir el cuadro de diálogo](../mfc/destroying-the-dialog-box.md)  
  
-   [Intercambio de datos de cuadros de diálogo (DDX) y la validación (DDV)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [Cuadros de diálogo de hoja de propiedades](../mfc/property-sheets-and-property-pages-mfc.md)  
  
## <a name="see-also"></a>Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)

