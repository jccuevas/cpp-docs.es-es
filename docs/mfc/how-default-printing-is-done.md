---
title: ¿Cómo se realiza la impresión predeterminada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90f6559459bed9376dba8b7d9059761e9ace5ac8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202835"
---
# <a name="how-default-printing-is-done"></a>Cómo se realiza la impresión predeterminada
En este artículo se explica el proceso de impresión de forma predeterminada en Windows en términos del marco de trabajo MFC.  
  
 En aplicaciones MFC, la clase de vista tiene una función miembro denominada `OnDraw` que contiene el código de dibujo. `OnDraw` toma un puntero a un [CDC](../mfc/reference/cdc-class.md) objeto como parámetro. Que `CDC` objeto representa el contexto de dispositivo que recibe la imagen generada por `OnDraw`. Cuando la ventana que muestra el documento recibe un [WM_PAINT](/windows/desktop/gdi/wm-paint) del mensaje, llama el marco `OnDraw` y lo pasa en un contexto de dispositivo para la pantalla (un [CPaintDC](../mfc/reference/cpaintdc-class.md) objeto, para ser específico). En consecuencia, `OnDraw`salida del producto afectado a la pantalla.  
  
 En la programación para Windows, es muy similar a la salida se envía a la pantalla de envío de resultados a la impresora. Esto es porque la interfaz de dispositivo de gráfico (GDI) de Windows es independiente del hardware. Puede usar las mismas funciones GDI para presentación en pantalla o para impresión utilizando el contexto de dispositivo adecuado. Si el `CDC` objeto que `OnDraw` recibe representa la impresora, `OnDraw`salida del producto afectado a la impresora.  
  
 Esto explica cómo las aplicaciones MFC pueden realizar la impresión simple sin necesidad de esfuerzo adicional por su parte. El marco de trabajo se encarga de mostrar el cuadro de diálogo de impresión y la creación de un contexto de dispositivo para la impresora. Cuando el usuario selecciona el comando Imprimir en el menú archivo, la vista pasa este contexto de dispositivo para `OnDraw`, que el documento basa en la impresora.  
  
 Sin embargo, hay algunas diferencias importantes entre la impresión y presentación en pantalla. Al imprimir, tendrá que dividir el documento en páginas distintas y ellos uno en uno, en lugar de mostrar cada parte es visible en una ventana de presentación. Como corolario, tendrá que tener en cuenta el tamaño del papel (si es el tamaño de letra, tamaño legal o un sobre). Desea imprimir en distintas orientaciones, como el modo horizontal o vertical. La biblioteca Microsoft Foundation Class no puede predecir cómo controlará la aplicación estos problemas, por lo que ofrece un protocolo para agregar estas capacidades.  
  
 Que el protocolo se describe en el artículo [documentos de varias páginas](../mfc/multipage-documents.md).  
  
## <a name="see-also"></a>Vea también  
 [Impresión](../mfc/printing.md)

