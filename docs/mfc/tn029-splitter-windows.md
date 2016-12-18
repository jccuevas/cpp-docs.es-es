---
title: "TN029: Ventanas divisoras | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.windows.splitter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ventanas divisoras, acerca de las ventanas divisoras"
  - "TN029"
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN029: Ventanas divisoras
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta nota describe MFC [CSplitterWnd Class](../mfc/reference/csplitterwnd-class.md), que proporciona las divisiones de la ventana y administra el tamaño de otras ventanas del panel.  
  
## Estilos splitter  
 `CSplitterWnd` admite dos estilos diferentes de dividir las ventanas.  
  
 En “divisores estáticos,” la ventana divisora crea los paneles cuando se crea.  El orden y el número de paneles nunca cambian.  Las barras de división se utilizan para cambiar el tamaño de los paneles distintos.  Puede utilizar este estilo para mostrar otra clase de vista en cada panel.  El editor de gráficos de Visual C\+\+ y el administrador de archivos de Windows son ejemplos de los programas que utilizan este estilo de división.  Este estilo de la ventana divisora no utiliza los cuadros splitter.  
  
 En “divisores dinámicos,” se crean y se destruyen los paneles adicionales como las divisiones del usuario y vistas de las O.N.U\- divisiones nuevas.  Este divisor comienza con una vista única y proporciona los cuadros splitter del usuario a dividir iniciado.  La ventana divisora crea dinámicamente un nuevo objeto de vista cuando la vista se divide en una dirección.  Este nuevo objeto de vista representa el nuevo panel.  Si la vista se divide en dos direcciones mediante la interfaz de teclado, la ventana divisora crea tres nuevos objetos de vista de los tres nuevos paneles.  Mientras la división está activo, Windows muestra el cuadro del divisor como una barra de división entre los paneles.  Windows destruye objetos de vista adicionales cuando el usuario quita una división, pero permanecen la vista original hasta que se destruya la ventana propio splitter.  Microsoft Excel y Microsoft Word son ejemplos de aplicaciones que utilizan el estilo dinámico splitter.  
  
 Cuando se crea una buena de la ventana divisora, debe especificar el número máximo de filas y columnas que el divisor administrar.  Un divisor estático creará los paneles para rellenar todas las filas y columnas.  Un divisor dinámico creará solo el primer panel cuando se crea `CSplitterWnd` .  
  
 El número máximo de paneles que puede especificar para los divisores estáticos es 16 filas por 16 columnas.  Las configuraciones recomendadas son:  
  
-   fila 1 x 2 columnas: normalmente con los paneles diferentes  
  
-   2 filas x 1 columna: normalmente con los paneles diferentes  
  
-   2 filas x 2 columnas: normalmente con los paneles similares  
  
 El número máximo de paneles que puede especificar para los divisores dinámicos es 2 filas por 2 columnas.  Las configuraciones recomendadas son:  
  
-   fila 1 x 2 columnas: para los datos acolumnados  
  
-   2 filas x 1 columna: para los datos de texto u otros  
  
-   2 filas x 2 columnas: para la cuadrícula o la tabla datos orientados  
  
## Ejemplos del divisor  
 Muchas de las ventanas divisoras de los programas de ejemplo de MFC directa o indirectamente.  El ejemplo [VIEWEX](../top/visual-cpp-samples.md) MFC General muestra varios usos de divisores estáticos, incluso cómo colocar un divisor en un divisor.  
  
 También puede utilizar ClassWizard para crear una clase de ventana secundaria de \(MDI\) de la nueva interfaz de múltiples documentos que contiene una ventana divisora.  Para obtener más información sobre las ventanas divisoras, vea [Tipos de documento, vistas, y cuadro varias Windows](../mfc/multiple-document-types-views-and-frame-windows.md).  
  
## Terminología utilizada por la implementación  
 A continuación se muestra una lista de términos específicos de las ventanas divisoras:  
  
 `CSplitterWnd`:  
 Una ventana que proporciona panel\- dividir los controles y las barras de desplazamiento que comparten todos los paneles en una fila o columna.  Especifica filas y columnas con números cero\- basados \(el primer panel es fila \= 0 y columna \= 0\).  
  
 Panel:  
 Una ventana específica de la aplicación que `CSplitterWnd` administra.  Un panel normalmente es un objeto que se deriva de [CView Class](../mfc/reference/cview-class.md), pero puede ser cualquier objeto de [CWnd](../mfc/reference/cwnd-class.md) que tiene el identificador adecuada de la ventana secundaria  
  
 Para utilizar `CWnd`\- objeto derivado, pase `RUNTIME_CLASS` de objeto a la función de `CreateView` como se si utiliza `CView`\- clase derivada.  La clase debe utilizar `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE` porque el marco de trabajo usa la creación dinámica en tiempo de ejecución.  Aunque hay mucho código en `CSplitterWnd` que es específico de la clase de `CView` , [CObject::IsKindOf](../Topic/CObject::IsKindOf.md) siempre se utiliza antes de realizar esas acciones.  
  
 Barra de división:  
 Un control que se coloca entre las filas y columnas de paneles.  Se puede utilizar para ajustar los tamaños de filas o columnas de paneles.  
  
 Cuadro splitter:  
 Un control en `CSplitterWnd` dinámico que puede utilizar para crear nuevas filas o columnas de paneles.  Se encuentra en la parte superior de las barras de desplazamiento vertical o a la izquierda de las barras de desplazamiento horizontal.  
  
 Intersección splitter:  
 La intersección de una barra de división vertical y una barra de división horizontal.  Puede arrastrarlo para ajustar el tamaño de una fila y una columna de paneles simultáneamente.  
  
## Barras de desplazamiento compartidas  
 La clase de `CSplitterWnd` también admite las barras de desplazamiento compartidas.  Estos controles de la barra de desplazamiento son elementos secundarios de `CSplitterWnd` y comparten con varios paneles del divisor.  
  
 Por ejemplo, en una 1 filas x ventana de 2 columnas, puede especificar WS\_VSCROLL al crear `CSplitterWnd`.  Windows crea un control de barra de desplazamiento especial que se comparte entre los dos paneles.  
  
```  
[      ][      ][^]  
[pane00][pane01][|]  
[      ][      ][v]  
```  
  
 Cuando el usuario mueve la barra de desplazamiento, los mensajes de `WM_VSCROLL` se enviará a ambas vistas.  Cuando cualquier vista establece la posición de la barra de desplazamiento, la barra de desplazamiento compartida se establecerá.  
  
 Observe que las barras de desplazamiento compartidas son más útiles con los objetos de vista similares.  Si se mezclan las vistas diferentes tipos en un divisor, puede tener que escribir código especial para coordinar las posiciones de desplazamiento.  Cualquier `CView`\- la clase derivada que usa la barra de desplazamiento API de `CWnd` delegará a la barra de desplazamiento compartida si existe.  La implementación de `CScrollView` es un ejemplo de una clase de `CView` que admite las barras de desplazamiento compartidas.  Las clases que no se derivan de `CView`, las clases que se basan en las barras de desplazamiento de la no de CONTROL, o las clases que utilizan las implementaciones estándar de Windows \(por ejemplo, `CEditView`\) no funcionarán con la característica compartida de la barra de desplazamiento de `CSplitterWnd`.  
  
## Tamaños mínimos  
 Para cada fila hay un alto de fila mínimo, y para cada columna hay un ancho de columna mínimo.  Este mínimo garantiza que un panel no es demasiado pequeño aparecer en detalle completo.  
  
 Para una ventana divisora estática, el alto de fila y el ancho de columna mínimos iniciales es 0.  Para una ventana dinámica splitter, el alto de fila y el ancho de columna mínimos iniciales se establecen mediante el parámetro de `sizeMin` de la función de `CSplitterWnd::Create` .  
  
 Puede cambiar esta tamaños mínimos mediante [CSplitterWnd::SetRowInfo](../Topic/CSplitterWnd::SetRowInfo.md) y [CSplitterWnd::SetColumnInfo](../Topic/CSplitterWnd::SetColumnInfo.md) funciona.  
  
## Real frente los tamaños de Ideal  
 El diseño de los paneles de la ventana divisora depende del tamaño del marco que los contiene.  Cuando un usuario cambia el tamaño del cuadro que contiene, `CSplitterWnd` coloca y cambia el tamaño de los paneles de nuevo para que quepan tan similar a como sea posible.  
  
 El usuario puede establecer manualmente los tamaños de alto de fila y el ancho de columna, o el programa puede establecer el tamaño ideal mediante la clase de `CSplitterWnd` .  El tamaño real puede ser menor o mayor que el ideal.  Windows se ajustará el tamaño real si no hay suficiente espacio para mostrar el tamaño ideal o hay demasiado espacio vacío de la derecha o inferior de la ventana divisora.  
  
## Controles personalizados  
 Puede reemplazar muchas funciones para proporcionar un comportamiento personalizado y una interfaz personalizada.  Puede invalidar este primer conjunto para proporcionar imágenes alternativas para los diferentes componentes gráficos de una ventana divisora.  
  
-   `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`  
  
-   `virtual void OnInvertTracker(const CRect& rect);`  
  
 Se llama a esta función para crear un control de barra de desplazamiento compartido.  Puede invalidarlo para crear controles adicionales al lado de la barra de desplazamiento.  
  
-   `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`  
  
 Estas funciones implementan la lógica de la ventana dinámica splitter.  Puede reemplazar esto para proporcionar una lógica más avanzadas del divisor.  
  
-   `virtual void DeleteView(int row, int col);`  
  
-   `virtual BOOL SplitRow(int cyBefore);`  
  
-   `virtual BOOL SplitColumn(int cxBefore);`  
  
-   `virtual void DeleteRow(int rowDelete);`  
  
-   `virtual void DeleteColumn(int colDelete);`  
  
## Funcionalidad de CView  
 La clase de `CView` utiliza los comandos de alto nivel siguientes de delegar a `CSplitterWnd` la implementación.  Dado que estos comandos son virtuales, la implementación estándar de `CView` no requieren la implementación completa de `CSplitterWnd` vincularse en.  Para las aplicaciones que utilizan `CView` pero no `CSplitterWnd`, la implementación de `CSplitterWnd` no se va a vincular a la aplicación.  
  
 `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`  
 Comprueba si ID\_NEXT\_PANE o ID\_PREV\_PANE está actualmente posible.  
  
 `virtual void ActivateNext(BOOL bPrev = FALSE);`  
 Ejecuta “panel siguiente” o “el comando del panel Anteriores de”.  
  
 `virtual BOOL DoKeyboardSplit();`  
 Ejecuta el comando partido de teclado, normalmente “ventana dividida”.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)