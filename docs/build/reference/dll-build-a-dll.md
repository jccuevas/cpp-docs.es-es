---
title: "/DLL (Compilar un archivo DLL) | Microsoft Docs"
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
  - "/dll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DLL (opción del vinculador) [C++]"
  - "-DLL (opción del vinculador)"
  - "DLL (opción del vinculador) [C++]"
  - "DLL [C++], compilar"
  - "exportar DLL [C++], especificar exportaciones"
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /DLL (Compilar un archivo DLL)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DLL  
```  
  
## Comentarios  
 La opción \/DLL compila una DLL como archivo de salida principal.  Las DLL normalmente contienen exportaciones que pueden utilizar otros programas.  Hay tres métodos para especificar exportaciones, que se muestran a continuación en el orden recomendado de uso:  
  
1.  [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md) en el código fuente.  
  
2.  Una instrucción [EXPORTS](../../build/reference/exports.md) en un archivo .def.  
  
3.  Una especificación [\/EXPORT](../../build/reference/export-exports-a-function.md) en un comando LINK.  
  
 Un programa puede utilizar más de un método.  
  
 Otro método para compilar una DLL es la instrucción de definición de módulos **LIBRARY**.  Las opciones \/BASE y \/DLL juntas equivalen a la instrucción **LIBRARY**.  
  
 Esta opción sólo debe usarse en la línea de comandos: no puede especificarse en el entorno de desarrollo.  Esta opción se establece cuando se crea un proyecto de DLL con el Asistente para aplicaciones.  
  
 Observe que si crea la biblioteca de importación en un paso preliminar, antes de crear la .dll, debe pasar el mismo conjunto de archivos objeto cuando genere la .dll que cuando generó la biblioteca de importación.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Propiedades de configuración**.  
  
3.  Haga clic en la página de propiedades **General**.  
  
4.  Modifique la propiedad **Tipo de configuración**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)