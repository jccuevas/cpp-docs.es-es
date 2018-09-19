---
title: Implementar una aplicación mediante el paquete redistribuible (C++) | Microsoft Docs
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
ms.openlocfilehash: 569c5c8adcb57ae92f111929efca544c76412a4b
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895284"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Tutorial: Implementar una aplicación de Visual C++ mediante el paquete redistribuible de Visual C++

En este artículo paso a paso se describe cómo usar el paquete redistribuible de Visual C++ para implementar una aplicación de Visual C++.

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, debe tener estos componentes:

- Un equipo con Visual Studio instalado.

- Un equipo adicional que no tenga las bibliotecas de Visual C++.

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Para usar el paquete redistribuible de Visual C++ para implementar una aplicación

1. Cree y compile una aplicación MFC siguiendo los tres primeros pasos de [Tutorial: Implementar una aplicación de Visual C++ mediante un proyecto de instalación](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

2. Cree un archivo, denomínelo setup.bat y agréguele los comandos siguientes. Cambie `MyMFCApplication` por el nombre del proyecto.

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```  

3. Cree un archivo de instalación autoextraíble:

   1. En un símbolo del sistema o en la ventana **Ejecutar**, ejecute iexpress.exe.

   2. Seleccione **Crear un nuevo archivo Self Extraction Directive** y, después, haga clic en el botón **Siguiente**.

   3. Seleccione **Extract files and run an installation command** (Extraer los archivos y ejecutar un comando de instalación) y, después, haga clic en el botón **Siguiente**.

   4. En el cuadro de texto, escriba el nombre de la aplicación MFC y, después, haga clic en el botón **Siguiente**.

   5. En la página **Pregunta de confirmación**, seleccione **No preguntar** y, después, haga clic en el botón **Siguiente**.

   6. En la página **Contrato de licencia**, seleccione **Do not display a license** (No mostrar una licencia) y, después, haga clic en **Siguiente**.

   7. En la página **Archivos del paquete**, agregue los archivos siguientes y, después, haga clic en **Siguiente**.

      - La aplicación MFC (archivo .exe).

      - vcredist_x86.exe. Este archivo se encuentra en \Archivos de programa\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\vcredist_x86\\.

      - El archivo setup.bat que creó en el paso anterior.

   8. En la página **Install Program to Launch** (Programa de instalación para iniciar), en el cuadro de texto **Programa de instalación**, escriba la línea de comandos siguiente y, después, haga clic en **Siguiente**.

      **cmd.exe /c "setup.bat"**  

   9. En la página **Mostrar ventana**, Seleccione **Predeterminada** y, después, haga clic en **Siguiente**.

   10. En la página **Finished message** (Mensaje finalizado), seleccione **Sin mensaje** y, después, haga clic en **Siguiente**.

   11. En la página **Package Name and Options** (Nombre y opciones del paquete), escriba un nombre para el archivo de instalación autoextraíble, seleccione la opción **Store files using Long File Name inside Package** (Almacenar los archivos con el nombre de archivo largo dentro del paquete) y, después, haga clic en **Siguiente**. El final del nombre de archivo debe ser Setup.exe; for ejemplo, MyMFCApplicationSetup.exe.

   12. En la página **Configure restart** (Configurar reinicio), seleccione **No restart** (Sin reinicio) y, después, haga clic en **Siguiente**.

   13. En la página **Save Self Extraction Directive** (Guardar directiva de extracción automática), seleccione **Save Self Extraction Directive (SED) file** (Guardar archivo de directiva de extracción automática [SED]) y, después, haga clic en **Siguiente**.

   14. En la página **Crear paquete**, haga clic en **Siguiente**.

4. Pruebe el archivo de instalación autoextraíble en el otro equipo, que no tiene las bibliotecas de Visual C++:

   1. En el otro equipo, descargue una copia del archivo de instalación y, después, ejecútelo para instalarlo y siga los pasos que proporciona.

   2. Ejecute la aplicación MFC.

      El archivo de instalación autoextraíble instala la aplicación MFC que se encuentra en la carpeta que especificó en el paso 2. La aplicación se ejecuta correctamente porque el instalador del paquete redistribuible de Visual C++ se incluye en el archivo de instalación autoextraíble.

      > [!IMPORTANT]
      > Para determinar qué versión del runtime está instalada, el programa de instalación comprueba la clave del Registro \HKLM\SOFTWARE\Microsoft\VisualStudio\11.0\VC\Runtime\\[plataforma]. Si la versión instalada actualmente es más reciente que la que el programa de instalación está intentando instalar, el programa de instalación devuelve un valor correcto sin instalar la versión anterior y deja una entrada adicional en la página de programas instalados del Panel de Control.

## <a name="see-also"></a>Vea también

[Ejemplos de implementación](../ide/deployment-examples.md)