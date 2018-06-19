---
title: Error PRJ0003 al compilar del proyecto | Documentos de Microsoft
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
ms.openlocfilehash: a44f272569741b1897caed1d1d64832d8b113eae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316441"
---
# <a name="project-build-error-prj0003"></a>Error PRJ0003 al compilar el proyecto  
  
> Error al generar '*línea de comandos*'.  
  
El *línea de comandos* comando formado a partir de datos en el **páginas de propiedades** cuadro de diálogo devolvió un código de error, pero no aparecerá ninguna información en el **salida** ventana.  

Posibles motivos de este error son:  
  
-   El proyecto depende de servidor ATL. A partir de Visual Studio 2008, el servidor ATL ya no se incluye como parte de Visual Studio, pero se ha publicado como un proyecto de código fuente compartido en CodePlex. Para descargar el código fuente del servidor ATL y herramientas, vaya a [biblioteca de servidor ATL y herramientas](http://go.microsoft.com/fwlink/p/?linkid=81979).  
  
-   Recursos del sistema es insuficiente. Cierre algunas aplicaciones para resolver este problema.  
  
-   Privilegios de seguridad insuficientes. Compruebe que dispone de suficientes privilegios de seguridad.  
  
-   Las rutas de acceso ejecutables especificados en **directorios de VC ++** no incluyen la ruta de acceso de la herramienta que está intentando ejecutar. Para obtener información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md)  
  
-   Para los proyectos de archivos MAKE, falta un comando para ejecutar en cualquier **crear línea de comandos** o **volver a generar la línea de comandos**.  
  
## <a name="see-also"></a>Vea también  
 [Errores y advertencias de compilación del proyecto (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)