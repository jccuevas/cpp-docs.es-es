---
title: "/QIfist (Suprimir _ftol) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/qifist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "QIfist (opción del compilador) [C++]"
  - "-QIfist (opción del compilador) [C++]"
  - "/QIfist (opción del compilador) [C++]"
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# /QIfist (Suprimir _ftol)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Suprime la llamada de la función auxiliar `_ftol` cuando se requiere la conversión de un tipo de punto flotante a un tipo entero.  
  
## Sintaxis  
  
```  
/QIfist  
```  
  
## Comentarios  
  
> [!NOTE]
>  **\/QIfist** solo está disponible en el compilador con destino en x86; esta opción del compilador no está disponible en los compiladores con destino en [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] o ARM.  
  
 Además de realizar la conversión de un tipo de punto flotante a un tipo entero, la función `_ftol` garantiza que el modo de redondeo de la unidad de punto flotante \(FPU\) se hace a cero \(se trunca\) mediante el establecimiento de los bits 10 y 11 de la palabra de control.  Esto garantiza que la conversión de un tipo de punto flotante en tipo entero se realiza como se describe en la norma ANSI C \(la parte fraccionaria del número se descarta\).  Si se utiliza **\/QIfist**, esta garantía ya no es aplicable.  El modo de redondeo será uno de los cuatro documentados en los manuales de referencia de Intel:  
  
-   Redondeo al más próximo \(número par si está equidistante\)  
  
-   Redondeo a infinito negativo  
  
-   Redondeo a infinito positivo  
  
-   Redondeo a cero  
  
 Puede utilizar la función en tiempo de ejecución [\_control87, \_controlfp, \_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) de C para modificar el comportamiento de redondeo de la FPU.  El modo de redondeo predeterminado de la FPU es "Redondeo al más próximo". El uso de **\/QIfist** puede mejorar el rendimiento de la aplicación, pero no está exento de riesgo.  Compruebe exhaustivamente las partes del código que sean sensibles al modo de redondeo antes de lanzar un código compilado con **\/QIfist** a los entornos de producción.  
  
 Las opciones [\/arch \(x86\)](../../build/reference/arch-x86.md) y **\/QIfist** no se pueden utilizar en la misma operación de compilación.  
  
> [!NOTE]
>  **\/QIfist** no está en vigor de manera predeterminada, ya que los bits de redondeo también afectan al redondeo de punto flotante a punto flotante \(que se produce después de cada cálculo\), de modo que, cuando se establecen las marcas para redondeo de estilo C \(a cero\), los cálculos de punto flotante podrían ser diferentes.  **\/QIfist** no debe usarse si el código depende del comportamiento esperado de truncar la parte fraccionaria del número de punto flotante.  Si no está seguro, no use **\/QIfist**.  
  
 **\/QIfist** está desusada.  Se han realizado mejoras importantes en el compilador en cuanto a la velocidad de conversión de los tipos float a int.  Para obtener más información, vea [Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/es-es/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [\/Q \(Opciones\) \(Operaciones de bajo nivel\)](../../build/reference/q-options-low-level-operations.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)