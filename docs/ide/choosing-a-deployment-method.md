---
title: "Elegir un método de implementación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- redistributing DLLs
- manifests [C++]
- DLLs [C++], redistributing
- side-by-side assemblies [C++]
- dynamic linking [C++]
- application deployment [C++], methods
- deploying applications [C++], methods
- static linking [C++]
- libraries [C++], application deployment issues
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
caps.latest.revision: "35"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c444b3319c60b80bdfdc14000a41d65869d0514
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="choosing-a-deployment-method"></a>Elegir un método de implementación
A menos que la aplicación de Visual C++ es independiente entre sí y se puede implementar mediante un comando de copia, se recomienda utilizar a Windows Installer para la implementación. Windows Installer admite la instalación, la reparación y la desinstalación, y también admite la actualización atómica de archivos, dependencias y entradas del Registro de una aplicación.  
  
> [!NOTE]
>  Aunque [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) implementación para aplicaciones nativas de Visual C++ es posible en Visual Studio, esto requiere pasos adicionales. Para obtener más información, vea [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md).  
  
## <a name="visual-c-libraries-are-shared-dlls"></a>Las bibliotecas de Visual C++ son archivos DLL compartidos  
 Puesto que el instalador de Visual Studio instala las bibliotecas de Visual C++ en el directorio %windir%\system32\, cuando se desarrolla una aplicación de Visual C++ que depende de ellas, se ejecuta de la forma esperada. Sin embargo, para implementar la aplicación en equipos que quizás no tengan Visual Studio, se recomienda asegurarse de que las bibliotecas se instalan en esos equipos junto con la aplicación.  
  
## <a name="redistributing-visual-c-libraries"></a>Redistribuir bibliotecas de Visual C++  
 En las implementaciones, puede redistribuir cualquier versión de una biblioteca de Visual C++ que está licencia de redistribución. He aquí tres maneras de implementarlas:  
  
-   Implementación central mediante paquetes redistribuibles, que instala las bibliotecas de Visual C++ como archivos DLL compartidos en %windir%\system32\\. (La instalación en esta carpeta requiere derechos de administrador). Se puede crear un script o un programa de instalación que ejecute el paquete redistribuible antes de instalar la aplicación en el equipo de destino. Hay disponibles paquetes redistribuibles para las plataformas x86, x64 y ARM (VCRedist_x86.exe, VCRedist_x64.exe o VCRedist_arm.exe). Visual Studio incluye estos paquetes en % ProgramFiles (x86) %\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\. También puede descargarlos desde el [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?linkid=132793). (En el centro de descarga, busque el "paquete redistribuible de Visual C++ *versión de Visual Studio y actualización*" que coincide con la aplicación. Por ejemplo, si usó la actualización 4 de Visual Studio 2012 para compilar la aplicación, busque “paquete redistribuible de Visual C++ 2012 actualización 4"). Para obtener información sobre cómo usar el paquete redistribuible, vea [Tutorial: implementar una Visual C++ aplicación mediante el paquete redistribuible de Visual C++](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
-   Implementación central mediante módulos de combinación, cada uno de los cuales instala una biblioteca concreta de Visual C++ como un archivo DLL compartido en %windir%\system32\\. (La instalación en esta carpeta requiere derechos de administrador). Los módulos de fusión mediante combinación forman parte del archivo instalador .msi de la aplicación. Los módulos de combinación redistribuibles de Visual C++ se incluyen en Visual Studio, en \Program (x86) \Common módulos\\. Para obtener más información, consulte [redistribuir por mediante módulos de combinación](../ide/redistributing-components-by-using-merge-modules.md).  
  
-   Implementación local, en el que se copia determinados archivos DLL de C++ Visual de la instalación de Visual Studio, normalmente se encuentra en \Program Files (x86) \Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\—and se instalan en equipos de destino en la misma carpeta que el ejecutable de la aplicación. Este método de implementación se puede usar para habilitar la instalación por parte de usuarios que no tienen derechos de administrador, o para las aplicaciones que se pueden ejecutar desde un recurso compartido de red.  
  
 Si una implementación emplea módulos de combinación redistribuibles y un usuario que no tiene derechos administrativos ejecuta una instalación, no se instalan los archivos de DLL de Visual C++ y no se ejecutará la aplicación. Además, los instaladores de aplicaciones compilados con módulos de fusión mediante combinación que permiten la instalación por usuario instalan las bibliotecas en una ubicación compartida que afecta a todos los usuarios del sistema. Puede usar la implementación local para instalar los archivos DLL de C++ Visual necesarios en el directorio de aplicación de un usuario determinado sin que ello afecte a otros usuarios o requerir derechos de administrador. Esto puede crear problemas de capacidad de servicio, no se recomienda la implementación local de archivos DLL redistribuibles de Visual C++.  
  
 La implementación incorrecta de las bibliotecas de Visual C++ puede dar lugar a errores en tiempo de ejecución cuando se ejecuta una aplicación que depende de ellas. Cuando el sistema operativo se cargue la aplicación, usa el orden de búsqueda descrito en [LoadLibraryEx](http://go.microsoft.com/fwlink/p/?linkid=132792)  
  
## <a name="dynamic-linking-is-better-than-static-linking"></a>La vinculación dinámica es mejor que la estática  
 Se recomienda evitar la vinculación estática cuando redistribuyen bibliotecas de Visual C++. Aunque la vinculación estática casi nunca mejora significativamente el rendimiento de una aplicación, casi siempre hace que el mantenimiento sea más costoso. Por ejemplo, imagine una aplicación que está vinculada estáticamente a una biblioteca que se ha actualizado con mejoras de seguridad; la aplicación no puede beneficiarse de ellos a menos que se recompile y se vuelva a implementar. En su lugar, se recomienda vincular dinámicamente las aplicaciones a las bibliotecas de las que dependen, de modo que las bibliotecas puedan actualizarse dondequiera que se implementen.  
  
## <a name="see-also"></a>Vea también  
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [No en la compilación: elegir una estrategia de implementación](http://msdn.microsoft.com/en-us/ecd632d8-063c-4028-b785-81bba045107b)   
 [Información general de implementación de Windows Installer](http://msdn.microsoft.com/en-us/3ce4610a-b54f-404e-b650-42f4a55dfc3b)   
 [Seguridad e implementación ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)   
 [Ejemplos de implementación](../ide/deployment-examples.md)