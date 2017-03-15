---
title: "/sdl (habilitar comprobaciones adicionales de seguridad) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.SDLCheck"
dev_langs: 
  - "C++"
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /sdl (habilitar comprobaciones adicionales de seguridad)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Agrega las comprobaciones recomendadas del ciclo de vida de desarrollo de seguridad \(SDL\).  Estas comprobaciones incluyen advertencias adicionales relativas a la seguridad como errores y características seguras adicionales de generación de código.  
  
## Sintaxis  
  
```  
/sdl[-]  
```  
  
## Comentarios  
 **\/sdl** habilita un supraconjunto de comprobaciones de seguridad de la línea de base proporcionadas por [\/GS](../../build/reference/gs-buffer-security-check.md) y reemplaza **\/GS\-**.  La opción **\/sdl** está desactivada de manera predeterminada.  **\/sdl\-** deshabilita las comprobaciones de seguridad adicionales.  
  
## Comprobaciones en tiempo de compilación  
 **\/sdl** habilita estas advertencias como errores:  
  
|Advertencia habilitada por \/sdl|Modificador equivalente de la línea de comandos|Descripción|  
|--------------------------------------|-----------------------------------------------------|-----------------|  
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|\/we4146|Se aplicó un operador unario menos a un tipo unsigned, lo que produce un resultado sin signo.|  
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|\/we4308|Una constante negativa de tipo entero se convirtió a un tipo sin signo, lo que produce un resultado que posiblemente carece de sentido.|  
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|\/we4532|El uso de las palabras clave `continue`, `break` o `goto` en un bloque `__finally`\/`finally` tiene un comportamiento indefinido durante la terminación anormal.|  
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|\/we4533|El código que inicializa una variable no se ejecuta.|  
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|\/we4700|Uso de una variable local sin inicializar.|  
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|\/we4703|Uso de una variable de puntero local potencialmente no inicializada.|  
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|\/we4789|Saturación del búfer cuando se utilizan funciones específicas de C en tiempo de ejecución \(CRT\).|  
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|\/we4995|Uso de una función marcada con una directiva pragma [desusada](../../preprocessor/deprecated-c-cpp.md).|  
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|\/we4996|Uso de una función marcada como [desusada](../../cpp/deprecated-cpp.md).|  
  
## Comprobaciones en tiempo de ejecución  
 Cuando se habilita **\/sdl**, el compilador genera código para realizar estas comprobaciones en tiempo de ejecución:  
  
-   Habilita el modo estricto de detección de saturación del búfer en tiempo de ejecución de **\/GS**, lo que equivale a compilar con `#pragma strict_gs_check(push, on)`.  
  
-   Realiza una inmunización de puntero limitada.  En las expresiones que no implican desreferenciación y en los tipos que no tienen un destructor definido por el usuario, las referencias de puntero se establecen en una dirección no válida después de una llamada a `delete`.  Esto ayuda a evitar la reutilización de las referencias de puntero obsoletas.  
  
-   Realiza la inicialización del miembro de clase.  Se inicializan automáticamente todos los miembros de clase a cero en la creación de instancias de objetos \(antes de que se ejecute el constructor\).  Esto ayuda a evitar el uso de los datos sin inicializar asociados a los miembros de clase que el constructor no inicializa explícitamente.  
  
## Comentarios  
 Para obtener más información, vea la entrada de blog sobre [advertencias, \/sdl y mejora de la detección de variables sin inicializar](http://go.microsoft.com/fwlink/p/?LinkId=331012).  
  
#### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  En la página **General**, seleccione la opción en la lista desplegable **Comprobaciones SDL**.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)