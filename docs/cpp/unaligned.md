---
title: "__unaligned | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__unaligned_cpp"
  - "__unaligned"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__unaligned (palabra clave) [C++]"
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# __unaligned
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se declara un puntero con el modificador `__unaligned`, el compilador supone que el puntero hace referencia a datos no alineados.  Por consiguiente, para una aplicación destinada a un equipo IPF, de la familia de procesadores Itanium, el compilador genera código que lee los datos sin alinear byte a byte.  
  
## Comentarios  
 El modificador `__unaligned` es válido para los compiladores [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] e [!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)], pero solo afecta a las aplicaciones destinadas a equipos IPF.  Este modificador describe la alineación de los datos objetivo solo; se supone que el puntero en sí está alineado.  
  
 El procesador [!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)] genera un error de alineación cuando tiene acceso a datos mal alineados, y el tiempo necesario para procesar el error afecta negativamente al rendimiento.  Use el modificador `__unaligned` para hacer que el procesador lea los datos byte a byte y evitar el error.  Este modificador no es necesario para las aplicaciones [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)], porque el procesador [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] administra los datos mal alineados sin generar errores.  
  
 Para obtener más información sobre la alineación, vea:  
  
-   [align](../cpp/align-cpp.md)  
  
-   [\_\_alignof \(Operador\)](../cpp/alignof-operator.md)  
  
-   [pack](../preprocessor/pack.md)  
  
-   [\/Zp \(Alineación de miembros de estructura\)](../build/reference/zp-struct-member-alignment.md)  
  
-   [Ejemplos de alineación de estructuras](../build/examples-of-structure-alignment.md)  
  
## Ejemplo  
  
```  
// unaligned_keyword.cpp  
// compile with: /c  
// processor: x64 IPF  
#include <stdio.h>  
int main() {  
   char buf[100];  
  
   int __unaligned *p1 = (int*)(&buf[37]);  
   int *p2 = (int *)p1;  
  
   *p1 = 0;   // ok  
  
   __try {  
      *p2 = 0;  // throws an exception  
   }  
   __except(1) {  
      puts("exception");  
   }  
}  
```  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)