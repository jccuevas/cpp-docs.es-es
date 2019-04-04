---
title: Elegir un método de implementación
ms.date: 03/14/2019
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
ms.openlocfilehash: 5ca1f33a809bc81b7dcc090231e507ba66775205
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786510"
---
# <a name="choosing-a-deployment-method"></a>Elegir un método de implementación

A menos que la aplicación de Visual C++ sea independiente y se pueda implementar mediante un comando de copia, se recomienda usar Windows Installer para la implementación. Windows Installer admite la instalación, la reparación y la desinstalación, y también admite la actualización atómica de archivos, dependencias y entradas del Registro de una aplicación.

> [!NOTE]
>  Aunque la implementación [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) para las aplicaciones nativas de Visual C++ sea posible en Visual Studio, requiere ciertos pasos adicionales. Para obtener más información, vea [ClickOnce Deployment for Visual C++ Applications](clickonce-deployment-for-visual-cpp-applications.md).

## <a name="visual-c-libraries-are-shared-dlls"></a>Las bibliotecas de Visual C++ son archivos DLL compartidos

Puesto que el instalador de Visual Studio instala las bibliotecas de Visual C++ en el directorio %windir%\system32\, cuando se desarrolla una aplicación de Visual C++ que depende de ellas, se ejecuta de la forma esperada. Sin embargo, para implementar la aplicación en equipos que quizás no tengan Visual Studio, se recomienda asegurarse de que las bibliotecas se instalan en esos equipos junto con la aplicación.

## <a name="redistributing-visual-c-libraries"></a>Redistribuir bibliotecas de Visual C++

En las implementaciones, puede redistribuir cualquier versión de una biblioteca de Visual C++ que está licencia de redistribución. He aquí tres maneras de implementarlas:

- Implementación central mediante paquetes redistribuibles, lo que instala las bibliotecas de Visual C++ como archivos DLL compartidos en %windir%\system32\\. (La instalación en esta carpeta requiere derechos de administrador). Se puede crear un script o un programa de instalación que ejecute el paquete redistribuible antes de instalar la aplicación en el equipo de destino. Hay disponibles paquetes redistribuibles para las plataformas x86, x64 y ARM (VCRedist_x86.exe, VCRedist_x64.exe o VCRedist_arm.exe). Visual Studio incluye estos paquetes en %ProgramFiles(x86)%\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\. También se pueden descargar desde el [Centro de descarga de Microsoft](https://www.microsoft.com/download). (Use el cuadro de búsqueda del Centro de descarga para buscar el "paquete redistribuible de Visual C++ *versión y actualización de Visual Studio*" que coincida con la aplicación. Por ejemplo, si usó la actualización 3 de Visual Studio 2015 para compilar la aplicación, busque "paquete redistribuible de Visual C++ 2015 actualización 3"). Para obtener más información sobre cómo usar un paquete redistribuible, vea [Tutorial: Implementar una aplicación de Visual C++ mediante el paquete redistribuible de Visual C++](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

- Implementación central mediante módulos de combinación, cada uno de los cuales instala una biblioteca concreta de Visual C++ como un archivo DLL compartido en %windir%\system32\\. (La instalación en esta carpeta requiere derechos de administrador). Los módulos de combinación forman parte del archivo instalador .msi de la aplicación. Los módulos de combinación redistribuibles de Visual C++ se incluyen en Visual Studio, en \Archivos de programa (x86)\Common Files\Merge Modules\\. Para obtener más información, vea [Redistribuir mediante módulos de combinación](redistributing-components-by-using-merge-modules.md).

- Implementación local, en la que se copian determinados archivos DLL de Visual C++ desde la instalación de Visual Studio (normalmente en \Archivos de programa (x86)\Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\) y se instalan en los equipos de destino en la misma carpeta que el archivo ejecutable de la aplicación. Este método de implementación se puede usar para habilitar la instalación por parte de usuarios que no tienen derechos de administrador, o para las aplicaciones que se pueden ejecutar desde un recurso compartido de red.

Si en una implementación se usan módulos de combinación redistribuibles y la instalación la realiza alguien sin derechos administrativos, los archivos DLL de Visual C++ no se instalan y la aplicación no se ejecuta. Además, los instaladores de aplicaciones compilados con módulos de fusión mediante combinación que permiten la instalación por usuario instalan las bibliotecas en una ubicación compartida que afecta a todos los usuarios del sistema. Se puede usar la implementación local para instalar los archivos DLL de Visual C++ necesarios en el directorio de la aplicación de un usuario determinado sin afectar por ello a otros usuarios o requerir derechos de administrador. Esto puede crear problemas de mantenimiento, por lo no se recomienda realizar la implementación local de archivos DLL redistribuibles de Visual C++.

La implementación incorrecta de las bibliotecas de Visual C++ puede dar lugar a errores en tiempo de ejecución cuando se ejecuta una aplicación que depende de ellas. Cuando el sistema operativo carga la aplicación, utiliza el orden de búsqueda descrito en [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

## <a name="dynamic-linking-is-better-than-static-linking"></a>La vinculación dinámica es mejor que la estática

Se recomienda evitar la vinculación estática cuando se redistribuyen bibliotecas de Visual C++. Aunque la vinculación estática casi nunca mejora significativamente el rendimiento de una aplicación, casi siempre hace que el mantenimiento sea más costoso. Por ejemplo, imagine una aplicación que está vinculada estáticamente a una biblioteca que se ha actualizado con mejoras de seguridad; la aplicación no puede beneficiarse de ellos a menos que se recompile y se vuelva a implementar. En su lugar, se recomienda vincular dinámicamente las aplicaciones a las bibliotecas de las que dependen, de modo que las bibliotecas puedan actualizarse dondequiera que se implementen.

## <a name="see-also"></a>Vea también

[Implementar aplicaciones de escritorio](deploying-native-desktop-applications-visual-cpp.md)<br>
[Seguridad e implementación ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Ejemplos de implementación](deployment-examples.md)
