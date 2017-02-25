---
title: "/IGNORE (ignorar advertencias espec&#237;ficas) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ignore"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/IGNORE (opción del vinculador)"
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# /IGNORE (ignorar advertencias espec&#237;ficas)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IGNORE:warning[,warning]  
```  
  
## Parámetros  
 `warning`  
 El número de advertencia del vinculador que se debe suprimir, en el intervalo de 4000 a 4999.  
  
## Comentarios  
 De manera predeterminada, LINK informa de todas las advertencias.  Especifique **\/IGNORE:**`warning` para indicarle al vinculador que debe suprimir un número de advertencia específico.  Para ignorar varias advertencias, separe los números de advertencia con comas.  
  
 El vinculador no permite omitir algunas advertencias.  En esta tabla se enumeran las advertencias que no se suprimen con **\/IGNORE**:  
  
|Advertencia del vinculador||  
|--------------------------------|-|  
|LNK4017|no se admite la instrucción `keyword` para la plataforma de destino; se ha omitido|  
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|opción no reconocida '`option`'; se ha omitido|  
|LNK4062|'`option`' no compatible con el equipo de destino '`architecture`'; opción omitida|  
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|se omite "`option1`" debido a la especificación "`option2`"|  
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|el punto de entrada '`function`' no es \_\_stdcall con '`number`' bytes de argumentos; es posible que la imagen no se pueda ejecutar|  
|LNK4088|la imagen se está generando debido a la opción \/FORCE; es posible que la imagen no se pueda ejecutar|  
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|ningún argumento especificado con la opción '`option`'; se omite el modificador|  
|LNK4203|error al leer la base de datos '`filename`' del programa; se vinculará el objeto sin tener en cuenta información de depuración|  
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|'`filename`' carece de información de depuración para hacer referencia al módulo; se vinculará el objeto sin tener en cuenta información de depuración|  
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|'`filename`' carece de información de depuración actual para hacer referencia al módulo; se vinculará el objeto sin tener en cuenta información de depuración|  
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|no se encontró información de tipo precompilado; '`filename`' no vinculado o reemplazado; se vinculará el objeto sin tener en cuenta información de depuración|  
|LNK4207|'`filename`' compilado \/Yc \/Yu \/Z7; no se puede crear PDB; vuelva a compilar con \/Zi; se vinculará el objeto sin tener en cuenta información de depuración|  
|LNK4208|formato PDB incompatible en '`filename`'; elimine y genere de nuevo; se vinculará el objeto sin tener en cuenta información de depuración|  
|LNK4209|información de depuración dañada; compile de nuevo el módulo; se vinculará el objeto sin tener en cuenta información de depuración|  
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option` ya no se admite; se omite|  
|LNK4228|'`option`' no es válido para una DLL; se ha omitido|  
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|se encontró la directiva \/`directive` no válida; se ha omitido|  
  
 En general, las advertencias del vinculador que no se pueden omitir representan errores de compilación, errores de la línea de comandos o errores de configuración que se deben corregir.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  En la carpeta **Vinculador**, seleccione la página de propiedades **Línea de comandos**.  
  
3.  Modifique la propiedad **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.