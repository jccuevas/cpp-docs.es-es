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
ms.openlocfilehash: c60d99fdebcd64ad844bc19918a30beb90b86af3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618938"
---
# <a name="drawing-in-a-view"></a>Dibujar en una vista

Casi todo el dibujo de la aplicación se produce en la `OnDraw` función miembro de la vista, que debe invalidar en la clase de vista. (La excepción es el dibujo del mouse, que se describe en [interpretar la entrada del usuario a través de una vista](interpreting-user-input-through-a-view.md)). La `OnDraw` invalidación:

1. Obtiene los datos llamando a las funciones miembro del documento que se proporcionan.

1. Muestra los datos mediante una llamada a las funciones miembro de un objeto de contexto de dispositivo al que pasa el marco de trabajo `OnDraw` .

Cuando los datos de un documento cambian de alguna manera, se debe volver a dibujar la vista para reflejar los cambios. Normalmente, esto sucede cuando el usuario realiza un cambio a través de una vista en el documento. En este caso, la vista llama a la función miembro [UpdateAllViews](reference/cdocument-class.md#updateallviews) del documento para notificar a todas las vistas en el mismo documento que se actualicen a sí mismas. `UpdateAllViews`llama a la función miembro [alactualizar](reference/cview-class.md#onupdate) de cada vista. La implementación predeterminada de `OnUpdate` invalida el área de cliente completa de la vista. Puede invalidarlo para invalidar solo las regiones del área de cliente que se asignan a las partes modificadas del documento.

La `UpdateAllViews` función miembro de clase `CDocument` y la `OnUpdate` función miembro de clase `CView` permiten pasar información que describe qué partes del documento se modificaron. Este mecanismo de "sugerencia" permite limitar el área que la vista debe volver a dibujar. `OnUpdate`toma dos argumentos de "sugerencia". La primera, *lHint*, de tipo **lParam**, le permite pasar cualquier dato que desee, mientras que el segundo, *pHint*, de tipo `CObject` *, le permite pasar un puntero a cualquier objeto derivado de `CObject` .

Cuando una vista deja de ser válida, Windows le envía un mensaje de **WM_PAINT** . La función de controlador [OnPaint](reference/cwnd-class.md#onpaint) de la vista responde al mensaje mediante la creación de un objeto de contexto de dispositivo de clase [CPaintDC](reference/cpaintdc-class.md) y llama a la `OnDraw` función miembro de la vista. Normalmente no es necesario escribir una función de controlador de reemplazo `OnPaint` .

Un [contexto de dispositivo](device-contexts.md) es una estructura de datos de Windows que contiene información sobre los atributos de dibujo de un dispositivo, como una pantalla o una impresora. Todas las llamadas de dibujo se realizan a través de un objeto de contexto de dispositivo. Para dibujar en la pantalla, `OnDraw` se pasa un `CPaintDC` objeto. Para dibujar en una impresora, se pasa un objeto [CDC](reference/cdc-class.md) configurado para la impresora actual.

El código para dibujar en la vista recupera primero un puntero al documento y, a continuación, realiza las llamadas de dibujo a través del contexto del dispositivo. En el siguiente `OnDraw` ejemplo simple se muestra el proceso:

[!code-cpp[NVC_MFCDocView#1](codesnippet/cpp/drawing-in-a-view_1.cpp)]

En este ejemplo, definiría la `GetData` función como un miembro de la clase de documento derivada.

En el ejemplo se imprime cualquier cadena que obtenga del documento, centrada en la vista. Si la `OnDraw` llamada es para el dibujo de la pantalla, el `CDC` objeto pasado en *pDC* es un `CPaintDC` cuyo constructor ya ha llamado `BeginPaint` . Las llamadas a las funciones de dibujo se realizan a través del puntero de contexto del dispositivo. Para más información sobre los contextos de dispositivo y las llamadas de dibujo, vea clase [CDC](reference/cdc-class.md) en la *referencia de MFC* y [trabajar con objetos de ventana](working-with-window-objects.md).

Para obtener más ejemplos de cómo escribir `OnDraw` , vea los [ejemplos de MFC](../overview/visual-cpp-samples.md#mfc-samples).

## <a name="see-also"></a>Consulte también

[Usar vistas](using-views.md)
