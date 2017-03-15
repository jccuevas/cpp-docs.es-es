---
title: "/GF (Eliminar cadenas duplicadas) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.StringPooling"
  - "VC.Project.VCCLWCECompilerTool.StringPooling"
  - "/gf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GF (opción del compilador) [C++]"
  - "cadenas duplicadas"
  - "Eliminar cadenas duplicadas (opción del compilador) [C++]"
  - "GF (opción del compilador) [C++]"
  - "-GF (opción del compilador) [C++]"
  - "agrupar cadenas (opción del compilador) [C++]"
  - "cadenas [C++], agrupación"
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# /GF (Eliminar cadenas duplicadas)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite al compilador crear una sola copia de cadenas idénticas en la imagen del programa y en la memoria durante la ejecución.  Se trata de una optimización llamada *agrupación de cadenas* que puede crear programas más pequeños.  
  
## Sintaxis  
  
```  
/GF  
```  
  
## Comentarios  
 Si utiliza **\/GF**, el sistema operativo no intercambia la parte de cadena de la memoria y permite leer las cadenas otra vez desde el archivo de imagen.  
  
 **\/GF** agrupa las cadenas como de sólo lectura.  Si intenta modificar las cadenas bajo **\/GF**, se producirá un error de aplicación.  
  
 La agrupación de cadenas permite convertir en varios punteros a un solo búfer lo que inicialmente se diseñó como varios punteros a múltiples búferes.  En el siguiente segmento de código, `s` y `t` se inicializan con la misma cadena.  La agrupación de cadenas hace que éstas señalen a la misma memoria:  
  
```  
char *s = "This is a character buffer";  
char *t = "This is a character buffer";  
```  
  
> [!NOTE]
>  La opción [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md), que se utiliza para Editar y continuar, establece la opción **\/GF** de forma automática.  
  
> [!NOTE]
>  La opción del compilador **\/GF** crea una sección direccionable para cada cadena única.  Además, de manera predeterminada, un archivo de objeto puede contener hasta 65.536 secciones direccionables.  Si el programa contiene más de 65.536 cadenas, use la opción del compilador [\/bigobj](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md) para crear más secciones.  
  
 **\/GF** está habilitado cuando se utiliza [\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) o **\/O2**.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Generación de código**.  
  
4.  Modifique la propiedad **Habilitar agrupación de cadenas**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)