---
title: Creación de una clase de cuadro de diálogo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d70f27639344fd00a2e99ad79bf2db166f3270a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341915"
---
# <a name="creating-your-dialog-class"></a>Creating Your Dialog (Clase)
Para cada cuadro de diálogo en el programa, cree una nueva clase de cuadro de diálogo para que funcione con el recurso de cuadro de diálogo.  
  
 [Agregar una clase](../ide/adding-a-class-visual-cpp.md) explica cómo crear una nueva clase de cuadro de diálogo. Cuando se crea una clase de cuadro de diálogo con el Asistente para agregar clases, escribe los siguientes elementos el. H y. Archivos CPP que especifique:  
  
 En. Archivo H:  
  
-   Una declaración de clase para la clase de cuadro de diálogo. La clase se deriva de [CDialog](../mfc/reference/cdialog-class.md).  
  
 En. Archivo CPP:  
  
-   Un mapa de mensajes para la clase.  
  
-   Un constructor estándar para el cuadro de diálogo.  
  
-   Una invalidación de la [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) función miembro. Edite esta función. Se utiliza para funciones de intercambio y validación de datos de cuadro de diálogo tal como se describe más adelante en [intercambio de datos de cuadros de diálogo y validación](../mfc/dialog-data-exchange-and-validation.md).  
  
## <a name="see-also"></a>Vea también  
 [Crear una clase de cuadro de diálogo con los asistentes para código](../mfc/creating-a-dialog-class-with-code-wizards.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

