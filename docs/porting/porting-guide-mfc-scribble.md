---
title: "Gu&#237;a de migraci&#243;n: Scribble de MFC | Microsoft Docs"
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
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# Gu&#237;a de migraci&#243;n: Scribble de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este es el primero de varios temas que presentan el procedimiento de actualización a [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] de proyectos de Visual C\+\+ que se crearon en versiones anteriores de Visual Studio.  Estos temas muestran el proceso de actualización mediante ejemplos, empezando por un proyecto muy simple y pasando a proyectos un poco más complejos.  En este tema mostramos todo el proceso de actualización de un proyecto específico, Scribble de MFC.  Es una apropiada introducción básica al proceso de actualización de proyectos de C\+\+.  
  
 Cada versión de Visual Studio presenta las posibles incompatibilidades que pueden complicar el paso del código de una versión anterior de Visual Studio a una más reciente.  A veces los cambios necesarios se encuentran en su código, por lo que debe volver a compilar y actualizar el código, y a veces los cambios necesarios se encuentran en los archivos del proyecto.  Cuando abre un proyecto que se creó con una versión anterior de Visual Studio, Visual Studio le pregunta automáticamente si desea actualizar un proyecto o solución a la versión más reciente.  Por lo general, estas herramientas solo actualizan los archivos del proyecto, pero no modifican el código fuente.  
  
## Scribble de MFC  
 Scribble de MFC es un ejemplo muy conocido que se ha incluido en muchas versiones diferentes de Visual C\+\+.  Es una sencilla aplicación de dibujo que muestra algunas de las características básicas de MFC.  Hay disponibles varias versiones de esta aplicación, incluidas las versiones de código administrado y nativo.  En este ejemplo encontramos una antigua versión de Scribble en código nativo de Visual Studio 2005 y la abrimos en [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)].  
  
 Antes de intentar actualizarla, hicimos una copia de seguridad de toda nuestra solución y de todo su contenido.  A continuación, teníamos que decidir el método de actualización específico que íbamos a utilizar.  Para las soluciones y proyectos más complejos que no se hayan actualizado durante mucho tiempo, debería considerar la posibilidad de actualizar las versiones de Visual Studio de una en una.  De ese modo, puede identificar qué versión de Visual Studio fue la que dio lugar a un problema.  En un proyecto sencillo vale la pena intentar abrirlo en la versión más reciente de Visual Studio y dejar que el asistente convierta el proyecto.  Si esto no funciona, puede probar a realizar las actualizaciones de una en una si tiene acceso a las versiones adecuadas de Visual Studio.  
  
 Tenga en cuenta que también puede ejecutar devenv en la línea de comandos mediante la opción `/Upgrade`, en lugar de usar el asistente para actualizar los proyectos.  Vea [\/Upgrade](../Topic/-Upgrade%20\(devenv.exe\).md).  Eso podría ayudar a automatizar el proceso de actualización para un gran número de proyectos.  
  
### Paso 1.Convertir el archivo del proyecto  
 Al abrir un archivo de proyecto antiguo en Visual Studio 2015, Visual Studio ofrece la opción de convertir el archivo del proyecto a la versión más reciente, lo cual aceptamos.  Se mostró el siguiente cuadro de diálogo:  
  
 ![Revisar cambios de proyectos y soluciones](../porting/media/scribbleprojectupgrade.png "ScribbleProjectUpgrade")  
  
 Se produjo un error por el que se nos informaba de que el destino de Itanium no estaba disponible y no se realizaría la conversión.  
  
  **La plataforma "Itanium" no está presente en este proyecto.  Se omitirán todas las configuraciones y sus valores de configuración de archivo específicos de esta plataforma.  Si quiere que se convierta esta plataforma, asegúrese de que la plataforma correspondiente esté instalada en "%vctargetpath%\\platforms\\Itanium".  ¿Desea convertir este proyecto sin esta plataforma?**  En el momento en que se creó el proyecto de Scribble anterior, Itanium era una plataforma de destino importante.  La plataforma Windows ya no admite Itanium, así que decidimos dejar de proporcionar compatibilidad con la plataforma Itanium.  
  
 A continuación, Visual Studio mostró un informe de migración de todos los problemas con el antiguo archivo de proyecto.  
  
 ![Informe de actualización](../porting/media/scribblemigrationreport.png "ScribbleMigrationReport")  
  
 En este caso, todos los problemas eran advertencias, y Visual Studio realizó los cambios pertinentes en el archivo del proyecto.  La gran diferencia en lo que se refiere al proyecto es que la herramienta de compilación cambió de vcbuild a msbuild.  Este cambio se introdujo por primera vez en Visual Studio 2010.  Otros de los cambios incluyen una determinada reorganización de la secuencia de elementos en el propio archivo de proyecto.  Ninguno de los problemas requirió atención adicional para este proyecto simple.  
  
### Paso 2.Hacer que compile  
 Antes de compilar, comprobamos el conjunto de herramientas de la plataforma para saber qué versión del compilador está utilizando el sistema del proyecto.  En el diálogo de propiedades del proyecto, bajo **Propiedades de configuración**, en la categoría **General**, examine la propiedad **Conjunto de herramientas de plataforma**.  Contiene la versión de Visual Studio y el número de versión de las herramientas de plataforma, que en este caso es v140 para la versión [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] de las herramientas.  Al convertir un proyecto que se compiló originalmente con Visual C\+\+ 2010, 2012 o 2013, el conjunto de herramientas no se actualiza automáticamente al conjunto de herramientas [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].  En el caso de Scribble, la versión que convertimos fue creada para Visual Studio 2005, por lo que se convierte para que utilice el conjunto de herramientas más reciente.  
  
 Al compilar, el primer problema que surge está relacionado con el código MBCS.  
  
  **error MSB8031:**  El vínculo del mensaje de error nos lleva a un tema sobre el desuso de MBCS en Visual Studio 2013.  De forma predeterminada, la instalación de MFC en Visual C\+\+ 2013 no incluye la versión MBCS de MFC.  Se requiere la versión MBCS de MFC para compilar este proyecto en su forma actual.  Podemos migrar el código para que utilice Unicode o podemos descargar e instalar la versión MBCS de MFC.  Si decidimos descargar la versión MBCS de MFC, podemos agregar una definición de la macro NO\_WARN\_MBCS\_MFC\_DEPRECATION para suprimir esta advertencia.  
  
 Para descargar la versión MBCS de MFC, lea primero la información sobre el desuso de la versión MBCS de MFC en el artículo [Complemento DLL de MBCS para MFC](../mfc/mfc-mbcs-dll-add-on.md) y en el blog de VC y descargue la versión MBCS de MFC [aquí](http://www.microsoft.com/download/details.aspx?id=44930).  En el cuadro de diálogo de propiedades de proyecto, bajo la categoría **C\/C\+\+**, en **Preprocesador**, agregue la macro NO\_WARN\_MBCS\_MFC\_DEPRECATION a la lista de macros predefinidas.  
  
 Para realizar el cambio a Unicode, abra las propiedades del proyecto y en **Propiedades de configuración** elija la sección **General** y busque la propiedad **Juego de caracteres**.  Cambie el valor **Utilizar juego de caracteres multibyte** por **Utilizar juego de caracteres Unicode**.  El efecto de este cambio es que ahora las macros \_UNICODE y UNICODE están definidas y \_MBCS no lo está. Puede comprobarlo en el diálogo de propiedades bajo la categoría **C\/C\+\+** en la propiedad **Línea de comandos**.  
  
  **\/GS \/analyze\- \/W4 \/Gy \/Zc:wchar\_t \/Zi \/Gm\- \/O2 \/Ob1 \/Fd".  \\Release\\vc140.pdb" \/Zc:inline \/fp:precise \/D "\_AFXDLL" \/D "WIN32" \/D "NDEBUG" \/D "\_WINDOWS" \/D "\_UNICODE" \/D "UNICODE" \/errorReport:prompt \/GF \/WX \/Zc:forScope \/Gd \/Oy \/MD \/Fa".  \\Release\\" \/EHsc \/nologo \/Fo".  \\Release\\" \/Fp".  \\Release\\Scribble.pch"**  Aunque el proyecto Scribble no se configuró para que se compilase con caracteres Unicode, ya estaba escrito con TCHAR en lugar de char, por lo que en realidad no hace falta cambiar nada.  El proyecto se compila correctamente con el juego de caracteres Unicode.  
  
 Sin embargo, hay otro problema.  El compilador nos indica que \_WINNT32\_WINNT no está definida:  
  
  **\_WIN32\_WINNT no está definida.  Se utilizará \_WIN32\_WINNT\_MAXVER como valor predeterminado \(vea WinSDKVer.h\)**  Esto es una advertencia, no un error, y se genera habitualmente al actualizar un proyecto de Visual C\+\+.  Esta es la macro que define cuál es la versión más antigua de Windows sobre la que se ejecutará nuestra aplicación.  Si omitimos la advertencia, aceptamos el valor predeterminado, \_WIN32\_WINNT\_MAXVER, que significa la versión actual de Windows.  Para ver una tabla con los posibles valores, vea [Uso de los encabezados de Windows](https://msdn.microsoft.com/en-us/library/aa383745.aspx).  Por ejemplo, podemos establecer que se ejecute en cualquier versión de Vista en adelante.  
  
```  
#define _WIN32_WINNT _WIN32_WINNT_VISTA  
```  
  
 Si el código utiliza partes de la API de Windows que no están disponibles en la versión de Windows que especifica con esta macro, debería mostrarse como un error del compilador.  En el caso del código de Scribble, no hay ningún error.  
  
### Paso 3.Pruebas y depuración  
 No hay ningún conjunto de pruebas, por lo que simplemente iniciamos la aplicación y probamos sus funciones manualmente mediante la interfaz de usuario.  No se observó ningún problema.  
  
### Paso 4.Mejorar el código  
 Ahora que ha migrado a Visual Studio 2015, puede que quiera realizar algunos cambios para aprovechar las nuevas características de C\+\+.  La versión actual del compilador de Visual C\+\+ es mucho más compatible con el estándar de C\+\+ que las versiones anteriores, por lo que si tiene pensado realizar cambios en el código para hacerlo más seguro y más portátil con respecto a otros compiladores y sistemas operativos, debería pensar en realizar algunas mejoras.  
  
## Pasos siguientes  
 Scribble era una aplicación de escritorio pequeña y simple de Windows, y no fue difícil de convertir.  Muchas aplicaciones pequeñas y sencillas son fáciles de convertir a la nueva versión.  Sin embargo, será necesario más tiempo para actualizar aplicaciones más complejas, con muchas más líneas de código, antiguo código heredado que podría no estar a la altura de los estándares de ingeniería modernos, varios proyectos y bibliotecas, o pasos de compilación personalizados, así como para actualizar aplicaciones con compilaciones complejas automatizadas mediante script.  Vaya al [siguiente ejemplo](../porting/porting-guide-com-spy.md), una aplicación ATL\/COM llamada COM Spy.  
  
## Vea también  
 [Migración y actualización: ejemplos y casos prácticos](../porting/porting-and-upgrading-examples-and-case-studies.md)   
 [Siguiente ejemplo: COM Spy](../porting/porting-guide-com-spy.md)