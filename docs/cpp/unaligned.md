---
title: __unaligned | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __unaligned_cpp
- __unaligned
dev_langs:
- C++
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 9f899add9a1306344a10840220f3b7504e917d91
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="unaligned"></a>__unaligned
Cuando se declara un puntero con el modificador `__unaligned`, el compilador supone que el puntero hace referencia a datos no alineados. Por consiguiente, para una aplicación destinada a un equipo IPF, de la familia de procesadores Itanium, el compilador genera código que lee los datos sin alinear byte a byte.  
  
## <a name="remarks"></a>Comentarios  
 El `__unaligned` modificador es válido para la [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] y [!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)] compiladores pero afecta a solo las aplicaciones que tienen como destino un equipo IPF. Este modificador describe la alineación de los datos objetivo solo; se supone que el puntero en sí está alineado.  
  
 El [!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)] procesador genera un error de alineación cuando tiene acceso a datos mal alineados, y el tiempo para procesar el error debilita rendimiento. Use el modificador `__unaligned` para hacer que el procesador lea los datos byte a byte y evitar el error. Este modificador no es necesario para [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] aplicaciones porque la [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] procesador controla datos mal alineados sin generar errores.  
  
 Para obtener más información sobre la alineación, vea:  
  
-   [align](../cpp/align-cpp.md)  
  
-   [__alignof (Operador)](../cpp/alignof-operator.md)  
  
-   [pack](../preprocessor/pack.md)  
  
-   [/Zp (alineación de miembros de estructura)](../build/reference/zp-struct-member-alignment.md)  
  
-   [Ejemplos de alineación de estructuras](../build/examples-of-structure-alignment.md)  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)
