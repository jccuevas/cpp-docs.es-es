---
title: "/Zl (Omitir nombres de biblioteca predeterminada) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/zi"
  - "VC.Project.VCCLCompilerTool.OmitDefaultLibName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zl (opción del compilador) [C++]"
  - "bibliotecas predeterminadas, omitir nombres"
  - "omitir nombre de biblioteca predeterminado (opción del compilador)"
  - "ZI (opción del compilador)"
  - "-Zl (opción del compilador) [C++]"
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# /Zl (Omitir nombres de biblioteca predeterminada)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Omite el nombre predeterminado de la biblioteca en tiempo de ejecución de C desde el archivo .obj.  De forma predeterminada, el compilador sitúa el nombre de la biblioteca en el archivo .obj para dirigir el vinculador a la biblioteca correcta.  
  
## Sintaxis  
  
```  
/Zl  
```  
  
## Comentarios  
 Para obtener más información acerca de la biblioteca predeterminada, vea [Utilizar la biblioteca en tiempo de ejecución](../../build/reference/md-mt-ld-use-run-time-library.md).  
  
 Puede usar **\/Zl** para compilar archivos .obj que piense incluir en una biblioteca.  Aunque la omisión del nombre de la biblioteca sólo guarda una pequeña cantidad de espacio para un archivo .obj individual, el espacio total que se guarda es significativo en una biblioteca que contiene muchos módulos de objetos.  
  
 Esta es una opción avanzada.  El establecimiento de esta opción quita en parte la compatibilidad de la biblioteca en tiempo de ejecución de C, que podría ser necesaria para la aplicación, por lo que si la aplicación depende de esta compatibilidad, se generarán errores en tiempo de vínculo.  Si utiliza esta opción, debe proporcionar los componentes necesarios de alguna otra manera.  
  
 Uso [\/NODEFAULTLIB \(Omitir bibliotecas\)](../../build/reference/nodefaultlib-ignore-libraries.md). para que el vinculador omitir las referencias de la biblioteca en todos los archivos .obj.  
  
 Para obtener más información, vea [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).  
  
 Al compilar con **\/Zl**, se define `_VC_NODEFAULTLIB`.  Por ejemplo:  
  
```  
// vc_nodefaultlib.cpp  
// compile with: /Zl  
void Test() {  
   #ifdef _VC_NODEFAULTLIB  
      int i;  
   #endif  
  
   int i;   // C2086  
}  
```  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Omitir nombres de biblioteca predeterminada**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)