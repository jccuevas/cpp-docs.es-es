---
title: "Reglas de coherencia para /Yc e /Yu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/yc"
  - "/yu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Yc (opción del compilador) [C++]"
  - "/Yu (opción del compilador) [C++]"
  - "Yc (opción del compilador) [C++]"
  - "-Yc (opción del compilador) [C++]"
  - "Yu (opción del compilador) [C++]"
  - "-Yu (opción del compilador) [C++]"
ms.assetid: 9dfb0e32-ec9b-4a36-9355-27a0e5fba512
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Reglas de coherencia para /Yc e /Yu
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando se utiliza un encabezado precompilado creado mediante \/Yc o \/Yu, el compilador compara el entorno de compilación actual con el que existía cuando se creó el archivo .pch.  Asegúrese de especificar un entorno coherente con el anterior \(utilice opciones coherentes del compilador, pragmas, etc.\) para la compilación actual.  Si el compilador detecta una incoherencia, emite una advertencia e identifica dicha incoherencia en los casos en que sea posible.  Tales advertencias no indican necesariamente un problema con el archivo .pch; simplemente avisan de posibles conflictos.  Las siguientes secciones explican los requisitos de coherencia para encabezados precompilados.  
  
## Coherencia entre las opciones del compilador  
 La tabla siguiente muestra opciones del compilador que podrían desencadenar una advertencia de incoherencia cuando se utiliza un encabezado precompilado:  
  
|Opción|Name|Regla|  
|------------|----------|-----------|  
|\/D|Definir constantes y macros|Debe ser igual en la compilación que creó el encabezado precompilado y en la compilación actual.  El estado de las constantes definidas no se comprueba, pero pueden producirse resultados imprevisibles si los archivos dependen de los valores de las constantes que cambian.|  
|\/E o \/EP|Copiar los resultados del preprocesador a resultados estándar|Los encabezados precompilados no funcionan con la opción \/E o \/EP.|  
|\/Fr o \/FR|Generar información del Explorador de código fuente de Microsoft|Para que las opciones \/Fr y \/FR sean válidas con la opción \/Yu, también deben haber estado activas cuando se creó el encabezado precompilado.  Las compilaciones sucesivas que utilizan el encabezado precompilado también generan información del Explorador de código fuente.  La información del Explorador se incluye en un único archivo .sbr y la referencia a ella desde otros archivos se realiza del mismo modo que para la información de CodeView.  La ubicación de la información del Explorador de código fuente no se puede cambiar.|  
|\/GA, \/GD, \/GE, \/Gw o \/GW|Opciones de protocolo de Windows|Debe ser igual en la compilación que creó el encabezado precompilado y en la compilación actual.  Si las opciones difieren, se produce un mensaje de advertencia.|  
|\/Zi|Generar información de depuración completa|Si esta opción está activa cuando se crea el encabezado precompilado, las compilaciones subsiguientes que utilizan la precompilación podrán hacer uso de la información de depuración.  Si \/Zi no está activa cuando se crea el encabezado precompilado, las compilaciones subsiguientes que utilizan la precompilación y la opción \/Zi producirán un mensaje de advertencia.  La información de depuración se coloca en el archivo .obj actual, pero los símbolos locales definidos en el encabezado precompilado no estarán disponibles para el depurador.|  
  
> [!NOTE]
>  Los encabezados precompilados están diseñados para su uso exclusivo con archivos que contengan archivos de código fuente de C y C\+\+.  
  
## Coherencia de la ruta de acceso de inclusión  
 Un encabezado precompilado creado con \/Yc no contiene información sobre la ruta de acceso de inclusión que estaba activa cuando se creó el archivo .pch.  Cuando se utiliza un archivo .pch, el compilador siempre usa la ruta de acceso de inclusión especificada en la compilación actual.  
  
## Coherencia de los archivos de código fuente  
 Cuando se utiliza un encabezado precompilado, el compilador no tiene en cuenta las directivas de preprocesador \(incluidas las directivas pragma\) que aparecen antes de la pragma hdrstop.  La compilación especificada por esas directivas de preprocesador debe ser la misma que la compilación utilizada para crear el archivo de encabezado precompilado.  
  
## Coherencia de pragmas  
 Las directivas pragma procesadas durante la compilación de un encabezado precompilado suelen afectar al archivo en el que el encabezado precompilado se utiliza posteriormente.  Las siguientes directivas pragma afectan únicamente al código interno del archivo .pch; no afectan al código que utiliza posteriormente el archivo .pch:  
  
||||  
|-|-|-|  
|Comment|page|subtitle|  
|Linesize|pagesize|Título|  
|Mensaje|skip||  
  
 Las siguientes directivas pragma se conservan como parte de un encabezado precompilado y afectan al resto de una compilación que hace uso de él.  
  
||||  
|-|-|-|  
|alloc\_text|function|optimize|  
|auto\_inline|inline\_depth|Pack|  
|check\_pointer|inline\_recursion|same\_seg|  
|check\_stack|intrinsic|warning|  
|code\_seg|loop\_opt||  
|data\_seg|native\_caller||  
  
## Vea también  
 [Reglas de coherencia de los encabezados precompilados](../../build/reference/precompiled-header-consistency-rules.md)   
 [\/Yc \(Crear archivo de encabezado precompilado\)](../../build/reference/yc-create-precompiled-header-file.md)   
 [\/Yu \(Utilizar el archivo de encabezado precompilado\)](../../build/reference/yu-use-precompiled-header-file.md)