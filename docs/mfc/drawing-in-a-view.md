---
title: "Dibujar en una vista | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contextos de dispositivo, dibujos de pantalla"
  - "dibujar, en vistas"
  - "dibujar mensajes en clase de vista"
  - "imprimir [MFC], vistas"
  - "imprimir vistas"
  - "vistas, imprimir"
  - "vistas, representar"
  - "vistas, actualizar"
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Dibujar en una vista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Prácticamente todo el gráfico en la aplicación aparece en la función miembro de `OnDraw` de la vista, que debe invalidar en la clase de vista. \(La excepción es gráfico de mouse, descritos en [Interpretar los datos proporcionados por el usuario a través de una vista](../mfc/interpreting-user-input-through-a-view.md).\) La invalidación de `OnDraw` :  
  
1.  Obtiene datos a las funciones miembro de documentos que proporciona.  
  
2.  Muestra los datos llamando a funciones miembro de un objeto de dispositivo\- contexto que pasa el marco a `OnDraw`.  
  
 Cuando los datos de un documento cambia de alguna manera, la vista se debe volver a dibujar para reflejar los cambios.  Normalmente, esto ocurre cuando el usuario realiza un cambio con una vista del documento.  En este caso, la vista llama a la función miembro de [UpdateAllViews](../Topic/CDocument::UpdateAllViews.md) del documento para notificar todas las vistas del mismo documento para actualizarse.  `UpdateAllViews` llama a la función miembro de [OnUpdate](../Topic/CView::OnUpdate.md) de cada vista.  La implementación predeterminada de `OnUpdate` reemplaza el área cliente completa de la vista.  Puede reemplazarlo para reemplazar solamente las regiones del área de cliente que se asignan a las partes modificadas del documento.  
  
 La función miembro de `UpdateAllViews` de la clase **CDocument** y la función miembro de `OnUpdate` de la clase `CView` permiten pasar información que describe qué partes del documento se modificaron.  Este mecanismo de “sugerencia” permite limitar el área de la vista debe actualizar.  `OnUpdate` toma dos argumentos de “sugerencia”.  El primer, `lHint`, de **LPARAM**escrito, permite pasar los datos que desee, mientras que el segundo, `pHint`, de `CObject`escriba \*, permite pasar un puntero a cualquier objeto derivado de `CObject`.  
  
 Cuando una vista deja de ser válida, Windows le envía un mensaje de `WM_PAINT` .  La función de controlador de [OnPaint](../Topic/CWnd::OnPaint.md) de vista responde al mensaje creando un objeto de dispositivo\- contexto de la clase [CPaintDC](../mfc/reference/cpaintdc-class.md) y llama a la función miembro de `OnDraw` de la vista.  No tiene que normalmente escribir una función de controlador de `OnPaint` de reemplazo.  
  
 [contexto de dispositivo](../mfc/device-contexts.md) es una estructura de datos de Windows que contiene información sobre los atributos del gráfico de un dispositivo como una pantalla o una impresora.  Todas las llamadas del gráfico se hace a través de un objeto de dispositivo\- contexto.  Para dibujar en la pantalla, `OnDraw` se pasa un objeto de `CPaintDC` .  Para dibujar en una impresora, se pasa un objeto de [CDC](../mfc/reference/cdc-class.md) configurar para la impresora actual.  
  
 El código para dibujar en la vista primero recupera un puntero al documento, haga llamadas de gráfico con el contexto del dispositivo.  El siguiente ejemplo simple de `OnDraw` muestra el proceso:  
  
 [!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/CPP/drawing-in-a-view_1.cpp)]  
  
 En este ejemplo, defina la función de `GetData` como miembro de la clase derivada del documento.  
  
 El ejemplo imprime cualquier cadena del documento, centrado en la vista.  Si la llamada de `OnDraw` es para el gráfico de la pantalla, el objeto de `CDC` pasado en `pDC` es `CPaintDC` cuyo constructor ha llamado ya `BeginPaint`.  Las llamadas a funciones de dibujo se hace a través del puntero de dispositivo\- contexto.  Para obtener información sobre los contextos de dispositivo y llamadas de dibujo, vea la clase [CDC](../mfc/reference/cdc-class.md) en *la referencia* y [Trabajar con objetos de la ventana](../mfc/working-with-window-objects.md)MFC.  
  
 Para obtener más ejemplos de cómo escribir `OnDraw`, vea [Ejemplos de MFC](../top/visual-cpp-samples.md).  
  
## Vea también  
 [Usar vistas](../mfc/using-views.md)