---
title: "Escribir y refactorizar c&#243;digo (C++) | Microsoft Docs"
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
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
caps.latest.revision: 6
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Escribir y refactorizar c&#243;digo (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El editor de código de Visual C\+\+ y el IDE proporcionan muchas ayudas a la codificación.  Algunas son exclusivas de C\+\+ y algunas son básicamente iguales para todos los lenguajes de Visual Studio.  Las opciones para habilitar y configurar estas características se encuentran en el diálogo Editor de texto de C\+\+ avanzado \(**Herramientas &#124; Opciones &#124; Editor de texto &#124; C\/C\+\+ &#124; Avanzado** o escriba "C\+\+ Advanced" en **Inicio rápido**\).  Después de elegir la opción que desee establecer, puede obtener más ayuda presionando **F1** cuando el diálogo tenga el foco.  Para las opciones de formato de código generales, escriba `Editor C++` en el **Inicio rápido**.  
  
## Agregar nuevo código  
 Después de crear un proyecto, puede comenzar a escribir código en los archivos que se generaron automáticamente.  Para agregar nuevos archivos, haga clic con el botón derecho en el nodo de proyecto que se muestra en el Explorador de soluciones y elija **Agregar &#124; Nuevo**.  
  
 Para establecer opciones de formato, como sangrías, finalización de llave y coloración, escriba `Formato C++` en la ventana **Inicio rápido**.  
  
### IntelliSense  
 IntelliSense es el nombre de un conjunto de características que proporcionan información en línea acerca de miembros, tipos y sobrecargas de función.  La siguiente ilustración muestra la lista desplegable de miembros que aparece a medida que escribe.  Puede presionar la tecla TAB para escribir el texto del elemento seleccionado en el archivo de código.  
  
 ![Lista desplegable lista de miembros de C&#43;&#43;](../ide/media/vs2015_cpp_statement_completion.png "vs2015\_cpp\_statement\_completion")  
  
 Para obtener información completa, vea [Intellisense de Visual C\+\+](../Topic/Visual%20C++%20Intellisense.md).  
  
### Insertar fragmentos de código  
 Un fragmento de código es una parte de código fuente predefinida.  Haga clic con el botón derecho en un único punto o en el texto seleccionado para insertar un fragmento de código o rodear el texto seleccionado con el fragmento de código.  La siguiente ilustración muestra los tres pasos necesarios para envolver una instrucción seleccionada con un bucle for.  Las partes resaltadas en amarillo de la imagen final son campos que se pueden editar y a los que puede acceder con la tecla TAB.  Para obtener más información, vea [Fragmentos de código](../Topic/Code%20Snippets.md).  
  
 ![Desplegable de insertar fragmento de código de Visual C&#43;&#43;](../ide/media/vs2015_cpp_surround_with.png "vs2015\_cpp\_surround\_with")  
  
### Agregar clase  
 Agregue una nueva clase desde el menú **Proyecto** mediante el Asistente para clases.  
  
 ![Agregar nueva clase en Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_class.png "vs2015\_cpp\_add\_class")  
  
### Asistente para clases  
 Modifique o examine una clase existente o agregue una nueva clase utilizando el Asistente para clases.  Para obtener más información, vea [Agregar funcionalidad con los asistentes para código \(C\+\+\)](../ide/adding-functionality-with-code-wizards-cpp.md).  
  
 ![Asistente de clases de C&#43;&#43;](../ide/media/vs2015_cpp_class_wizard.png "vs2015\_cpp\_class\_wizard")  
  
## Refactorización  
 Se puede acceder a las refactorizaciones bajo el elemento de menú contextual de Acción rápida o haciendo clic en una [bombilla](../Topic/Perform%20quick%20actions%20with%20light%20bulbs.md) en el editor.  
  
### Cambiar nombre  
 Cambie el tipo, función o variable siempre que se use en el ámbito especificado.  En la siguiente ilustración, se cambiará el nombre del método `Eat` por `Devour` tanto en la clase derivada como en la clase base.  
  
 ![Cambiar el nombre del cuadro de diálogo de Visual C&#43;&#43;](../ide/media/vss2015_cpp_rename.png "vss2015\_cpp\_rename")  
  
### Acción rápida: Mover ubicación de definición  
 Mueva una o varias definiciones de función al archivo de encabezado que tiene el mismo nombre que el archivo de código.  Se creará un nuevo encabezado si aún no existe.  Las definiciones resultantes se muestran en línea en una ventana de Peek.  
  
 ![Mover definición en Visual C&#43;&#43;](../ide/media/vs2015_cpp_move_definition.png "vs2015\_cpp\_move\_definition")  
  
### Acción rápida: Crear declaración\/definición  
 Cree una o varias definiciones en el archivo de código asociado para las declaraciones de encabezado seleccionadas.  
  
 ![Opción Crear definición de Visual C&#43;&#43;](../ide/media/vs2015_cpp_create_declaration.png "vs2015\_cpp\_create\_declaration")  
  
### Acción rápida: Implementar todas las virtuales puras para una clase  
 Genere rápidamente códigos auxiliares de implementación vacíos para todas las funciones virtuales heredadas en una clase.  Para implementar solo las funciones virtuales en una clase base determinada, basta con resaltar la clase base en la declaración de clase derivada.  
  
 ![Ventana Implementar virtuales de Visual C&#43;&#43;](../ide/media/vs2015_cpp_implement_virtuals.png "vs2015\_cpp\_implement\_virtuals")  
  
### Convertir en literal de cadena sin formato  
 Si coloca el cursor sobre un literal de cadena, puede hacer clic con el botón derecho y elegir **Acciones rápidas &#124; Convertir en literal de cadena sin formato** para convertir una cadena normal en un literal de la cadena sin formato de C\+\+ 11.  
  
 ![Refactorización de C&#43;&#43; a un literal de cadena sin formato](../ide/media/vs2015_cpp_raw_string_literal.png "vs2015\_cpp\_raw\_string\_literal")  
  
### Función Extraer \(extensión de Visual Studio\)  
 Utilice la característica de la función extraer \(disponible como una [extensión en la Galería de Visual Studio](https://visualstudiogallery.msdn.microsoft.com/a081dc8c-c805-4589-9b8b-c2c309a05789)\) para mover una sección de código a su propia función y reemplazar el código por una llamada a esa función.  
  
 ![Cuadro de diálogo de la función Extraer de Visual C&#43;&#43;](../ide/media/vs2015_cpp_extract_function.png "vs2015\_cpp\_extract\_function")  
  
## Navegar y comprender  
  
### InformaciónRápida  
 Coloque el mouse sobre una variable para ver su información de tipo.  InformaciónRápida  
  
 ![InformaciónRápida de Visual C&#43;&#43;](../ide/media/vs2015_cpp_quickinfo.png "vs2015\_cpp\_quickInfo")  
  
### Abrir documento \(Ir a encabezado\)  
 Haga clic con el botón derecho en el nombre del encabezado en una directiva `#include` y abra el archivo de encabezado.  
  
 ![Opción de menú Abrir documento de Visual C&#43;&#43;](../ide/media/vs2015_cpp_open_document.png "vs2015\_cpp\_open\_document")  
  
### Ver la definición  
 Coloque el mouse sobre una declaración de variable o función y, a continuación, elija **Ver la definición** para ver una vista en línea de su definición.  Para obtener más información, vea [Ver la definición \(Alt\+F12\)](../Topic/How%20to:%20View%20and%20Edit%20Code%20by%20Using%20Peek%20Definition%20\(Alt+F12\).md).  
  
 ![Definición de Peek de Visual C&#43;&#43;](../ide/media/vs2015_cpp_peek_definition.png "vs2015\_cpp\_peek\_definition")  
  
### Ir a definición  
 Coloque el mouse sobre una declaración de variable o función, haga clic con el botón secundario y, a continuación, elija **Ir a definición** para abrir el documento donde se define el objeto.  
  
### Ver jerarquía de llamadas  
 Haga clic con el botón derecho en cualquier llamada a función y vea una lista recursiva de todas las funciones a las que llama y de todas las funciones que la llaman.  Cada una de las funciones de la lista se pueden expandir de la misma manera.  Para obtener más información, vea [Jerarquía de llamadas](../Topic/Call%20Hierarchy.md).  
  
 ![Jerarquía de llamadas de Visual C&#43;&#43;](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015\_cpp\_call\_hierarchy")  
  
### Alternar archivo de encabezado\/código  
 Haga clic con el botón derecho en Alternar archivo de encabezado\/código para alternar entre un archivo de encabezado y su archivo de código asociado.  
  
### Esquematización  
 Haga clic con el botón derecho en un archivo de código fuente y elija **Esquematización** para contraer o expandir definiciones o regiones personalizadas para que sea más fácil examinar únicamente las partes que le interesen.  Para obtener más información, vea [Esquematización](../Topic/Outlining.md).  
  
 ![Esquematización de Visual C&#43;&#43;](../ide/media/vs2015_cpp_outlining.png "vs2015\_cpp\_outlining")  
  
### Modo de mapa de barra de desplazamiento  
 El modo de mapa de barra de desplazamiento permite desplazarse y examinar rápidamente un archivo de código sin abandonar realmente su ubicación actual.  También puede hacer clic en cualquier parte del mapa de código para ir directamente a esa ubicación.  
  
 ![Mapa de código en Visual C&#43;&#43;](../ide/media/vs2015_cpp_code_map.png "vs2015\_cpp\_code\_map")  
  
### Generar gráfico de archivos de inclusión  
 Haga clic con el botón derecho en su proyecto y elija **Generar gráfico de archivos de inclusión** para ver un gráfico en el que se muestra qué archivos son incluidos por otros archivos.  
  
 ![Gráfico de Visual C&#43;&#43; de archivos de inclusión](../ide/media/vs2015_cpp_include_graph.png "vs2015\_cpp\_include\_graph")  
  
### F1 Ayuda  
 Coloque el cursor encima o justo después de cualquier tipo, palabra clave o función y presione F1 para ir directamente al tema de referencia pertinente de MSDN.  F1 también funciona en elementos de la lista de errores y en muchos cuadros de diálogo.  
  
### Inicio rápido  
 Para navegar fácilmente hasta cualquier ventana o herramienta de Visual Studio, simplemente escriba su nombre en la ventana Inicio rápido situada en la esquina superior derecha de la interfaz de usuario.  Se filtrará la lista de finalización automática a medida que escriba.  
  
 ![Inicio rápido de Visual Studio](../ide/media/vs2015_cpp_quick_launch.png "vs2015\_cpp\_quick\_launch")