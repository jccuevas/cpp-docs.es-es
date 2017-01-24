---
title: "/Zg (Generar prototipos de funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/zg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zg (opción del compilador) [C++]"
  - "prototipos de función, generar prototipos de función (opción del compilador)"
  - "generar prototipos de función (opción del compilador)"
  - "Zg (opción del compilador) [C++]"
  - "-Zg (opción del compilador) [C++]"
ms.assetid: c8df1b46-24ff-46f2-8356-e0a144b21dd2
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zg (Generar prototipos de funci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Quitado. Crea un prototipo de función para cada función definida en el archivo de origen, pero no compila el archivo de origen.  
  
## Sintaxis  
  
```  
/Zg  
```  
  
## Comentarios  
 Esta opción de compilador ya no está disponible. Se quitó en Visual C\+\+ 2015. Esta página se conserva para usuarios de versiones anteriores de Visual C\+\+.  
  
 El prototipo de función incluye el tipo de valor devuelto de función y una lista de tipos de argumento. La lista de tipos de argumento se crea a partir de los tipos de los parámetros formales de la función. Se omiten los prototipos de función ya presentes en el archivo de origen.  
  
 La lista de prototipos se escribe en la salida estándar. Esta lista puede resultarle útil para comprobar que los argumentos reales y los parámetros formales de una función son compatibles. Para guardar la lista, redirija la salida estándar a un archivo. A continuación, puede usar **\#include** para que la lista de prototipos de función forme parte del archivo de origen. Al hacerlo, el compilador realizará una comprobación de tipos de argumento.  
  
 Si usa la opción **\/Zg** y el programa contiene parámetros formales con los tipos struct, enum o union \(o punteros a estos tipos\), la declaración de cada tipo struct, enum o union debe tener una etiqueta \(nombre\). En el ejemplo siguiente, el nombre de etiqueta es `MyStruct`.  
  
```  
// Zg_compiler_option.c  
// compile with: /Zg  
typedef struct MyStruct { int i; } T2;  
void f2(T2 * t) {}  
```  
  
 **\/Zg** está desusada. Está previsto quitar la compatibilidad del compilador de Visual C\+\+ con el código de estilo de C anterior. Para obtener más información, consulte las [Opciones obsoletas del compilador en Visual C\+\+ 2005](http://msdn.microsoft.com/es-es/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)