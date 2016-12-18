---
title: "Compilar bibliotecas de importaci&#243;n y archivos de exportaci&#243;n | Microsoft Docs"
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
  - "VC.Project.VCLibrarianTool.ModuleDefinitionFile"
  - "VC.Project.VCLibrarianTool.ExportNamedFunctions"
  - "VC.Project.VCLibrarianTool.GenerateDebug"
  - "VC.Project.VCLibrarianTool.ForceSymbolReferences"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".lib (archivos)"
  - "/DEF (opción del administrador de bibliotecas)"
  - "/EXPORT (opción del administrador de bibliotecas)"
  - "/INCLUDE (opción del administrador de bibliotecas)"
  - "/OUT (opción del administrador de bibliotecas)"
  - "DEF (opción del administrador de bibliotecas)"
  - "-DEF (opción del administrador de bibliotecas)"
  - "EXP (archivos)"
  - "EXPORT (opción del administrador de bibliotecas)"
  - "-EXPORT (opción del administrador de bibliotecas)"
  - "exportar datos"
  - "exportar datos, archivos de exportación (.exp)"
  - "bibliotecas de importación, compilar"
  - "INCLUDE (opción del administrador de bibliotecas)"
  - "-INCLUDE (opción del administrador de bibliotecas)"
  - "OUT (opción del administrador de bibliotecas)"
  - "-OUT (opción del administrador de bibliotecas)"
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compilar bibliotecas de importaci&#243;n y archivos de exportaci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para compilar una biblioteca de importación, que es también un archivo de exportación, utilice la sintaxis siguiente:  
  
```  
LIB /DEF[:deffile] [options] [objfiles] [libraries]  
```  
  
 Cuando se especifica \/DEF, LIB crea los archivos de salida a partir de especificaciones de exportación que se pasan en el comando LIB.  Hay tres métodos para especificar exportaciones, que se muestran a continuación en el orden recomendado de uso:  
  
1.  Una definición **\_\_declspec\(dllexport\)** en uno de los archivos \(*objfiles*\) o una de las bibliotecas \(*libraries*\)  
  
2.  Una especificación de \/EXPORT:*name* en la línea de comandos de LIB  
  
3.  Una definición en una instrucción **EXPORTS** de un archivo \(`deffile`\)  
  
 Éstos son los mismos métodos que deberá utilizar para especificar exportaciones al vincular un programa exportador.  Un programa puede utilizar más de un método.  Puede especificar partes del comando LIB \(como varios archivos \(*objfiles*\) o especificaciones \/EXPORT\) en un archivo de comandos del comando LIB, de la misma manera que en un comando LINK.  
  
 Al compilar una biblioteca de importación y un archivo de exportación puede utilizar las siguientes opciones:  
  
 \/OUT: *import*  
 Reemplaza el nombre de archivo de salida predeterminado para la biblioteca de importación que se está creando.  Cuando no se especifica \/OUT, el nombre predeterminado será el nombre base del primer archivo objeto o biblioteca de comando LIB, y le asigna la extensión .lib.  Al archivo de exportación se le asigna el mismo nombre base que a la biblioteca de importación, con la extensión .exp.  
  
 \/EXPORT: *entryname*\[\= *internalname*\]\[,@ `ordinal`\[, **NONAME**\]\]\[, **DATA**\]  
 Exporta una función desde el programa para permitir que otros programas llamen a la función.  También puede exportar datos \(mediante la palabra clave **DATA**\).  Las exportaciones se suelen definir en archivos DLL.  
  
 El valor de *entryname* es el nombre de la función o el elemento de datos que va a utilizar el programa que llama.  De forma opcional, puede especificar el valor de *internalname* como la función conocida en el programa que define; de manera predeterminada, el valor de *internalname* coincide con el de *entryname*.  El valor de `ordinal` especifica un índice en la tabla de exportación, comprendido en el intervalo de 1 a 65535; si no especifica el valor de `ordinal`, LIB asigna un valor.  La palabra clave **NONAME** sólo exporta la función como un valor ordinal, sin un valor de *entryname*.  La palabra clave **DATA** se utiliza para exportar objetos que sólo contienen datos.  
  
 \/INCLUDE: `symbol`  
 Agrega el símbolo especificado a la tabla de símbolos.  Esta opción resulta útil para obligar al usuario a utilizar un objeto de biblioteca que no se podría incluir de otro modo.  
  
 Observe que si crea la biblioteca de importación en un paso preliminar, antes de crear la .dll, debe pasar el mismo conjunto de archivos objeto cuando genere la .dll que cuando generó la biblioteca de importación.  
  
## Vea también  
 [Trabajar con bibliotecas de importación y archivos de exportación](../../build/reference/working-with-import-libraries-and-export-files.md)