---
title: 'Tutorial: Actualizar la aplicación Scribble MFC (parte 2) | Documentos de Microsoft'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bccc10e1aa2d984486c3cadfd45a14a6625ec959
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122410"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Tutorial: Actualizar la aplicación Scribble de MFC (Parte 2)

[Parte 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) de este tutorial ha mostrado cómo agregar una cinta de Office Fluent en el clásico Scribble de aplicación. Esta parte muestra cómo agregar controles que los usuarios pueden usar en lugar de los menús y comandos y paneles de cinta de opciones.

## <a name="prerequisites"></a>Requisitos previos

[Ejemplos de Visual C++](../visual-cpp-samples.md)

##  <a name="top"></a> Secciones

Esta parte del tutorial tiene las secciones siguientes:

- [Agregar nuevos paneles a la cinta de opciones](#addnewpanel)

- [Agregar un Panel de ayuda a la cinta de opciones](#addhelppanel)

- [Agregar un Panel de lápiz a la cinta de opciones](#addpenpanel)

- [Agregar un botón de Color a la cinta de opciones](#addcolorbutton)

- [Agregar a un miembro de Color a la clase de documento](#addcolormember)

- [Inicializar lápices y guardar las preferencias](#initpensave)

##  <a name="addnewpanel"></a> Agregar nuevos paneles a la cinta de opciones

Estos pasos muestran cómo agregar un **vista** panel que contiene dos casillas de verificación que controlan la visibilidad de la barra de herramientas y la barra de estado, y también un **ventana** panel que contiene una división una orientación vertical botón que controla la creación y disposición de las ventanas de interfaz de múltiples documentos (MDI).

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Para agregar un panel de vista y el panel de ventana a la barra de cinta

1. Crear un panel denominado `View`, que tiene dos casillas de verificación que activar o desactivar la barra de estado y la barra de herramientas.

   1. Desde el **cuadro de herramientas**, arrastre un **Panel** a la **inicio** categoría. A continuación, arrastre dos **casillas de verificación** al panel.

   2. Haga clic en el panel para modificar sus propiedades. Cambio **título** a `View`.

   3. Haga clic en la primera casilla de verificación para modificar sus propiedades. Cambio **identificador** a `ID_VIEW_TOOLBAR` y **título** a `Toolbar`.

   4. Haga clic en la segunda casilla de verificación para modificar sus propiedades. Cambio **identificador** a `ID_VIEW_STATUS_BAR` y **título** a `Status Bar`.

2. Crear un panel denominado `Window` que tiene un botón de expansión. Cuando un usuario hace clic en el botón de expansión, un menú contextual muestra los tres comandos que ya están definidos en la aplicación Scribble.

   1. Desde el **cuadro de herramientas**, arrastre un **Panel** a la **inicio** categoría. A continuación, arrastre un **botón** al panel.

   2. Haga clic en el panel para modificar sus propiedades. Cambio **título** a `Window`.

   3. Haga clic en el botón. Cambio **título** a `Windows`, **claves** a `w`, **índice de imagen grande** a `1`, y **modo de división** para `False`. A continuación, haga clic en el botón de puntos suspensivos (**...** ) junto a **elementos de menú** para abrir el **Editor de elementos** cuadro de diálogo.

   4. Haga clic en **agregar** tres veces para agregar tres botones.

   5. Haga clic en el primer botón y, a continuación, cambiar **título** a `New Window`, y **identificador** a `ID_WINDOW_NEW`.

   6. Haga clic en el segundo botón y, a continuación, cambiar **título** a `Cascade`, y **identificador** a `ID_WINDOW_CASCADE`.

   7. Haga clic en el tercer botón y, a continuación, cambiar **título** a `Tile`, y **identificador** a `ID_WINDOW_TILE_HORZ`.

3. Guarde los cambios y, a continuación, compile y ejecute la aplicación. El **vista** y **ventana** paneles deben mostrarse. Haga clic en los botones para confirmar que funcionan correctamente.

[[Secciones](#top)]

##  <a name="addhelppanel"></a> Agregar un Panel de ayuda a la cinta de opciones

Ahora, puede asignar dos elementos de menú que se definen en la aplicación Scribble para botones de la cinta que se denominan **temas de Ayuda** y **acerca de Scribble**. Los botones se agregan a un nuevo panel denominado **ayuda**.

### <a name="to-add-a-help-panel"></a>Para agregar un panel de ayuda

1. Desde el **cuadro de herramientas**, arrastre un **Panel** a la **inicio** categoría. A continuación, arrastre dos **botones** al panel.

2. Haga clic en el panel para modificar sus propiedades. Cambio **título** a `Help`.

3. Haga clic en el primer botón. Cambio **título** a `Help Topics`, y **identificador** a `ID_HELP_FINDER`.

4. Haga clic en el segundo botón. Cambio **título** a `About Scribble...`, y **identificador** a `ID_APP_ABOUT`.

5. Guarde los cambios y, a continuación, compile y ejecute la aplicación. A **ayuda** se debe mostrar el panel que contiene dos botones de la cinta de opciones.

   > [!IMPORTANT]
   > Al hacer clic en el **temas de Ayuda** botón, la aplicación Scribble abre un archivo de Ayuda HTML (.chm) comprimido denominado *your_project_name*. archivo chm. Por lo tanto, si el proyecto no se denomina Scribble, debe cambiar el nombre del archivo de ayuda para el nombre del proyecto.

[[Secciones](#top)]

##  <a name="addpenpanel"></a> Agregar un Panel de lápiz a la cinta de opciones

Ahora, agregue un panel para mostrar botones que controlan el grosor y el color del lápiz. Este panel contiene una casilla de verificación que alterne entre lápices gruesas y finas. Su funcionalidad se parece al de la **línea gruesa** elemento de menú en la aplicación Scribble.

La aplicación original Scribble permite al usuario seleccionar el ancho del lápiz en un cuadro de diálogo que aparece cuando el usuario hace clic en **grosores de lápiz** en el menú. Dado que la barra de cinta tiene suficiente espacio para nuevos controles, puede reemplazar el cuadro de diálogo mediante dos cuadros combinados en la cinta de opciones. Un cuadro combinado ajusta el ancho del lápiz fino y el otro cuadro combinado ajusta el ancho del lápiz grueso.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Para agregar un panel y combinado cuadros de lápiz a la cinta de opciones

1. Desde el **cuadro de herramientas**, arrastre un **Panel** a la **inicio** categoría. A continuación, arrastre un **casilla de verificación** y dos **cuadros combinados** al panel.

2. Haga clic en el panel para modificar sus propiedades. Cambio **título** a `Pen`.

3. Haga clic en la casilla de verificación. Cambio **título** a `Use Thick`, y **identificador** a `ID_PEN_THICK_OR_THIN`.

4. Haga clic en el primer cuadro combinado. Cambio **título** a `Thin Pen`, **identificador** a `ID_PEN_THIN_WIDTH`, **texto** a `2`, **tipo** a `Drop List`, y **datos** a `1;2;3;4;5;6;7;8;9;`.

5. Haga clic en el segundo cuadro combinado. Cambio **título** a `Thick Pen`, **identificador** a `ID_PEN_THICK_WIDTH`, **texto** a `5`, **tipo** a `Drop List`, y **datos** a `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`.

6. Los cuadros combinados nueva no se corresponden con los elementos de menú existentes. Por lo tanto, debe crear un elemento de menú para cada opción de lápiz.

   1. En el **vista de recursos** ventana, abra el recurso de menú IDR_SCRIBBTYPE.

   2. Haga clic en **lápiz** para abrir el p**en** menú. A continuación, haga clic en **escriba aquí** y escriba `Thi&n Pen`.

   3. Haga clic en el texto que acaba de escribir para abrir la **propiedades** ventana y, a continuación, cambiar el identificador de propiedad para `ID_PEN_THIN_WIDTH`.

   4. También debe crear un controlador de eventos para cada elemento de menú de lápiz. Haga clic en el **este & brir n** elemento de menú que acaba de crear y, a continuación, haga clic en **Agregar controlador de eventos**. El **Asistente para controladores de eventos** se muestra.

   5. En el **lista de clases** cuadro en el asistente, seleccione **CScribbleDoc** y, a continuación, haga clic en **agregar y editar**. Esto crea un controlador de eventos denominado `CScribbleDoc::OnPenThinWidth`.

   6. Agregue el código siguiente a `CScribbleDoc::OnPenThinWidth`.

    ```cpp
    // Get a pointer to the ribbon bar
    CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
    ASSERT_VALID(pRibbon);

    // Get a pointer to the Thin Width combo box
    CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
    CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THIN_WIDTH));

    //Get the selected value
    int nCurSel = pThinComboBox->GetCurSel();
    if (nCurSel>= 0)
    {
        m_nThinWidth = atoi(pThinComboBox->GetItem(nCurSel));
    }
    
    // Create a new pen using the selected width
    ReplacePen();
    ```

7. A continuación, crear un menú de elemento y controladores de eventos para el lápiz grueso.

   1. En el **vista de recursos** ventana, abra el recurso de menú IDR_SCRIBBTYPE.

   2. Haga clic en **lápiz** para abrir el menú de lápiz. A continuación, haga clic en **escriba aquí** y escriba `Thic&k Pen`.

   3. Haga clic en el texto que acaba de escribir para mostrar el **propiedades** ventana. Cambiar la propiedad ID en `ID_PEN_THICK_WIDTH`.

   4. Haga clic en el **lápiz grueso** elemento de menú que acaba de crear y, a continuación, haga clic en **Agregar controlador de eventos**. El **Asistente para controladores de eventos** se muestra.

   5. En el **lista de clases** cuadro del asistente, seleccione **CScribbleDoc** y, a continuación, haga clic en **agregar y editar**. Esto crea un controlador de eventos denominado `CScribbleDoc::OnPenThickWidth`.

   6. Agregue el código siguiente a `CScribbleDoc::OnPenThickWidth`.

      ```cpp
      // Get a pointer to the ribbon bar
      CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
      ASSERT_VALID(pRibbon);

      CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
          CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
      // Get the selected value
      int nCurSel = pThickComboBox->GetCurSel();
      if (nCurSel>= 0)
      {
          m_nThickWidth = atoi(pThickComboBox->GetItem(nCurSel));
      }
      
      // Create a new pen using the selected width
      ReplacePen();
      ```

8. Guarde los cambios y, a continuación, compile y ejecute la aplicación. Deben mostrarse nuevos botones y cuadros combinados. Pruebe a usar ancho de lápiz diferente a mano alzada.

[[Secciones](#top)]

##  <a name="addcolorbutton"></a> Agregar un botón de Color en el Panel de lápiz

A continuación, agregue un [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) objeto que permite al usuario scribble en color.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>Para agregar un botón de color en el panel de lápiz

1. Antes de agregar el botón de color, crear un elemento de menú para él. En el **vista de recursos** ventana, abra el recurso de menú IDR_SCRIBBTYPE. Haga clic en el **lápiz** elemento de menú para abrir el menú de lápiz. A continuación, haga clic en **escriba aquí** y escriba `&Color`. Haga clic en el texto que acaba de escribir para mostrar el **propiedades** ventana. Cambie el identificador a `ID_PEN_COLOR`.

2. Ahora agregue el botón de color. Desde el **cuadro de herramientas**, arrastre un **botón de Color** a la **lápiz** panel.

3. Haga clic en el botón de color. Cambio **título** a `Color`, **identificador** a `ID_PEN_COLOR`, **SimpleLook** a `True`, **índice de imagen grande** a `1`, y **modo de división** a `False`.

4. Guarde los cambios y, a continuación, compile y ejecute la aplicación. El nuevo botón de color se debe mostrar en el **lápiz** panel. Sin embargo, no puede usarse porque no tiene todavía un controlador de eventos. Los pasos siguientes muestran cómo agregar un controlador de eventos para el botón de color.

[[Secciones](#top)]

##  <a name="addcolormember"></a> Agregar a un miembro de Color a la clase de documento

Dado que la aplicación original Scribble no tienen lápices de color, debe escribir una implementación para ellos. Para almacenar el color del lápiz del documento, agregue a un nuevo miembro a la clase de documento, `CscribbleDoc.`

### <a name="to-add-a-color-member-to-the-document-class"></a>Para agregar a un miembro de color a la clase de documento

1. En scribdoc.h, en la `CScribbleDoc` clase, busque la `// Attributes` sección. Agregue las siguientes líneas de código después de la definición de la `m_nThickWidth` miembro de datos.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

2. Cada documento que contiene una lista de los trazos que el usuario ya ha dibujado. Cada trazo se define mediante una `CStroke` objeto. La `CStroke` clase no incluye información sobre el color del lápiz. Por lo tanto, debe modificar la clase. En scribdoc.h, en la `CStroke` de clases, agregue las siguientes líneas de código después de la definición de la `m_nPenWidth` miembro de datos.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

3. En scribdoc.h, agregue un nuevo `CStroke` constructor cuyos parámetros especifican un ancho y color. Agregue la siguiente línea de código después de la `CStroke(UINT nPenWidth);` instrucción.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

4. En scribdoc.cpp, agregue la implementación del nuevo `CStroke` constructor. Agregue el código siguiente después de la implementación de la `CStroke::CStroke(UINT nPenWidth)` constructor.

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

5. Cambiar la segunda línea de la `CStroke::DrawStroke` método tal como se indica a continuación.

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

6. Establecer el color del lápiz predeterminado para la clase de documento. En scribdoc.cpp, agregue las siguientes líneas a `CScribbleDoc::InitDocument`, después la `m_nThickWidth = 5;` instrucción.

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

7. En scribdoc.cpp, cambie la primera línea de la `CScribbleDoc::NewStroke` método al siguiente.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

8. Cambie la última línea de la `CScribbleDoc::ReplacePen` método al siguiente.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

9. Ha agregado la `m_penColor` miembro en un paso anterior. Ahora, cree un controlador de eventos para el botón de color que establece al miembro.

   1. En el **vista de recursos** ventana, abra el recurso de menú IDR_SCRIBBTYPE.

   2. Haga clic en el **Color** elemento de menú y haga clic en **Agregar controlador de eventos**. El **Asistente para controladores de eventos** aparece.

   3. En el **lista de clases** cuadro en el asistente, seleccione **CScribbleDoc** y, a continuación, haga clic en el **agregar y editar** botón. Esto crea la `CScribbleDoc::OnPenColor` código auxiliar del controlador de eventos.

10. Reemplace el código auxiliar para el `CScribbleDoc::OnPenColor` controlador de eventos con el código siguiente.

   ```cpp
   void CScribbleDoc::OnPenColor()
   {
       // Change pen color to reflect color button's current selection
       CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
       ASSERT_VALID(pRibbon);

       CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
           CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

       m_penColor = pColorBtn->GetColor();
       // Create new pen using the selected color
       ReplacePen();
   }
   ```

11. Guarde los cambios y, a continuación, compile y ejecute la aplicación. Puede presionar el botón de color y cambiar el color del lápiz.

[[Secciones](#top)]

##  <a name="initpensave"></a> Inicializar lápices y guardar las preferencias

A continuación, inicialice el color y el ancho de los lápices. Por último, guardar y cargar un color de un archivo de dibujo.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Para inicializar los controles en la barra de cinta

1. Inicializar los lápices en la barra de cinta de opciones.

   Agregue el código siguiente a scribdoc.cpp, en la `CScribbleDoc::InitDocument` (método), después el `m_sizeDoc = CSize(200,200)` instrucción.

   ```cpp
   // Reset the ribbon UI to its initial values
   CMFCRibbonBar* pRibbon =
       ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
   ASSERT_VALID(pRibbon);

   CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
       CMFCRibbonColorButton,
       pRibbon->FindByID(ID_PEN_COLOR));

   // Set ColorButton to black
   pColorBtn->SetColor(RGB(0, 0, 0));

   CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THIN_WIDTH));

   // Set Thin pen combobox to 2
   pThinComboBox->SelectItem(1);

   CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THICK_WIDTH));

   // Set Thick pen combobox to 5
   pThickComboBox->SelectItem(0);
   ```

2. Guardar un color de dibujo a un archivo. Agregue la siguiente instrucción para scribdoc.cpp, en la `CStroke::Serialize` (método), después el `ar << (WORD)m_nPenWidth;` instrucción.

   ```cpp
   ar << (COLORREF)m_penColor;
    ```

3. Por último, cargue un color de un archivo de dibujo. Agregue la siguiente línea de código, en la `CStroke::Serialize` (método), después el `m_nPenWidth = w;` instrucción.

   ```cpp
   ar >> m_penColor;
   ```

4. Ahora a mano alzada en color y guarde el dibujo en un archivo.

[[Secciones](#top)]

## <a name="conclusion"></a>Conclusión

Se actualizó la aplicación Scribble de MFC. Use este tutorial como guía cuando modifique las aplicaciones existentes.

## <a name="see-also"></a>Vea también

[Tutoriales](../mfc/walkthroughs-mfc.md)  
[Tutorial: Actualizar la aplicación Scribble de MFC (parte 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)  
