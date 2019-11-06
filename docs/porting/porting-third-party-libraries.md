---
title: Migración de bibliotecas de terceros
ms.date: 10/29/2019
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
ms.openlocfilehash: 89460af1ad0b356f4f5952141636a9f067131750
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627192"
---
# <a name="porting-third-party-libraries"></a>Migración de bibliotecas de terceros

Al actualizar un proyecto de Visual Studio 2013 o anterior a la versión actual de Visual C++, también tiene que actualizar las bibliotecas que usa el proyecto, de modo que la biblioteca y el proyecto se compilan con la misma versión y el mismo tipo del compilador. Si no tiene acceso al código fuente de la biblioteca y la biblioteca no está disponible a través de vcpkg, debe obtener un archivo binario actualizado del proveedor de la biblioteca. (Para obtener más información, vea [Información general sobre posibles problemas de actualización](overview-of-potential-upgrade-issues-visual-cpp.md)).

Al actualizar una aplicación desde Visual Studio 2015 o Visual Studio 2017 a Visual Studio 2019, no es necesario actualizar las dependencias, ya que el código generado por estas tres versiones es compatible de forma binaria. Para obtener más información, vea [ C++ compatibilidad binaria entre Visual Studio 2015 y Visual Studio 2019](binary-compat-2015-2017.md).

## <a name="vcpkg-for-open-source-libraries"></a>vcpkg para bibliotecas de código abierto

Antes, el proceso de buscar y actualizar bibliotecas de terceros era a veces una tarea de considerable dificultad. Para facilitar C++ la adquisición y recompilación de bibliotecas de código abierto de terceros, el equipo C++ visual ha creado una herramienta de línea de comandos denominada **herramienta de empaquetado de VC + +** o **vcpkg**. Vcpkg tiene un catálogo que permite la búsqueda de muchas bibliotecas populares de código abierto de C++. Puede instalar cualquier biblioteca del catálogo directamente desde la línea de comandos de Vcpkg. Cuando se instala una biblioteca, Vcpkg crea un árbol de directorios en la máquina y agrega el archivo .h, el archivo .lib y los binarios en esta carpeta. Puede usar esta carpeta en la línea de comandos de la compilación, o bien integrarla en Visual Studio 2015 o versiones posteriores mediante el comando de instalación de integración de Vcpkg. Después de integrar una ubicación de biblioteca, Visual Studio puede buscarla y agregarla a cualquier proyecto que cree. Para usar una biblioteca, basta con usar `#include` y Visual Studio agregará automáticamente la ruta de acceso .lib a la configuración del proyecto y copiará la dll en la carpeta de la solución. Para más información, vea [Vcpkg: Administrador de paquetes de C++ para Windows](../build/vcpkg.md).

## <a name="reporting-issues"></a>Notificar problemas

Si la biblioteca de código abierto no está presente en el catálogo de **vcpkg** , puede abrir un problema en el [repositorio de github](https://github.com/Microsoft/vcpkg/issues) en el que la C++ comunidad y el equipo de Visual puedan verlo y, potencialmente, crear el archivo de puerto para esta biblioteca.

## <a name="see-also"></a>Vea también

[Guía de migración y actualización de Visual C++](visual-cpp-porting-and-upgrading-guide.md)
