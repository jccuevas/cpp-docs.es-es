---
title: operador __uuidof | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
dev_langs: C++
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c5d83f99b40e6eb897212fbcfb03c01b4f6b55e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="uuidof-operator"></a>__uuidof (Operador)
**Específicos de Microsoft**  
  
 Recupera el GUID asociado a la expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      __uuidof (  
   expression   
)  
```  
  
## <a name="remarks"></a>Comentarios  
 El *expresión* puede ser un nombre de tipo, el puntero, referencia o matriz de ese tipo, una plantilla especializada en estos tipos, o una variable de estos tipos. El argumento es válido siempre y cuando el compilador pueda utilizarlo para encontrar el GUID asociado.  
  
 Un caso especial de este intrínseco es cuando cualquier **0** o **NULL** se proporciona como argumento. En este caso, `__uuidof` devolverá un GUID compuesto de ceros.  
  
 Utilice esta palabra clave para extraer el GUID asociado a lo siguiente:  
  
-   Un objeto por el [uuid](../cpp/uuid-cpp.md) atributo extendido.  
  
-   Un bloque de biblioteca creado con la [módulo](../windows/module-cpp.md) atributo.  
  
> [!NOTE]
>  En una compilación de depuración, `__uuidof` siempre inicializa un objeto dinámicamente (en tiempo de ejecución). En una compilación de versión, `__uuidof` puede inicializar estáticamente (en tiempo de compilación) un objeto.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente (compilado con ole32.lib) mostrará el uuid de un bloque de biblioteca creado con el atributo module:  
  
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
  
## <a name="comments"></a>Comentarios  
 En casos donde el nombre de biblioteca ya no está en ámbito, puede usar __LIBID\_ en lugar de `__uuidof`. Por ejemplo:  
  
```  
StringFromCLSID(__LIBID_, &lpolestr);  
```  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Palabras clave](../cpp/keywords-cpp.md)