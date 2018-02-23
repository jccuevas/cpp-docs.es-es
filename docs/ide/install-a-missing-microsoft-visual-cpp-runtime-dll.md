---
title: "Instalar una DLL que falta de Visual C++ en tiempo de ejecución de Microsoft | Documentos de Microsoft"
description: "Cómo buscar e instalar los archivos DLL en tiempo de ejecución de Visual C++ que faltan."
ms.date: 08/30/2017
ms.topic: article
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d40e1594b2190d4bbfd2fe52fddaad04af527573
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2018
---
# <a name="install-a-missing-microsoft-visual-c-runtime-dll"></a>Instalar una DLL que falta de Visual C++ en tiempo de ejecución de Microsoft

Programas creados con Microsoft Visual C++ a menudo requieren algunos archivos de biblioteca en tiempo de ejecución de Visual C++ adicionales o archivos DLL, para que se ejecute. Tiempo de ejecución de estas DLL están disponibles en un *Redistributable Package*, un programa de instalación del archivo de biblioteca, para cada versión de Visual C++. Su programa de instalación debe incluir el paquete redistribuible requerido por cualquier programa. Si no es así, en ocasiones, puede instalar un paquete redistribuible usted mismo y corregir un error del sistema al ejecutar el programa. 

Puede indicar que un programa le falta un archivo DLL de tiempo de ejecución de Visual C++ si recibe un error del sistema al iniciar el programa que dice algo como "el programa no se puede iniciar porque VCRuntime140.dll no está presente en el equipo". A menudo, se puede corregir este problema mediante la desinstalación del programa, a continuación, volver a instalarla. Se recomienda intentar este paso en primer lugar, antes de cualquier otro posibles correcciones.

A veces, el paquete redistribuible instalado por un programa está anticuado. Microsoft hace que las versiones actualizadas de lo archivos DLL en tiempo de ejecución estén disponibles de vez en cuando, para resolver errores y problemas de seguridad. Para mantener el equipo que ejecuta de forma segura y correcta, es una buena idea usar la actualización más reciente de cualquier archivo DLL en tiempo de ejecución. Compruebe si hay un instalador actualizado disponible para el programa, que puede proporcionar esta actualización automáticamente. Si no hay, a continuación, utilice al instalador actualizado para volver a instalar el programa.

Si volver a instalar el programa no hace que el error del sistema desaparecer, a continuación, el programa de instalación puede esté roto o dañado, o lo archivos DLL de tiempo de ejecución en el equipo puede estar dañada. Intente descargar una nueva copia del instalador para el programa y utilizarlo para volver a instalar primero. Si esto no funciona, o un instalador no está disponible, a continuación, puede merecer la pena para comprobar las instalaciones de Microsoft Visual C++ Redistributable en el equipo. 

Esta tabla muestra una lista de los archivos DLL que se incluyen en uno o más paquetes redistribuibles, junto con los vínculos para descargar una copia del paquete redistribuible. Antes de descargar una nueva copia del paquete redistribuible, debería ver si puede reparar una instalación existente.

|Falta el archivo DLL  |Paquete redistribuible  |
|---------|---------|
|atl80.dll<br />msvcm80.dll<br />msvcp80.dll<br />msvcr80.dll<br />mfc80.dll<br />mfc80u.dll<br />mfcm80.dll<br />mfcm80u.dll|[Microsoft Visual C++ 2005 Redistributable (x86)](https://www.microsoft.com/en-us/download/details.aspx?id=5638)<br />[Paquete redistribuible de Microsoft Visual C++ 2005 (x64)](https://www.microsoft.com/en-us/download/details.aspx?id=18471)<br />[Actualización de seguridad MFC de paquete redistribuible de Microsoft Visual C++ 2005 Service Pack 1](https://www.microsoft.com/en-us/download/details.aspx?id=26347)|
|atl90.dll<br />msvcr90.dll<br />msvcm90.dll<br />msvcp90.dll<br />mfc90.dll<br />mfc90u.dll<br />mfcmifc80.dll<br />mfcm90.dll<br />mfcm90u.dll|[Microsoft Visual C++ 2008 Redistributable - x86](https://www.microsoft.com/en-us/download/details.aspx?id=5582)<br />[Microsoft Visual C++ 2008 Redistributable - x64](https://www.microsoft.com/en-us/download/details.aspx?id=2092)<br />[Actualización de seguridad MFC de paquete redistribuible de Microsoft Visual C++ 2008 Service Pack 1](https://www.microsoft.com/en-us/download/details.aspx?id=26368)|
|atl100.dll<br />msvcr100.dll<br />msvcp100.dll<br />msdia71.dll<br />vcomp100.dll<br />mfc100.dll<br />mfc100u.dll<br />mfcmifc80.dll<br />mfcm100.dll<br />mfcm100u.dll|[Microsoft Visual C++ 2010 x86 redistribuible](https://www.microsoft.com/en-us/download/details.aspx?id=8328)<br />[Microsoft Visual C++ 2010 x64 redistribuible](https://www.microsoft.com/en-us/download/details.aspx?id=13523)<br />[Actualización de seguridad MFC de paquete redistribuible de Microsoft Visual C++ 2010 Service Pack 1](https://www.microsoft.com/en-us/download/details.aspx?id=26999)|
|atl110.dll<br />msvcr110.dll<br />msvcp110.dll<br />mfc110.dll<br />mfc110u.dll<br />mfcmifc80.dll<br />mfcm110.dll<br />mfcm110u.dll<br />concrt110.dll<br />vccorlib110.dll<br />vcamp110.dll<br />vcomp110.dll|[Microsoft Visual C++ 2012 Redistributable (para Visual Studio 2012 Update 4)](https://www.microsoft.com/en-us/download/details.aspx?id=30679)|
|msvcr120.dll<br />msvcp120.dll<br />mfc120.dll<br />mfc120u.dll<br />mfcmifc80.dll<br />mfcm120.dll<br />mfcm120u.dll<br />concrt120.dll<br />vccorlib120.dll<br />vcamp120.dll<br />vcomp120.dll|[Microsoft Visual C++ 2013 Redistributable (vínculos a las descargas individuales)](https://support.microsoft.com/en-us/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package)<br />[Biblioteca MFC multibyte para Visual Studio 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40770)<br />[Visual C++ 2013 en tiempo de ejecución para las aplicaciones de instalación de prueba de Windows 8.1 (descarga de .zip)](http://download.microsoft.com/download/5/F/0/5F0F8404-9329-44A9-8176-ED6F7F746F25/VCLibs_Redist_Packages.zip)|
|vcruntime140.dll<br />vcruntime140_app.dll<br />msvcp140.dll<br />mfc140.dll<br />mfc140u.dll<br />mfcmifc80.dll<br />mfcm140.dll<br />mfcm140u.dll<br />concrt140.dll<br />vccorlib140.dll<br />vcamp140.dll<br />vcomp140.dll|[Microsoft Visual C++ 2017 (x86) redistribuible](https://go.microsoft.com/fwlink/?LinkId=746571)<br />[Microsoft Visual C++ 2017 (x64) redistribuible](https://go.microsoft.com/fwlink/?LinkId=746572)|
|msvcr100_clr0400.dll<br />msvcr110_clr0400.dll<br />msvcr120_clr0400.dll|[Descargar .NET Framework](https://www.microsoft.com/net/download/framework)|

### <a name="to-repair-an-existing-redistributable-package"></a>Para reparar un paquete redistribuible existente

1. Abra el Panel de Control. En Windows 10, escriba *el panel de control* en el escritorio de control de búsqueda en la barra de tareas y, a continuación, elija **el Panel de Control** entre las opciones.

2. En el Panel de Control, elija **programas** > **programas y características**. Seleccione la versión de Microsoft Visual C++ Redistributable que corresponde al archivo DLL que falta. Si un **cambio** botón aparece en la parte superior de la lista, selecciónelo. Si es la única opción **desinstalar**, no se puede reparar esta versión del paquete redistribuible.

3. Elija **reparación** en el cuadro de diálogo de instalación para el paquete redistribuible. Que necesite reiniciar una vez completada la reparación. 