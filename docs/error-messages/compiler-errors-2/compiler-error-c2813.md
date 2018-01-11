---
title: Error del compilador C2813 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3cc6ac0e287894dc2202814c55dac37569650f5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2813"></a>Error del compilador C2813
\#no se admite la importación con /MP  
  
 El error C2813 se genera si en un comando de compilador se especifica la opción del compilador **/MP** y dos o más archivos para compilar y uno o varios de los archivos contiene la directiva de preprocesador[#import](../../preprocessor/hash-import-directive-cpp.md) . La directiva [#import](../../preprocessor/hash-import-directive-cpp.md) genera clases de C++ a partir de los tipos de la biblioteca de tipos especificada y, a continuación, escribe las clases en dos archivos de encabezado. La directiva [#import](../../preprocessor/hash-import-directive-cpp.md) no se admite la directiva porque si varias unidades de compilación importan la misma biblioteca de tipos, las unidades entran en conflicto al intentar escribir los mismos archivos de encabezado al mismo tiempo.  
  
 Este error del compilador y el **/MP** opción del compilador son nuevas en Visual Studio 2008.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C2813. La línea de comandos del comentario "compile with:" indica al compilador que debe usar las opciones del compilador **/MP** y **/c** para compilar varios archivos. Al menos uno de los archivos contiene la directiva [#import](../../preprocessor/hash-import-directive-cpp.md) . El mismo archivo se usa dos veces para probar este ejemplo.  
  
```  
// C2813.cpp  
// compile with: /MP /c C2813.cpp C2813.cpp  
#import "C:\windows\system32\stdole2.tlb"   // C2813  
int main()   
{  
}  
```