---
title: Dibujar en una vista
ms.date: 11/04/2016
helpviewer_keywords:
- drawing [MFC], in views
- views [MFC], printing
- views [MFC], updating
- printing [MFC], views
- views [MFC], rendering
- printing views [MFC]
- paint messages in view class [MFC]
- device contexts, screen drawings
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
ms.openlocfilehash: bc461347b56379976cdf62014507e3a15529f081
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772558"
---
# <a name="drawing-in-a-view"></a>Dibujar en una vista

Casi todos los dibujos en la aplicación se produce en la vista `OnDraw` función miembro, que se debe reemplazar en la clase de vista. (La excepción es el mouse de dibujo, que se describe en [interpretar usuario entrada mediante una vista](../mfc/interpreting-user-input-through-a-view.md).) Su `OnDraw` invalidar:

1. Obtiene los datos mediante una llamada al documento proporcionan las funciones miembro.

1. Muestra los datos mediante una llamada a funciones miembro de un objeto de contexto de dispositivo que el marco de trabajo pasa a `OnDraw`.

Cuando cambian los datos de un documento de alguna manera, se debe volver a dibujar la vista para reflejar los cambios. Normalmente, esto sucede cuando el usuario realiza un cambio a través de una vista en el documento. En este caso, llama a la vista del documento [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) función miembro para notificar a todas las vistas en el mismo documento que se actualizan. `UpdateAllViews` llama a cada vista [OnUpdate](../mfc/reference/cview-class.md#onupdate) función miembro. La implementación predeterminada de `OnUpdate` invalida el área de cliente completa de la vista. Se puede reemplazar para invalidar sólo aquellas regiones del área de cliente que se asignan a las partes modificadas del documento.

El `UpdateAllViews` función miembro de clase `CDocument` y `OnUpdate` función miembro de clase `CView` permiten pasar información que describe qué partes del documento se han modificado. Este mecanismo de "sugerencia" le permite limitar el área que debe volver a dibujar la vista. `OnUpdate` toma dos argumentos de "sugerencia". La primera, *lHint*, del tipo **LPARAM**, permite pasar los datos deseados, mientras que el segundo, *pHint*, del tipo `CObject`*, permite pasar un puntero a cualquier objeto derivado desde `CObject`.

Cuando se convierte en una vista no válida, Windows envía una **WM_PAINT** mensaje. La vista [OnPaint](../mfc/reference/cwnd-class.md#onpaint) función de controlador responde al mensaje mediante la creación de un objeto de contexto de dispositivo de clase [CPaintDC](../mfc/reference/cpaintdc-class.md) y llama a la vista `OnDraw` función miembro. Normalmente no tiene que escribir una invalidación `OnPaint` función de controlador.

Un [contexto de dispositivo](../mfc/device-contexts.md) es una estructura de datos de Windows que contiene información sobre los atributos de dibujo de un dispositivo como una pantalla o una impresora. Todas las llamadas de dibujos se realizan a través de un objeto de contexto de dispositivo. Para dibujar en la pantalla, `OnDraw` se pasa un `CPaintDC` objeto. Para dibujar en una impresora, se pasa un [CDC](../mfc/reference/cdc-class.md) objeto configurado para la impresora actual.

En primer lugar, el código para dibujar en la vista recupera un puntero al documento y luego realiza llamadas de dibujo a través del contexto de dispositivo. El siguiente sencillo `OnDraw` ejemplo ilustra el proceso:

[!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]

En este ejemplo, tendría que definir el `GetData` funcionar como un miembro de la clase derivada de documento.

El ejemplo imprime cualquier cadena que se obtiene del documento, centrado en la vista. Si el `OnDraw` llamada es para el dibujo de la pantalla, el `CDC` objeto pasado en *pDC* es un `CPaintDC` cuyo constructor ya ha llamado a `BeginPaint`. Las llamadas a funciones de dibujo se realizan a través del puntero de contexto de dispositivo. Para obtener información acerca de los contextos de dispositivo y llamadas de dibujo, vea la clase [CDC](../mfc/reference/cdc-class.md) en el *referencia de MFC* y [trabajar con objetos Window](../mfc/working-with-window-objects.md).

Para obtener más ejemplos de cómo escribir `OnDraw`, consulte el [ejemplos de MFC](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Vea también

[Uso de vistas](../mfc/using-views.md)
