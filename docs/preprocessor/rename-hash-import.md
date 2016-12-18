---
title: "rename (#import) | Microsoft Docs"
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
  - "Rename"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "cambiar nombre de atributo"
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rename (#import)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Resuelve problemas del conflicto de nombres.  
  
## Sintaxis  
  
```  
rename("OldName","NewName")  
```  
  
#### Parámetros  
 `OldName`  
 Nombre anterior en la biblioteca de tipos.  
  
 `NewName`  
 Nombre usado en lugar del nombre anterior.  
  
## Comentarios  
 Si se especifica este atributo, el compilador reemplaza todas las apariciones de *OldName* en una biblioteca de tipos por el *NewName* proporcionado por el usuario en los archivos de encabezado resultantes.  
  
 Este atributo se puede utilizar cuando un nombre en la biblioteca de tipos coincide con una definición de macro en los archivos de encabezado del sistema.  Si esta situación no se resuelve, se generarán distintos errores de sintaxis, como [Error del compilador C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) y [Error del compilador C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md).  
  
> [!NOTE]
>  La sustitución se aplica a un nombre usado en la biblioteca de tipos, no a un nombre usado en el archivo de encabezado resultante.  
  
 Suponga, por ejemplo, que hay una propiedad denominada `MyParent` en una biblioteca de tipos y que se define una macro `GetMyParent` en un archivo de encabezado y se utiliza antes de `#import`.  Como `GetMyParent` es el nombre predeterminado de una función contenedora para la propiedad **get** del control de errores, se produce un conflicto de nombres.  Para solucionar el problema, utilice el siguiente atributo en la instrucción `#import`:  
  
```  
rename("MyParent","MyParentX")  
```  
  
 que cambia el nombre `MyParent` en la biblioteca de tipos.  Un intento de cambiar el nombre del contenedor `GetMyParent` producirá un error:  
  
```  
rename("GetMyParent","GetMyParentX")  
```  
  
 Esto se debe a que el nombre `GetMyParent` solo aparece en el archivo de encabezado resultante de la biblioteca de tipos.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)