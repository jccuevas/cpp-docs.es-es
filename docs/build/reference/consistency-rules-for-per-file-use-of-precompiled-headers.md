---
title: "Reglas de coherencia para el uso de encabezados precompilados por cada archivo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch (archivos), reglas de coherencia"
  - "PCH (archivos), reglas de coherencia"
  - "archivos de encabezado precompilados, reglas de coherencia"
ms.assetid: afd49365-48bc-41f4-b700-fe8297b944a1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Reglas de coherencia para el uso de encabezados precompilados por cada archivo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La opción [\/Yu](../../build/reference/yu-use-precompiled-header-file.md) del compilador permite especificar qué archivo de encabezado precompilado \(PCH\) se debe utilizar.  
  
 Cuando se utiliza un PCH, el compilador presupone el mismo entorno de compilación \(usa opciones coherentes del compilador, pragmas, etc.\) que se utilizó cuando se creó el PCH, a menos que se especifique lo contrario.  Si el compilador detecta una incoherencia, emite una advertencia e identifica dicha incoherencia en los casos en que sea posible.  Tales advertencias no indican necesariamente un problema con el PCH; simplemente avisan de posibles conflictos.  Los requisitos de coherencia para archivos PCH se describen en las siguientes secciones.  
  
## Coherencia entre las opciones del compilador  
 Las siguientes opciones del compilador pueden desencadenar una advertencia de incoherencia cuando se utiliza un PCH:  
  
-   Las macros creadas con la opción \(\/D\) del preprocesador deben coincidir en la compilación que creó el PCH y la compilación actual.  El estado de las constantes definidas no se comprueba, pero pueden producirse resultados imprevisibles si éstas cambian.  
  
-   Los archivos PCH no funcionan con las opciones \/E y \/EP.  
  
-   Los PCH deben crearse con la opción Generar información de exploración \(\/FR\) o con la opción Excluir variables locales \(\/Fr\) antes de que posteriores compilaciones que utilizan el PCH puedan usar estas opciones.  
  
## Compatible con C 7.0 \(\/Z7\)  
 Si esta opción está activa cuando se crea el PCH, las compilaciones subsiguientes que utilizan el PCH podrán hacer uso de la información de depuración.  
  
 Si la opción Compatible con C 7.0 \(\/Z7\) no se encuentra activa al crear el PCH, las compilaciones posteriores que utilizan el PCH y la opción \/Z7 generarán un mensaje de advertencia.  La información de depuración se coloca en el archivo .obj actual, pero los símbolos locales definidos en el PCH no estarán disponibles para el depurador.  
  
## Coherencia de la ruta de acceso de inclusión  
 Un PCH no contiene información sobre la ruta de acceso de inclusión que estaba vigente cuando se creó el PCH.  Cuando se utiliza un archivo .pch, el compilador siempre usa la ruta de acceso de inclusión especificada en la compilación actual.  
  
## Coherencia de los archivos de código fuente  
 Cuando se especifica la opción Utilizar archivo de encabezado precompilado \(\/Yu\), el compilador no tiene en cuenta las directivas de preprocesador \(incluidas las pragmas\) que aparecen en el código fuente que se va a precompilar.  La compilación especificada por esas directivas de preprocesador debe ser la misma que la compilación utilizada para la opción Crear archivo de encabezado precompilado \(\/Yc\).  
  
## Coherencia de pragmas  
 Las directivas pragma procesadas durante la creación de un PCH afectan normalmente al archivo con el que posteriormente se utiliza el PCH.  Las pragmas de comentario y mensaje no afectan al resto de la compilación.  
  
 Las siguientes directivas pragma se conservan como parte de un PCH y afectan al resto de la compilación que utiliza el PCH.  
  
||||  
|-|-|-|  
|alloc\_text|include\_alias|pack|  
|auto\_inline|init\_seg|pointers\_to\_members|  
|check\_stack|inline\_depth|setlocale|  
|code\_seg|inline\_recursion|vtordisp|  
|data\_seg|intrinsic|warning|  
|function|optimize||  
  
## Vea también  
 [Reglas de coherencia de los encabezados precompilados](../../build/reference/precompiled-header-consistency-rules.md)   
 [\/Yu \(Utilizar el archivo de encabezado precompilado\)](../../build/reference/yu-use-precompiled-header-file.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)