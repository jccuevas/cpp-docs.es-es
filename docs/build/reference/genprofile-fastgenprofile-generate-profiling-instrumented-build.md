---
title: "/GENPROFILE, /FASTGENPROFILE (Generar compilaci&#243;n instrumentada de generaci&#243;n de perfiles) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GENPROFILE"
  - "FASTGENPROFILE"
  - "/GENPROFILE"
  - "/FASTGENPROFILE"
helpviewer_keywords: 
  - "GENPROFILE"
  - "FASTGENPROFILE"
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# /GENPROFILE, /FASTGENPROFILE (Generar compilaci&#243;n instrumentada de generaci&#243;n de perfiles)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifican la generación de un archivo .pgd mediante el enlazador para admitir la optimización guiada por perfiles \(PGO\).  \/GENPROFILE y \/FASTGENPROFILE usan parámetros predeterminados diferentes. Use \/GENPROFILE para favorecer la precisión sobre el uso de memoria y velocidad durante la generación de perfiles. Use \/FASTGENPROFILE para favorecer el menor uso de memoria y velocidad sobre la precisión.  
  
## Sintaxis  
  
```  
/{GENPROFILE|FASTGENPROFILE}[:{COUNTER32|COUNTER64|EXACT|MEMMAX=#|MEMMIN=#|NOEXACT|NOPATH|NOTRACKEH|PATH|PGD=filename|TRACKEH}]   
```  
  
## Comentarios  
 COUNTER32 &#124; COUNTER64  
 Use COUNTER32 para especificar el uso de contadores de sondeo de 32 bits y COUNTER64 para especificar contadores de sondeo de 64 bits. Si se especifica \/GENPROFILE, el valor predeterminado es COUNTER64. Si se especifica \/FASTGENPROFILE, el valor predeterminado es COUNTER32.  
  
 EXACT &#124; NOEXACT  
 Use EXACT para especificar incrementos interbloqueados seguros para subprocesos para los sondeos. NOEXACT especifica las operaciones de incremento no protegido para los sondeos. El valor predeterminado es NOEXACT.  
  
 MEMMAX\=value, MEMMIN\=value  
 Use MEMMAX y MEMMIN para especificar los tamaños de reserva máximo y mínimo para los datos de entrenamiento en memoria. El valor es la cantidad de memoria que se reserva en bytes.  De forma predeterminada, estos valores se determinan mediante una heurística interna.  
  
 PATH &#124; NOPATH  
 Use PATH para especificar un conjunto independiente de contadores PGO para cada ruta de acceso única a una función. Use NOPATH para especificar solo un conjunto de contadores para cada función.   Si se especifica \/GENPROFILE, el valor predeterminado es PATH. Si se especifica \/FASTGENPROFILE, el valor predeterminado es NOPATH.  
  
 TRACKEH &#124; NOTRACKEH  
 Especifican si se deben usar contadores adicionales para mantener un recuento preciso cuando se produzcan excepciones durante el entrenamiento. Use TRACKEH para especificar contadores adicionales para un recuento exacto. Use NOTRACKEH para especificar contadores únicos para el código que no usa el control de excepciones o que no produce excepciones en los escenarios de entrenamiento.  Si se especifica \/GENPROFILE, el valor predeterminado es TRACKEH. Si se especifica \/FASTGENPROFILE, el valor predeterminado es NOTRACKEH.  
  
 PGD\=filename  
 Especifica un nombre de archivo base para el archivo .pgd. De forma predeterminada, el enlazador usa el nombre de archivo de imagen ejecutable base con una extensión .pgd.  
  
 Las opciones \/GENPROFILE y \/FASTGENPROFILE indican al enlazador que genere el archivo de instrumentación de generación de perfiles necesario para admitir el entrenamiento de la aplicación para la optimización guiada por perfiles \(PGO\). La información de generación de perfiles creada mediante el entrenamiento de la aplicación se usa como entrada para realizar optimizaciones dirigidas de todo el programa durante las compilaciones.   Se pueden establecer opciones adicionales para controlar diversas características de generación de perfiles de rendimiento durante el entrenamiento de la aplicación y las compilaciones. Las opciones predeterminadas especificadas por \/GENPROFILE proporcionan resultados más precisos, especialmente para las aplicaciones multiproceso grandes y complejas. La opción \/FASTGENPROFILE usa valores predeterminados diferentes para un menor consumo de memoria y un rendimiento más rápido durante el entrenamiento, a costa de precisión.  
  
 La información de generación de perfiles se captura cuando se ejecuta la aplicación instrumentada después de compilar mediante \/GENPROFILE de \/FASTGENPROFILE. El enlazador usa esta información cuando se especifica la opción \/USEPROFILE. Para obtener más información sobre cómo entrenar su aplicación según los datos recopilados, vea optimización guiada por perfiles.  
  
 También es necesario especificar\/LTCG al especificar \/GENPROFILE o \/FASTGENPROFILE.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [\/LTCG \(Generación de código en tiempo de enlace\)](../../build/reference/ltcg-link-time-code-generation.md)