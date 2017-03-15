---
title: "Optimizaci&#243;n guiada por perfiles del concentrador Rendimiento y diagn&#243;sticos | Microsoft Docs"
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
ms.assetid: dc3a1914-dbb6-4401-bc63-10665a8c8943
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Optimizaci&#243;n guiada por perfiles del concentrador Rendimiento y diagn&#243;sticos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El complemento Optimización guiada por perfiles para Visual C\+\+, en el concentrador de rendimiento y diagnósticos, racionaliza la experiencia de optimización guiada por perfiles para desarrolladores.  Puede [descargar el complemento](http://go.microsoft.com/fwlink/p/?LinkId=327915) desde el sitio web de Visual Studio.  
  
 La optimización guiada por perfiles \(PGO\) ayuda a crear compilaciones de aplicaciones nativas x86 y x64 optimizadas para la forma en que los usuarios interactúan con ellas.  PGO es un proceso de varios pasos: el usuario crea una compilación de la aplicación instrumentada para la generación de perfiles y, después, realiza un proceso de “entrenamiento”, es decir, ejecuta la aplicación instrumentada en diversos escenarios comunes de interacción con el usuario.  Los datos de generación de perfiles capturados se guardan y después la aplicación se recompila, usando los resultados para orientar la optimización de todo el programa.  Si bien estos pasos pueden realizarse individualmente en Visual Studio o en la línea de comandos, el complemento PGO centraliza y simplifica el proceso.  El complemento PGO establece todas las opciones necesarias, le guía a través de cada paso, presenta el análisis obtenido y, a continuación, usa los resultados para configurar la compilación de forma que se optimice el tamaño o la velocidad de cada función.  Además, dicho complemento facilita volver a ejecutar el entrenamiento de la aplicación y actualizar los datos de optimización de la compilación cuando cambia el código.  
  
## Requisitos previos  
 Debe [descargar el complemento PGO](http://go.microsoft.com/fwlink/p/?LinkId=327915) e instalarlo en Visual Studio antes de que pueda usarlo en el concentrador de Rendimiento y diagnósticos.  
  
## Tutorial: usar el complemento PGO para optimizar una aplicación  
 En primer lugar, se creará una aplicación de escritorio de Win32 básica en Visual Studio.  Si ya tiene una aplicación nativa que desea optimizar, puede usarla y omitir este paso.  
  
#### Para crear una aplicación  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Instalado**, **Plantillas**, **Visual C\+\+** y, a continuación, seleccione **MFC**.  
  
3.  En el panel central, seleccione **Aplicación MFC**.  
  
4.  Especifique un nombre para el proyecto; por ejemplo, SamplePGOProject, en el cuadro **Nombre**.  Elija el botón **Aceptar**.  
  
5.  En la página **Información general** del cuadro de diálogo **Asistente para aplicaciones MFC**, elija el botón **Finalizar**.  
  
 A continuación, establezca la configuración de compilación de la aplicación en Lanzamiento para prepararla para los pasos de compilación y entrenamiento de PGO.  
  
#### Para establecer la configuración de compilación  
  
1.  En la barra de menús, elija **Compilar**, **Administrador de configuración**.  
  
2.  En el cuadro de diálogo **Administrador de configuración**, elija el botón desplegable **Configuración de soluciones activas** y seleccione **Versión**.  Elija el botón **Cerrar**.  
  
 Abra el concentrador de rendimiento y diagnósticos; en la barra de menús, elija **Analizar**, **Rendimiento y diagnósticos**.  Esto abre una página de la sesión de diagnósticos con las herramientas de análisis disponibles para el tipo de proyecto.  
  
 ![PGO en el concentrador de Rendimiento y diagnósticos](../../build/reference/media/pgofig0hub.png "PGOFig0Hub")  
  
 En **Herramientas disponibles**, active la casilla **Optimización guiada por perfiles**.  Elija el botón **Iniciar** para iniciar el complemento PGO.  
  
 ![Página de introducción de PGO](../../build/reference/media/pgofig1start.png "PGOFig1Start")  
  
 En la página **Optimización guiada por perfiles** se describen los pasos usados por el complemento para mejorar el rendimiento de la aplicación.  Elija el botón **Iniciar**.  
  
 ![Página de instrumentación de PGO](../../build/reference/media/pgofig2instrument.png "PGOFig2Instrument")  
  
 En la sección **Instrumentación**, use la opción de **habilitación inicial del entrenamiento** para elegir si se va incluir la fase de inicio de la aplicación como parte del entrenamiento.  Si no se selecciona esta opción, los datos de entrenamiento no se registran en una aplicación instrumentada en ejecución hasta que no se habilite explícitamente el entrenamiento.  
  
 Elija el botón **Instrumentar** para compilar la aplicación con un conjunto especial de opciones del compilador.  El compilador inserta instrucciones de sondeo en el código generado.  Estas instrucciones registran los datos de generación de perfiles durante la fase de entrenamiento.  
  
 ![Página de compilación instrumentada de PGO](../../build/reference/media/pgofig3build.PNG "PGOFig3Build")  
  
 Cuando la compilación instrumentada de la aplicación se completa, la aplicación se inicia automáticamente.  
  
 Si se producen errores o advertencias durante la compilación, corríjalos y elija la opción de **reiniciar compilación** para reiniciar la compilación instrumentada.  
  
 Al iniciarse la aplicación, puede usar los vínculos para **iniciar entrenamiento** y **pausar entrenamiento** de la sección de **entrenamiento** para controlar cuándo se registra la información de generación de perfiles.  Puede usar los vínculos **Detener aplicación** e **Iniciar aplicación** para detener y reiniciar la aplicación.  
  
 ![Página de aprendizaje de PGO](../../build/reference/media/pgofig4training.PNG "PGOFig4Training")  
  
 Durante el entrenamiento, recorra los escenarios de usuario para capturar la información de generación de perfiles que el complemento PGO necesita para optimizar el código.  Cuando haya completado el entrenamiento, cierre la aplicación o elija el vínculo **Detener aplicación**.  Elija el botón **Analizar** para iniciar el paso de análisis.  
  
 Una vez completado el análisis, en la sección **Análisis** se muestra un informe de la información de generación de perfiles que se capturó durante la fase de entrenamiento del escenario de usuario.  Puede usar este informe para examinar las funciones a las que más llamó la aplicación y a las que dedicó más tiempo.  El complemento PGO usa la información para determinar en qué funciones de la aplicación se va a optimizar la velocidad y en cuáles el tamaño.  El complemento PGO configura optimizaciones de compilación a fin de crear la aplicación más pequeña y rápida para los escenarios de usuario registrados durante el entrenamiento.  
  
 ![Página de análisis de PGO](../../build/reference/media/pgofig5analyze.png "PGOFig5Analyze")  
  
 Si el entrenamiento capturó la información de generación de perfiles esperada, puede elegir **Guardar cambios** para guardar los datos de perfil analizados en el proyecto a fin de optimizar futuras compilaciones.  Para descartar los datos de perfil y volver a iniciar el entrenamiento desde el principio, elija la opción para **rehacer el entrenamiento**.  
  
 El archivo de datos del perfil se guarda en el proyecto en una carpeta de **datos de entrenamiento de PGO**.  Estos datos se usan para controlar la configuración de optimización de compilación del compilador en la aplicación.  
  
 ![Archivo de datos de PGO en el Explorador de soluciones](../../build/reference/media/pgofig6data.png "PGOFig6Data")  
  
 Después del análisis, el complemento PGO establece opciones de compilación en el proyecto para usar los datos de perfil para optimizar selectivamente la aplicación durante la compilación.  Puede seguir modificando y compilando la aplicación con los mismos datos de perfil.  Cuando se compila la aplicación, los resultados de la compilación notifican cuántas funciones e instrucciones se optimizaron usando los datos de perfil.  
  
 ![Diagnósticos de salida de PGO](../../build/reference/media/pgofig7diagnostics.png "PGOFig7Diagnostics")  
  
 Si realiza cambios de código significativos durante el desarrollo, es posible que tenga que volver a aplicar el entrenamiento a la aplicación para obtener las mejores optimizaciones.  Se recomienda volver a aplicar el entrenamiento a la aplicación cuando los resultados de la compilación notifican que menos del 80 % de las funciones o instrucciones se optimizaron usando los datos de perfil.