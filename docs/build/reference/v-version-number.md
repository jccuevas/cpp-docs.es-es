---
title: "/V (N&#250;mero de versi&#243;n) | Microsoft Docs"
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
  - "/v"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/V (opción del compilador) [C++]"
  - "incrustar cadenas de versión"
  - "V (opción del compilador) [C++]"
  - "-V (opción del compilador) [C++]"
  - "números de versión, especificar para .obj"
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /V (N&#250;mero de versi&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Incrusta una cadena de textoen el archivo .obj.  Obsoleto.  
  
## Sintaxis  
  
```  
/Vstring  
```  
  
## Argumentos  
 `string`  
 Cadena que especifica el número de versión o el aviso de copyright que se incrusta en un archivo .obj.  
  
## Comentarios  
 La cadenapuede etiquetar un archivo .obj con un número de versión o un aviso de copyright.  Cualquier carácter de espacio o tabulación debe escribirse entre comillas dobles \("\) si forma parte de la cadena.  Una barra diagonal inversa \(\\\) debe preceder a las comillas dobles si estás forman parte de la cadena.  Dejar un espacio entre **\/V** y `string` es opcional.  
  
 También puede usar [comentario](../../preprocessor/comment-c-cpp.md) con el argumento de tipo de comentario del compilador para incluir el nombre y el número de versión del compilador en el archivo .obj.  
  
 **\/V** ha quedado desusado; **\/V** se usaba fundamentalmente para ofrecer compatibilidad con la compilación de controladores de dispositivos virtuales \(VxD\), y el conjunto de herramientas de [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] ya no es compatible con este tipo de compilación.  Para obtener más información, vea [Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/es-es/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce).  
  
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