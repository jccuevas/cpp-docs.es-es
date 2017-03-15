---
title: "Tutorial: Implementar el programa (C++) | Microsoft Docs"
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
helpviewer_keywords: 
  - "implementar aplicaciones [C++], tutoriales"
  - "configurar proyectos [C++]"
  - "implementaciones de programas [C++]"
  - "proyectos [C++], configurar"
  - "proyectos [C++], implementar programas"
  - "implementación de aplicaciones [C++], tutoriales"
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Implementar el programa (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ahora que ha creado la aplicación completando los tutoriales relacionados anteriores, que se enumeran en [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C\+\+](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md), el último paso es crear un instalador para que otros usuarios puedan instalar el programa en sus equipos.  Para ello, agregue un nuevo proyecto a la solución existente.  El resultado de este nuevo proyecto es un archivo setup.exe que instalará la aplicación en otro equipo.  
  
 En este tutorial muestra cómo utilizar Windows Installer para implementar la aplicación.  También puede utilizar ClickOnce para implementar una aplicación.  Para obtener más información, vea [Implementación de ClickOnce para aplicaciones de Visual C\+\+](../ide/clickonce-deployment-for-visual-cpp-applications.md).  Para obtener más información acerca de la implementación en general, vea [Implementar aplicaciones, servicios y componentes](../Topic/Deploying%20Applications,%20Services,%20and%20Components.md).  
  
## Requisitos previos  
  
-   En este tutorial se da por supuesto que conoce los fundamentos del lenguaje C\+\+.  
  
-   También se presupone que ha completado los tutoriales relacionados anteriores que se enumeran en [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C\+\+](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
-   Este tutorial no se puede completar en las ediciones Express de Visual Studio.  
  
-   Si no lo ha hecho todavía, descargue InstallShield Limited Edition \(ISLE\), como se describe en los pasos especificados más adelante en este artículo.  ISLE es gratis para desarrolladores de Visual Studio y reemplaza a la funcionalidad de las plantillas de proyecto de instalación e implementación en ediciones anteriores de Visual Studio.  
  
### Para instalar la plantilla de proyecto de implementación y configuración de ISLE  
  
1.  Si está conectado a Internet, en la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**.  
  
2.  En el panel izquierdo del cuadro de diálogo, expanda los nodos **Instalado**, **Plantillas** y **Otros tipos de proyectos** y seleccione **Instalación e implementación**.  En el panel central, seleccione **Habilitar InstallShield Limited Edition** y elija el botón de **Aceptar**.  
  
3.  Siga las instrucciones para instalar InstallShield Limited Edition para Visual Studio \(ISLE\).  
  
4.  Después de haber descargado, instalado y activado ISLE, cierre Visual Studio y ábralo de nuevo.  
  
5.  En la barra de menús, elija **Archivo**, **Proyectos y soluciones recientes** y elija la solución **Juego** para volver a abrirla.  
  
### Para crear un proyecto de instalación e instalar su programa  
  
1.  Cambie la configuración de soluciones activa a Lanzamiento.  En la barra de menús, elija **Compilar**, **Administrador de configuración**.  En el cuadro de diálogo **Administrador de configuración**, en la lista desplegable **Configuración de soluciones activas**, seleccione **Versión**.  Elija el botón **Cerrar** para guardar la configuración.  
  
2.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**.  
  
3.  En el panel izquierdo del cuadro de diálogo, expanda los nodos **Instalado**, **Plantillas** y **Otros tipos de proyectos** y seleccione **Instalación e implementación**.  En el panel central, seleccione **Proyecto de InstallShield Limited Edition**.  
  
4.  Escriba un nombre para el modelo de instalación en el cuadro **Nombre**.  Para este ejemplo, escriba Game Installer.  En la lista desplegable **Solución**, seleccione **Agregar a solución**.  Elija el botón **Aceptar** para crear el proyecto de instalación.  Se abrirá una pestaña **Asistente para proyectos \(Game Installer\)** en la ventana del editor.  
  
5.  En la parte inferior de la pestaña **Asistente para proyectos \(Game Installer\)**, elija el vínculo **Información de la aplicación**.  
  
6.  En la página de **Información de la aplicación**, especifique el nombre de la compañía como desea que aparezca en el instalador.  Puede utilizar el nombre de su compañía, o bien utilice Contoso para este ejemplo.  Especifique el nombre de aplicación; en este ejemplo, especifique el juego.  Especifique la dirección web de la compañía, o para este ejemplo, utilice http:\/\/www.contoso.com.  
  
7.  En la parte inferior de la pestaña **Asistente para proyectos \(Game Installer\)**, elija el vínculo **Entrevista de la instalación**.  
  
8.  En la página de **Entrevista de la instalación**, en **Desea mostrar un diálogo del contrato de licencia**, seleccione el botón de opción de **No**.  Cuando se le pregunte si **desea pedir a los usuarios escribir el nombre de la organización y nombre de usuario**, seleccione el botón de opción **No**.  
  
9. En el **Explorador de soluciones**, expanda el proyecto de **Game Installer**, expanda el nodo de **Organice la configuración** y abra la página de **Información general**.  
  
10. En la pestaña de **Información general \(Game Installer\)** en la ventana del editor, especifique **Identificador del Autor de la etiqueta**, por ejemplo, regid.2012\-12.com.Contoso.  
  
11. En el **Explorador de soluciones**, bajo el proyecto de **Game Installer**, expanda el nodo de **Especifique los datos de la aplicación** y abra la página de **Archivos**.  
  
12. En la pestaña de **Archivos \(Game Installer\)** en la ventana del editor, en **Archivos de equipo de origen**, abra el menú contextual para **Resultado principal del juego** y elija **Copia**.  
  
13. Abra un menú contextual en el espacio en la columna de **Nombre** en **Archivos de equipo de destino** y elija **Pegar**.  Aparecerá un nuevo elemento denominado **Game.Primary Output**.  
  
14. En el **Explorador de soluciones**, bajo el nodo de **Especifique los datos de la aplicación**, abra la página de **Redistribuibles**.  
  
15. En la pestaña de **Redistribuibles \(Game Installer\)** en la ventana del editor, active la casilla de **Visual C\+\+ 11.0 CRT \(x86\)**.  
  
16. En la barra de menús, elija **Compilación**, **Compilar solución** para compilar el proyecto de juego y el proyecto de instalador de juego.  
  
17. En la carpeta de soluciones, busque el programa setup.exe compilado del proyecto de instalador de juego y después ejecútelo para instalar la aplicación de juego en el equipo.  Puede copiar este archivo para instalar la aplicación y sus archivos de biblioteca necesarios en otro equipo.  
  
18. Puede establecer muchas opciones en el proyecto de instalación para satisfacer sus requisitos.  Para obtener más información, en **Explorador de soluciones**, en el proyecto de **Game Installer**, abra la página **Introducción** y, a continuación, seleccione la tecla F1 para abrir la biblioteca de Ayuda ISLE.  
  
## Pasos siguientes  
 **Anterior:** [Tutorial: Depurar un proyecto \(C\+\+\)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## Vea también  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)