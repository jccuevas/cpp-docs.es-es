---
title: "/EXPORT (Exporta una funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.ExportFunctions"
  - "/export"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/EXPORT (opción del vinculador)"
  - "EXPORT (opción del vinculador)"
  - "-EXPORT (opción del vinculador)"
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /EXPORT (Exporta una funci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/EXPORT:entryname[,@ordinal[,NONAME]][,DATA]  
```  
  
## Comentarios  
 Esta opción permite exportar una función desde el programa, de modo que otros programas también puedan llamarla.  Permite además exportar datos.  Las exportaciones se suelen definir en archivos DLL.  
  
 El valor de *entryname* es el nombre de la función o el elemento de datos que va a utilizar el programa que llama.  El valor de `ordinal` especifica un índice en la tabla de exportación, comprendido en el intervalo de 1 a 65.535; si no especifica el valor de `ordinal`, LINK asigna un valor.  La palabra clave **NONAME** sólo exporta la función como un valor ordinal, sin un valor de *entryname*.  
  
 La palabra clave **DATA** especifica que el elemento exportado es de datos.  El elemento de datos del programa cliente debe declararse mediante **extern \_\_declspec\(dllimport\)**.  
  
 Existen tres métodos para exportar una definición, que se indican en el orden de uso recomendado:  
  
1.  [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md) en el código fuente.  
  
2.  Una instrucción [EXPORTS](../../build/reference/exports.md) en un archivo .def.  
  
3.  Una especificación \/EXPORT en un comando LINK  
  
 Los tres métodos se pueden utilizar en el mismo programa.  Cuando LINK compila un programa que contiene exportaciones, crea además una biblioteca de importación, a menos que se utilice un archivo .exp en la compilación.  
  
 LINK usa formatos representativos para los identificadores.  El compilador decora los identificadores cuando crea el archivo .obj.  Si se especifica *entryname* para el vinculador en su formato no representativo \(tal como aparece en el código fuente\), LINK intentará encontrar el nombre.  Y, si no encuentra una única coincidencia, generará un mensaje de error.  La herramienta [DUMPBIN](../../build/reference/dumpbin-reference.md) se utiliza para obtener el formato de [nombres representativos](../../build/reference/decorated-names.md) de un identificador que necesite especificarse en el vinculador.  
  
> [!NOTE]
>  No se debe especificar la forma representativa de los identificadores de C declarados con `__cdecl` o `__stdcall`.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)