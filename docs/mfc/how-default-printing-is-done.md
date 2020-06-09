---
title: Cómo se realiza la impresión predeterminada
ms.date: 11/04/2016
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
ms.openlocfilehash: 9ca79ec69037b960e7c455f6ab8abd8833b9a8a0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618585"
---
# <a name="how-default-printing-is-done"></a>Cómo se realiza la impresión predeterminada

En este artículo se explica el proceso de impresión predeterminado en Windows en lo que respecta al marco de trabajo de MFC.

En las aplicaciones MFC, la clase de vista tiene una función miembro denominada `OnDraw` que contiene todo el código de dibujo. `OnDraw`toma un puntero a un objeto [CDC](reference/cdc-class.md) como parámetro. Ese `CDC` objeto representa el contexto de dispositivo para recibir la imagen generada por `OnDraw` . Cuando la ventana que muestra el documento recibe un mensaje [WM_PAINT](/windows/win32/gdi/wm-paint) , el marco de trabajo llama a `OnDraw` y le pasa un contexto de dispositivo para la pantalla (un objeto [CPaintDC](reference/cpaintdc-class.md) , para que sea específico). En consecuencia, la `OnDraw` salida de se dirige a la pantalla.

En la programación de Windows, el envío de la salida a la impresora es muy similar al envío de la salida a la pantalla. Esto se debe a que la interfaz de dispositivo gráfico (GDI) de Windows es independiente del hardware. Puede usar las mismas funciones GDI para la presentación en pantalla o para imprimir simplemente mediante el contexto de dispositivo adecuado. Si el `CDC` objeto que `OnDraw` recibe representa la impresora, la `OnDraw` salida de se dirige a la impresora.

Esto explica cómo las aplicaciones MFC pueden realizar una impresión simple sin necesidad de esfuerzo adicional por su parte. El marco se encarga de mostrar el cuadro de diálogo Imprimir y crear un contexto de dispositivo para la impresora. Cuando el usuario selecciona el comando imprimir en el menú Archivo, la vista pasa este contexto de dispositivo a `OnDraw` , que dibuja el documento en la impresora.

Sin embargo, hay algunas diferencias importantes entre la impresión y la presentación en pantalla. Al imprimir, tiene que dividir el documento en páginas distintas y mostrarlos de uno en uno, en lugar de mostrar la parte visible en una ventana. Como consecuencia, tiene que tener en cuenta el tamaño del papel (ya sea el tamaño de la carta, el tamaño legal o un sobre). Puede que desee imprimir en distintas orientaciones, como el modo horizontal o vertical. El biblioteca MFC no puede predecir cómo controlará la aplicación estos problemas, por lo que proporciona un protocolo para que agregue estas funcionalidades.

Dicho Protocolo se describe en el artículo [documentos MultiPage](multipage-documents.md).

## <a name="see-also"></a>Consulte también

[Impresión](printing.md)
