---
title: "Tutorial: Actualizar la aplicaci&#243;n Scribble de MFC (Parte 2) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tutoriales [C++]"
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
caps.latest.revision: 36
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# Tutorial: Actualizar la aplicaci&#243;n Scribble de MFC (Parte 2)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[Parte 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) de este tutorial ha mostrado cómo agregar una cinta de opciones de Office Fluent a la aplicación clásica scribble.  Esta parte muestra cómo agregar paneles y controles de la cinta de opciones que los usuarios pueden utilizar en lugar de menús y comandos.  
  
## Requisitos previos  
 [Ejemplos de Visual C\+\+](../top/visual-cpp-samples.md)  
  
##  <a name="top"></a> Secciones  
 Esta parte del tutorial tiene las secciones siguientes:  
  
-   [Paneles de Nuevo a la cinta de opciones](#addNewPanel)  
  
-   [Agregar un panel de Ayuda a la cinta de opciones](#addHelpPanel)  
  
-   [Agregar un panel de lápiz a la cinta de opciones](#addPenPanel)  
  
-   [Agregar un botón de color para la cinta de opciones](#addColorButton)  
  
-   [Agregar un miembro de color para la clase document](#addColorMember)  
  
-   [Lápices que inicializan y guardar preferencias](#initPenSave)  
  
##  <a name="addNewPanel"></a> Paneles de Nuevo a la cinta de opciones  
 Estos pasos se muestra cómo agregar un panel de **Visualización** que contiene dos casillas que controlan la visibilidad de la barra de herramientas y de la barra de estado, y también un panel de **Ventana** que contiene un botón de expansión verticalmente orientado a objetos que controla la creación y la organización de ventanas de \(MDI\) de interfaz de múltiples documentos.  
  
#### Para agregar un panel de la vista y el panel de la ventana a la barra de la cinta de opciones  
  
1.  Cree un panel denominado `Visualización`, que tiene dos casillas que alternen la barra de estado y la barra de herramientas.  
  
    1.  De **Cuadro de herramientas**, arrastre **Panel** a la categoría de **Domicilio** .  A continuación arrastre dos **Casillas** al panel.  
  
    2.  Haga clic en el panel para modificar sus propiedades.  Cambio **caption** a `Visualización`.  
  
    3.  Haga clic en la primera casilla para modificar sus propiedades.  Cambie **Id** a `ID_VIEW_TOOLBAR` y **caption** a `Toolbar`.  
  
    4.  Haga clic en la segunda casilla para modificar sus propiedades.  Cambie **Id** a `ID_VIEW_STATUS_BAR` y **caption** a `Barra de estado`.  
  
2.  Cree un panel denominado `Ventana` que tenga un botón de expansión.  Cuando un usuario hace clic en el botón de expansión, se muestra un menú contextual tres comandos que ya están definidos en la aplicación scribble.  
  
    1.  De **Cuadro de herramientas**, arrastre **Panel** a la categoría de **Domicilio** .  A continuación **Button** arrastre al panel.  
  
    2.  Haga clic en el panel para modificar sus propiedades.  Cambio **caption** a `Ventana`.  
  
    3.  Haga clic en el botón.  Cambie **caption** a `Ventanas`, **Teclas** a `v`, **Índice grande de la imagen** a `1`, y **Modo dividido** a `False`.  Haga clic en los puntos suspensivos \(**...**\) junto a **Elementos de menú** para abrir el cuadro de diálogo **Editor de elementos** .  
  
    4.  Haga clic en **Add** tres veces para agregar tres botones.  
  
    5.  Haga clic en el primer botón y después cambie **caption** a `Nueva ventana`, y **Id** a `ID_WINDOW_NEW`.  
  
    6.  Haga clic en el segundo botón y después cambie **caption** a `Cascada`, y **Id** a `ID_WINDOW_CASCADE`.  
  
    7.  Haga clic en el tercer botón y después cambie **caption** a `Mosaico`, y **Id** a `ID_WINDOW_TILE_HORZ`.  
  
3.  Guarde los cambios y, a continuación, compile y ejecute la aplicación.  Los paneles de **Visualización** y de **Ventana** deben mostrarse.  Haga clic en los botones para confirmar que funcionan correctamente.  
  
 \[[Secciones](#top)\]  
  
##  <a name="addHelpPanel"></a> Agregar un panel de Ayuda a la cinta de opciones  
 Ahora, puede asignar dos elementos de menú definidos en la aplicación scribble a los botones de la cinta que se denominan **Temas de Ayuda** y **Sobre scribble**.  Los botones se agregan a un nuevo panel denominado **Ay&uda**.  
  
#### Para agregar un panel de Ayuda  
  
1.  De **Cuadro de herramientas**, arrastre **Panel** a la categoría de **Domicilio** .  A continuación arrastre dos **Botones** al panel.  
  
2.  Haga clic en el panel para modificar sus propiedades.  Cambio **caption** a `Ay&uda`.  
  
3.  Haga clic en el primer botón.  Cambio **caption** a `Temas de Ayuda`, y **Id** a `ID_HELP_FINDER`.  
  
4.  Haga clic en el segundo botón.  Cambio **caption** a `Sobre scribble…`, y **Id** a `ID_APP_ABOUT`.  
  
5.  Guarde los cambios y, a continuación, compile y ejecute la aplicación.  Un panel de **Ay&uda** que contiene dos botones de cinta debe mostrar.  
  
    > [!IMPORTANT]
    >  Al hacer clic en el botón de **Temas de Ayuda** , la aplicación scribble abra HTML comprimido \(.chm\) *your\_project\_name*denominado archivo de ayuda .chm.  Por consiguiente, si el proyecto no se denomina scribble, debe cambiar el nombre del archivo de ayuda en el nombre del proyecto.  
  
 \[[Secciones](#top)\]  
  
##  <a name="addPenPanel"></a> Agregar un panel de lápiz a la cinta de opciones  
 Ahora, agregue un panel a los botones de la pantalla que controlan el grosor y el color del lápiz.  Este panel contiene una casilla que alterna los lápices entre gruesos y precisión.  Su funcionalidad se parece al del elemento de menú de **Línea gruesa** en la aplicación scribble.  
  
 La aplicación original scribble permite al usuario seleccionar el ancho del lápiz de un cuadro de diálogo que aparece cuando el usuario hace clic en **Ancho del lápiz** en el menú.  Dado que la barra de la cinta de opciones tenga espacio suficiente para los nuevos controles, puede reemplazar el cuadro de diálogo mediante dos cuadros combinados de la cinta de opciones.  Un cuadro combinado contiene el ancho del lápiz preciso y el otro cuadro combinado contiene el ancho del lápiz general.  
  
#### Para agregar un panel y los cuadros combinados de lápiz a la cinta de opciones  
  
1.  De **Cuadro de herramientas**, arrastre **Panel** a la categoría de **Domicilio** .  A continuación arrastre **Casilla** y dos **Cuadros combinados** al panel.  
  
2.  Haga clic en el panel para modificar sus propiedades.  Cambio **caption** a `Lápiz`.  
  
3.  Haga clic en la casilla.  Cambio **caption** a `Uso densamente`, y **Id** a `ID_PEN_THICK_OR_THIN`.  
  
4.  Haga clic en el primer cuadro combinado.  Cambio **caption** a `Delgada el lápiz`, a **Id** a `ID_PEN_THIN_WIDTH`, a **Texto** a `2`, a **Tipo** a `Drop List`, y a **datos** a `1; 2; 3; 4; 5; 6; 7; 8; 9;`.  
  
5.  Haga clic en el segundo cuadro combinado.  Cambio **caption** a `Lápiz generales`, a **Id** a `ID_PEN_THICK_WIDTH`, a **Texto** a `5`, a **Tipo** a `Drop List`, y a **datos** a `5; 6; 7; 8; 9; 10; 11; 12; 13; 14; 15; 16; 17; 18; 19; 20;`.  
  
6.  Los nuevos cuadros combinados no corresponden a los elementos de menú existente.  Por consiguiente, debe crear un elemento de menú para cada opción de lápiz.  
  
    1.  En la ventana de **vista de recursos** , abra el recurso de menú de IDR\_SCRIBBTYPE.  
  
    2.  Haga clic en **Lápiz** para abrir el menú de**es** de p.  Haga clic en **Escriba aquí** y escriba `Thi&lápiz n`.  
  
    3.  Haga clic con el botón secundario en el texto que acaba de escribir para abrir la ventana de **Propiedades** , y cambie la propiedad ID en `ID_PEN_THIN_WIDTH`.  
  
    4.  También debe crear un controlador para cada elemento de menú del lápiz.  Haga clic con el botón secundario en el elemento de menú de **Thi&lápiz n** recién creada y haga clic en **Agregar controlador de eventos**.  Se muestra **Asistente para controladores de eventos** .  
  
    5.  En el cuadro de **Lista de clase** en el asistente, seleccione **CScribbleDoc** y haga clic en **Agregar y editar**.  Esto crea un controlador de eventos denominado `CScribbleDoc::OnPenThinWidth`.  
  
    6.  Agregue el código siguiente a `CScribbleDoc::OnPenThinWidth`.  
  
        ```  
        // Get a pointer to the ribbon bar  
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();  
        ASSERT_VALID(pRibbon);  
        // Get a pointer to the Thin Width combo box  
        CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(  
           CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THIN_WIDTH));  
        //Get the selected value  
        int nCurSel = pThinComboBox->GetCurSel();  
        if (nCurSel >= 0)  
        {  
           m_nThinWidth = atoi(pThinComboBox->GetItem(nCurSel));  
        }  
        // Create a new pen using the selected width  
        ReplacePen();    
        ```  
  
7.  A continuación, cree un elemento de menú y controladores de eventos para el lápiz general.  
  
    1.  En la ventana de **vista de recursos** , abra el recurso de menú de IDR\_SCRIBBTYPE.  
  
    2.  Haga clic en **Lápiz** para abrir el menú del lápiz.  Haga clic en **Escriba aquí** y escriba `Thic&lápiz de k`.  
  
    3.  Haga clic con el botón secundario en el texto que acaba de escribir para mostrar la ventana de **Propiedades** .  Cambie la propiedad ID en `ID_PEN_THICK_WIDTH`.  
  
    4.  Haga clic con el botón secundario en el elemento de menú de **Lápiz generales** recién creada y haga clic en **Agregar controlador de eventos**.  Se muestra **Asistente para controladores de eventos** .  
  
    5.  En el cuadro de **Lista de clase** del asistente, seleccione **CScribbleDoc** y haga clic en **Agregar y editar**.  Esto crea un controlador de eventos denominado `CScribbleDoc::OnPenThickWidth`.  
  
    6.  Agregue el código siguiente a `CScribbleDoc::OnPenThickWidth`.  
  
        ```  
        // Get a pointer to the ribbon bar  
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();  
        ASSERT_VALID(pRibbon);  
        CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(  
           CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));  
        // Get the selected value  
        int nCurSel = pThickComboBox->GetCurSel();  
        if (nCurSel >= 0)  
        {  
           m_nThickWidth = atoi(pThickComboBox->GetItem(nCurSel));  
        }  
        // Create a new pen using the selected width  
        ReplacePen();  
        ```  
  
8.  Guarde los cambios y, a continuación, compile y ejecute la aplicación.  Los nuevos botones y cuadros combinados deben mostrarse.  Intente usar diferentes anchos del pincel a garabatear.  
  
 \[[Secciones](#top)\]  
  
##  <a name="addColorButton"></a> Agregar un botón de color al panel del lápiz  
 A continuación, agregue un objeto de [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) que permite al usuario garabatear de color.  
  
#### Para agregar un botón de color al panel del lápiz  
  
1.  Antes de agregar el botón de color, cree un elemento de menú para él.  En la ventana de **vista de recursos** , abra el recurso de menú de IDR\_SCRIBBTYPE.  Haga clic en el elemento de menú de **Lápiz** para abrir el menú del lápiz.  Haga clic en **Escriba aquí** y escriba `&Color`.  Haga clic con el botón secundario en el texto que acaba de escribir para mostrar la ventana de **Propiedades** .  Cambie el identificador a `ID_PEN_COLOR`.  
  
2.  Ahora agregue el botón de color.  De **Cuadro de herramientas**, arrastre **Botón Color** al panel de **Lápiz** .  
  
3.  Haga clic en el botón de color.  Cambie **caption** a `Color`, **Id** a `ID_PEN_COLOR`, **SimpleBusque** a `VERDADERO`, **Índice grande de la imagen** a `1`, y **Modo dividido** a `False`.  
  
4.  Guarde los cambios y, a continuación, compile y ejecute la aplicación.  El nuevo botón de color se debería mostrar en el panel de **Lápiz** .  Sin embargo, no puede utilizar porque todavía no tiene un controlador de eventos.  Los pasos siguientes se muestra cómo agregar un controlador de eventos para el botón de color.  
  
 \[[Secciones](#top)\]  
  
##  <a name="addColorMember"></a> Agregar un miembro de color para la clase document  
 Dado que la aplicación original scribble no tiene lápices color, debe escribir una implementación para ellos.  Para almacenar el color del lápiz del documento, agregue un nuevo miembro a la clase document, `CscribbleDoc.`  
  
#### Para agregar un miembro de color para la clase document  
  
1.  En scribdoc.h, en la clase de `CScribbleDoc` , busque la sección de `// Attributes` .  Agregue las siguientes líneas de código después de la definición de miembros de datos de `m_nThickWidth` .  
  
    ```  
    // Current pen color  
    COLORREF   m_penColor;  
    ```  
  
2.  Cada documento contiene una lista de alimenta que el usuario ha dibujado.  Cada trazo se define como un objeto de `CStroke` .  La clase de `CStroke` no incluye información sobre el color del lápiz.  Por consiguiente, debe modificar la clase.  En scribdoc.h, en la clase de `CStroke` , agregue las siguientes líneas de código después de la definición de miembros de datos de `m_nPenWidth` .  
  
    ```  
    // Pen color for the stroke  
    COLORREF   m_penColor;  
    ```  
  
3.  En scribdoc.h, agregue un nuevo constructor de `CStroke` cuyos parámetros especifican un ancho y color.  Agregue la siguiente línea de código después de la instrucción de `CStroke(UINT nPenWidth);` .  
  
    ```  
    CStroke(UINT nPenWidth, COLORREF penColor);  
    ```  
  
4.  En scribdoc.cpp, agregue la implementación del nuevo constructor de `CStroke` .  Agregue el código siguiente después de la implementación de constructor de `CStroke::CStroke(UINT nPenWidth)` .  
  
    ```  
    // Constructor that uses the document's current width and color  
    CStroke::CStroke(UINT nPenWidth, COLORREF penColor)  
    {  
       m_nPenWidth = nPenWidth;  
       m_penColor = penColor;  
       m_rectBounding.SetRectEmpty();  
    }  
    ```  
  
5.  Cambie la segunda línea del método de `CStroke::DrawStroke` como sigue.  
  
    ```  
    if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))  
    ```  
  
6.  Establezca el color del lápiz predeterminado para la clase del documento.  En scribdoc.cpp, agregue las líneas siguientes a `CScribbleDoc::InitDocument`, después de la instrucción de `m_nThickWidth = 5;` .  
  
    ```  
    // default pen color is black  
    m_penColor = RGB(0,0,0);   
    ```  
  
7.  En scribdoc.cpp, cambie la primera línea del método de `CScribbleDoc::NewStroke` al siguiente.  
  
    ```  
    CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);  
    ```  
  
8.  Cambie la última línea del método de `CScribbleDoc::ReplacePen` al siguiente.  
  
    ```  
    m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);  
    ```  
  
9. Agregó al miembro de `m_penColor` en un paso anterior.  Ahora, cree un controlador de eventos para el botón de color que establezca el miembro.  
  
    1.  En la ventana de **vista de recursos** , abra el recurso de menú de IDR\_SCRIBBTYPE.  
  
    2.  Haga clic con el botón secundario en el elemento de menú y haga clic en **Agregar controlador de eventos...**de **Color** .  **Asistente para controladores de eventos** Aparece.  
  
    3.  En el cuadro de **Lista de clase** en el asistente, seleccione **CScribbleDoc** y haga clic en el botón de **Agregar y editar** .  Esto crea el código auxiliar del controlador de eventos `CScribbleDoc::OnPenColor` .  
  
10. Reemplace el código auxiliar para el controlador de eventos `CScribbleDoc::OnPenColor` con el código siguiente.  
  
    ```  
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
  
11. Guarde los cambios y, a continuación, compile y ejecute la aplicación.  Debe poder presionar el botón de color y cambiar el color del lápiz.  
  
 \[[Secciones](#top)\]  
  
##  <a name="initPenSave"></a> Lápices que inicializan y guardar preferencias  
 A continuación, inicializa el color y el ancho de los lápices.  Finalmente, guardado y carga un gráfico de color de un archivo.  
  
#### Para inicializar los controles de la barra de la cinta de opciones  
  
1.  Inicializa los lápices en la barra de la cinta de opciones.  
  
     Agregue el código siguiente a scribdoc.cpp, en el método de `CScribbleDoc::InitDocument` , después de la instrucción de `m_sizeDoc = CSize(200,200)` .  
  
    ```  
    // Reset the ribbon UI to its initial values  
    CMFCRibbonBar* pRibbon =   
       ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();  
    ASSERT_VALID(pRibbon);  
    CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(  
       CMFCRibbonColorButton,   
       pRibbon->FindByID(ID_PEN_COLOR));  
    // Set ColorButton to black  
    pColorBtn->SetColor(RGB(0,0,0));    
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
  
2.  Guardar un gráfico de color en un archivo.  Agregue la instrucción siguiente a scribdoc.cpp, en el método de `CStroke::Serialize` , después de la instrucción de `ar << (WORD)m_nPenWidth;` .  
  
    ```  
    ar << (COLORREF)m_penColor;  
    ```  
  
3.  Finalmente, cargue un gráfico de color de un archivo.  Agregue la siguiente línea de código, en el método de `CStroke::Serialize` , después de la instrucción de `m_nPenWidth = w;` .  
  
    ```  
    ar >> m_penColor;  
    ```  
  
4.  Ahora scribble de color y guarde el gráfico en un archivo.  
  
 \[[Secciones](#top)\]  
  
## Conclusión  
 Se ha actualizado la aplicación scribble de MFC.  Utilice este tutorial como guía al modificar las aplicaciones existentes.  
  
## Vea también  
 [Tutoriales](../mfc/walkthroughs-mfc.md)   
 [Tutorial: Actualizar la aplicación Scribble de MFC \(Parte 1\)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)