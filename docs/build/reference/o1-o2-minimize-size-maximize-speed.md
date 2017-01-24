---
title: "/O1, /O2 (Minimizar tama&#241;o, maximizar velocidad) | Microsoft Docs"
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
  - "/o2"
  - "/o1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/O1 (opción del compilador) [C++]"
  - "/O2 (opción del compilador) [C++]"
  - "código rápido"
  - "maximizar velocidad (opción del compilador) [C++]"
  - "minimizar tamaño (opción del compilador) [C++]"
  - "O1 (opción del compilador) [C++]"
  - "-O1 (opción del compilador) [C++]"
  - "O2 (opción del compilador) [C++]"
  - "-O2 (opción del compilador) [C++]"
  - "código pequeño"
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /O1, /O2 (Minimizar tama&#241;o, maximizar velocidad)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Selecciona un conjunto predefinido de opciones que afectan al tamaño y a la velocidad de los archivos.  
  
## Sintaxis  
  
```  
/O1  
/O2  
```  
  
## Comentarios  
 En la siguiente tabla se describen las opciones **\/O1** y **\/O2**.  
  
|Opción|Equivale a|Comment|  
|------------|----------------|-------------|  
|**\/O1** \(Minimizar tamaño\)|**\/Og \/Os \/Oy \/Ob2 \/Gs \/GF \/Gy**|Crea el código más pequeño en la mayor parte de los casos.|  
|**\/O2** \(Maximizar velocidad\)|**\/Og \/Oi \/Ot \/Oy \/Ob2 \/Gs \/GF \/Gy**|Crea el código más rápido en la mayoría de los casos. \(configuración predeterminada en las versiones de lanzamiento\)|  
  
 Las opciones **\/O1** y **\/O2** también habilitan la optimización del valor devuelto con nombre, que elimina el constructor y el destructor de copias de un valor devuelto basado en la pila.  Observe el siguiente ejemplo.  La función `Test` no creará el constructor o el destructor de copias.  Agregue las instrucciones de salida al constructor, a un destructor y el constructor de copias para ver el efecto de optimización del valor devuelto Named al ejecutarlo.  Para obtener más información, vea [Optimización denominada el valor devuelto en Visual C\+\+ 2005](http://go.microsoft.com/fwlink/?linkid=131571).  
  
```  
// O1_O2_NRVO.cpp  
// compile with: /O1  
struct A {  
   A() {}  
   ~A() {}  
   A(const A& aa) {}  
};  
  
A Test() {  
   A a;  
   return a;  
}  
int main() {  
   A aa;  
   aa = Test();  
}  
```  
  
 **Específico de x86**  
  
 Estas opciones implican el uso de la opción [\/Oy](../../build/reference/oy-frame-pointer-omission.md) \(omisión de puntero a marco\).  
  
 **Específico de END x86**  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Optimización**.  
  
4.  Modifique la propiedad **Optimización**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.  
  
## Vea también  
 [\/O \(Opciones\) \(Optimizar código\)](../../build/reference/o-options-optimize-code.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [\/EH \(Modelo de control de excepciones\)](../../build/reference/eh-exception-handling-model.md)