---
title: "Advertencia del compilador (nivel 4) C4510 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4510"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4510"
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 4) C4510
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase' : no se pudo generar un constructor predeterminado  
  
 El compilador no puede generar un constructor predeterminado para la clase especificada y no se ha creado ningún constructor definido por el usuario.  No se podrán crear objetos de este tipo.  
  
 Hay varias funciones que impiden que el compilador genere un constructor predeterminado, incluidas:  
  
-   Un miembro de datos const.  
  
-   Un miembro de datos que sea una referencia.  
  
 Es necesario crear un constructor predeterminado definido por el usuario para la clase que inicializa estos miembros.  
  
 El código siguiente genera el error C4510:  
  
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