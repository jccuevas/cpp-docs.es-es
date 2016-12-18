---
title: "__uuidof (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__LIBID_"
  - "__LIBID_cpp"
  - "__uuidof"
  - "__uuidof_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__LIBID_ (palabra clave) [C++]"
  - "__uuidof (palabra clave) [C++]"
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __uuidof (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Recupera el GUID asociado a la expresión.  
  
## Sintaxis  
  
```  
  
      __uuidof (  
   expression   
)  
```  
  
## Comentarios  
 *expression* puede ser un nombre de tipo, un puntero, una referencia o una matriz de ese tipo, una plantilla especializada en estos tipos, o una variable de estos tipos.  El argumento es válido siempre y cuando el compilador pueda utilizarlo para encontrar el GUID asociado.  
  
 Un caso especial de este intrínseco es cuando se proporciona **0** o **NULL** como argumento.  En este caso, `__uuidof` devolverá un GUID compuesto de ceros.  
  
 Utilice esta palabra clave para extraer el GUID asociado a lo siguiente:  
  
-   Un objeto por el atributo extendido [uuid](../cpp/uuid-cpp.md).  
  
-   Un bloque de biblioteca creado con el atributo [module](../windows/module-cpp.md).  
  
> [!NOTE]
>  En una compilación de depuración, `__uuidof` siempre inicializa un objeto dinámicamente \(en tiempo de ejecución\).  En una compilación de versión, `__uuidof` puede inicializar estáticamente \(en tiempo de compilación\) un objeto.  
  
## Ejemplo  
 El código siguiente \(compilado con ole32.lib\) mostrará el uuid de un bloque de biblioteca creado con el atributo module:  
  
```  
// expre_uuidof.cpp  
// compile with: ole32.lib  
#include "stdio.h"  
#include "windows.h"  
  
[emitidl];  
[module(name="MyLib")];  
[export]  
struct stuff {  
   int i;  
};  
  
int main() {  
   LPOLESTR lpolestr;  
   StringFromCLSID(__uuidof(MyLib), &lpolestr);  
   wprintf_s(L"%s", lpolestr);  
   CoTaskMemFree(lpolestr);  
}  
```  
  
## Comentarios  
 En aquellos casos en los que el nombre de biblioteca ya no se encuentre en el ámbito, puede utilizar \_\_LIBID\_ en lugar de `__uuidof`.  Por ejemplo:  
  
```  
StringFromCLSID(__LIBID_, &lpolestr);  
```  
  
 **Específicos de Microsoft: END**  
  
## Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)