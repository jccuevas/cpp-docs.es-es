---
title: "Conceptos de implementaci&#243;n | Microsoft Docs"
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
  - "implementación de aplicaciones [C++], acerca de la implementación de aplicaciones"
  - "dependencias [C++], implementación de aplicaciones y"
  - "implementar aplicaciones [C++], acerca de la implementación de aplicaciones"
  - "bibliotecas [C++], problemas en la implementación de aplicaciones"
  - "Windows Installer [C++]"
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Conceptos de implementaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta sección trata sobre las consideraciones principales a la hora de implementar las aplicaciones de C\+\+.  
  
## Implementación de Windows Installer en C\+\+  
 Los proyectos de Visual C\+\+ utilizan normalmente la instalación de Windows Installer tradicional para la implementación.  Para preparar una implementación con Windows Installer, se ha de empaquetar la aplicación en un archivo setup.exe y distribuir este archivo junto con un paquete del instalador \(.msi\).  A continuación, los usuarios ejecutarán setup.exe para instalar la aplicación.  
  
 La aplicación se empaqueta agregando un proyecto de instalación a la solución; una vez compilado, crea los archivos del paquete del instalador y de configuración que se distribuyen a los usuarios.  Para obtener más información, vea [Elegir un método de implementación](../ide/choosing-a-deployment-method.md).  
  
## Dependencias de la biblioteca  
 Cuando una aplicación de C\/C\+\+ se compila utilizando una funcionalidad proporcionada por las bibliotecas de Visual C\+\+, se hace dependiente en presencia de dichas bibliotecas en tiempo de ejecución.  Para que la aplicación se ejecute, se debe vincular, estática o dinámicamente, a las bibliotecas de Visual C\+\+ necesarias.  Si una aplicación se vincula dinámicamente a una biblioteca de Visual C\+\+, cuando se ejecute, esa biblioteca debe estar presente para que se puede cargar.  Por otro lado, si la aplicación se vincula estáticamente a una biblioteca de Visual C\+\+, no es necesario que el archivo DLL correspondiente esté presente en el equipo del usuario.  Sin embargo, la vinculación estática tiene algunos efectos negativos, como el aumento del tamaño de los archivos de la aplicación y la posibilidad de que el mantenimiento sea más difícil.  Para obtener más información, vea [Ventajas de utilizar archivos DLL](../build/advantages-of-using-dlls.md).  
  
## Empaquetado y redistribución  
 Las bibliotecas de Visual C\+\+ se empaquetan como archivos DLL y todas las bibliotecas necesarias para las aplicaciones de C\/C\+\+ las instala Visual Studio en el equipo del desarrollador.  Sin embargo, al implementar la aplicación para sus usuarios, no es factible en muchos casos pedirles que instalen Visual Studio para ejecutar la aplicación.  Es importante redistribuir solamente las partes de Visual C\+\+ que necesita la aplicación para ejecutarse correctamente.  
  
 Para obtener más información sobre el empaquetado y la redistribución, vea los siguientes temas:  
  
-   [Determinar qué archivos DLL se redistribuirán](../ide/determining-which-dlls-to-redistribute.md).  
  
-   [Elegir un método de implementación](../ide/choosing-a-deployment-method.md).  
  
 Si desea obtener ejemplos de implementación y sugerencias para solucionar problemas, vea:  
  
-   [Ejemplos de implementación](../ide/deployment-examples.md).  
  
-   [Solución de problemas](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).  
  
## Vea también  
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Descripción de las dependencias de una aplicación de Visual C\+\+](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)   
 [Windows Installer Deployment](http://msdn.microsoft.com/es-es/121be21b-b916-43e2-8f10-8b080516d2a0)