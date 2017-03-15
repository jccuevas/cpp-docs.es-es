---
title: "/Zm (Especificar el l&#237;mite de asignaci&#243;n de memoria del encabezado precompilado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/zm"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch (archivos), límite de asignación de memoria"
  - "/Zm (opción del compilador) [C++]"
  - "cl.exe (compilador), límite de asignación de memoria"
  - "asignación de memoria, límite de asignación de memoria (opción del compilador)"
  - "PCH (archivos), límite de asignación de memoria"
  - "archivos de encabezado precompilados, límite de asignación de memoria"
  - "especificar límite de asignación de memoria de encabezado precompilado (opción del compilador)"
  - "Zm (opción del compilador) [C++]"
  - "-Zm (opción del compilador) [C++]"
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# /Zm (Especificar el l&#237;mite de asignaci&#243;n de memoria del encabezado precompilado)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina la cantidad de memoria que el compilador asigna para construir encabezados precompilados.  
  
## Sintaxis  
  
```  
/Zmfactor  
```  
  
## Argumentos  
 `factor`  
 Factor de escala que determina la cantidad de memoria que el compilador utiliza para construir encabezados precompilados.  
  
 El argumento `factor` es un porcentaje del tamaño predeterminado de un búfer de trabajo definido por el compilador.  El valor predeterminado del argumento `factor` es 100 \(en tanto por ciento\), pero puede especificar cantidades mayores o menores.  
  
## Comentarios  
 En versiones anteriores de Visual C\+\+, el compilador utilizaba varios montones discretos, cada uno con un límite finito.  Actualmente, el compilador aumenta dinámicamente los montones según sea necesario hasta un límite de tamaño de montón total, y solo requiere un búfer de tamaño fijo para construir los encabezados precompilados.  Por consiguiente, la opción **\/Zm** del compilador casi nunca es necesaria.  
  
 Si el compilador se ejecuta fuera del espacio del montón y emite el mensaje de error [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) al utilizar la opción **\/Zm** del compilador, tal vez se deba a que ha reservado demasiada memoria.  Pruebe a quitar la opción **\/Zm**.  Si el compilador emite el mensaje de error [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md), junto a él aparecerá un mensaje [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) en el que se especifica el argumento `factor` que se debe usar al recompilar con la opción **\/Zm** del compilador.  
  
 En la tabla siguiente se muestra cómo el argumento `factor` afecta al límite de asignación de memoria suponiendo que el tamaño del búfer del encabezado precompilado predeterminado es de 75 MB.  
  
|Valor de `factor`|Límite de asignación de memoria|  
|-----------------------|-------------------------------------|  
|10|7.5 MB|  
|100|75 MB|  
|200|150 MB|  
|1000|750 MB|  
|2000|1500 MB|  
  
## Otras maneras de establecer el límite de la asignación de memoria  
  
#### Para establecer la opción \/Zm del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  En el panel de navegación, seleccione **Propiedades de configuración**, **C\/C\+\+** y **Línea de comandos**.  
  
3.  Escriba la opción **\/Zm** del compilador en el cuadro **Opciones adicionales**.  
  
#### Para establecer la opción \/Zm del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)