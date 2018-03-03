---
title: Las herramientas del vinculador LNK1179 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1179
dev_langs:
- C++
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93b042e928331e369d64a45aa27f5f613ce9fc31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1179"></a>Error de las herramientas del vinculador LNK1179
archivo no válido o dañado: 'filename' de COMDAT duplicado  
  
 Un módulo de objeto contiene dos o más archivos de COMDAT con el mismo nombre.  
  
 Este error puede deberse al uso [/H](../../build/reference/h-restrict-length-of-external-names.md), lo que limita la longitud de los nombres externos, y [/Gy](../../build/reference/gy-enable-function-level-linking.md), que empaqueta las funciones en COMDAT.  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente, `function1` y `function2` son idénticas en los primeros ocho caracteres. Compilar con **/Gy** y **/H8 se** produce un error de vínculo.  
  
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