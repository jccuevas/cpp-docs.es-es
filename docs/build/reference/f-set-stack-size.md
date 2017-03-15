---
title: "/F (Establecer el tama&#241;o de la pila) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/f"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/F (opción del compilador) [C++]"
  - "F (opción del compilador) [C++]"
  - "-F (opción del compilador) [C++]"
  - "establecer tamaño de pila (opción del compilador)"
  - "pila, establecer el tamaño"
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /F (Establecer el tama&#241;o de la pila)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el tamaño de pila del programa en bytes.  
  
## Sintaxis  
  
```  
/F number  
```  
  
## Argumentos  
 `number`  
 Tamaño de la pila en bytes.  
  
## Comentarios  
 Sin ella, el tamaño predeterminado de la pila es de 1 MB.  Especifique el argumento `number` en notación decimal o en la notación del lenguaje C.  El valor del argumento puede ser desde 1 hasta el tamaño máximo de la pila aceptado por el vinculador.  El vinculador redondeará el valor especificado a los 4 bytes más próximos.  El espacio entre **\/F** y `number`es opcional.  
  
 Puede ser necesario aumentar el tamaño de la pila si un programa obtiene mensajes de desbordamiento de pila.  
  
 También puede establecer el tamaño de pila:  
  
-   Por medio de la opción **\/STACK** del vinculador.  Para obtener más información, vea [\/STACK](../../build/reference/stack.md).  
  
-   Mediante EDITBIN en el archivo .exe.  Para obtener más información, vea [Referencia de EDITBIN](../../build/reference/editbin-reference.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)