---
title: Error PRJ0003 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: 59028c6d886630ef7db115a2ea93327669b2fcfd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192931"
---
# <a name="project-build-error-prj0003"></a>Error PRJ0003 al compilar el proyecto

> Error al generar '*línea de comandos*'.

El comando de *línea de comandos* formado a partir de la entrada en el cuadro de diálogo **páginas de propiedades** devolvió un código de error, pero no aparece ninguna información en la ventana de **salida** .

Entre los posibles motivos de este error se incluyen:

- El proyecto depende del servidor ATL. A partir de Visual Studio 2008, el servidor ATL ya no se incluye como parte de Visual Studio, pero se ha publicado como un proyecto de código fuente compartido en CodePlex. Para descargar el código fuente y las herramientas de servidor ATL, vaya a la [biblioteca de servidor ATL y las](https://go.microsoft.com/fwlink/p/?linkid=81979)herramientas.

- Pocos recursos del sistema. Cierre algunas aplicaciones para resolver este fin.

- Privilegios de seguridad insuficientes. Compruebe que dispone de suficientes privilegios de seguridad.

- Las rutas de acceso del archivo ejecutable especificadas en los **directorios de VC + +** no incluyen la ruta de acceso de la herramienta que está intentando ejecutar. Para obtener más información, vea [establecer las propiedades del compilador y compilación](../../build/working-with-project-properties.md)

- En el caso de los proyectos de archivos make, falta un comando para ejecutarlo en la línea de comandos de compilación o en la **línea de comandos**de **recompilación** .

## <a name="see-also"></a>Consulte también

[Errores y advertencias de compilación del proyecto (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
