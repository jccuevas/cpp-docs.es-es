---
title: "Componentes de cuadro de diálogo en el marco de trabajo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 840e66def6a908b26b5021537eddee68c50a9628
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-box-components-in-the-framework"></a>Componentes de cuadro de diálogo en el marco
En el marco de trabajo MFC, un cuadro de diálogo tiene dos componentes:  
  
-   Un recurso de plantilla de cuadro de diálogo que especifica los controles del cuadro de diálogo y su ubicación.  
  
     El recurso de cuadro de diálogo almacena una plantilla de cuadro de diálogo desde el que Windows crea la ventana de cuadro de diálogo y lo muestra. La plantilla especifica las características del cuadro de diálogo, incluyendo su tamaño, ubicación, estilo y los tipos y posiciones de los controles del cuadro de diálogo. Normalmente se utiliza una plantilla de cuadro de diálogo almacenada como un recurso, pero también puede crear su propia plantilla en la memoria.  
  
-   Deriva una clase de cuadro de diálogo, [CDialog](../mfc/reference/cdialog-class.md), para proporcionar una interfaz de programación para administrar el cuadro de diálogo.  
  
     Un cuadro de diálogo es una ventana y se adjuntará a una ventana de Windows cuando está visible. Cuando se crea el cuadro de diálogo, el recurso de plantilla de cuadro de diálogo se usa como plantilla para crear controles de ventana para el cuadro de diálogo de secundarias.  
  
## <a name="see-also"></a>Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

