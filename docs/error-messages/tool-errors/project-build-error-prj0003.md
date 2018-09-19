---
title: Error PRJ0003 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0003
dev_langs:
- C++
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d1a23b8171c916b05df1d715f803893ab0720e6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053822"
---
# <a name="project-build-error-prj0003"></a>Error PRJ0003 al compilar el proyecto

> Error al generar '*línea de comandos*'.

El *línea de comandos* comando tiene el formato de entrada en el **páginas de propiedades** cuadro de diálogo devolvió un código de error, pero se muestra ninguna información en el **salida** ventana.

Las posibles razones para este error incluyen:

- El proyecto depende del servidor ATL. A partir de Visual Studio 2008, servidor ATL ya no se incluye como parte de Visual Studio, pero se ha publicado como un proyecto de código fuente compartido en CodePlex. Para descargar las herramientas y el código fuente del servidor ATL, vaya a [herramientas y la biblioteca de servidor ATL](http://go.microsoft.com/fwlink/p/?linkid=81979).

- Recursos del sistema insuficientes. Cierre algunas aplicaciones para resolver este problema.

- Privilegios de seguridad insuficientes. Compruebe que dispone de suficientes privilegios de seguridad.

- Las rutas de acceso ejecutable especificados en **directorios de VC ++** no incluyen la ruta de acceso para la herramienta que está intentando ejecutar. Para obtener información, consulte [trabajar con las propiedades del proyecto](../../ide/working-with-project-properties.md)

- Para proyectos de archivos MAKE, falta un comando para ejecutarse en cualquiera **crear línea de comandos** o **volver a generar la línea de comandos**.

## <a name="see-also"></a>Vea también

[Errores y advertencias de compilación del proyecto (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)