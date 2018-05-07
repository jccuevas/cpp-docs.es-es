---
title: Error de línea de comandos D8016 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8016
dev_langs:
- C++
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6f9709da189403f2594d76751430d30554bffe5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-error-d8016"></a>Error de la línea de comandos D8016
Opciones de línea de comandos 'opción1' y 'opción2' son incompatibles  
  
 Las opciones de línea de comandos no se pueden especificar juntas.  
  
 Compruebe las variables de entorno, como CL, especificaciones de opción.  
  
 **/ CLR** implica **/EHa**, y no se puede especificar cualquier otro **/EH** opción del compilador con **/CLR**. Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 D8016 puede aparecer después de actualizar un [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] proyecto 6.0: el proceso del Asistente de actualización de proyecto puede ofrecer **/RTC** para cada archivo de código fuente en el proyecto, que reemplaza el **/RTC** establecer para el proyecto.  Para resolver, cambie la **/RTC** de configuración para cada archivo de código fuente en el proyecto de la configuración predeterminada, lo que significa que la configuración del proyecto para **/RTC** entrará en vigor para cada archivo.  
  
 Vea [/RTC (comprobaciones de errores de tiempo de ejecución)](../../build/reference/rtc-run-time-error-checks.md) para obtener información acerca de cómo cambiar la **/RTC** configuración de la propiedad.