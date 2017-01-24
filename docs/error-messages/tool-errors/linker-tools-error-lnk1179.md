---
title: "Error de las herramientas del vinculador LNK1179 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1179"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1179"
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK1179
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

archivo no válido o dañado: 'nombredearchivo' de COMDAT duplicado  
  
 Un módulo de objeto contiene dos o más archivos de COMDAT con el mismo nombre.  
  
 Este error puede producirse por el hecho de utilizar [\/H](../../build/reference/h-restrict-length-of-external-names.md), lo que limita la longitud de los nombres externos, y [\/Gy](../../build/reference/gy-enable-function-level-linking.md), que empaqueta las funciones en secciones de COMDAT.  
  
## Ejemplo  
 En el código siguiente, `function1` y `function2` son idénticas en los primeros ocho caracteres.  Al compilar con **\/Gy** y **\/H8** se produce un error de vinculación.  
  
```  
void function1(void);  
void function2(void);  
  
int main() {  
    function1();  
    function2();  
}  
  
void function1(void) {}  
void function2(void) {}  
```