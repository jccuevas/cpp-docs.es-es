---
title: Implementar aplicaciones de escritorio nativas (Visual C++)
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
- Visual C++, application deployment
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- distributing applications [C++]
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
ms.openlocfilehash: 46ced4ac5f7952a9b7f66418ea037e053b16e9be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346124"
---
# <a name="deploying-native-desktop-applications-visual-c"></a>Implementar aplicaciones de escritorio nativas (Visual C++)

La implementación es el proceso mediante el cual se distribuye una aplicación o un componente acabado para instalarse en otros equipos. La planeación de la implementación se inicia cuando se crea una aplicación en el equipo de un desarrollador. La implementación finaliza cuando se instala la aplicación y está preparada para ejecutarse en el equipo del usuario.

Visual Studio proporciona diferentes tecnologías para implementar aplicaciones Windows. Entre ellas se incluyen las implementaciones ClickOnce y Windows Installer.

- ClickOnce se puede usar para implementar aplicaciones de C++ destinadas a Common Language Runtime (CLR): ensamblados mixtos, puros y comprobables. Aunque se puede usar Windows Installer para implementar una aplicación administrada, se recomienda usar ClickOnce porque aprovecha las características de seguridad de .NET Framework, como la firma de manifiestos. ClickOnce no admite la implementación de aplicaciones de C++ nativas. Para obtener más información, vea [ClickOnce Deployment for Visual C++ Applications](clickonce-deployment-for-visual-cpp-applications.md).

- La tecnología de Windows Installer puede usarse para implementar aplicaciones de C++ nativas o aplicaciones de C++ orientadas a CLR.

Los artículos de esta sección de la documentación explican cómo asegurarse de que una aplicación de Visual C++ nativa se ejecute en cualquier equipo que proporciona una plataforma de destino admitida, cuyos archivos se deben incluir en un paquete de instalación, así como los métodos recomendados para redistribuir los componentes que dependen la aplicación.

## <a name="in-this-section"></a>En esta sección

- [Implementación en Visual C++](deployment-in-visual-cpp.md)

- [Conceptos de implementación](deployment-concepts.md)

- [Descripción de las dependencias de una aplicación de Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md)

- [Determinar qué archivos DLL se redistribuirán](determining-which-dlls-to-redistribute.md)

- [Elegir un método de implementación](choosing-a-deployment-method.md)

- [Implementación de CRT universal](universal-crt-deployment.md).

- [Redistribuir archivos de Visual C++](redistributing-visual-cpp-files.md)

- [Ejemplos de implementación](deployment-examples.md)

- [Redistribuir aplicaciones cliente web](redistributing-web-client-applications.md)

- [Implementación de ClickOnce para aplicaciones de Visual C++](clickonce-deployment-for-visual-cpp-applications.md)

- [Ejecutar una aplicación /clr de C++ en una versión anterior del Runtime](running-a-cpp-clr-application-on-a-previous-runtime-version.md)

## <a name="related-sections"></a>Secciones relacionadas

- [Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

- [Implementación](/dotnet/framework/deployment/index)

- [Solución de problemas de aplicaciones aisladas y ensamblados simultáneos de C/C++](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)