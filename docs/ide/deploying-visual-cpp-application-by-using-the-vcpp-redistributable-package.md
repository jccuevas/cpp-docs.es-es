---
title: Implementar una aplicación mediante el paquete redistribuible (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37bba00efdf0368973fa4ffbac1cbc6bb6298ce1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Tutorial: Implementar una aplicación de Visual C++ mediante el paquete redistribuible de Visual C++
En este artículo paso a paso describe cómo usar el paquete redistribuible de Visual C++ para implementar una aplicación de Visual C++.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Debe disponer de estos componentes para completar este tutorial:  
  
-   Un equipo que tiene instalado Visual Studio.  
  
-   Un equipo adicional que no tenga las bibliotecas de Visual C++.  
  
### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Usar el paquete redistribuible de Visual C++ para implementar una aplicación  
  
1.  Cree y compile una aplicación MFC siguiendo los tres primeros pasos en [Tutorial: implementar una Visual C++ aplicación mediante un proyecto de instalación](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
2.  Crear un archivo, denomínelo setup.bat y agregue los siguientes comandos en ella. Cambio `MyMFCApplication` para el nombre del proyecto.  
  
    ```cmd
    @echo off  
    vcredist_x86.exe  
    mkdir "C:\Program Files\MyMFCApplication"  
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"  
    ```  
  
3.  Crear un archivo de instalación autoextraíble:  
  
    1.  En un símbolo del sistema o en la **ejecutar** ventana, ejecute iexpress.exe.  
  
    2.  Seleccione **crear nuevo archivo de directiva de extracción automática** y, a continuación, elija la **siguiente** botón.  
  
    3.  Seleccione **extraer los archivos y ejecutar un comando de instalación** y, a continuación, elija **siguiente**.  
  
    4.  En el cuadro de texto, escriba el nombre de la aplicación MFC y, a continuación, elija **siguiente**.  
  
    5.  En el **mensaje de confirmación** página, seleccione **ningún símbolo del sistema** y, a continuación, elija **siguiente**.  
  
    6.  En el **del acuerdo de licencia** página, seleccione **no muestran una licencia** y, a continuación, elija **siguiente**.  
  
    7.  En el **los archivos del paquete** página, agregue los archivos siguientes y, a continuación, elija **siguiente**.  
  
        -   La aplicación de MFC (archivo .exe).  
  
        -   vcredist_x86.exe. Este archivo se encuentra en \Program SDKs\Windows\v7.0A\Bootstrapper\Packages\vcredist_x86\\.  
  
        -   El archivo setup.bat que creó en el paso anterior.  
  
    8.  En el **programa de instalación para iniciar** página, en la **programa de instalación de** cuadro de texto, escriba la siguiente línea de comandos y, a continuación, elija **siguiente**.  
  
         **cmd.exe /c "setup.bat"**  
  
    9. En el **Mostrar ventana** página, seleccione **predeterminado** y, a continuación, elija **siguiente**.  
  
    10. En el **mensaje finalizado** página, seleccione **ningún mensaje** y, a continuación, elija **siguiente**.  
  
    11. En el **nombre de paquete y sus opciones** página, escriba un nombre para el archivo de instalación autoextraíble, seleccione la **almacenar los archivos con el nombre de archivo largo dentro de paquete** opción y, a continuación, elija **siguiente**. El final del nombre de archivo debe ser Setup.exe—for ejemplo, MyMFCApplicationSetup.exe.  
  
    12. En el **configurar reinicio** página, seleccione **sin reiniciar el equipo** y, a continuación, elija **siguiente**.  
  
    13. En el **Save Self Extraction Directive** página, seleccione **archivo de directiva de extracción automática guardar (SED)** y, a continuación, elija **siguiente**.  
  
    14. En el **crear paquete** página, elija **siguiente**.  
  
4.  Probar el archivo de instalación autoextraíble en el otro equipo, que no está disponible en las bibliotecas de Visual C++:  
  
    1.  En el otro equipo, descargue una copia del archivo de instalación y vuelva a instalarlo después ejecutarlo y siguiendo los pasos que proporciona.  
  
    2.  Ejecute la aplicación MFC.  
  
         El archivo de instalación autoextraíble instala la aplicación MFC que se encuentra en la carpeta que especificó en el paso 2. La aplicación se ejecuta correctamente porque el instalador del paquete redistribuible de Visual C++ se incluye en el archivo de instalación autoextraíble.  
  
        > [!IMPORTANT]
        >  Para determinar qué versión del runtime está instalada, el programa de instalación comprueba la \HKLM\SOFTWARE\Microsoft\VisualStudio\11.0\VC\Runtimes clave del registro\\[plataforma]. Si la versión instalada actualmente es más reciente que la versión que está intentando instalar el programa de instalación, el programa de instalación devuelve un valor correcto sin tener que instalar la versión anterior y deja una entrada adicional en la página de programas instalados en el Panel de Control.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplos de implementación](../ide/deployment-examples.md)