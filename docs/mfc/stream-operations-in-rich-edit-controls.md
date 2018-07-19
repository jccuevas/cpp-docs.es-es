---
title: Secuencia de operaciones en los controles Rich Edit | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66afb05031b302877dfd34f64e6076f882a256d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379930"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Operaciones de secuencia en los controles Rich Edit
Puede utilizar secuencias para transferir datos entre o salga de un control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Un flujo se define mediante una [estructura EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) estructura, que especifica un búfer y una función de devolución de llamada definida por la aplicación.  
  
 Para leer datos en un amplio control de edición (es decir, los datos de secuencia), utilice la [función miembro StreamIn](../mfc/reference/cricheditctrl-class.md#streamin) función miembro. El control llama repetidamente a la función de devolución de llamada definida por la aplicación, que transfiere una parte de los datos en el búfer cada vez.  
  
 Para guardar el contenido de los datos completos de un control de edición (es decir, transmitir por secuencias los datos de salida), puede usar el [función miembro StreamOut](../mfc/reference/cricheditctrl-class.md#streamout) función miembro. El control escribe varias veces en el búfer y, a continuación, llama a la función de devolución de llamada definida por la aplicación. Para cada llamada, la función de devolución de llamada guarda el contenido del búfer.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)

