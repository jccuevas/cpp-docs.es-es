---
title: Redistribuir componentes mediante módulos de fusión mediante combinación
ms.date: 11/04/2016
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
ms.openlocfilehash: 36dc115987b051f117264991927c2599a88deda6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514774"
---
# <a name="redistributing-components-by-using-merge-modules"></a>Redistribuir componentes mediante módulos de fusión mediante combinación

Visual Studio incluye [módulos de combinación](/windows/win32/Msi/about-merge-modules) para cada componente de Visual C++ con licencia para redistribuirse con una aplicación. Cuando un módulo de fusión mediante combinación se compila en un archivo de instalación de Windows Installer, habilita la implementación de determinados archivos DLL en los equipos que tienen una plataforma específica. En el archivo de instalación, especifique que los módulos de combinación son requisitos previos para la aplicación. Cuando se instala Visual Studio, los módulos de combinación se instalan en la carpeta \Archivos de programa\Common Files\Merge Modules\\. (Solo se pueden redistribuir las versiones que no son de depuración de los archivos DLL de Visual C++). Para obtener más información y un vínculo a una lista de los módulos de combinación que se pueden redistribuir, vea [Redistribuir archivos de Visual C++](redistributing-visual-cpp-files.md).

Puede usar los módulos de combinación para habilitar la instalación de los archivos DLL redistribuibles de Visual C++ en la carpeta %SYSTEMROOT%\system32\. (El propio Visual Studio emplea esta técnica). Aun así, la instalación en esta carpeta producirá un error a menos que el usuario que realiza la instalación tenga derechos de administrador.

Se recomienda no usar módulos de fusión mediante combinación excepto cuando no tenga que mantener la aplicación y no tenga dependencias en más de una versión de los archivos DLL. Los módulos de combinación para versiones diferentes del mismo archivo DLL no se pueden incluir en un instalador y los módulos de combinación hacen que sea difícil mantener los archivos DLL independientemente de la aplicación. En su lugar, se recomienda instalar un paquete redistribuible de Visual C++.

## <a name="see-also"></a>Vea también

[Redistribuir archivos de Visual C++](redistributing-visual-cpp-files.md)
