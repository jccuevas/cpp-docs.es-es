---
title: "Migración de bibliotecas de terceros | Microsoft Docs"
ms.custom: 
ms.date: 01/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
caps.latest.revision: 0
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 8630a5c0b97b85e0dc75e8b470974bb7d223a511
ms.openlocfilehash: 1d85010b6068d52d8522875a3c47561ad777d345
ms.lasthandoff: 02/24/2017

---

# <a name="porting-third-party-libraries"></a>Migración de bibliotecas de terceros

Cuando actualice un proyecto a la versión actual de Visual C++, también debe actualizar las bibliotecas que usa el proyecto para que así la biblioteca y el proyecto estén compilados con la misma versión y tipo de compilador. (Para obtener más información, vea [Información general sobre posibles problemas de actualización](overview-of-potential-upgrade-issues-visual-cpp.md)). 

## <a name="introducing-vcpkg"></a>Introducción a Vcpkg
Antes, el proceso de buscar y actualizar bibliotecas de terceros era a veces una tarea de considerable dificultad. Para facilitar la adquisición y la recompilación de bibliotecas de código abierto de terceros de C++, el equipo de Visual C++ ha creado una herramienta de línea de comandos denominada **Herramienta de empaquetado de VC++** o **Vcpkg**. Vcpkg tiene un catálogo que permite la búsqueda de muchas bibliotecas populares de código abierto de C++. Puede instalar cualquier biblioteca del catálogo directamente desde la línea de comandos de Vcpkg. Cuando se instala una biblioteca, Vcpkg crea un árbol de directorios en la máquina y agrega el archivo .h, el archivo .lib y los binarios en esta carpeta. Puede usar esta carpeta en la línea de comandos de la compilación, o bien integrarla en Visual Studio 2015 o versiones posteriores mediante el comando de instalación de integración de Vcpkg. Después de integrar una ubicación de biblioteca, Visual Studio puede buscarla y agregarla a cualquier proyecto que cree. Para usar una biblioteca, basta con que la incluya y Visual Studio agregará automáticamente la ruta de acceso .lib a la configuración del proyecto y copiará la dll en la carpeta de la solución.

## <a name="acquisition-and-usage"></a>Adquisición y uso

Puede descargar Vcpkg desde [Vcpkg](https://github.com/Microsoft/vcpkg/)[repositorio de GitHub de Vcpkg].

 - Para buscar una biblioteca en el catálogo: vcpkg search <LibName>
 - Para adquirir una biblioteca (por ejemplo, Boost): vcpkg install boost
 - Para enumerar las bibliotecas que están instaladas actualmente: vcpkg list

En la entrada de blog [Vcpkg: a tool to acquire and build C++ open source libraries on Windows](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) (Vcpkg: una herramienta para adquirir y compilar bibliotecas de código abierto de C++ en Windows) se explica el funcionamiento de Vcpkg y se proporciona una lista de bibliotecas compatibles. La lista se actualiza cada semana.

## <a name="reporting-issues"></a>Notificar problemas
Si su biblioteca no está presente en el catálogo de Vcpkg, puede abrir una incidencia en el [repositorio de GitHub](https://github.com/Microsoft/vcpkg/issues) para que la comunidad y el equipo de Visual C++ puedan verlo y crear el archivo de migración para esta biblioteca.

En el caso de bibliotecas propiedad de terceros (que no son de código abierto), recomendamos que se ponga en contacto con el proveedor de la biblioteca. Aun así, nos interesa saber qué bibliotecas propiedad de terceros lo bloquean, por lo que agradecemos que nos comunique cuáles son las bibliotecas de las que depende (puede ponerse en contacto con nosotros a través de vcupgrade@microsoft.com).

  
## <a name="see-also"></a>Vea también  
 [Guía de migración y actualización de Visual C++](visual-cpp-porting-and-upgrading-guide.md)

