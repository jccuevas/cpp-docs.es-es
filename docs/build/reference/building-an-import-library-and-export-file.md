---
title: Creación de una biblioteca de importación y archivos de exportación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
dev_langs:
- C++
helpviewer_keywords:
- OUT library manager option
- INCLUDE library manager option
- /DEF library manager option
- exporting data
- import libraries, building
- -INCLUDE library manager option
- /OUT library manager option
- DEF library manager option
- -DEF library manager option
- -OUT library manager option
- /INCLUDE library manager option
- -EXPORT library manager option
- exporting data, export (.exp) files
- /EXPORT library manager option
- EXPORT library manager option
- .lib files
- EXP files
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93f817aadf2de826c628a14255ae9257be2f29ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="building-an-import-library-and-export-file"></a>Compilar bibliotecas de importación y archivos de exportación
Para crear una biblioteca de importación y exportación de archivo, use la sintaxis siguiente:  
  
```  
LIB /DEF[:deffile] [options] [objfiles] [libraries]  
```  
  
 Cuando se especifica/def, LIB crea los archivos de salida de las especificaciones de exportación que se pasan en el comando LIB. Existen tres métodos para especificar exportaciones, aparecen en el orden recomendado de uso:  
  
1.  A **__declspec (dllexport)** definición en uno de los *archivos (objfiles)* o *bibliotecas*  
  
2.  Una especificación de/Export:*nombre* en la línea de comandos LIB  
  
3.  Una definición en un **exportaciones** instrucción en un `deffile`  
  
 Estos son los mismos métodos que usan para especificar exportaciones al vincular un programa exportador. Un programa puede usar más de un método. Puede especificar partes del comando LIB (como varios *archivos (objfiles)* o especificaciones/Export) en un archivo de comandos en el comando LIB, tal y como lo pueden realizar en un comando de LINK.  
  
 Las siguientes opciones se aplican a la creación de una biblioteca de importación y exportación archivo:  
  
 / OUT: *importar*  
 Invalida el nombre del archivo de salida predeterminado para la *importar* biblioteca que se va a crear. Cuando no se especifica/out, el nombre predeterminado es el nombre base del primer archivo objeto o biblioteca en el comando LIB y la extensión. lib. El archivo de exportación tiene el mismo nombre base que la biblioteca de importación y la extensión. exp.  
  
 / EXPORT: *entrada*[= *internalname*] [, @ `ordinal`[, **NONAME**]] [, **datos**]  
 Exporta una función desde el programa para permitir que otros programas para llamar a la función. También puede exportar datos (mediante la **datos** palabra clave). Exportaciones generalmente se definen en un archivo DLL.  
  
 El *entrada* es el nombre de la función o elemento de datos que va a ser utilizada por el programa que realiza la llamada. Si lo desea, puede especificar el *internalname* como la función conocida en el programa que define; de forma predeterminada, *internalname* es el mismo que *entrada*. El `ordinal` especifica un índice en la tabla de exportación en el intervalo 1 a 65535; si no se especifica `ordinal`, LIB asigna un valor. El **NONAME** palabra clave exporta la función solo como un valor ordinal, sin un *entrada*. El **datos** palabra clave se utiliza para exportar objetos exclusivo de datos.  
  
 / INCLUYEN: `symbol`  
 Agrega el símbolo especificado a la tabla de símbolos. Esta opción es útil para forzar el uso de un objeto de biblioteca que de lo contrario no se incluye.  
  
 Tenga en cuenta que si crea la biblioteca de importación en un paso preliminar, antes de crear el archivo .dll, debe pasar el mismo conjunto de archivos de objeto al crear el archivo .dll, tal y como se haya pasado al crear la biblioteca de importación.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con bibliotecas de importación y archivos de exportación](../../build/reference/working-with-import-libraries-and-export-files.md)