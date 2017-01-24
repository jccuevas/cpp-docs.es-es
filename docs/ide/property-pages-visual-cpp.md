---
title: "P&#225;ginas de propiedades (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.NotAProp.Edit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "macro de compilación"
  - "macros, archivo de proyecto"
  - "propiedades de proyectos [C++], valores predeterminados"
  - "propiedades de proyectos [C++], establecer"
  - "macro de archivo de proyecto"
  - "páginas de propiedades, configuración del proyecto"
  - "macros definidas por el usuario"
  - "valores definidos por el usuario"
  - "proyectos de Visual C++, propiedades"
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# P&#225;ginas de propiedades (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Con las páginas de propiedades, puede especificar la configuración de los proyectos de Visual Studio.  Para abrir el cuadro de diálogo **Páginas de propiedades** de un proyecto de Visual Studio, en el menú **Proyecto**, haga clic en **Propiedades**.  
  
 Puede especificar la configuración del proyecto para que se aplique a todas las configuraciones de compilación o bien puede especificar propiedades de proyecto diferentes para cada configuración de compilación.  Por ejemplo, puede especificar ciertos valores para la configuración de versión y otros para la configuración de depuración.  
  
 No todas las páginas disponibles se muestran necesariamente en el cuadro de diálogo **Páginas de propiedades**.  Las páginas que se muestran dependen de los tipos de archivo del proyecto.  
  
 Para obtener más información, vea [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
## Propiedades predeterminadas frente apropiedades modificadas  
 Cuando se usa el cuadro de diálogo **Nuevo proyecto** para crear un proyecto, [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] utiliza la plantilla de proyecto especificada para inicializar las propiedades del proyecto.  Por lo tanto, los valores de las propiedades de la plantilla pueden considerarse como valores predeterminados para ese tipo de proyecto.  En otros tipos de proyecto, las propiedades pueden tener diferentes valores predeterminados.  
  
 Un valor de propiedad de proyecto aparece en negrita si se ha modificado.  Una propiedad de proyecto puede modificarse por las razones siguientes:  
  
-   El Asistente para aplicaciones cambia la propiedad porque necesita un valor de propiedad diferente al que se ha especificado en la plantilla de proyecto.  
  
-   El usuario especifica un valor de propiedad distinto en el cuadro de diálogo **Nuevo proyecto**.  
  
-   El usuario especifica un valor de propiedad distinto en una página de propiedades de proyecto.  
  
> [!TIP]
>  Para ver el conjunto final de valores de propiedad que utiliza MSBuild para compilar el proyecto, examine el archivo de resultados del preprocesador, que puede generar mediante esta línea de comandos: **MSBuild \/preprocess:***preprocessor\_output\_filename*opt *project\_filename*opt  
  
## Restablecer propiedades  
 Cuando ve el cuadro de diálogo **Páginas de propiedades** de un proyecto y el nodo del proyecto está seleccionado en el **Explorador de soluciones**, para muchas propiedades, puede seleccionar **Heredar de primario o valores pred. del proyecto** o modificar el valor de otra manera.  
  
 Cuando ve el cuadro de diálogo **Páginas de propiedades** de un proyecto y un archivo está seleccionado en el **Explorador de soluciones**, para muchas propiedades, puede seleccionar **Heredar de primario o valores pred. del proyecto** o modificar el valor de otra manera.  Sin embargo, si el proyecto contiene muchos archivos que tienen valores de propiedad que difieren de los valores predeterminados del proyecto, se tardará más tiempo en compilarlo.  
  
> [!TIP]
>  Para actualizar el cuadro de diálogo **Páginas de propiedades** de modo que muestre las selecciones más recientes, haga clic en **Aplicar**.  
  
 La mayoría de los valores predeterminados del proyecto son valores predeterminados del sistema \(plataforma\).  Algunos valores predeterminados del proyecto derivan de las hojas de estilos que se aplican al actualizar las propiedades de la sección **Valores predeterminados del proyecto** de la página de propiedades de configuración **General** del proyecto.  Para obtener más información, vea [Página de propiedades General \(Proyecto\)](../ide/general-property-page-project.md).  
  
## Especificar valores definidos por el usuario  
 Debe definir el valor de algunas propiedades.  Un valor definido por el usuario puede contener uno o más caracteres alfanuméricos o nombres de macro de archivo de proyecto.  Algunas de estas propiedades pueden tomar un único valor definido por el usuario, pero otras pueden tomar una lista delimitada por puntos y coma de varios valores.  
  
 Para especificar un valor definido por el usuario para una propiedad, o una lista si la propiedad puede tomar varios valores definidos por el usuario, en la columna situada a la derecha del nombre de la propiedad, realice una de las siguientes acciones:  
  
-   Escriba el valor o la lista de valores.  
  
-   Haga clic en la flecha desplegable.  Si **Editar** está disponible, haga clic en él y, a continuación, en el cuadro de texto, escriba el valor o la lista de valores.  Un medio alternativo de especificar una lista es escribir cada valor en una línea independiente del cuadro de texto.  En la página de propiedades, los valores se mostrarán como una lista delimitada por puntos y coma.  
  
     Para insertar una macro de archivo de proyecto como un valor, haga clic en **Macros** y, a continuación, haga doble clic en el nombre de la macro.  
  
-   Haga clic en la flecha desplegable.  Si **Examinar** está disponible, haga clic en él y, a continuación, seleccione uno o más valores.  
  
 Para una propiedad con varios valores, la opción **Heredar de primario o valores pred. del proyecto** está disponible al hacer clic en la flecha desplegable de la columna situada a la derecha del nombre de la propiedad y, a continuación, hacer clic en **Editar**.  La opción se encuentra activada de forma predeterminada.  
  
 Observe que una página de propiedades solo muestra la configuración en el nivel actual de una propiedad con varios valores que hereda de otro nivel.  Por ejemplo, si se selecciona un archivo en el **Explorador de soluciones** y selecciona la propiedad **Definiciones de preprocesador** de C\/C \+\+, se muestran las definiciones de nivel de archivo pero no las definiciones heredadas de nivel de proyecto.  Para ver los valores de nivel actual y heredados, haga clic en la flecha desplegable de la columna situada a la derecha del nombre de la propiedad y, a continuación, haga clic en **Editar**.  Si utiliza el [modelo de proyecto de Visual C\+\+](http://msdn.microsoft.com/es-es/06c1bbd9-4c79-4f97-ad6d-2b1dea8ecd1f), este comportamiento también afecta a los objetos de los proyectos y archivos.  Es decir, al consultar los valores de una propiedad en el nivel de archivo, no obtendrá los valores de esa misma propiedad en el nivel de proyecto.  Tiene que obtener explícitamente los valores de la propiedad en el nivel de proyecto.  Además, algunos valores heredados de una propiedad pueden proceder de una hoja de estilos, a la que no se tiene acceso mediante programación.  
  
## En esta sección  
  
1.  [Agregar ruta de búsqueda de referencias \(Cuadro de diálogo\)](http://msdn.microsoft.com/es-es/4520d80d-aa9f-4d11-b92b-2f64a1fd5cb2)  
  
2.  [Avanzadas, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de \<Projectname\> \(Cuadro de diálogo\)](../ide/advanced-manifest-tool.md)  
  
3.  [Páginas de propiedades Línea de comandos](../ide/command-line-property-pages.md)  
  
4.  [Paso de compilación personalizada \(Página de propiedades\): General](../ide/custom-build-step-property-page-general.md)  
  
5.  [Agregar referencias](../ide/adding-references-in-visual-cpp-projects.md)  
  
6.  [Página de propiedades General \(Archivo\)](../ide/general-property-page-file.md)  
  
7.  [Página de propiedades General \(Proyecto\)](../ide/general-property-page-project.md)  
  
8.  [General, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de \<Projectname\> \(Cuadro de diálogo\)](../ide/general-manifest-tool-configuration-properties.md)  
  
9. [Páginas de propiedades HLSL](../ide/hlsl-property-pages.md)  
  
10. [Páginas de propiedades HLSL: Avanzadas](../ide/hlsl-property-pages-advanced.md)  
  
11. [Páginas de propiedades HLSL: General](../ide/hlsl-property-pages-general.md)  
  
12. [Páginas de propiedades HLSL: archivos de salida](../ide/hlsl-property-pages-output-files.md)  
  
13. [Entrada y salida, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de \<Projectname\> \(Cuadro de diálogo\)](../ide/input-and-output-manifest-tool.md)  
  
14. [COM aislado, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de \<Projectname\> \(Cuadro de diálogo\)](../ide/isolated-com-manifest-tool.md)  
  
15. [Páginas de propiedades Vinculador](../ide/linker-property-pages.md)  
  
16. [Página de propiedades Recursos administrados](../ide/managed-resources-property-page.md)  
  
17. [Herramienta Manifiesto \(Páginas de propiedades\)](../ide/manifest-tool-property-pages.md)  
  
18. [Páginas de propiedades MIDL](../ide/midl-property-pages.md)  
  
19. [Páginas de propiedades MIDL: Avanzadas](../ide/midl-property-pages-advanced.md)  
  
20. [Páginas de propiedades MIDL: General](../ide/midl-property-pages-general.md)  
  
21. [Páginas de propiedades MIDL: Resultados](../ide/midl-property-pages-output.md)  
  
22. [Página de propiedades NMake](../ide/nmake-property-page.md)  
  
23. [Páginas de propiedades Recursos](../ide/resources-property-pages.md)  
  
24. [Directorios de VC\+\+ \(Página de propiedades\)](../ide/vcpp-directories-property-page.md)  
  
25. [Página de propiedades Referencias Web](../ide/web-references-property-page.md)  
  
26. [Herramienta Generador de datos HTML \(Página de propiedades\)](../ide/xml-data-generator-tool-property-page.md)  
  
27. [Herramienta Generador de documentos XML \(Páginas de propiedades\)](../ide/xml-document-generator-tool-property-pages.md)  
  
## Vea también  
 [Cómo: Crear y quitar dependencias del proyecto](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)   
 [Cómo: Crear y editar configuraciones](../Topic/How%20to:%20Create%20and%20Edit%20Configurations.md)   
 [Implementar aplicaciones](http://msdn.microsoft.com/es-es/4ff8881d-0daf-47e7-bfe7-774c625031b4)