---
title: 'TN029: Ventanas divisoras'
ms.date: 11/04/2016
f1_keywords:
- vc.windows.splitter
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
ms.openlocfilehash: 6c2f619d9cd619ca598c66ca657faa1b9dccaaa2
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781736"
---
# <a name="tn029-splitter-windows"></a>TN029: Ventanas divisoras

Esta nota describe las MFC [CSplitterWnd (clase)](../mfc/reference/csplitterwnd-class.md), que proporciona la ventana divide y administra el cambio de tamaño de otras ventanas del panel.

## <a name="splitter-styles"></a>Estilos del divisor

Un `CSplitterWnd` admite dos estilos diferentes de la división de windows.

En "divisores estáticos", la ventana divisora crea los paneles cuando se crea. Nunca cambian el orden y el número de paneles. Barras de división se usan para cambiar el tamaño de los distintos paneles. Puede usar este estilo para mostrar una clase de vista diferente en cada panel. El editor de gráficos de Visual C++ y el Administrador de archivos de Windows son ejemplos de programas que utilizan este estilo de separador. Este estilo de ventana divisora no usa los cuadros del divisor.

En los divisores dinámicos"," paneles adicionales se crean y destruyen como el usuario divisiones y anular divisiones nuevas vistas. Este separador comienza con una sola vista y proporciona cuadros de separador para el usuario inicie la división. La ventana divisora dinámica crea un nuevo objeto de vista cuando la vista se divide en una dirección. Este nuevo objeto de vista representa el nuevo panel. Si la vista está dividida en dos direcciones mediante la interfaz de teclado, la ventana divisora crea tres nuevos objetos de vista para los tres paneles nuevo. Mientras está activa la división, Windows muestra el cuadro de divisor como una barra divisora entre los paneles. Windows destruye los objetos de vista adicionales cuando el usuario quita una división, pero la vista original se conserva hasta que la propia ventana divisora se destruye. Microsoft Excel y Microsoft Word son ejemplos de las aplicaciones que usan el estilo divisoras dinámicas.

Cuando se crea cualquier tipo de ventana divisora, debe especificar el número máximo de filas y columnas que se va a administrar el divisor. Un divisora estática creará paneles para rellenar todas las filas y columnas. Un divisoras dinámicas creará solo el primer panel cuando el `CSplitterWnd` se crea.

El número máximo de paneles, que puede especificar para divisores estáticos es 16 filas por 16 columnas. Las configuraciones recomendadas son:

- las columnas 1 fila x 2: normalmente con diferentes paneles

- columna 2 filas 1: normalmente con diferentes paneles

- las columnas 2 filas x 2: normalmente con los paneles similares

El número máximo de paneles que se pueden especificar para los separadores dinámicos es 2 filas por 2 columnas. Las configuraciones recomendadas son:

- las columnas 1 fila x 2: para los datos en columnas

- columna 2 filas 1: textual u otros datos

- las columnas 2 filas x 2: tabla o cuadrícula orientada a datos

## <a name="splitter-examples"></a>Ejemplos del divisor

Muchos de los programas de ejemplo MFC usan ventanas divisoras directa o indirectamente. El ejemplo General de MFC [VIEWEX](../overview/visual-cpp-samples.md) se muestran varios usos de divisores estáticas, incluida la forma de colocar un divisor en un divisor.

También puede usar ClassWizard para crear un nuevo varios documento MDI (interfaz) ventana clase de marco secundario que contiene una ventana divisora. Para obtener más información sobre las ventanas divisoras, consulte [varios tipos de documentos, vistas y marco Windows](../mfc/multiple-document-types-views-and-frame-windows.md).

## <a name="terminology-used-by-implementation"></a>Terminología usada por implementación

Esta es una lista de términos que son específicas de las ventanas divisoras:

`CSplitterWnd`: Una ventana que proporciona controles de separación de panel y las barras de desplazamiento que se comparten entre todos los paneles en una fila o columna. Especificar las filas y columnas con números de base cero (el primer panel es la fila = 0 y la columna = 0).

Panel: Una ventana específica de la aplicación que un `CSplitterWnd` administra. Un panel normalmente es un objeto que se deriva el [CView (clase)](../mfc/reference/cview-class.md), pero puede ser cualquier [CWnd](../mfc/reference/cwnd-class.md) objeto que tiene el identificador de ventana de secundario correspondiente.

Para usar un `CWnd`-derivados de objeto, pase el RUNTIME_CLASS del objeto para el `CreateView` funcionando como lo haría si estuviera usando un `CView`-clase derivada. Debe utilizar la clase DECLARE_DYNCREATE e IMPLEMENT_DYNCREATE porque el marco de trabajo utiliza la creación dinámica en tiempo de ejecución. Aunque hay una gran cantidad de código en `CSplitterWnd` que es específico para el `CView` (clase), [CObject:: IsKindOf](../mfc/reference/cobject-class.md#iskindof) siempre se utiliza antes de que se llevan a cabo esas acciones.

Barra de división: Un control que se coloca entre las filas y columnas de paneles. Se puede usar para ajustar los tamaños de las filas o columnas de paneles.

Divisor de cuadro: Un control en un dinámico `CSplitterWnd` que puede usar para crear nuevas filas o columnas de paneles. Se encuentra en la parte superior de las barras de desplazamiento vertical o a la izquierda de las barras de desplazamiento horizontal.

Divisor intersección: La intersección de una barra divisora vertical y una barra divisora horizontal. Puede arrastrar para ajustar el tamaño de una fila y columna de paneles al mismo tiempo.

## <a name="shared-scroll-bars"></a>Las barras de desplazamiento compartido

La `CSplitterWnd` clase también es compatible con las barras de desplazamiento compartido. Estos controles de barra de desplazamiento son elementos secundarios de la `CSplitterWnd` y se comparten con los distintos paneles en el divisor.

Por ejemplo, en una ventana de la columna 1 fila x 2, puede especificar WS_VSCROLL al crear el `CSplitterWnd`. Windows crea un control de barra de desplazamiento especial que se comparte entre los dos paneles.

```
[      ][      ][^]
[pane00][pane01][|]
[      ][      ][v]
```

Cuando el usuario mueve la barra de desplazamiento, se enviarán mensajes WM_VSCROLL en ambas vistas. Cuando cualquiera de las vistas establece la posición de la barra de desplazamiento, se establecerá la barra de desplazamiento compartido.

Tenga en cuenta que las barras de desplazamiento compartido son más útiles con los objetos de vista similares. Si mezcla las vistas de diferentes tipos en un divisor, es posible que deba escribir código especial para coordinar sus posiciones de desplazamiento. Cualquier `CView`-clase derivada que usa el `CWnd` barra de desplazamiento API delegará en la barra de desplazamiento compartido si existe. El `CScrollView` implementación es un ejemplo de un `CView` comparte de clase que es compatible con las barras de desplazamiento. Las clases que no se derivan `CView`, las clases que se basan en las barras de desplazamiento que no son de control o las clases que utilizan las implementaciones estándar de Windows (por ejemplo, `CEditView`) no funcionará con la característica de barra de desplazamiento compartido de `CSplitterWnd`.

## <a name="minimum-sizes"></a>Tamaños mínimos

Para cada fila hay un alto de fila mínimo, y para cada columna, hay un ancho de columna mínimo. Este mínimo garantiza que un panel no es demasiado pequeño para mostrarse en detalle.

Para una ventana divisora estática, el mínimo de la fila inicial alto y ancho de columna es 0. Para una ventana divisora dinámica, Establece el ancho mínimo de la fila inicial de alto de columna y el *sizeMin* parámetro de la `CSplitterWnd::Create` función.

Puede cambiar estos tamaños mínimos mediante la [CSplitterWnd::SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo) y [CSplitterWnd::SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo) funciones.

## <a name="actual-vs-ideal-sizes"></a>Real frente a. Tamaños ideales

El diseño de los paneles en la ventana divisora depende del tamaño del marco que los contiene. Cuando un usuario cambia el tamaño del marco que contiene, el `CSplitterWnd` cambia de posición y cambia el tamaño de los paneles para que se ajusten lo mejor posible.

El usuario puede establecer manualmente a la fila alto de columna y tamaños de ancho o el programa puede establecer el tamaño ideal con la `CSplitterWnd` clase. El tamaño real puede ser mayor o menor que lo más conveniente. Windows ajustarán el tamaño real si no hay espacio suficiente para mostrar el tamaño ideal o si no hay mucho espacio vacío a la derecha o la parte inferior de la ventana divisora.

## <a name="custom-controls"></a>Controles personalizados

Puede invalidar muchas funciones para proporcionar el comportamiento personalizado y una interfaz personalizada. Puede invalidar este primer conjunto para proporcionar imágenes alternativas para los distintos componentes gráficos de una ventana divisora.

- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`

- `virtual void OnInvertTracker(const CRect& rect);`

Se llama a esta función para crear un control de barra de desplazamiento compartido. Puede invalidar para crear controles adicionales al lado de la barra de desplazamiento.

- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`

Estas funciones implementan la lógica de la ventana divisora dinámica. Puede invalidar estos elementos para proporcionar lógica de divisor más avanzado.

- `virtual void DeleteView(int row, int col);`

- `virtual BOOL SplitRow(int cyBefore);`

- `virtual BOOL SplitColumn(int cxBefore);`

- `virtual void DeleteRow(int rowDelete);`

- `virtual void DeleteColumn(int colDelete);`

## <a name="cview-functionality"></a>CView funcionalidad

El `CView` clase usa los siguientes comandos de alto niveles para delegar a los `CSplitterWnd` implementación. Dado que estos comandos son virtuales, el estándar `CView` implementación no necesita toda la `CSplitterWnd` implementación vinculada en. Para las aplicaciones que usan `CView` pero no `CSplitterWnd`, el `CSplitterWnd` implementación no se vinculará a la aplicación.

- `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`

   Comprueba si es actualmente posible ID_NEXT_PANE o ID_PREV_PANE.

- `virtual void ActivateNext(BOOL bPrev = FALSE);`

   Ejecuta el comando "Panel siguiente" o "Panel anterior".

- `virtual BOOL DoKeyboardSplit();`

   Ejecuta el comando, normalmente "división de la ventana" de la división de teclado.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
