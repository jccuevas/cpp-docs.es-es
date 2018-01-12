---
title: Compilador advertencia (nivel 4) C4510 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4510
dev_langs: C++
helpviewer_keywords: C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4bfef2780f338357b600f8fae28559d4c7c00e49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4510"></a>Advertencia del compilador (nivel 4) C4510
'clase': no se pudo generar un constructor predeterminado  
  
 El compilador no puede generar un constructor predeterminado para la clase especificada y se ha creado ningún constructor definido por el usuario. No podrá crear objetos de este tipo.  
  
 Hay varias situaciones que impiden que el compilador genere un constructor predeterminado, incluidas:  
  
-   Un miembro de datos const.  
  
-   Un miembro de datos que es una referencia.  
  
 Debe crear un constructor predeterminado definido por el usuario para la clase que inicializa a estos miembros.  
  
 El ejemplo siguiente genera C4510:  
  
```  
// C4510.cpp  
// compile with: /W4  
struct A {  
   const int i;  
   int &j;  
   A& operator=( const A& ); // C4510 expected  
   // uncomment the following line to resolve this C4510  
   // A(int ii, int &jj) : i(ii), j(jj) {}  
};   // C4510  
  
int main() {  
}  
```