---
title: Redistribuir archivos de Visual C++ | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
caps.latest.revision: "50"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 106123557c4efab5ccddf9f1292570d36b0f8313
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="redistributing-visual-c-files"></a>Redistribuir archivos de Visual C++
Al implementar una aplicación, también debe implementar los archivos necesarios para asistirla. Si alguno de estos archivos los proporciona Microsoft, compruebe si está permitida su redistribución. Para revisar los términos de licencia de Visual Studio, vea el vínculo términos de licencia en el cuadro de diálogo acerca de Microsoft Visual Studio en el IDE o descargar el [términos de licencia del Software de Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=831114) archivo. Para ver la "lista REDIST" que se hace referencia en la sección "Código distribuible" de los términos de licencia del Software de Microsoft para determinadas ediciones de Visual Studio, vea [código distribuible para Microsoft Visual Studio 2017 y Microsoft Visual Studio 2017 SDK (incluye utilidades y archivos BuildServer)](http://go.microsoft.com/fwlink/p/?LinkId=823098), o para Visual Studio 2015, vea [código distribuible para Microsoft Visual Studio 2015 y Microsoft Visual Studio 2015 SDK](http://go.microsoft.com/fwlink/p/?LinkId=523763). Para obtener más información acerca de los archivos redistribuibles, consulte [determinar qué archivos DLL se redistribuirán](../ide/determining-which-dlls-to-redistribute.md) y [ejemplos de implementación](../ide/deployment-examples.md).  
  
 Para implementar los archivos redistribuibles de Visual C++, puede usar los paquetes redistribuibles de Visual C++ (VCRedist\_x86.exe, VCRedist\_x64.exe o VCRedist\_arm.exe) que se incluyen en Visual Studio. En Visual Studio de 2017, estos archivos pueden encontrarse en los archivos de programa [(x86)]\\Microsoft Visual Studio\\2017\\_edición_\\VC\\Redist\\ MSVC\\_lib versión_ carpeta, donde _edición_ es la edición de Visual Studio instalada, y _versión lib_ es la versión de la bibliotecas para redistribuir. En Visual Studio 2015, estos archivos pueden encontrarse en el directorio de instalación de Visual Studio en archivos de programa [(x 86)] \Microsoft Visual Studio *versión*\VC\redist\\*configuración regional* \\. Otra opción consiste en usar módulos de combinación redistribuibles (archivos .msm), que en Visual Studio de 2017 pueden encontrarse en los archivos de programa [(x 86)]\\Microsoft Visual Studio\\2017\\_edición_ \\ VC\\Redist\\MSVC\\_lib versión_\\MergeModules\\ carpeta. En Visual Studio 2015 puede encontrarlos en programa [(x 86)] \Common módulos\\. También es posible instalar directamente Visual C++ archivos DLL redistribuibles en la *carpeta local de la aplicación*, que es la carpeta que contiene el archivo ejecutable de aplicación. Por razones del servicio, se recomienda no usar esta ubicación para la instalación.  
  
 Los paquetes redistribuibles de Visual C++ instalan y registran todas las bibliotecas de Visual C++. Si usa alguno, debe configurarlo para que se ejecute en el sistema de destino como un requisito previo para la instalación de la aplicación. Se recomienda usar estos paquetes para las implementaciones, ya que habilitan la actualización automática de las bibliotecas de Visual C++. Para obtener un ejemplo sobre cómo usar estos paquetes, consulte [Tutorial: implementar una Visual C++ aplicación mediante el paquete redistribuible de Visual C++](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
 Cada paquete redistribuible de Visual C++ comprueba si existe una versión más reciente en el equipo. Si se encuentra una versión más reciente, el paquete no se instala. A partir de Visual Studio 2015, los paquetes redistribuibles muestran un mensaje de error que indica que la instalación no se pudo realizar. Si se ejecuta un paquete mediante el uso de la **/quiet** marca, ningún mensaje de error se muestra. En cualquier caso, Microsoft Installer registrará un error y devolverá un resultado de error al llamador. A partir de los paquetes de Visual Studio 2015, puede evitar este error si examina el registro para averiguar si hay instalada una versión más reciente. La versión instalada actualmente se almacena en la \Microsoft\VisualStudio HKEY_LOCAL_MACHINE\SOFTWARE [\Wow6432Node]\\_vs-version_\VC\Runtimes\\{x86 | x64 | Clave ARM}, donde _vs-version_ es el número de versión para Visual Studio (14.0 para Visual Studio 2015 y Visual Studio de 2017, porque el paquete redistribuible de 2017 actualizado es binario compatible con la versión 2015), y donde la clave es ARM, x 86 o x64 según las versiones de vcredist instalados para la plataforma. (No es necesario comprobar bajo la subclave Wow6432Node a menos que se utilice RegEdit para ver la versión de la x86 instalado el paquete en un x64 plataforma.) El número de versión se almacena en el valor de cadena REG_SZ **versión** y también en el conjunto de **principal**, **secundaria**, **Bld**y **Rbld** valores REG_DWORD. Para evitar un error durante la instalación, debe omitir la instalación del paquete redistribuible si la versión instalada actualmente es más reciente.  
  
 Si usa un módulo de fusión mediante combinación que contenga un archivo DLL de Visual C++, debe incluirlo en el paquete de Windows Installer (o paquete de instalación similar) que esté usando para implementar la aplicación. Para obtener más información, consulte [redistribuir por mediante módulos de combinación](../ide/redistributing-components-by-using-merge-modules.md). Para obtener un ejemplo, vea [Tutorial: implementar una Visual C++ aplicación mediante un proyecto de instalación](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md), que también muestra cómo usar InstallShield Limited Edition para crear un paquete de instalación.  
  
## <a name="potential-run-time-errors"></a>Posibles errores en tiempo de ejecución  
 Si una biblioteca DLL de Visual C++ no está disponible y Windows no puede cargarla para la aplicación, puede aparecer este mensaje: **esta aplicación no se ha podido iniciar porque MSVCR\<número de versión > .dll no se encontró. La reinstalación de la aplicación puede solucionar el problema.**  
  
 Para resolver este tipo de errores, debe asegurarse de que la aplicación se compila correctamente y de que las bibliotecas de Visual C++ se implementan correctamente en el sistema de destino. Para obtener más información, consulte [descripción de las dependencias de una aplicación de Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Redistribuir mediante módulos de combinación](../ide/redistributing-components-by-using-merge-modules.md)|Describe cómo usar módulos de combinación redistribuibles de Visual C++ para instalar las bibliotecas en tiempo de ejecución de Visual C++ como archivos DLL compartidos en la carpeta %windir%\system32\.|  
|[Redistribuir controles ActiveX de Visual C++](../ide/redistributing-visual-cpp-activex-controls.md)|Describe cómo redistribuir una aplicación que utiliza controles ActiveX.|  
|[Redistribuir archivos de compatibilidad con bases de datos](../ide/redistributing-database-support-files.md)|Analiza cómo redistribuir los archivos de compatibilidad para Data Access Objects (DAO) y las tecnologías de base de datos disponibles en el Kit de desarrollo de software (SDK) de Microsoft Data Access.|  
|[Redistribuir la biblioteca MFC](../ide/redistributing-the-mfc-library.md)|Describe cómo redistribuir una aplicación que utiliza MFC.|  
|[Redistribuir una aplicación ATL](../ide/redistributing-an-atl-application.md)|Describe cómo redistribuir una aplicación que usa ATL. A partir de Visual Studio 2012, no es necesaria ninguna biblioteca redistribuible para ATL.|  
|[Ejemplos de implementación](../ide/deployment-examples.md)|Vínculos a ejemplos que muestran cómo implementar aplicaciones de Visual C++.|  
|[Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)|Presenta los conceptos y las tecnologías de implementación de Visual C++.|