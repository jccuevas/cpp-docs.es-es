---
title: Dibujar en una vista | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc716800c35aa922f7912f586d6e5b8429593615
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="drawing-in-a-view"></a>Dibujar en una vista
Casi todos los dibujos en la aplicación se produce en la vista `OnDraw` función de miembro, que se debe reemplazar en la clase de vista. (La excepción es mouse dibujo, que se describe en [interpretación usuario entrada mediante una vista](../mfc/interpreting-user-input-through-a-view.md).) Su `OnDraw` invalidar:  
  
1.  Obtiene los datos mediante una llamada al documento proporcionan las funciones miembro.  
  
2.  Muestra los datos mediante una llamada a las funciones miembro de un objeto de contexto de dispositivo que el marco de trabajo pasa a `OnDraw`.  
  
 Cuando cambian los datos de un documento de alguna manera, se debe volver a dibujar la vista para reflejar los cambios. Normalmente, esto sucede cuando el usuario realiza un cambio a través de una vista en el documento. En este caso, llama a la vista del documento [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) función de miembro para notificar a todas las vistas en el mismo documento que se actualicen. `UpdateAllViews` llama a cada vista [OnUpdate](../mfc/reference/cview-class.md#onupdate) función miembro. La implementación predeterminada de `OnUpdate` invalida el área de cliente completa de la vista. Se puede reemplazar para invalidar sólo aquellas regiones del área de cliente que se asignan a las partes modificadas del documento.  
  
 El `UpdateAllViews` función miembro de clase **CDocument** y `OnUpdate` función miembro de clase `CView` permiten pasar información que describe qué partes del documento se han modificado. Este mecanismo de "sugerencia" permite limitar el área que debe volver a dibujar la vista. `OnUpdate` toma dos argumentos de "sugerencia". La primera, `lHint`, del tipo **LPARAM**, permite pasar cualquier dato que quiera, mientras que la segunda, `pHint`, del tipo `CObject`*, permite pasar un puntero a cualquier objeto derivado de `CObject`.  
  
 Cuando una vista deja de ser válida, Windows envía una `WM_PAINT` mensaje. La vista [OnPaint](../mfc/reference/cwnd-class.md#onpaint) función de controlador responde al mensaje mediante la creación de un objeto de contexto de dispositivo de clase [CPaintDC](../mfc/reference/cpaintdc-class.md) y llama a la vista `OnDraw` función miembro. Normalmente no es necesario escribir un reemplazo `OnPaint` función de controlador.  
  
 A [contexto de dispositivo](../mfc/device-contexts.md) es una estructura de datos de Windows que contiene información sobre los atributos de dibujo de un dispositivo, como una pantalla o una impresora. Todas las llamadas de dibujo se realizan a través de un objeto de contexto de dispositivo. Para dibujar en la pantalla, `OnDraw` se pasa un `CPaintDC` objeto. Para dibujar en una impresora, se pasa un [CDC](../mfc/reference/cdc-class.md) objeto configurado para la impresora actual.  
  
 El código para dibujar en la vista primero recupera un puntero al documento, después, realiza llamadas de dibujo a través del contexto de dispositivo. El simple siguiente `OnDraw` en el ejemplo se ilustra el proceso:  
  
 [!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]  
  
 En este ejemplo, tendría que definir la `GetData` función como un miembro de la clase derivada de documento.  
  
 El ejemplo imprime cualquier cadena que obtiene del documento, en el centro de la vista. Si el `OnDraw` es llamada de dibujo en pantalla, el `CDC` objeto pasado en `pDC` es un `CPaintDC` cuyo constructor ya ha llamado `BeginPaint`. Llamadas a funciones de dibujo se realizan a través del puntero de contexto de dispositivo. Para obtener información acerca de contextos de dispositivo y llamadas de dibujo, vea la clase [CDC](../mfc/reference/cdc-class.md) en el *referencia de MFC* y [trabajar con objetos Window](../mfc/working-with-window-objects.md).  
  
 Para obtener más ejemplos de cómo escribir `OnDraw`, consulte el [ejemplos de MFC](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Vea también  
 [Uso de vistas](../mfc/using-views.md)

