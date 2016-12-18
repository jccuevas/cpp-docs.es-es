---
title: "/vmm, /vms, /vmv (Representaci&#243;n de prop&#243;sito general) | Microsoft Docs"
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
  - "/vms"
  - "/vmm"
  - "/vmv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/vmm (opción del compilador) [C++]"
  - "/vms (opción del compilador) [C++]"
  - "/vmv (opción del compilador) [C++]"
  - "representación de propósito general (opciones del compilador)"
  - "herencia simple (opción del compilador)"
  - "herencia virtual (opción del compilador)"
  - "vmm (opción del compilador) [C++]"
  - "-vmm (opción del compilador) [C++]"
  - "vms (opción del compilador) [C++]"
  - "-vms (opción del compilador) [C++]"
  - "vmv (opción del compilador) [C++]"
  - "-vmv (opción del compilador) [C++]"
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /vmm, /vms, /vmv (Representaci&#243;n de prop&#243;sito general)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza cuando se selecciona [\/vmb, \/vmg \(Método de representación\)](../../build/reference/vmb-vmg-representation-method.md) como [método de representación](../../build/reference/vmb-vmg-representation-method.md).  Estas opciones indican el modelo de herencia de la definición de clase aún no encontrada.  
  
## Sintaxis  
  
```  
/vmm  
/vms  
/vmv  
```  
  
## Comentarios  
 Estas opciones se describen en la siguiente tabla.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**\/vmm**|Especifica la representación más general de un puntero a un miembro de una clase como aquella que utiliza herencia múltiple.<br /><br /> La [palabra clave de herencia](../../cpp/inheritance-keywords.md) correspondiente y el argumento para [\#pragma pointers\_to\_members](../../preprocessor/pointers-to-members.md) es **multiple\_inheritance**.<br /><br /> Esta representación es de mayor tamaño que la requerida para la herencia simple.<br /><br /> Si el modelo de herencia de una definición de clase para la que se declara un puntero a un miembro es virtual, el compilador genera un error.|  
|**\/vms**|Especifica la representación más general de un puntero a un miembro de una clase como aquella que no utiliza herencia múltiple ni herencia simple.<br /><br /> La [palabra clave de herencia](../../cpp/inheritance-keywords.md) correspondiente y el argumento para [\#pragma pointers\_to\_members](../../preprocessor/pointers-to-members.md) es **single\_inheritance**.<br /><br /> Ésta es la representación más pequeña posible de un puntero a un miembro de una clase.<br /><br /> Si el modelo de herencia de una definición de clase para la que se declara un puntero a un miembro es múltiple o virtual, el compilador genera un error.|  
|**\/vmv**|Especifica la representación más general de un puntero a un miembro de una clase como aquella que utiliza herencia virtual.  Nunca causa un error y es el valor predeterminado.<br /><br /> La [palabra clave de herencia](../../cpp/inheritance-keywords.md) correspondiente y el argumento para [\#pragma pointers\_to\_members](../../preprocessor/pointers-to-members.md) es **virtual\_inheritance**.<br /><br /> Esta opción requiere un puntero de mayor tamaño que las otras opciones, así como código adicional para interpretar el puntero.|  
  
 Si especifica una de estas opciones de modelo de herencia, se utiliza el modelo seleccionado para todos los punteros de miembros de clase, con independencia de su tipo de herencia o de si el puntero se declara antes o después que la clase.  Por lo tanto, si siempre utiliza clases de herencia simple, puede reducir el tamaño del código utilizando la opción **\/vms** para compilar; no obstante, si desea utilizar el caso más general \(a expensas de una representación de datos de tamaño más grande\), compile con la opción  **\/vmv**.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [\/vmb, \/vmg \(Método de representación\)](../../build/reference/vmb-vmg-representation-method.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)