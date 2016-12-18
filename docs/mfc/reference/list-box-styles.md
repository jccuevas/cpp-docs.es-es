---
title: "Estilos de cuadro de lista | Microsoft Docs"
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
  - "LBS_STANDARD"
  - "LBS_NODATA"
  - "LBS_OWNERDRAWVARIABLE"
  - "LBS_EXTENDEDSEL"
  - "LBS_USETABSTOPS"
  - "LBS_WANTKEYBOARDINPUT"
  - "LBS_NOTIFY"
  - "LBS_DISABLENOSCROLL"
  - "LBS_HASSTRINGS"
  - "LBS_NOREDRAW"
  - "LBS_NOSEL"
  - "LBS_NOINTEGRALHEIGHT"
  - "LBS_MULTICOLUMN"
  - "LBS_SORT"
  - "LBS_MULTIPLESEL"
  - "LBS_OWNERDRAWFIXED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LBS_DISABLENOSCROLL (constante)"
  - "LBS_EXTENDEDSEL (constante)"
  - "LBS_HASSTRINGS (constante)"
  - "LBS_MULTICOLUMN (constante)"
  - "LBS_MULTIPLESEL (constante)"
  - "LBS_NODATA (constante)"
  - "LBS_NOINTEGRALHEIGHT (constante)"
  - "LBS_NOREDRAW (constante)"
  - "LBS_NOSEL (constante)"
  - "LBS_NOTIFY (constante)"
  - "LBS_OWNERDRAWFIXED (constante)"
  - "LBS_OWNERDRAWVARIABLE (constante)"
  - "LBS_SORT (constante)"
  - "LBS_STANDARD (constante)"
  - "LBS_USETABSTOPS (constante)"
  - "LBS_WANTKEYBOARDINPUT (constante)"
  - "cuadros de lista, estilos"
ms.assetid: 3f357b8d-9118-4f41-9e28-02ed92d1e88f
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Estilos de cuadro de lista
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   El cuadro de lista de**LBS\_DISABLENOSCROLL**The muestra una barra de desplazamiento vertical deshabilitada cuando el cuadro de lista no contiene suficientes elementos para desplazarse.  Sin este estilo, se oculta la barra de desplazamiento cuando el cuadro de lista no contiene suficientes elementos.  
  
-   El usuario de**LBS\_EXTENDEDSEL**The puede seleccionar varios elementos mediante la tecla MAYÚS y las combinaciones de teclas del mouse o especiales.  
  
-   **LBS\_HASSTRINGS** especifica un cuadro de lista de propietario\- dibujo que contiene elementos que constan de las cadenas.  El cuadro de lista mantiene una y punteros para cadenas para que la aplicación puede utilizar la función miembro de `GetText` para recuperar el texto para un elemento determinado.  
  
-   **LBS\_MULTICOLUMN** especifica un cuadro de lista de varias columnas que se desplaza horizontalmente.  La función miembro de `SetColumnWidth` establece el ancho de las columnas.  
  
-   Se alterna la selección de la cadena de**LBS\_MULTIPLESEL**cada vez que el usuario hace clic en o haga doble clic en la cadena.  Cualquier número de cadenas puede seleccionar.  
  
-   **LBS\_NODATA** especifica un cuadro de lista de los ninguno\-datos.  Especifique este estilo cuando el número de elementos del cuadro de lista excederá de mil.  Un cuadro de lista de los ninguno\- datos también debe tener el estilo de **LBS\_OWNERDRAWFIXED** , pero no debe tener el estilo de **LBS\_SORT** o de **LBS\_HASSTRINGS** .  
  
     Un cuadro de lista de los ninguno\- datos se parece a un cuadro de lista propietario\- dibujado pero no contiene datos de cadena o mapas de bits para un elemento.  Los comandos de agregar, insertar, o eliminar un elemento omiten siempre los datos especificado del elemento; solicitudes para buscar una cadena en el error del cuadro de lista siempre.  El sistema envía el mensaje de `WM_DRAWITEM` a la ventana propietaria cuando un elemento se debe dibujar.  El miembro itemID de la estructura de `DRAWITEMSTRUCT` última con el mensaje de `WM_DRAWITEM` especifica el número de línea del elemento que se va a dibujar.  Un cuadro de lista de los ninguno\-datos no envía un mensaje de `WM_DELETEITEM` .  
  
-   El tamaño de**LBS\_NOINTEGRALHEIGHT**el cuadro de lista es exactamente el tamaño especificado por la aplicación cuando creó el cuadro de lista.  Normalmente, tamaños de Windows un cuadro de lista de modo que el cuadro de lista no muestra elementos parciales.  
  
-   No se actualiza la presentación del cuadro de lista de**LBS\_NOREDRAW**cuando se realizan modificaciones.  Este estilo puede cambiar en cualquier momento enviando un mensaje de **WM\_SETREDRAW** .  
  
-   **LBS\_NOSEL** especifica que el cuadro de lista contiene los elementos que se pueden ver sólo el no seleccionado.  
  
-   La ventana primaria de**LBS\_NOTIFY**recibe un mensaje de entrada siempre que el usuario haga clic en o haga doble clic en una cadena.  
  
-   El propietario de**LBS\_OWNERDRAWFIXED**el cuadro de lista es responsable de dibujar el contenido; los elementos del cuadro de lista son el mismo alto.  
  
-   El propietario de**LBS\_OWNERDRAWVARIABLE**el cuadro de lista es responsable de dibujar el contenido; los elementos del cuadro de lista son variables de alto.  
  
-   Las cadenas de**LBS\_SORT**en el cuadro de lista se ordenan alfabéticamente.  
  
-   Las cadenas de**LBS\_STANDARD**en el cuadro de lista se ordenan alfabéticamente, y la ventana primaria recibe un mensaje de entrada siempre que el usuario haga clic en o haga doble clic en una cadena.  El cuadro de lista contiene los bordes todos los lados.  
  
-   **LBS\_USETABSTOPS** Permitir un cuadro de lista a reconocer y a expandir caracteres de tabulación al dibujar las cadenas.  Las posiciones predeterminadas de pestaña son 32 unidades de cuadro de diálogo. \(La unidad del diálogo de A es una distancia horizontal o vertical.  Una unidad horizontal del diálogo es igual a un cuarto de la unidad de ancho actual del diálogo.  Las unidades base de diálogo se calculan según el alto y ancho de fuentes del sistema actual.  La función de **GetDialogBaseUnits** Windows devuelve las unidades base actuales del diálogo en píxeles\). Este estilo no debe utilizarse con **LBS\_OWNERDRAWFIXED**.  
  
-   El propietario de**LBS\_WANTKEYBOARDINPUT**el cuadro de lista recibe `WM_VKEYTOITEM` o mensajes de `WM_CHARTOITEM` siempre que el usuario presione una tecla mientras el cuadro de lista tiene foco.  Esto permite una aplicación para realizar el procesamiento especial en la entrada del teclado.  
  
## Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CListBox::Create](../Topic/CListBox::Create.md)   
 [List Box Styles](http://msdn.microsoft.com/library/windows/desktop/bb775149)