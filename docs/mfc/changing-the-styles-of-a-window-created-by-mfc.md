---
title: "Cambiar los estilos de una ventana creada por MFC | Microsoft Docs"
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
  - "CFrameWnd (clase), estilos de ventanas"
  - "ventanas secundarias, estilos"
  - "CMainFrame (clase)"
  - "CMDIChildWnd (clase), cambiar estilos de ventana"
  - "CREATESTRUCT (macro)"
  - "estilo de ancho predeterminado"
  - "valores predeterminados [C++], estilo de ventana"
  - "MDI [C++], estilos de ventanas"
  - "MFC [C++], ventanas"
  - "estilo de interfaz de varios documentos"
  - "PreCreateWindow (método), cambiar estilos de ventana"
  - "PreCreateWindow (método), estilos de ventanas"
  - "interfaz de único documento (SDI), cambiar atributos de ventana"
  - "interfaz de único documento (SDI), estilo"
  - "estilos, ventanas"
  - "estilos de ventanas [C++]"
  - "ventanas [C++], MFC"
  - "WS_OVERLAPPEDWINDOW (macro)"
ms.assetid: 77fa4f03-96b4-4687-9ade-41e46f7e4b0a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Cambiar los estilos de una ventana creada por MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En la versión de la función de `WinMain` , MFC registra varias clases de ventana estándar para usted.  Porque no modifica normalmente `WinMain`de MFC, la función no proporciona ninguna posibilidad de cambiar los estilos de ventana predeterminado de MFC.  En este artículo se explica cómo puede cambiar los estilos de una clase de ventana en preregistered en una aplicación existente.  
  
##  <a name="_core_changing_styles_in_a_new_mfc_application"></a> Cambiar estilos en una aplicación MFC New  
 Si utiliza Visual C\+\+ 2.0 o posterior, puede cambiar los estilos de ventana predeterminadas en el Asistente para aplicaciones al crear la aplicación.  En las características página de la interfaz de usuario del Asistente para aplicaciones, puede cambiar los estilos de la ventana de marco principal y las ventanas MDI secundarias.  Para cualquier tipo de la ventana, puede especificar el grosor del marco \(general o enrarecer\) y cualquiera de los siguientes:  
  
-   Si la ventana tiene Minimizar o controles Maximizar.  
  
-   Si aparece la ventana minimizada inicialmente, maximizar, o ninguno.  
  
 Para las ventanas de marco principal, también puede especificar si la ventana tiene un menú sistema.  Para las ventanas MDI secundarias, puede especificar si la ventana admite paneles splitter.  
  
##  <a name="_core_changing_styles_in_an_existing_application"></a> Cambiar estilos en una aplicación existente  
 Si cambia los atributos de la ventana en una aplicación existente, siga las instrucciones del resto de este artículo en su lugar.  
  
 Para cambiar los atributos de ventana predeterminados utilizados por una aplicación creada de marco con el Asistente para aplicaciones, reemplace la función miembro virtual de [PreCreateWindow](../Topic/CWnd::PreCreateWindow.md) de la ventana.  `PreCreateWindow` permite que una aplicación para tener acceso al proceso de creación administrado normalmente internamente por la clase de [CDocTemplate](../mfc/reference/cdoctemplate-class.md) .  El marco de trabajo llama a `PreCreateWindow` justo antes de crear la ventana.  Modificar la estructura de [CREATESTRUCT](../mfc/reference/createstruct-structure.md) pasada a `PreCreateWindow`, la aplicación puede cambiar los atributos utilizados para crear la ventana.  Por ejemplo, para asegurarse de que una ventana no utilice una leyenda, utilice la operación bit a bit siguiente:  
  
 [!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/CPP/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]  
  
 La aplicación de ejemplo de [CTRLBARS](../top/visual-cpp-samples.md) muestra esta técnica para cambiar los atributos de la ventana.  Dependiendo de lo que cambia la aplicación en `PreCreateWindow`, puede ser necesario a la implementación de la clase base de la función.  
  
 La siguiente discusión cubre el caso SDI y [Caso de MDI](#_core_the_mdi_case).  
  
##  <a name="_core_the_sdi_case"></a> El caso SDI  
 En una aplicación de \(SDI\) de interfaz de un único documento, el estilo de ventana predeterminada en el marco es una combinación de los estilos de **WS\_OVERLAPPEDWINDOW** y de **FWS\_ADDTOTITLE** .  **FWS\_ADDTOTITLE** es un estilo MFC\- específico que indica al marco para agregar el título del documento a la leyenda de la ventana.  Para cambiar los atributos de la ventana en una aplicación SDI, reemplace la función de `PreCreateWindow` en la clase derivada de `CFrameWnd` \(que los nombres `CMainFrame`del Asistente para aplicaciones\).  Por ejemplo:  
  
 [!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/CPP/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]  
  
 Este código crea una ventana de marco principal sin Minimizar y los botones Maximizar y sin borde importante.  La ventana se centra inicialmente en la pantalla.  
  
##  <a name="_core_the_mdi_case"></a> El caso de MDI  
 Un poco más trabajo se requiere para cambiar el estilo de ventana de ventana secundaria en una aplicación de \(MDI\) de interfaz de múltiples documentos.  De forma predeterminada, una aplicación creada MDI con el Asistente para aplicaciones utiliza la clase de [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) predeterminado definida en MFC.  Para cambiar el estilo de ventana de una ventana MDI secundaria, debe derivar una nueva clase de `CMDIChildWnd` y reemplazar todas las referencias a `CMDIChildWnd` en el proyecto con referencias a la nueva clase.  Probablemente, la única referencia a `CMDIChildWnd` en la aplicación se encuentra en la función miembro de `InitInstance` de la aplicación.  
  
 El estilo de ventana predeterminada utilizada en una aplicación MDI es una combinación de los estilos de **WS\_CHILD**, de **WS\_OVERLAPPEDWINDOW**, y de **FWS\_ADDTOTITLE** .  Para cambiar los atributos de la ventana de las ventanas secundarias de una aplicación MDI, reemplace la función de [PreCreateWindow](../Topic/CWnd::PreCreateWindow.md) en la clase derivada de `CMDIChildWnd`.  Por ejemplo:  
  
 [!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/CPP/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]  
  
 Este código crea las ventanas secundarias MDI sin un botón de maximizar.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Estilos de Windows](../mfc/reference/window-styles.md)  
  
-   [Estilos de la Cuadro\-ventana](../mfc/frame-window-styles-cpp.md)  
  
-   [\<caps:sentence id\="tgt44" sentenceid\="26254917059da4aba50f886a6c5db931" class\="tgtSentence"\>Estilos de ventana\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms632600)  
  
## Vea también  
 [Estilos de ventana de marco](../mfc/frame-window-styles-cpp.md)