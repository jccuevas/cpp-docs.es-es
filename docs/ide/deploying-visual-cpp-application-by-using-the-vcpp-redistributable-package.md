---
title: "Tutorial: Implementar una aplicaci&#243;n de Visual C++ mediante el paquete redistribuible de Visual C++ | Microsoft Docs"
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
  - "tutorial, implementar una aplicación de Visual C++ mediante el paquete redistribuible"
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Implementar una aplicaci&#243;n de Visual C++ mediante el paquete redistribuible de Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este artículo paso a paso describe cómo usar el paquete redistribuible de Visual C\+\+ para implementar una aplicación de Visual C\+\+.  
  
## Requisitos previos  
 Debe tener estos componentes para completar este tutorial:  
  
-   Un equipo que tiene instalado Visual Studio.  
  
-   Un equipo adicional que no disponga de las bibliotecas de Visual C\+\+.  
  
### Para usar el paquete redistribuible de Visual C\+\+ para implementar una aplicación  
  
1.  Cree y compile una aplicación MFC siguiendo los tres primeros pasos de [Walkthrough: Deploying a Visual C\+\+ Application By Using a Setup Project](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
2.  Cree un archivo, denomínelo setup.bat, y agregue los comandos siguientes para.  Cambie `MyMFCApplication` al nombre del proyecto.  
  
    ```  
    @echo off  
    vcredist_x86.exe  
    mkdir "C:\Program Files\MyMFCApplication"  
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"  
    ```  
  
3.  Cree un archivo de instalación autoextraíble:  
  
    1.  En un símbolo del sistema o en la ventana **Ejecutar** , ejecute iexpress.exe.  
  
    2.  **Cree el nuevo archivo auto de la directiva de extracción** seleccione y elija el botón **Siguiente** .  
  
    3.  **Archivos de extraer y ejecute un comando de instalación** seleccione y elija **Siguiente**.  
  
    4.  En el cuadro de texto, escriba el nombre de la aplicación MFC y elija **Siguiente**.  
  
    5.  En la página **Indicador de confirmación** , **Ningún indicador** seleccione y elija **Siguiente**.  
  
    6.  En la página **Contrato de licencia** , **No muestre una licencia** seleccione y elija **Siguiente**.  
  
    7.  En la página **Archivos empaquetados** , agregue los siguientes archivos y elija **Siguiente**.  
  
        -   La aplicación MFC \(archivo .exe\).  
  
        -   vcredist\_x86.exe.  Este archivo se encuentra en \\program files\\microsoft sdks\\windows\\v7.0a\\bootstrapper\\packages \\ vcredist\_x86 \\.  
  
        -   El archivo setup.bat que creó en el paso anterior.  
  
    8.  En la página del **Programa de instalación al iniciar** , en el cuadro de texto **Programa de instalación** , escriba la siguiente línea de comandos y elija **Siguiente**.  
  
         **cmd.exe \/c "setup.bat"**  
  
    9. En la página **Ventana de presentación** , **Predeterminado** seleccione y elija **Siguiente**.  
  
    10. En la página **Mensaje finalizado** , **Ningún mensaje** seleccione y elija **Siguiente**.  
  
    11. En la página **Nombre del paquete y opciones**, escriba un nombre para el archivo de instalación autoextraíble, seleccione la opción **Archivos de almacenamiento mediante el paquete dentro de nombre largo de archivo** , y después elija **Siguiente**.  El final del nombre de archivo debe ser el ejemplo de Setup.exe\-for, MyMFCApplicationSetup.exe.  
  
    12. En la página **Configure el reinicio** , **Ningún reinicio** seleccione y elija **Siguiente**.  
  
    13. En la página **Guarde la directiva auto de extracción** , **Guarde el archivo de directivas de \(SED\) de extracción auto** seleccione y elija **Siguiente**.  
  
    14. En la página **Crear paquete** , elija **Siguiente**.  
  
4.  Pruebe el archivo de instalación autoextraíble en otro equipo, que no tiene las bibliotecas de Visual C\+\+:  
  
    1.  En otro equipo, descargue una copia del archivo de instalación y, a continuación instalela ejecutándola y siguiendo los pasos que proporcionan.  
  
    2.  Ejecute la aplicación MFC.  
  
         El archivo de instalación autoextraíble instala la aplicación MFC que está en la carpeta que especificó en el paso 2.  La aplicación se ejecuta correctamente porque el instalador del paquete redistribuible de Visual C\+\+ está incluido en el archivo de instalación autoextraíble.  
  
        > [!IMPORTANT]
        >  Para determinar qué versión del runtime instalada, las comprobaciones de instalador la clave del Registro \\HKLM\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\VC\\Runtimes \\ \[plataforma\].  Si la versión instalada actualmente es más reciente que la versión que el instalador intenta instalar, el instalador devuelve correctamente sin instalar la versión anterior y sale de una entrada adicional en la página instalada de programas en el Panel de control.  
  
## Vea también  
 [Ejemplos de implementación](../ide/deployment-examples.md)