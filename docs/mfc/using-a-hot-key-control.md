---
title: Con un Control de tecla de acceso rápido | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4442d45cffdae63600fa3a405e29a139b149175
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382949"
---
# <a name="using-a-hot-key-control"></a>Usar un control de tecla de acceso rápido
Uso típico de un control de tecla de acceso rápido sigue el modelo siguiente:  
  
-   Se crea el control. Si el control se especifica en una plantilla de cuadro de diálogo, la creación es automática cuando se crea el cuadro de diálogo. (Debe tener un [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) miembro en la clase de cuadro de diálogo que se corresponde con el control de tecla de acceso rápido.) Como alternativa, puede usar el [crear](../mfc/reference/chotkeyctrl-class.md#create) función de miembro para crear el control como una ventana secundaria de cualquier ventana.  
  
-   Si desea establecer un valor predeterminado para el control, llame a la [función miembro SetHotKey](../mfc/reference/chotkeyctrl-class.md#sethotkey) función miembro. Si desea prohibir ciertos Estados MAYÚS, llame a [SetRules](../mfc/reference/chotkeyctrl-class.md#setrules). Para los controles en un cuadro de diálogo, es un buen momento para hacer esto en el cuadro de diálogo [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) función.  
  
-   El usuario interactúa con el control presionando una combinación de teclas de acceso rápida cuando el control de tecla de acceso rápido tiene el foco. El usuario, a continuación, algún modo indica que esta tarea se ha completado, quizás haciendo clic en un botón en el cuadro de diálogo.  
  
-   Cuando se notifica al programa que el usuario ha seleccionado una tecla de acceso rápido, debe usar la función miembro [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) para recuperar los valores de estado de clave y MAYÚS virtuales desde el control de tecla de acceso rápido.  
  
-   Una vez que sepa qué clave seleccionados por el usuario, puede establecer la tecla de acceso rápido mediante uno de los métodos descritos en [establecer una tecla de acceso rápido](../mfc/setting-a-hot-key.md).  
  
-   Si el control de tecla de acceso rápido se encuentra en un cuadro de diálogo y el `CHotKeyCtrl` automáticamente se destruirá el objeto. Si no es así, debe asegurarse de que tanto el control y la `CHotKeyCtrl` objeto se han destruido correctamente.  
  
## <a name="see-also"></a>Vea también  
 [Usar CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Controles](../mfc/controls-mfc.md)

