---
title: Constantes globales en C++ | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f1ee5fdf3d50f30e02bd48fe3664c10d26a8449
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="global-constants-in-c"></a>Constantes globales en C++
Constantes globales de C++ tienen vinculación estática. Esto es diferente de C. Si intenta utilizar un global constante en C++ en varios archivos obtendrá un error externo sin resolver. El compilador optimiza las constantes globales, sin dejar espacio reservado para la variable.  
  
 Una manera de resolver este error es incluir las inicializaciones constantes en un archivo de encabezado e incluir dicho encabezado en los archivos CPP cuando sea necesario, como si fuera un prototipo de función. Otra posibilidad es hacer que la variable no sea constante y usar una referencia constante al evaluarla.  
  
 El ejemplo siguiente genera C2019:  
  
```  
// global_constants.cpp  
// LNK2019 expected  
void test(void);  
const int lnktest1 = 0;  
  
int main() {  
   test();  
}  
```  
  
 Y luego,  
  
```  
// global_constants_2.cpp  
// compile with: global_constants.cpp  
extern int lnktest1;  
  
void test() {  
  int i = lnktest1;   // LNK2019  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)