---
title: "Barras de cuadro de diálogo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3d9d7319f23741f683e31cfd683a8ebd6d25acdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-bars"></a>Barras de cuadro de diálogo
Una barra de cuadro de diálogo es una barra de herramientas, un tipo de [barra de control](../mfc/control-bars.md) que puede contener cualquier tipo de control. Dado que tiene las características de un cuadro de diálogo no modal, un [CDialogBar](../mfc/reference/cdialogbar-class.md) objeto proporciona una barra de herramientas más eficaces.  
  
 Hay varias diferencias claves entre una barra de herramientas y un `CDialogBar` objeto. Un `CDialogBar` objeto se crea a partir de un recurso de plantilla de cuadro de diálogo, que puede crear con el editor de cuadro de diálogo de Visual C++ y que puede contener cualquier tipo de control de Windows. El usuario puede cambiar mediante tabulación desde el control al control. Y puede especificar un estilo de alineación para alinear la barra de cuadro de diálogo con cualquier parte de la ventana de marco primaria, o incluso dejar en su lugar si cambia el elemento primario. La siguiente ilustración muestra una barra de cuadro de diálogo con una variedad de controles.  
  
 ![Barra de cuadro de diálogo de VC](../mfc/media/vc378t1.gif "vc378t1")  
Una barra de cuadro de diálogo  
  
 En otros aspectos, trabajar con un `CDialogBar` objeto es similar a trabajar con un cuadro de diálogo no modal. Usar el editor de cuadro de diálogo para diseñar y crear el recurso de cuadro de diálogo.  
  
 Una de las virtudes de barras de cuadro de diálogo es que pueden incluir controles diferentes de los botones.  
  
 Aunque es normal para derivar sus propias clases de cuadro de diálogo de `CDialog`, no es habitual derivar su propia clase de una barra de cuadro de diálogo. Barras de cuadro de diálogo son extensiones de una ventana principal y los mensajes de notificación de controles de barra de cuadro de diálogo, como **BN_CLICKED** o **EN_CHANGE**, se enviará al elemento primario del cuadro de diálogo de la barra, la ventana principal.  
  
## <a name="see-also"></a>Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)   
 [Ejemplo](../visual-cpp-samples.md)

