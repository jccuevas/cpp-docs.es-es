---
title: "detect_mismatch | Microsoft Docs"
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
  - "vc-pragma.detect_mismatch"
  - "detect_mismatch_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "detect_mismatch (pragma)"
  - "pragma (directivas), detect_mismatch"
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# detect_mismatch
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inserta un registro en un objeto.  El vinculador comprueba estos registros para detectar potenciales discordancias.  
  
## Sintaxis  
  
```  
#pragma detect_mismatch( "name", "value"))  
```  
  
## Comentarios  
 Cuando se vincula el proyecto, el vinculador produce un error `LNK2038` si el proyecto contiene dos objetos que tengan el mismo `name` pero cada uno tiene diferente `value`.  Utilice esta directiva pragma para evitar la vinculación de archivos objeto incoherentes.  
  
 El nombre y el valor son literales de cadena y siguen las reglas para los literales de cadena con respecto a los caracteres de escape y concatenación.  Distinguen entre mayúsculas y minúsculas y no pueden contener comas, el signo igual, comillas dobles o el carácter `null`.  
  
## Ejemplo  
 En este ejemplo se crean dos archivos que tienen números de versión diferentes para la misma etiqueta de versión.  
  
```  
// pragma_directive_detect_mismatch_a.cpp  
#pragma detect_mismatch("myLib_version", "9")  
int main ()  
{  
   return 0;  
}  
  
// pragma_directive_detect_mismatch_b.cpp  
#pragma detect_mismatch("myLib_version", "1")  
```  
  
 Si compila ambos archivos mediante la línea de comandos `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp`, recibirá el error `LNK2038`.  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)