---
title: Error de compilador Error C3172 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3172
dev_langs:
- C++
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: a53e7bc0b8543813e5745773f6a7548eb9a83442
ms.lasthandoff: 04/04/2017

---
# <a name="compiler-error-c3172"></a>Error de C3172 de Error de compilador
'nombre_de_módulo': no se puede especificar distintos atributos idl_module en un proyecto  
  
 [idl_module](../../windows/idl-module.md) atributos con el mismo nombre pero con distintos `dllname` o `version` se han encontrado los parámetros en dos de los archivos en una compilación. Solo un único `idl_module` atributo se puede especificar por cada compilación.  
  
 Idénticos `idl_module` atributos se pueden especificar más de un archivo de código fuente.  
  
 Por ejemplo, si el siguiente `idl_module` se encontraron atributos:  
  
```  
// C3172.cpp  
[module(name="MyMod")];  
[ idl_module(name="x", dllname="file.dll", version="1.1") ];  
int main() {}  
```  
  
 Y luego,  
  
```  
// C3172b.cpp  
// compile with: C3172.cpp  
// C3172 expected  
[ idl_module(name="x", dllname="file.dll", version="1.0") ];  
```  
  
 el compilador generará el error C3172 (Observe los diferentes valores de versión).
