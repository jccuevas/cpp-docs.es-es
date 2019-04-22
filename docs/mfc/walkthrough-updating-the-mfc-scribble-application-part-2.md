---
title: 'Tutorial: Actualizar la aplicación Scribble MFC (parte 2)'
ms.date: 09/20/2018
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: c22a11c54b1957c1d4ac735fe8cb577d9c483d35
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781710"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Tutorial: Actualizar la aplicación Scribble MFC (parte 2)

[Parte 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) de este tutorial ha mostrado cómo agregar una cinta de Office Fluent en el clásico Scribble de aplicación. Esta parte muestra cómo agregar paneles de cinta y los controles que los usuarios pueden usar en lugar de los menús y comandos.

## <a name="prerequisites"></a>Requisitos previos

[Ejemplos de Visual C++](../overview/visual-cpp-samples.md)

##  <a name="top"></a> Secciones

Esta parte del tutorial tiene las secciones siguientes:

- [Agregar nuevos paneles a la cinta de opciones](#addnewpanel)

- [Agregar un Panel de ayuda a la cinta de opciones](#addhelppanel)

- [Agregar un Panel de lápiz a la cinta de opciones](#addpenpanel)

- [Agregar un botón de Color a la cinta de opciones](#addcolorbutton)

- [Agregar a un miembro de Color a la clase de documento](#addcolormember)

- [Inicializando lápices y guardar preferencias](#initpensave)

##  <a name="addnewpanel"></a> Agregar nuevos paneles a la cinta de opciones

Estos pasos muestra cómo agregar un **vista** panel que contiene dos casillas de verificación que controlan la visibilidad de la barra de herramientas y la barra de estado, y también un **ventana** panel que contiene una división de orientación vertical botón que controla la creación y disposición de las ventanas de interfaz de múltiples documentos (MDI).

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Para agregar un panel de vista y el panel de ventana a la barra de cinta

1. Crear un panel denominado `View`, que tiene dos casillas de verificación Activar o desactivar la barra de estado y la barra de herramientas.

   1. Desde el **cuadro de herramientas**, arrastre un **Panel** a la **inicio** categoría. A continuación, arrastre dos **casillas** al panel.

   1. Haga clic en el panel para modificar sus propiedades. Cambio **título** a `View`.

   1. Haga clic en la primera casilla de verificación para modificar sus propiedades. Cambio **ID** a `ID_VIEW_TOOLBAR` y **título** a `Toolbar`.

   1. Haga clic en la segunda casilla de verificación para modificar sus propiedades. Cambio **ID** a `ID_VIEW_STATUS_BAR` y **título** a `Status Bar`.

1. Crear un panel denominado `Window` que tiene un botón de expansión. Cuando un usuario hace clic en el botón de expansión, un menú contextual muestra tres comandos que ya están definidos en la aplicación Scribble.

   1. Desde el **cuadro de herramientas**, arrastre un **Panel** a la **inicio** categoría. A continuación, arrastre un **botón** al panel.

   1. Haga clic en el panel para modificar sus propiedades. Cambio **título** a `Window`.

   1. Haga clic en el botón. Cambio **título** a `Windows`, **claves** a `w`, **índice de imagen grandes** a `1`, y **modo de división** para `False`. A continuación, haga clic en el botón de puntos suspensivos (**...** ) junto a **elementos de menú** para abrir el **Editor elementos** cuadro de diálogo.

   1. Haga clic en **agregar** tres veces para agregar tres botones.

   1. Haga clic en el primer botón y, a continuación, cambie **título** a `New Window`, y **ID** a `ID_WINDOW_NEW`.

   1. Haga clic en el segundo botón y, a continuación, cambie **título** a `Cascade`, y **ID** a `ID_WINDOW_CASCADE`.

   1. Haga clic en el tercer botón y, a continuación, cambie **título** a `Tile`, y **ID** a `ID_WINDOW_TILE_HORZ`.

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. El **vista** y **ventana** se deben mostrar los paneles. Haga clic en los botones para confirmar que funcionan correctamente.

##  <a name="addhelppanel"></a> Agregar un Panel de ayuda a la cinta de opciones

Ahora, puede asignar dos elementos de menú que se definen en la aplicación Scribble de botones de cinta de opciones que se denominan **temas de Ayuda** y **acerca de Scribble**. Los botones se agregan a un nuevo panel denominado **ayuda**.

### <a name="to-add-a-help-panel"></a>Para agregar un panel de ayuda

1. Desde el **cuadro de herramientas**, arrastre un **Panel** a la **inicio** categoría. A continuación, arrastre dos **botones** al panel.

1. Haga clic en el panel para modificar sus propiedades. Cambio **título** a `Help`.

1. Haga clic en el primer botón. Cambio **título** a `Help Topics`, y **ID** a `ID_HELP_FINDER`.

1. Haga clic en el segundo botón. Cambio **título** a `About Scribble...`, y **ID** a `ID_APP_ABOUT`.

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. Un **ayuda** se debe mostrar el panel que contiene dos botones de la cinta.

   > [!IMPORTANT]
   > Al hacer clic en el **temas de Ayuda** botón, la aplicación Scribble abre un archivo de Ayuda HTML (.chm) comprimido denominado *your_project_name*. archivo chm. Por lo tanto, si el proyecto no se denomina Scribble, debe cambiar el nombre del archivo de ayuda para el nombre del proyecto.

##  <a name="addpenpanel"></a> Agregar un Panel de lápiz a la cinta de opciones

Ahora, agregue un panel para mostrar botones que controlan el grosor y el color del lápiz. Este panel contiene una casilla de verificación que alterne entre gruesas y finas lápices. Su funcionalidad es similar al de la **línea gruesa** elemento de menú en la aplicación Scribble.

La aplicación original Scribble permite al usuario seleccionar el ancho del lápiz de un cuadro de diálogo que aparece cuando el usuario hace clic **lápiz anchos** en el menú. Dado que la barra de cinta tiene suficiente espacio para nuevos controles, puede reemplazar el cuadro de diálogo mediante el uso de dos cuadros combinados en la cinta de opciones. Un cuadro combinado ajusta el ancho del lápiz fino y el otro cuadro combinado ajusta el ancho del lápiz grueso.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Para agregar un panel y combinado cuadros de lápiz a la cinta de opciones

1. Desde el **cuadro de herramientas**, arrastre un **Panel** a la **inicio** categoría. A continuación, arrastre un **casilla** y dos **cuadros combinados** al panel.

1. Haga clic en el panel para modificar sus propiedades. Cambio **título** a `Pen`.

1. Haga clic en la casilla de verificación. Cambio **título** a `Use Thick`, y **ID** a `ID_PEN_THICK_OR_THIN`.

1. Haga clic en el primer cuadro combinado. Cambio **título** a `Thin Pen`, **ID** a `ID_PEN_THIN_WIDTH`, **tipo** a `Drop List`, **datos** a `1;2;3;4;5;6;7;8;9;`, y **texto** a `2`.

1. Haga clic en el segundo cuadro combinado. Cambio **título** a `Thick Pen`, **ID** a `ID_PEN_THICK_WIDTH`, **tipo** a `Drop List`, **datos** a `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`, y **texto** a `5`.

1. Los nuevos cuadros combinados no corresponden a los elementos de menú existentes, por lo que debe crear un elemento de menú para cada opción de lápiz.

   1. En el **vista de recursos** ventana, abra el **IDR_SCRIBBTYPE** recurso de menú.

   1. Haga clic en **lápiz** para abrir el menú de lápiz. A continuación, haga clic en **escriba aquí** y tipo `Thi&n Pen`.

   1. Haga clic en el texto que ha escrito para abrir el **propiedades** ventana y, a continuación, cambiar el identificador de propiedad para `ID_PEN_THIN_WIDTH`.

   1. Cree un controlador de eventos para cada elemento de menú lápiz. Haga clic en el **Thi a & brir n** elemento de menú que ha creado y, a continuación, haga clic en **Add Event Handler**. El **Asistente para controladores de eventos** se muestra.

   1. En el **clase lista** cuadro en el asistente, seleccione **CScribbleDoc** y, a continuación, haga clic en **agregar y editar**. El comando crea un controlador de eventos denominado `CScribbleDoc::OnPenThinWidth`.

   1. Agregue el código siguiente a `CScribbleDoc::OnPenThinWidth`.

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
            m_nThinWidth = atoi(CStringA(pThinComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. A continuación, cree un menú de elemento y controladores de eventos para la pluma gruesa.

   1. En el **vista de recursos** ventana, abra el **IDR_SCRIBBTYPE** recurso de menú.

   1. Haga clic en **lápiz** para abrir el menú de lápiz. A continuación, haga clic en **escriba aquí** y tipo `Thic&k Pen`.

   1. Haga clic en el texto que ha escrito para mostrar el **propiedades** ventana. Cambiar la propiedad ID en `ID_PEN_THICK_WIDTH`.

   1. Haga clic en el **pluma gruesa** elemento de menú que ha creado y, a continuación, haga clic en **Add Event Handler**. El **Asistente para controladores de eventos** se muestra.

   1. En el **clase lista** cuadro del asistente, seleccione **CScribbleDoc** y, a continuación, haga clic en **agregar y editar**. El comando crea un controlador de eventos denominado `CScribbleDoc::OnPenThickWidth`.

   1. Agregue el código siguiente a `CScribbleDoc::OnPenThickWidth`.

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
            m_nThickWidth = atoi(CStringA(pThickComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. Deben mostrarse nuevos botones y cuadros combinados. Pruebe a usar los anchos de pluma diferentes a mano alzada.

##  <a name="addcolorbutton"></a> Agregar un botón de Color en el Panel de lápiz

A continuación, agregue un [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) objeto que permite al usuario scribble en color.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>Para agregar un botón de color en el panel de lápiz

1. Antes de agregar el botón de color, cree un elemento de menú para él. En el **vista de recursos** ventana, abra el **IDR_SCRIBBTYPE** recurso de menú. Haga clic en el **lápiz** elemento de menú para abrir el menú de lápiz. A continuación, haga clic en **escriba aquí** y tipo `&Color`. Haga clic en el texto que ha escrito para mostrar el **propiedades** ventana. Cambie el identificador a `ID_PEN_COLOR`.

1. Ahora, agregue el botón de color. Desde el **cuadro de herramientas**, arrastre un **botón Color** a la **lápiz** panel.

1. Haga clic en el botón de color. Cambio **título** a `Color`, **ID** a `ID_PEN_COLOR`, **Simple vistazo** a `True`, **índice de imagen grandes** a `1`, y **modo de división** a `False`.

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. El nuevo botón de color debe mostrarse en el **lápiz** panel. Sin embargo, no puede utilizarse porque aún no tiene un controlador de eventos. Los pasos siguientes muestran cómo agregar un controlador de eventos para el botón de color.

##  <a name="addcolormember"></a> Agregar a un miembro de Color a la clase de documento

Puesto que la aplicación original Scribble no tiene los lápices de color, debe escribir una implementación para ellos. Para almacenar el color del lápiz del documento, agregue un nuevo miembro a la clase de documento, `CscribbleDoc`.

### <a name="to-add-a-color-member-to-the-document-class"></a>Para agregar a un miembro de color a la clase de documento

1. En scribdoc.h, en el `CScribbleDoc` clase, busque el `// Attributes` sección. Agregue las siguientes líneas de código después de la definición de la `m_nThickWidth` miembro de datos.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. Cada documento contiene una lista de los trazos que el usuario haya dibujado. Cada trazo se define mediante un `CStroke` objeto. La `CStroke` clase no incluye información sobre el color del lápiz, por lo que debe modificar la clase. En scribdoc.h, en el `CStroke` de clases, agregue las siguientes líneas de código después de la definición de la `m_nPenWidth` miembro de datos.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. En scribdoc.h, agregue un nuevo `CStroke` constructor cuyos parámetros que especifican un ancho y color. Agregue la siguiente línea de código tras el `CStroke(UINT nPenWidth);` instrucción.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. En scribdoc.cpp, agregue la implementación del nuevo `CStroke` constructor. Agregue el código siguiente después de la implementación de la `CStroke::CStroke(UINT nPenWidth)` constructor.

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. Cambiar la segunda línea de la `CStroke::DrawStroke` método tal como se indica a continuación.

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. Establecer el color del lápiz predeterminado para la clase de documento. En scribdoc.cpp, agregue las líneas siguientes al `CScribbleDoc::InitDocument`, después el `m_nThickWidth = 5;` instrucción.

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. En scribdoc.cpp, cambie la primera línea de la `CScribbleDoc::NewStroke` método a la siguiente.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. Cambiar la última línea de la `CScribbleDoc::ReplacePen` método a la siguiente.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. Ha agregado el `m_penColor` miembro en un paso anterior. Ahora, cree un controlador de eventos para el botón de color que establece al miembro.

   1. En el **vista de recursos** ventana, abra el recurso de menú IDR_SCRIBBTYPE.

   1. Haga clic en el **Color** elemento de menú y haga clic en **Add Event Handler**. El **Asistente para controladores de eventos** aparece.

   1. En el **clase lista** cuadro en el asistente, seleccione **CScribbleDoc** y, a continuación, haga clic en el **agregar y editar** botón. El comando crea el `CScribbleDoc::OnPenColor` código auxiliar del controlador de eventos.

1. Reemplace el código auxiliar para el `CScribbleDoc::OnPenColor` controlador de eventos con el código siguiente.

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

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. Ahora puede presionar el botón de color y cambiar el color del lápiz.

##  <a name="initpensave"></a> Inicializando lápices y guardar preferencias

A continuación, inicialice el color y ancho de las plumas. Por último, guardar y cargar un color de dibujo de un archivo.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Para inicializar los controles en la barra de cinta

1. Inicializar los lápices en la barra de cinta de opciones.

   Agregue el código siguiente al scribdoc.cpp, en el `CScribbleDoc::InitDocument` método, después el `m_sizeDoc = CSize(200,200)` instrucción.

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

1. Guardar un color de dibujo a un archivo. Agregue la siguiente instrucción para scribdoc.cpp, en el `CStroke::Serialize` método, después el `ar << (WORD)m_nPenWidth;` instrucción.

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. Por último, cargue un color de dibujo de un archivo. Agregue la siguiente línea de código, en el `CStroke::Serialize` método, después el `m_nPenWidth = w;` instrucción.

   ```cpp
   ar >> m_penColor;
   ```

1. Ahora a mano alzada en color y guardar el dibujo en un archivo.

## <a name="conclusion"></a>Conclusión

Ha actualizado la aplicación Scribble de MFC. Use este tutorial como guía cuando modifique las aplicaciones existentes.

## <a name="see-also"></a>Vea también

[Tutoriales](../mfc/walkthroughs-mfc.md)<br/>
[Tutorial: Actualizar la aplicación Scribble MFC (parte 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
