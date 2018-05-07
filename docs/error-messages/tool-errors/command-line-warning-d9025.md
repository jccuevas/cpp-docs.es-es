---
title: Advertencia de línea de comandos D9025 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9025
dev_langs:
- C++
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3875a2cbd065fd5ad887267bcc80748fa9845d0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-warning-d9025"></a>Advertencia de la línea de comandos D9025
reemplazar 'opción1' con 'opción2'  
  
 El *opción1* se especificó la opción pero, a continuación, se reemplazó por *opción2*. El *opción2* se usó la opción.  
  
 Si dos opciones especifican directivas contradictorias o incompatibles, se usa la directiva especificadas o implícitas en la opción situado más a la derecha en la línea de comandos.  
  
 Si aparece esta advertencia al compilar desde el entorno de desarrollo y no está seguro de dónde proceden las opciones incompatibles, considere lo siguiente:  
  
-   Una opción puede especificarse en el código o en la configuración del proyecto. Si observa el compilador [páginas de propiedades de línea de comandos](../../ide/command-line-property-pages.md) y si ve las opciones incompatibles en el **todas las opciones de** , a continuación, se establecen las opciones de páginas de propiedades del proyecto, en caso contrario, las opciones de campo se establecen en el código fuente.  
  
     Si se establecen las opciones de páginas de propiedades del proyecto, busque en la página de propiedades preprocesador del compilador (con el nodo del proyecto seleccionado en el Explorador de soluciones).  Si no ve la opción definida allí, revise la configuración de la página de propiedades preprocesador para cada archivo de código fuente (en el Explorador de soluciones) para asegurarse de que no se agrega no existe.  
  
     Si las opciones se establecen en el código se puede establecer en el código o en los encabezados de windows.  Puede intentar crear un archivo preprocesado ([/P](../../build/reference/p-preprocess-to-a-file.md)) y búsqueda del símbolo.