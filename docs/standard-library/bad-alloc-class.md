---
title: "bad_alloc (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::bad_alloc"
  - "new/std:bad_alloc"
  - "bad_alloc"
  - "std.bad_alloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_alloc (clase)"
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
caps.latest.revision: 26
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# bad_alloc (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase que describe una excepción que se produce para indicar que una solicitud de asignación no se realizó correctamente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class bad_alloc : public exception {  
    bad_alloc();
virtual ~bad_alloc();

};  
```  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto por **qué** es una cadena de C definido por la implementación. Ninguna de las funciones miembro produce excepciones.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< new>  
  
 **Espacio de nombres:** std  
  
## <a name="example"></a>Ejemplo  
  
```  
// bad_alloc.cpp  
// compile with: /EHsc  
#include<new>  
#include<iostream>  
using namespace std;  
  
int main() {  
   char* ptr;  
   try {  
      ptr = new char[(~unsigned int((int)0)/2) - 1];  
      delete[] ptr;  
   }  
   catch( bad_alloc &ba) {  
      cout << ba.what( ) << endl;  
   }  
}  
```  
  
## <a name="sample-output"></a>Resultados del ejemplo  
  
```  
bad allocation  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< new>  
  
## <a name="see-also"></a>Vea también
 [Clase Exception](../standard-library/exception-class1.md)  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

