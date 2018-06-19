---
title: 'TN029: Ventanas divisoras | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.windows.splitter
dev_langs:
- C++
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca18f12c5aa1ae767b8921c28e650f3fb69d9942
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384728"
---
# <a name="tn029-splitter-windows"></a>TN029: Ventanas divisoras
Esta nota describe la MFC [CSplitterWnd clase](../mfc/reference/csplitterwnd-class.md), que proporciona la ventana se divide y administra el cambio de tamaño de otras ventanas de panel.  
  
## <a name="splitter-styles"></a>Estilos de división  
 Un `CSplitterWnd` admite dos estilos diferentes de división de windows.  
  
 En los divisores estáticos"," la ventana divisora crea los paneles cuando se crea. El orden y el número de paneles nunca cambian. Barras de división se usan para cambiar el tamaño de los distintos paneles. Puede usar este estilo para mostrar una clase de vista diferente en cada panel. El editor de gráficos de Visual C++ y el Administrador de archivos de Windows son ejemplos de programas que utilizan este estilo divisor. Este estilo de ventana divisora no usa cuadros divisor.  
  
 En "dinámicas divisores," paneles adicionales se crean y destruyen como las vistas nuevo de divisiones y divisiones de anulación de usuario. Este separador empieza con una vista única y proporciona cuadros de división para el usuario iniciar la división. La ventana divisora crea un nuevo objeto de vista de forma dinámica cuando la vista se divide en una dirección. Este nuevo objeto de vista representa el nuevo panel. Si la vista se divide en dos direcciones mediante la interfaz de teclado, la ventana divisora crea tres nuevos objetos de vista para los tres paneles nuevo. Mientras la división está activa, Windows muestra el cuadro de división como una barra de división entre los paneles. Windows destruye los objetos de vista adicionales cuando el usuario quita una división, pero la vista original se conserva hasta que la propia ventana divisora se destruye. Microsoft Excel y Microsoft Word son ejemplos de aplicaciones que usan el estilo divisoras dinámicas.  
  
 Al crear cualquier tipo de ventana divisora, debe especificar el número máximo de filas y columnas que se va a administrar el divisor. Paneles para rellenar todas las filas y columnas, creará un divisor estático. Un divisoras dinámicas creará solo el primer panel cuando el `CSplitterWnd` se crea.  
  
 El número máximo de paneles que puede especificar para divisores estáticos es 16 filas por 16 columnas. Las configuraciones recomendadas son:  
  
-   las columnas de la 1 fila x 2: normalmente con los paneles  
  
-   columna de 2 filas 1: normalmente con los paneles  
  
-   columnas de 2 filas x 2: normalmente con paneles similar  
  
 El número máximo de paneles que se pueden especificar para divisores dinámicos es 2 filas por 2 columnas. Las configuraciones recomendadas son:  
  
-   las columnas de la 1 fila x 2: para los datos en columnas  
  
-   columna de 2 filas 1: para los datos de texto u otros  
  
-   columnas de 2 filas x 2: tabla o cuadrícula orientadas a datos  
  
## <a name="splitter-examples"></a>Ejemplos de división  
 Muchos de los programas de ejemplo MFC usan ventanas divisoras directa o indirectamente. El ejemplo General de MFC [VIEWEX](../visual-cpp-samples.md) muestran varios usos de divisores estáticos, incluido cómo colocar un divisor en un divisor.  
  
 También puede usar el Asistente para crear un nuevo documento MDI (interfaz) secundario marco clase de ventana múltiples que contiene una ventana divisora. Para obtener más información sobre las ventanas divisoras, consulte [varios tipos de documentos, vistas y ventanas de marco](../mfc/multiple-document-types-views-and-frame-windows.md).  
  
## <a name="terminology-used-by-implementation"></a>Terminología usada por la implementación  
 Esta es una lista de términos que son específicas de las ventanas divisoras:  
  
 `CSplitterWnd`:  
 Una ventana que proporciona controles de panel de división y barras de desplazamiento que se comparten entre todos los paneles en una fila o columna. Especificar filas y columnas con números basados en cero (el primer panel es fila = 0 y la columna = 0).  
  
 Panel:  
 Una ventana específica de la aplicación que un `CSplitterWnd` administra. Un panel normalmente es un objeto que se deriva de la [CView (clase)](../mfc/reference/cview-class.md), pero puede ser cualquier [CWnd](../mfc/reference/cwnd-class.md) objeto que tiene el identificador de ventana de secundario correspondiente.  
  
 Para usar un `CWnd`-derivados de objetos, pasar la `RUNTIME_CLASS` del objeto que se la `CreateView` funcionando como lo haría si estuviera usando un `CView`-clase derivada. Debe usar la clase `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE` porque el marco de trabajo usa la creación dinámica en tiempo de ejecución. Aunque no hay una gran cantidad de código en `CSplitterWnd` que es específico de la `CView` (clase), [CObject:: IsKindOf](../mfc/reference/cobject-class.md#iskindof) siempre se utiliza antes de que se llevan a cabo dichas acciones.  
  
 Barra de división:  
 Un control que se coloca entre las filas y columnas de paneles. Se puede usar para ajustar el tamaño de filas o columnas de paneles.  
  
 Cuadro de división:  
 Un control en un dinámico `CSplitterWnd` que puede usar para crear nuevas filas o columnas de paneles. Se encuentra en la parte superior de las barras de desplazamiento vertical o a la izquierda de las barras de desplazamiento horizontal.  
  
 Divisor intersección:  
 La intersección de una barra divisora vertical y una barra divisora horizontal. Puede arrastrar para ajustar el tamaño de una fila y columna de paneles al mismo tiempo.  
  
## <a name="shared-scroll-bars"></a>Barras de desplazamiento compartido  
 La `CSplitterWnd` clase también es compatible con las barras de desplazamiento compartido. Estos controles de barra de desplazamiento son elementos secundarios de la `CSplitterWnd` y se comparten con los distintos paneles de la división.  
  
 Por ejemplo, en una ventana de la columna 1 fila x 2, puede especificar WS_VSCROLL al crear la `CSplitterWnd`. Windows crea un control de barra de desplazamiento especial que se comparte entre los dos paneles.  
  
```  
[      ][      ][^]  
[pane00][pane01][|]  
[      ][      ][v]  
```  
  
 Cuando el usuario mueve la barra de desplazamiento `WM_VSCROLL` mensajes se enviarán a ambas vistas. Cuando cualquiera de las vistas establece la posición de la barra de desplazamiento, se establecerá la barra de desplazamiento compartido.  
  
 Tenga en cuenta que las barras de desplazamiento compartidas son más útiles con los objetos de vista similares. Si mezcla las vistas de tipos diferentes de un divisor, tendrá que escribir código especial para coordinar sus posiciones de desplazamiento. Cualquier `CView`-clase derivada que utiliza el `CWnd` barra de desplazamiento API delegará en la barra de desplazamiento compartido si existe. El `CScrollView` implementación es un ejemplo de un `CView` compartido de clase que es compatible con las barras de desplazamiento. Las clases que no se derivan de `CView`, las clases que se basan en las barras de desplazamiento no sea un control o las clases que utilizan las implementaciones estándar de Windows (por ejemplo, `CEditView`) no funcionarán con la característica de la barra de desplazamiento compartido de `CSplitterWnd`.  
  
## <a name="minimum-sizes"></a>Tamaños mínimos  
 Para cada fila hay un alto mínimo de la fila, y para cada columna hay un ancho de columna mínimo. Este valor mínimo garantiza que un panel no es demasiado pequeño para mostrarse en obtener detalles completos.  
  
 Para una ventana divisora estática, el mínimo de la fila inicial alto y ancho de columna es 0. Para una ventana divisora dinámica, el mínimo de la fila inicial alto y ancho de columna se establecen el `sizeMin` parámetro de la `CSplitterWnd::Create` (función).  
  
 Puede cambiar estos tamaños mínimos mediante la [CSplitterWnd::SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo) y [CSplitterWnd::SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo) funciones.  
  
## <a name="actual-vs-ideal-sizes"></a>Vs reales. Tamaños ideales  
 El diseño de los paneles en la ventana divisora depende del tamaño del fotograma que los contiene. Cuando un usuario cambia el tamaño del marco que lo contiene, el `CSplitterWnd` cambia de posición y cambia el tamaño de los paneles para que se ajusten lo mejor posible.  
  
 El usuario puede establecer manualmente a la fila alto de columna y tamaños de ancho o el programa puede establecer el tamaño ideal con la `CSplitterWnd` clase. El tamaño real puede ser menor o mayor que la ideal. Si no hay espacio suficiente para mostrar el tamaño ideal o si hay demasiado espacio vacío a la derecha o la parte inferior de la ventana divisora, Windows ajustará el tamaño real.  
  
## <a name="custom-controls"></a>Controles personalizados  
 Puede invalidar muchas funciones para proporcionar una interfaz personalizada y un comportamiento personalizado. Puede invalidar este primer conjunto para proporcionar imágenes alternativas para los distintos componentes gráficos de una ventana divisora.  
  
- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`  
  
- `virtual void OnInvertTracker(const CRect& rect);`  
  
 Se llama a esta función para crear un control de barra de desplazamiento compartido. Se puede invalidar para crear controles adicionales junto a la barra de desplazamiento.  
  
- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`  
  
 Estas funciones implementan la lógica de la ventana divisora dinámica. Puede invalidar estos elementos para proporcionar lógica de divisor más avanzada.  
  
- `virtual void DeleteView(int row, int col);`  
  
- `virtual BOOL SplitRow(int cyBefore);`  
  
- `virtual BOOL SplitColumn(int cxBefore);`  
  
- `virtual void DeleteRow(int rowDelete);`  
  
- `virtual void DeleteColumn(int colDelete);`  
  
## <a name="cview-functionality"></a>Funcionalidad de CView  
 El `CView` clase utiliza los siguientes comandos de alto niveles para delegar en el `CSplitterWnd` implementación. Dado que estos comandos son virtuales, el estándar `CView` implementación requerirá que no toda la matriz `CSplitterWnd` implementación debe vincularse en. Para las aplicaciones que utilizan `CView` pero no `CSplitterWnd`, el `CSplitterWnd` implementación no se vinculará a la aplicación.  
  
 `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`  
 Comprueba si es posible actualmente ID_NEXT_PANE o ID_PREV_PANE.  
  
 `virtual void ActivateNext(BOOL bPrev = FALSE);`  
 Ejecuta el comando "Sección siguiente" o "Panel anterior".  
  
 `virtual BOOL DoKeyboardSplit();`  
 Ejecuta el comando, normalmente "división de la ventana" de división de teclado.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

