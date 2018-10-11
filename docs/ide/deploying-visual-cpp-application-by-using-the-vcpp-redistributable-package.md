---
title: Implementar una aplicación mediante el paquete redistribuible (C++) | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
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
ms.openlocfilehash: 9759811554fd0998a919c9939a0441c63c26a3f8
ms.sourcegitcommit: 338e1ddc2f3869d92ba4b73599d35374cf1d5b69
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494353"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Tutorial: Implementar una aplicación de Visual C++ mediante el paquete redistribuible de Visual C++

En este artículo paso a paso se describe cómo usar el paquete redistribuible de Visual C++ para implementar una aplicación de Visual C++.

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, debe tener estos componentes:

- Un equipo con Visual Studio instalado.

- Un equipo adicional que no tenga las bibliotecas de Visual C++.

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Para usar el paquete redistribuible de Visual C++ para implementar una aplicación

1.  Cree y compile una aplicación MFC siguiendo los pasos de [Tutorial: Implementar una aplicación de Visual C++ mediante un proyecto de instalación](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Cree un archivo, denomínelo setup.bat y agréguele los comandos siguientes. Cambie `MyMFCApplication` por el nombre del proyecto.

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```

1. Cree un archivo de instalación autoextraíble:

   1. En un símbolo del sistema o en la ventana **Ejecutar**, ejecute iexpress.exe.

   1. Seleccione **Crear un nuevo archivo Self Extraction Directive** y, después, haga clic en el botón **Siguiente**.

   1. Seleccione **Extract files and run an installation command** (Extraer los archivos y ejecutar un comando de instalación) y, después, haga clic en el botón **Siguiente**.

   1. En el cuadro de texto, escriba el nombre de la aplicación MFC y, después, haga clic en el botón **Siguiente**.

   1. En la página **Pregunta de confirmación**, seleccione **No preguntar** y, después, haga clic en el botón **Siguiente**.

   1. En la página **Contrato de licencia**, seleccione **Do not display a license** (No mostrar una licencia) y, después, haga clic en **Siguiente**.

   1. En la página **Archivos del paquete**, agregue los archivos siguientes y, después, haga clic en **Siguiente**.

      - La aplicación MFC (archivo .exe).

      - vcredist_x86.exe. Este archivo se encuentra en \Archivos de programa (x86)\Microsoft Visual Studio \<versión>\SDK\Bootstrapper\Packages\. También puede descargar este archivo desde [Microsoft](https://www.microsoft.com/download/confirmation.aspx?id=5555).

      - El archivo setup.bat que creó en el paso anterior.

   1. En la página **Install Program to Launch** (Programa de instalación para iniciar), en el cuadro de texto **Programa de instalación**, escriba la línea de comandos siguiente y, después, haga clic en **Siguiente**.

      **cmd.exe /c "setup.bat"**

   1. En la página **Mostrar ventana**, Seleccione **Predeterminada** y, después, haga clic en **Siguiente**.

   1. En la página **Finished message** (Mensaje finalizado), seleccione **Sin mensaje** y, después, haga clic en **Siguiente**.

   1. En la página **Package Name and Options** (Nombre y opciones del paquete), escriba un nombre para el archivo de instalación autoextraíble, seleccione la opción **Store files using Long File Name inside Package** (Almacenar los archivos con el nombre de archivo largo dentro del paquete) y, después, haga clic en **Siguiente**. El final del nombre de archivo debe ser Setup.exe; por ejemplo, *MyMFCApplicationSetup.exe*.

   1. En la página **Configure restart** (Configurar reinicio), seleccione **No restart** (Sin reinicio) y, después, haga clic en **Siguiente**.

   1. En la página **Save Self Extraction Directive** (Guardar directiva de extracción automática), seleccione **Save Self Extraction Directive (SED) file** (Guardar archivo de directiva de extracción automática [SED]) y, después, haga clic en **Siguiente**.

   1. En la página **Crear paquete**, haga clic en **Siguiente**. Elija **Finalizar**.

1. Pruebe el archivo de instalación autoextraíble en el otro equipo, que no tiene las bibliotecas de Visual C++:

   1. En el otro equipo, descargue una copia del archivo de instalación y, después, ejecútelo para instalarlo y siga los pasos que proporciona. Según las opciones seleccionadas, la instalación podría requerir el comando **Ejecutar como administrador**.

   1. Ejecute la aplicación MFC.

      El archivo de instalación autoextraíble instala la aplicación MFC que se encuentra en la carpeta que especificó en el paso 2. La aplicación se ejecuta correctamente porque el instalador del paquete redistribuible de Visual C++ se incluye en el archivo de instalación autoextraíble.

      > [!IMPORTANT]
      > Para determinar qué versión del tiempo de ejecución está instalada, el programa de instalación comprueba la clave del Registro \HKLM\SOFTWARE\Microsoft\VisualStudio\\\<versión>\VC\Runtimes\\<platform>. Si la versión instalada actualmente es más reciente que la que el programa de instalación está intentando instalar, el programa de instalación devuelve un valor correcto sin instalar la versión anterior y deja una entrada adicional en la página de programas instalados del Panel de Control.

## <a name="see-also"></a>Vea también

[Ejemplos de implementación](deployment-examples.md)<br/>
