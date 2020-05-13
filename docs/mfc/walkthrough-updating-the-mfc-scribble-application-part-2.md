---
title: 'Tutorial: Actualizar la aplicación Scribble de MFC (Parte 2)'
ms.date: 04/25/2019
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: bc204a152168accf3731eede8ca9ef960ab121d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360228"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Tutorial: Actualizar la aplicación Scribble de MFC (Parte 2)

[En la parte 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) de este tutorial se muestra cómo agregar una cinta de Office Fluent a la aplicación clásica de Scribble. Esta parte muestra cómo agregar paneles de la cinta de opciones y controles que los usuarios pueden usar en lugar de menús y comandos.

## <a name="prerequisites"></a>Prerrequisitos

[Ejemplos de Visual C++](../overview/visual-cpp-samples.md)

## <a name="sections"></a><a name="top"></a>Secciones

Esta parte del tutorial tiene las secciones siguientes:

- [Adición de nuevos paneles a la cinta de opciones](#addnewpanel)

- [Agregar un panel de ayuda a la cinta de opciones](#addhelppanel)

- [Agregar un panel de lápiz a la cinta de opciones](#addpenpanel)

- [Agregar un botón de color a la cinta de opciones](#addcolorbutton)

- [Agregar un miembro de color a la clase de documento](#addcolormember)

- [Inicialización de bolígrafos y preferencias de ahorro](#initpensave)

## <a name="adding-new-panels-to-the-ribbon"></a><a name="addnewpanel"></a>Adición de nuevos paneles a la cinta de opciones

Estos pasos muestran cómo agregar un panel **De** vista que contiene dos casillas de verificación que controlan la visibilidad de la barra de herramientas y la barra de estado, y también un panel **Ventana** que contiene un botón de división orientado verticalmente que controla la creación y disposición de ventanas de interfaz de varios documentos (MDI).

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Para agregar un panel Ver y un panel Ventana a la barra de la cinta de opciones

1. Cree un `View`panel denominado , que tenga dos casillas de verificación que alternan la barra de estado y la barra de herramientas.

   1. Desde el **cuadro de herramientas**, arrastre un **panel** a la categoría **Inicio.** A continuación, arrastre dos casillas de **verificación** al panel.

   1. Haga clic en el panel para modificar sus propiedades. Cambie **Caption** Subtítulo `View`a .

   1. Haga clic en la primera casilla de verificación para modificar sus propiedades. Cambie **ID** ID `ID_VIEW_TOOLBAR` a `Toolbar`y **Subtítulo** a .

   1. Haga clic en la segunda casilla de verificación para modificar sus propiedades. Cambie **ID** ID `ID_VIEW_STATUS_BAR` a `Status Bar`y **Subtítulo** a .

1. Cree un `Window` panel denominado que tenga un botón de división. Cuando un usuario hace clic en el botón de división, un menú contextual muestra tres comandos que ya están definidos en la aplicación Scribble.

   1. Desde el **cuadro de herramientas**, arrastre un **panel** a la categoría **Inicio.** A continuación, arrastre un **botón** al panel.

   1. Haga clic en el panel para modificar sus propiedades. Cambie **Caption** Subtítulo `Window`a .

   1. Haga clic en el botón. Cambie **Caption** Subtítulo `Windows`a `w`, **Claves** a `1`, índice de imagen **grande** a , y **Modo dividido** a `False`. A continuación, haga clic en los puntos suspensivos (**...**) **situados** junto a Elementos de menú para abrir el cuadro de diálogo **Editor de elementos.**

   1. Haga clic en **Agregar** tres veces para agregar tres botones.

   1. Haga clic en el primer `New Window`botón `ID_WINDOW_NEW`y, a continuación, cambie **Subtítulo** a , e **ID** a .

   1. Haga clic en el segundo `Cascade`botón `ID_WINDOW_CASCADE`y, a continuación, cambie **Subtítulo** a , e **ID** a .

   1. Haga clic en el tercer `Tile`botón `ID_WINDOW_TILE_HORZ`y, a continuación, cambie **Subtítulo** a , e **ID** a .

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. Se deben mostrar los paneles **Vista** y **Ventana.** Haga clic en los botones para confirmar que funcionan correctamente.

## <a name="adding-a-help-panel-to-the-ribbon"></a><a name="addhelppanel"></a>Agregar un panel de ayuda a la cinta de opciones

Ahora, puede asignar dos elementos de menú definidos en la aplicación Garabato a botones de la cinta de opciones denominados Temas de **ayuda** y **Acerca de Garabato**. Los botones se agregan a un nuevo panel denominado **Ayuda**.

### <a name="to-add-a-help-panel"></a>Para agregar un panel de ayuda

1. Desde el **cuadro de herramientas**, arrastre un **panel** a la categoría **Inicio.** A continuación, arrastre dos **botones** al panel.

1. Haga clic en el panel para modificar sus propiedades. Cambie **Caption** Subtítulo `Help`a .

1. Haga clic en el primer botón. Cambie **Caption** Subtítulo `Help Topics`a , `ID_HELP_FINDER`e **ID** a .

1. Haga clic en el segundo botón. Cambie **Caption** Subtítulo `About Scribble...`a , `ID_APP_ABOUT`e **ID** a .

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. Se debe mostrar un panel de **ayuda** que contiene dos botones de la cinta de opciones.

   > [!IMPORTANT]
   > Al hacer clic en el botón Temas de **ayuda,** la aplicación Scribble abre un archivo de ayuda HTML comprimido (.chm) denominado *your_project_name*.chm. Por lo tanto, si el proyecto no se denomina Scribble, debe cambiar el nombre del archivo de ayuda por el nombre del proyecto.

## <a name="adding-a-pen-panel-to-the-ribbon"></a><a name="addpenpanel"></a>Agregar un panel de lápiz a la cinta de opciones

Ahora, agregue un panel para mostrar botones que controlen el grosor y el color de la pluma. Este panel contiene una casilla de verificación que alterna entre plumas gruesas y delgadas. Su funcionalidad es similar a la del elemento de menú **Línea gruesa** de la aplicación Garabato.

La aplicación Scribble original permite al usuario seleccionar anchos de lápiz en un cuadro de diálogo que aparece cuando el usuario hace clic en **Anchos** de lápiz en el menú. Dado que la barra de la cinta de opciones tiene un amplio espacio para los nuevos controles, puede reemplazar el cuadro de diálogo mediante dos cuadros combinados en la cinta de opciones. Un cuadro combinado ajusta el ancho de la pluma delgada y el otro cuadro combinado ajusta el ancho de la pluma gruesa.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Para agregar un panel Pluma y cuadros combinados a la cinta de opciones

1. Desde el **cuadro de herramientas**, arrastre un **panel** a la categoría **Inicio.** A continuación, arrastre una casilla de **verificación** y dos **cuadros combinados** al panel.

1. Haga clic en el panel para modificar sus propiedades. Cambie **Caption** Subtítulo `Pen`a .

1. Haga clic en la casilla. Cambie **Caption** Subtítulo `Use Thick`a , `ID_PEN_THICK_OR_THIN`e **ID** a .

1. Haga clic en el primer cuadro combinado. Cambie **Caption** Subtítulo `Thin Pen`a `ID_PEN_THIN_WIDTH`, **ID** a `1;2;3;4;5;6;7;8;9;`, **Escriba** a `Drop List`, **Datos** a , y **Texto** a `2`.

1. Haga clic en el segundo cuadro combinado. Cambie **Caption** Subtítulo `Thick Pen`a `ID_PEN_THICK_WIDTH`, **ID** a `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`, **Escriba** a `Drop List`, **Datos** a , y **Texto** a `5`.

1. Los nuevos cuadros combinados no se corresponden con ningún elemento de menú existente, por lo que debe crear un elemento de menú para cada opción de lápiz.

   1. En la ventana **Vista** de recursos, abra el recurso de menú **IDR_SCRIBBTYPE.**

   1. Haga clic en **Pluma** para abrir el menú de plumillas. A **continuación,** haga `Thi&n Pen`clic en Escriba aquí y escriba .

   1. Haga clic con el botón derecho **Properties** en el texto que ha `ID_PEN_THIN_WIDTH`escrito para abrir la ventana Propiedades y, a continuación, cambie la propiedad ID a .

   1. Cree un controlador de eventos para cada elemento de menú de lápiz. Haga clic con el **botón derecho** en el elemento de menú Thi&n Pen que ha creado y, a continuación, haga clic en **Agregar controlador de eventos**. Se muestra el **Asistente para controladores** de eventos.

   1. En el cuadro de **lista Clase** del asistente, seleccione **CScribbleDoc** y, a continuación, haga clic en **Agregar y editar**. El comando crea un `CScribbleDoc::OnPenThinWidth`controlador de eventos denominado .

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

1. A continuación, cree un elemento de menú y controladores de eventos para el lápiz grueso.

   1. En la ventana **Vista** de recursos, abra el recurso de menú **IDR_SCRIBBTYPE.**

   1. Haga clic en **Pluma** para abrir el menú de plumillas. A **continuación,** haga `Thic&k Pen`clic en Escriba aquí y escriba .

   1. Haga clic con el botón derecho en el texto que ha escrito para mostrar la ventana **Propiedades.** Cambie la propiedad `ID_PEN_THICK_WIDTH`ID a .

   1. Haga clic con el botón derecho en el elemento de menú **Pluma gruesa** que ha creado y, a continuación, haga clic en Agregar controlador **de eventos**. Se muestra el **Asistente para controladores** de eventos.

   1. En el cuadro de **lista Clase** del asistente, seleccione **CScribbleDoc** y, a continuación, haga clic en **Agregar y editar**. El comando crea un `CScribbleDoc::OnPenThickWidth`controlador de eventos denominado .

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

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. Se deben mostrar nuevos botones y cuadros combinados. Intente usar diferentes anchos de pluma para garabatear.

## <a name="adding-a-color-button-to-the-pen-panel"></a><a name="addcolorbutton"></a>Adición de un botón de color al panel Pluma

A continuación, agregue un [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) objeto que permite al usuario garabatear en color.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>Para añadir un botón de color al panel Pluma

1. Antes de agregar el botón de color, cree un elemento de menú para él. En la ventana **Vista** de recursos, abra el recurso de menú **IDR_SCRIBBTYPE.** Haga clic en el elemento de menú **Pluma** para abrir el menú de plumillas. A **continuación,** haga `&Color`clic en Escriba aquí y escriba . Haga clic con el botón derecho en el texto que ha escrito para mostrar la ventana **Propiedades.** Cambie el identificador a `ID_PEN_COLOR`.

1. Ahora agregue el botón de color. En el **cuadro de herramientas**, arrastre un **botón** de color al panel **Pluma.**

1. Haga clic en el botón de color. Cambie **Caption** Subtítulo `Color`a `ID_PEN_COLOR`, **ID** `True`a , Simple **Look** to `False`, Large **Image Index** a `1`, y Split **Mode** a .

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. El nuevo botón de color debe mostrarse en el panel **Pluma.** Sin embargo, no se puede usar porque aún no tiene un controlador de eventos. Los pasos siguientes muestran cómo agregar un controlador de eventos para el botón de color.

## <a name="adding-a-color-member-to-the-document-class"></a><a name="addcolormember"></a>Agregar un miembro de color a la clase de documento

Dado que la aplicación Scribble original no tiene plumillas de color, debe escribir una implementación para ellos. Para almacenar el color del lápiz del documento, `CscribbleDoc`agregue un nuevo miembro a la clase de documento, .

### <a name="to-add-a-color-member-to-the-document-class"></a>Para agregar un miembro de color a la clase de documento

1. En scribdoc.h, `CScribbleDoc` en la `// Attributes` clase, busque la sección. Agregue las siguientes líneas de código `m_nThickWidth` después de la definición del miembro de datos.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. Cada documento contiene una lista de stokes que el usuario ya ha dibujado. Cada trazo se `CStroke` define mediante un objeto. La `CStroke` clase no incluye información sobre el color del lápiz, por lo que debe modificar la clase. En scribdoc.h, `CStroke` en la clase, agregue las siguientes `m_nPenWidth` líneas de código después de la definición del miembro de datos.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. En scribdoc.h, agregue `CStroke` un nuevo constructor cuyos parámetros especifiquen un ancho y un color. Agregue la siguiente línea `CStroke(UINT nPenWidth);` de código después de la instrucción.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. En scribdoc.cpp, agregue la `CStroke` implementación del nuevo constructor. Agregue el código siguiente después de la implementación del `CStroke::CStroke(UINT nPenWidth)` constructor.

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. Cambie la segunda `CStroke::DrawStroke` línea del método de la siguiente manera.

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. Establezca el color de lápiz predeterminado para la clase de documento. En scribdoc.cpp, agregue las `CScribbleDoc::InitDocument`siguientes `m_nThickWidth = 5;` líneas a , después de la instrucción.

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. En scribdoc.cpp, cambie la `CScribbleDoc::NewStroke` primera línea del método a la siguiente.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. Cambie la última `CScribbleDoc::ReplacePen` línea del método a la siguiente.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. Agregó `m_penColor` el miembro en un paso anterior. Ahora, cree un controlador de eventos para el botón de color que establece el miembro.

   1. En la ventana **Vista** de recursos, abra el recurso de menú IDR_SCRIBBTYPE.

   1. Haga clic con el botón derecho en el elemento de menú **Color** y haga clic en **Agregar controlador de eventos**. Aparece el **Asistente para controlador es** de eventos.

   1. En el cuadro de **lista Clase** del asistente, seleccione **CScribbleDoc** y, a continuación, haga clic en el botón **Agregar y editar.** El comando `CScribbleDoc::OnPenColor` crea el código auxiliar del controlador de eventos.

1. Reemplace el código `CScribbleDoc::OnPenColor` auxiliar del controlador de eventos por el código siguiente.

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

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. Ahora puede pulsar el botón de color y cambiar el color del lápiz.

## <a name="initializing-pens-and-saving-preferences"></a><a name="initpensave"></a>Inicialización de bolígrafos y preferencias de ahorro

A continuación, inicialice el color y el ancho de las plumas. Por último, guarde y cargue un dibujo de color desde un archivo.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Para inicializar controles en la barra de la cinta de opciones

1. Inicializar los bolígrafos en la barra de la cinta de opciones.

   Agregue el código siguiente a scribdoc.cpp, en el `CScribbleDoc::InitDocument` método, después de la `m_sizeDoc = CSize(200,200)` instrucción.

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

1. Guarde un dibujo de color en un archivo. Agregue la siguiente instrucción a scribdoc.cpp, en el `CStroke::Serialize` método, después de la `ar << (WORD)m_nPenWidth;` instrucción.

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. Por último, cargue un dibujo de color desde un archivo. Agregue la siguiente línea de `CStroke::Serialize` código, `m_nPenWidth = w;` en el método, después de la instrucción.

   ```cpp
   ar >> m_penColor;
   ```

1. Ahora garabatea en color y guarda el dibujo en un archivo.

## <a name="conclusion"></a>Conclusión

Ha actualizado la aplicación MFC Scribble. Utilice este tutorial como guía al modificar las aplicaciones existentes.

## <a name="see-also"></a>Consulte también

[Tutoriales](../mfc/walkthroughs-mfc.md)<br/>
[Tutorial: Actualizar la aplicación Scribble de MFC (parte 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
