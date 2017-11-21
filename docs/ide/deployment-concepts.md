---
title: "Conceptos de implementación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Installer [C++]
- dependencies [C++], application deployment and
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- libraries [C++], application deployment issues
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3b3aaf970e51f867d36cae288e8d025730093937
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="deployment-concepts"></a>Conceptos de implementación
En esta sección se explica las consideraciones principales para implementar aplicaciones de C++.  
  
## <a name="windows-installer-deployment-in-c"></a>Implementación de Windows Installer en C++  
 Proyectos de Visual C++ suelen utilizan el programa de instalación de Windows Installer tradicional para la implementación. Para preparar una implementación de Windows Installer, empaquetar la aplicación en un archivo setup.exe y distribuir ese archivo, junto con un paquete de instalador (.msi). Los usuarios, a continuación, ejecutan setup.exe para instalar la aplicación.  
  
 Empaquetar la aplicación mediante la adición de un proyecto de instalación a la solución; Cuando compila, crea la instalación y el instalador de archivos de paquete que se distribuyen a los usuarios. Para obtener más información, consulte [elegir un método de implementación](../ide/choosing-a-deployment-method.md).  
  
## <a name="library-dependencies"></a>Dependencias de biblioteca  
 Cuando se compila una aplicación de C/C ++ mediante la funcionalidad proporcionada por las bibliotecas de Visual C++, se vuelve dependiente de la presencia de dichas bibliotecas en tiempo de ejecución. En orden para ejecutar la aplicación, debe vincular, estática o dinámicamente, a las bibliotecas de Visual C++ es necesarias. Si una aplicación dinámicamente vínculos a una biblioteca de Visual C++, a continuación, cuando se ejecuta dicha biblioteca deben estar presentes para que se puede cargar. Por otro lado, si la aplicación se vincula estáticamente a una biblioteca de Visual C++, a continuación, no es necesario el archivo DLL correspondiente esté presente en el equipo del usuario. Sin embargo, se la vinculación estática, tiene algunos efectos negativos, por ejemplo, el aumento del tamaño de los archivos de aplicación y realizar el mantenimiento sea más difícil. Para obtener más información, consulte [ventajas de utilizar archivos DLL](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls).  
  
## <a name="packaging-and-redistributing"></a>Empaquetado y redistribución  
 Bibliotecas de Visual C++ se empaquetan como archivos DLL y todas las bibliotecas necesarias para las aplicaciones de C o C++ se instalan Visual Studio en el equipo del desarrollador. Sin embargo, al implementar su aplicación a los usuarios, no es factible en la mayoría de los casos a necesario volver a instalar Visual Studio para ejecutar la aplicación. Es importante poder redistribuir solamente las partes de Visual C++ que son requeridas por la aplicación se ejecute correctamente.  
  
 Para obtener más información sobre cómo empaquetar y redistribuir, vea los temas siguientes:  
  
-   [Determinar qué archivos DLL se redistribuirán](../ide/determining-which-dlls-to-redistribute.md).  
  
-   [Elegir un método de implementación](../ide/choosing-a-deployment-method.md).  
  
 Para obtener ejemplos de implementación y sugerencias sobre solución de problemas, consulte:  
  
-   [Ejemplos de implementación](../ide/deployment-examples.md).  
  
-   [Solución de problemas de C o C++ aplicaciones aisladas y ensamblados en paralelo](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).  
  
## <a name="see-also"></a>Vea también  
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Descripción de las dependencias de una aplicación de Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)   
 [Implementación de Windows Installer](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)