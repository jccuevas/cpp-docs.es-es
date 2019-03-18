---
title: Error PRJ0003 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: a6530045870573921cf626ceeec4c1dca10cdbfb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816183"
---
# <a name="project-build-error-prj0003"></a>Error PRJ0003 al compilar el proyecto

> Error al generar '*línea de comandos*'.

El *línea de comandos* comando tiene el formato de entrada en el **páginas de propiedades** cuadro de diálogo devolvió un código de error, pero se muestra ninguna información en el **salida** ventana.

Las posibles razones para este error incluyen:

- El proyecto depende del servidor ATL. A partir de Visual Studio 2008, servidor ATL ya no se incluye como parte de Visual Studio, pero se ha publicado como un proyecto de código fuente compartido en CodePlex. Para descargar las herramientas y el código fuente del servidor ATL, vaya a [herramientas y la biblioteca de servidor ATL](http://go.microsoft.com/fwlink/p/?linkid=81979).

- Recursos del sistema insuficientes. Cierre algunas aplicaciones para resolver este problema.

- Privilegios de seguridad insuficientes. Compruebe que dispone de suficientes privilegios de seguridad.

- Las rutas de acceso ejecutable especificados en **directorios de VC ++** no incluyen la ruta de acceso para la herramienta que está intentando ejecutar. Para obtener información, consulte [establecer compilador y las propiedades de compilación](../../build/working-with-project-properties.md)

- Para proyectos de archivos MAKE, falta un comando para ejecutarse en cualquiera **crear línea de comandos** o **volver a generar la línea de comandos**.

## <a name="see-also"></a>Vea también

[Errores y advertencias de compilación del proyecto (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)