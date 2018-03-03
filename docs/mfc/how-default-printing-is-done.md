---
title: "Cómo se realiza la impresión predeterminada | Documentos de Microsoft"
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
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5001026f1e5fe9e1fed86a49b0565b09ddd6b555
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-default-printing-is-done"></a>Cómo se realiza la impresión predeterminada
Este artículo explica el proceso de impresión de forma predeterminada en Windows en términos del marco de trabajo MFC.  
  
 En las aplicaciones MFC, la clase de vista tiene una función miembro denominada `OnDraw` que contiene el código de dibujo. `OnDraw`toma un puntero a un [CDC](../mfc/reference/cdc-class.md) objeto como parámetro. Que `CDC` objeto representa el contexto de dispositivo que recibe la imagen producida por `OnDraw`. Cuando la ventana que muestra el documento recibe un [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) mensaje, llama el marco `OnDraw` y le pasa un contexto de dispositivo para la pantalla (un [CPaintDC](../mfc/reference/cpaintdc-class.md) objeto, para ser específico). En consecuencia, `OnDraw`la salida del producto afectado a la pantalla.  
  
 En la programación para Windows, el envío de resultados a la impresora es muy similar al envío de salida a la pantalla. Esto es porque la interfaz de dispositivo de gráficos (GDI) de Windows es independiente del hardware. Puede utilizar las mismas funciones GDI para la presentación en pantalla o para impresión simplemente mediante el contexto de dispositivo apropiados. Si el `CDC` objeto que `OnDraw` recibe representa la impresora, `OnDraw`va de salida de la a la impresora.  
  
 Explica cómo las aplicaciones MFC pueden realizar la impresión básica sin necesidad de esfuerzo adicional por su parte. El marco de trabajo se encarga de mostrar el cuadro de diálogo de impresión y la creación de un contexto de dispositivo para la impresora. Cuando el usuario selecciona el comando Imprimir en el menú archivo, la vista pasa el contexto del dispositivo a `OnDraw`, que basa el documento en la impresora.  
  
 Sin embargo, hay algunas diferencias significativas entre impresión y visualización en pantalla. Al imprimir, tendrá que dividir el documento en páginas distintas y ellos uno en uno, en lugar de mostrar cada parte está visible en una ventana de presentación. Como un corolario, se debe tener en cuenta el tamaño del papel (si está tamaño carta, tamaño válido o un sobre). Puede que desee imprimir en distintas orientaciones, como el modo horizontal o vertical. La biblioteca Microsoft Foundation Class no puede predecir cómo controlará la aplicación estos problemas, por lo que ofrece un protocolo para agregar estas capacidades.  
  
 Que el protocolo se describe en el artículo [documentos de varias páginas](../mfc/multipage-documents.md).  
  
## <a name="see-also"></a>Vea también  
 [Impresión](../mfc/printing.md)

