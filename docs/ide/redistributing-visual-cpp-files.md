---
title: "Redistribuir archivos de Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "implementación de aplicaciones [C++], redistribuir archivo"
  - "implementar aplicaciones [C++], redistribuir archivo"
  - "redistribuir archivo [C++]"
  - "redistribuir aplicaciones [C++]"
  - "redistribuir aplicaciones [C++], acerca de la redistribución de aplicaciones"
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
caps.latest.revision: 50
caps.handback.revision: 48
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Redistribuir archivos de Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al implementar una aplicación, también debe implementar los archivos necesarios para asistirla.  Si alguno de estos archivos los proporciona Microsoft, compruebe si está permitida su redistribución.  Para ver los Términos de licencia de software de Microsoft, vea License.htm en el directorio donde esté instalado Visual Studio, o en el disco de instalación de Visual Studio.  Para ver la “lista REDIST” a la que se hace referencia en la sección “Código distribuible” de los Términos de licencia del software de Microsoft para determinadas ediciones de Visual Studio, vea [Código distribuible para Microsoft Visual Studio 2013 y Microsoft Visual Studio 2013 SDK](http://go.microsoft.com/fwlink/p/?LinkId=313603) en el sitio web de Microsoft.  Para obtener más información acerca de los archivos redistribuibles, consulte [Determinar qué archivos DLL se redistribuirán](../ide/determining-which-dlls-to-redistribute.md) y [Ejemplos de implementación](../ide/deployment-examples.md).  
  
 Para implementar los archivos redistribuibles de Visual C\+\+, puede usar los paquetes redistribuibles de Visual C\+\+ \(VCRedist\_x86.exe, VCRedist\_x64.exe o VCRedist\_arm.exe\) que se incluyen en Visual Studio.  Estos archivos pueden encontrarse en el directorio de instalación de Visual Studio en Archivos de programa \[\(x 86\)\]\\*versión* de Microsoft Visual Studio \\VC\\redist\\*locale*\\.  Otra opción es usar módulos de combinación redistribuible \(archivos .msm\), que se encuentran en Archivos de programa \[\(x 86\)\]\\Common Files\\Merge Modules\\.  También es posible instalar directamente los archivos DLL redistribuibles de Visual C\+\+ en la *carpeta local de la aplicación*, que es la carpeta que contiene el archivo ejecutable de la aplicación.  Por razones del servicio, se recomienda no usar esta ubicación para la instalación.  
  
 Los paquetes redistribuibles de Visual C\+\+ instalan y registran todas las bibliotecas de Visual C\+\+.  Si usa alguno, debe configurarlo para que se ejecute en el sistema de destino como un requisito previo para la instalación de la aplicación.  Se recomienda usar estos paquetes para las implementaciones, ya que habilitan la actualización automática de las bibliotecas de Visual C\+\+.  Para obtener un ejemplo sobre cómo utilizar estos paquetes, consulte [Tutorial: Implementar una aplicación de Visual C\+\+ mediante el paquete redistribuible de Visual C\+\+](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
 Cada paquete redistribuible de Visual C\+\+ comprueba si existe una versión más reciente en el equipo.  Si se encuentra una versión más reciente, el paquete no se instala.  A partir de Visual Studio 2015, los paquetes redistribuibles muestran un mensaje de error que indica que la instalación no se pudo realizar.  Si se ejecuta un paquete mediante la marca **\/quiet**, no se mostrará ningún mensaje de error.  En cualquier caso, Microsoft Installer registrará un error y devolverá un resultado de error al llamador.  A partir de los paquetes de 2015 de Visual Studio, puede comprobar un valor del Registro para averiguar si hay instalada una versión más reciente.  La versión actual se almacena como valor REG\_SZ en la clave de versión en HKEY\_LOCAL\_MACHINE\\SOFTWARE\[\\Wow6432Node\]\\Microsoft\\DevDiv\\vc\\Servicing\\14.0\\RuntimeMinimum.  No es necesario instalar el paquete redistribuible si la versión actual instalada es más reciente.  
  
 Si usa un módulo de combinación que contenga un archivo DLL de Visual C\+\+, debe incluirlo en el paquete de Windows Installer \(o paquete de instalación similar\) que esté usando para implementar la aplicación.  Para obtener más información, consulte [Redistribuir mediante módulos de combinación](../ide/redistributing-components-by-using-merge-modules.md).  Para obtener un ejemplo, vea [Tutorial: Implementar una aplicación de Visual C\+\+ mediante un proyecto de instalación](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md), que muestra también cómo usar InstallShield Limited Edition para crear un paquete de instalación.  
  
## Posibles errores en tiempo de ejecución  
 Si una biblioteca DLL de Visual C\+\+ no está disponible y Windows no puede cargarla para la aplicación, puede aparecer este mensaje: **Error de inicio de la aplicación porque el \<número de versión\> del archivo .dll de MSVCR no se encontró. La reinstalación de la aplicación puede solucionar el problema.**  
  
 Para resolver este tipo de errores, debe asegurarse de que la aplicación se compila correctamente y de que las bibliotecas de Visual C\+\+ se implementan correctamente en el sistema de destino.  Para obtener más información, consulte [Descripción de las dependencias de una aplicación de Visual C\+\+](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Redistribuir mediante módulos de combinación](../ide/redistributing-components-by-using-merge-modules.md)|Describe cómo usar los módulos de combinación redistribuibles de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] para instalar las bibliotecas en tiempo de ejecución de Visual C\+\+ como archivos DLL compartidos en la carpeta %windir%\\system32\\.|  
|[Redistribuir controles ActiveX de Visual C\+\+](../ide/redistributing-visual-cpp-activex-controls.md)|Describe cómo redistribuir una aplicación que utiliza controles ActiveX.|  
|[Redistribuir archivos de compatibilidad con bases de datos](../ide/redistributing-database-support-files.md)|Analiza cómo redistribuir los archivos de compatibilidad para Data Access Objects \(DAO\) y las tecnologías de base de datos disponibles en el Kit de desarrollo de software \(SDK\) de Microsoft Data Access.|  
|[Redistribuir la biblioteca MFC](../ide/redistributing-the-mfc-library.md)|Describe cómo redistribuir una aplicación que utiliza MFC.|  
|[Redistribuir una aplicación ATL](../ide/redistributing-an-atl-application.md)|Describe cómo redistribuir una aplicación que usa ATL.  A partir de Visual Studio 2012, no es necesaria ninguna biblioteca redistribuible para ATL.|  
|[Ejemplos de implementación](../ide/deployment-examples.md)|Vínculos a ejemplos que muestran cómo implementar aplicaciones de Visual C\+\+.|  
|[Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)|Presenta los conceptos y las tecnologías de implementación de Visual C\+\+.|