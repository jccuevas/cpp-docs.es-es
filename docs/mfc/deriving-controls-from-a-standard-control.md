---
title: Derivar controles de un Control estándar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- standard controls [MFC], deriving controls from
- common controls [MFC], deriving from
- derived controls
- controls [MFC], derived
- Windows common controls [MFC], deriving from
- standard controls
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4ae7fb09e1f453b6d7bc82a7fb038567809f872
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932252"
---
# <a name="deriving-controls-from-a-standard-control"></a>Derivar controles de un control estándar
Como con cualquier [CWnd](../mfc/reference/cwnd-class.md)-clase derivada, puede modificar el comportamiento de un control derivando una nueva clase de una clase de control existente.  
  
### <a name="to-create-a-derived-control-class"></a>Para crear una clase derivada de control  
  
1.  Derive la clase de una clase de control existente y, opcionalmente, invalide el `Create` función miembro para que proporcione los argumentos necesarios para la clase base `Create` función.  
  
2.  Proporcionar funciones de miembro de controlador de mensajes y entradas de mapa de mensajes para modificar el comportamiento del control en respuesta a los mensajes de Windows específicos. Vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).  
  
3.  Proporciona nuevas funciones miembro para ampliar la funcionalidad del control (opcional).  
  
 El uso de un control derivado en un cuadro de diálogo requiere trabajo adicional. Los tipos y las posiciones de los controles en un cuadro de diálogo normalmente se especifican en un recurso de plantilla de cuadro de diálogo. Si crea una clase derivada de control, no se puede especificar en una plantilla de cuadro de diálogo ya que el compilador de recursos no sabe nada acerca de la clase derivada.  
  
#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>Para colocar el control derivado en un cuadro de diálogo  
  
1.  Incrustar un objeto de la clase de control derivada en la declaración de la clase de cuadro de diálogo derivada.  
  
2.  Invalidar el `OnInitDialog` función miembro en la clase de cuadro de diálogo para llamar a la `SubclassDlgItem` función de miembro para el control derivado.  
  
 `SubclassDlgItem` "dinámicamente las subclases" crea un control de una plantilla de cuadro de diálogo. Cuando un control de forma dinámica es una subclase, enlazar en Windows, algunos mensajes se procesen en su propia aplicación y pasar los mensajes restantes a Windows. Para obtener más información, consulte el [SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem) función miembro de clase `CWnd` en el *referencia de MFC*. En el ejemplo siguiente se muestra cómo se puede escribir una invalidación de `OnInitDialog` para llamar a `SubclassDlgItem`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]  
  
 Dado que el control derivado está incrustado en la clase de cuadro de diálogo, se construirá cuando se crea el cuadro de diálogo, y se destruirá cuando se destruye el cuadro de diálogo. Compare este código con el ejemplo de [agregar controles manualmente](../mfc/adding-controls-by-hand.md).  
  
## <a name="see-also"></a>Vea también  
 [Crear y utilizar controles](../mfc/making-and-using-controls.md)   
 [Controles](../mfc/controls-mfc.md)

