---
title: Declaraciones y definiciones de C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c459999ab902a2498d4ffe4cc2d437a0a432b9b7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381570"
---
# <a name="c-declarations-and-definitions"></a>Declaraciones y definiciones de C
Una “declaración” establece una asociación entre una variable, función o tipo determinado y sus atributos. En [Información general de declaraciones](../c-language/overview-of-declarations.md) se proporciona la sintaxis ANSI de la `declaration` no terminal. Una declaración también especifica dónde y cuándo se puede acceder a un identificador (la "vinculación" de un identificador). Vea [Duración, ámbito, visibilidad y vinculación](../c-language/lifetime-scope-visibility-and-linkage.md) para obtener información sobre la vinculación.  
  
 Una “definición” de una variable establece las mismas asociaciones que una declaración pero también hace que se asigne almacenamiento a la variable.  
  
 Por ejemplo, las funciones `main`, `find` y `count` y las variables `var` y `val` se definen en un archivo de código fuente, en este orden:  
  
```  
int main() {}  
  
int var = 0;  
double val[MAXVAL];  
char find( fileptr ) {}  
int count( double f ) {}  
```  
  
 Las variables `var` y `val` se pueden utilizar en las funciones `find` y `count`; no se requieren más declaraciones. Pero estos nombres no son visibles (no se puede acceder a ellos) en `main`.  
  
## <a name="see-also"></a>Vea también  
 [Archivos de código fuente y programas origen](../c-language/source-files-and-source-programs.md)