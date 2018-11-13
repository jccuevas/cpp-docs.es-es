---
title: Redistribuir componentes mediante módulos de fusión mediante combinación
ms.date: 11/04/2016
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
ms.openlocfilehash: 8fa717f376017560c4bd2e9012bd25c5190da563
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676465"
---
# <a name="redistributing-components-by-using-merge-modules"></a>Redistribuir componentes mediante módulos de fusión mediante combinación

Visual Studio incluye [módulos de combinación](/windows/desktop/Msi/about-merge-modules) para cada componente de Visual C++ con licencia para redistribuirse con una aplicación. Cuando un módulo de fusión mediante combinación se compila en un archivo de instalación de Windows Installer, habilita la implementación de determinados archivos DLL en los equipos que tienen una plataforma específica. En el archivo de instalación, especifique que los módulos de fusión mediante combinación son requisitos previos para la aplicación. Cuando se instala Visual Studio, los módulos de combinación se instalan en la carpeta \Archivos de programa\Common Files\Merge Modules\\. (Solo se pueden redistribuir las versiones que no son de depuración de los archivos DLL de Visual C++). Para obtener más información y un vínculo a una lista de los módulos de combinación que se pueden redistribuir, vea [Redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md).

Puede usar los módulos de combinación para habilitar la instalación de los archivos DLL redistribuibles de Visual C++ en la carpeta %SYSTEMROOT%\system32\. (El propio Visual Studio emplea esta técnica). Sin embargo, la instalación en esta carpeta producirá un error a menos que el usuario que realiza la instalación tenga derechos de administrador.

Se recomienda no usar módulos de fusión mediante combinación excepto cuando no tenga que mantener la aplicación y no tenga dependencias en más de una versión de los archivos DLL. Los módulos de fusión mediante combinación para versiones diferentes del mismo archivo DLL no se pueden incluir en un instalador y los módulos de fusión mediante combinación hacen que sea difícil mantener los archivos DLL independientemente de la aplicación. En su lugar, se recomienda instalar un paquete redistribuible de Visual C++.

## <a name="see-also"></a>Vea también

[Redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md)