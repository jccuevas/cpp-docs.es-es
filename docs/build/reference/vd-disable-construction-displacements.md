---
title: "/vd (Deshabilitar desplazamientos de constructores) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/vd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/vd0 (opción del compilador) [C++]"
  - "/vd1 (opción del compilador) [C++]"
  - "/vdn (deshabilitar desplazamientos de constructores): opción del compilador"
  - "desplazamientos de constructor"
  - "deshabilitar desplazamientos de constructores (opción del compilador)"
  - "displacements (opción del compilador)"
  - "vd0 (opción del compilador) [C++]"
  - "-vd0 (opción del compilador) [C++]"
  - "vd1 (opción del compilador) [C++]"
  - "-vd1 (opción del compilador) [C++]"
  - "vtordisp (campos)"
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /vd (Deshabilitar desplazamientos de constructores)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
/vdn  
```  
  
## Argumentos  
 `0`  
 Suprime el miembro de desplazamiento de constructor\/destructor de vtordisp.  Elija esta opción solamente si tiene la certeza de que todos los constructores y destructores de clases llaman a las funciones virtuales de manera virtual.  
  
 `1`  
 Habilita la creación de los miembros de desplazamiento de constructor\/destructor de vtordisp ocultos.  Éste es el valor predeterminado.  
  
 `2`  
 Le permite utilizar [dynamic\_cast \(Operador\)](../../cpp/dynamic-cast-operator.md) en un objeto en construcción.  Por ejemplo, un dynamic\_cast de una clase base virtual a una clase derivada.  
  
 **\/vd2** agrega un campo vtordisp cuando hay una base virtual con funciones virtuales.  **\/vd1** debería ser suficiente.  El caso más común en que **\/vd2** es necesario es cuando la única función virtual en la base virtual es un destructor.  
  
## Comentarios  
 Estas opciones sólo se aplican al código de C\+\+ que usa bases virtuales.  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] implementa la compatibilidad con el desplazamiento de construcción de C\+\+ en aquellas situaciones donde se utiliza herencia virtual.  Los desplazamientos de construcción resuelven el problema creado cuando desde un constructor se llama a una función virtual, declarada en una base virtual y reemplazada en una clase derivada, durante la construcción de otra clase derivada.  
  
 El problema es que la función virtual puede recibir un puntero `this` incorrecto como consecuencia de discrepancias entre los desplazamientos a las bases virtuales de una clase y los desplazamientos a sus clases derivadas.  La solución proporciona un solo ajuste de desplazamiento de construcción, denominado campo vtordisp, para cada base virtual de una clase.  
  
 De forma predeterminada, los campos vtordisp se introducen siempre que el código define constructores y destructores definidos por el usuario y también reemplaza a funciones virtuales de bases virtuales.  
  
 Estas opciones afectan a archivos de código fuente completos.  Utilice [vtordisp](../../preprocessor/vtordisp.md) para suprimir campos vtordisp y después volver a habilitarlos clase por clase.  
  
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