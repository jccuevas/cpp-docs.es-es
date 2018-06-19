---
title: Las herramientas del vinculador LNK1179 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1179
dev_langs:
- C++
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72a531397c3c101fbff937f293f772c5f6778523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300220"
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