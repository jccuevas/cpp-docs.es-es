---
title: "Inicializar matrices | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inicializar matrices"
  - "matrices [C++], inicializar"
ms.assetid: 41efe5f0-15b5-4f49-9196-c4902f8fc705
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Inicializar matrices
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si una clase tiene un constructor, las matrices de esa clase las inicializa un constructor. Si hay menos elementos en la lista de inicializadores que en la matriz, se usa el constructor predeterminado para los elementos restantes. Si no se define ningún constructor predeterminado para la clase, la lista de inicializadores debe estar completa (es decir, debe haber un inicializador para cada elemento de la matriz).  
  
 Considere la clase `Point`, que define dos constructores:  
  
```  
// initializing_arrays1.cpp  
class Point  
{  
public:  
   Point()   // Default constructor.  
   {  
   }  
   Point( int, int )   // Construct from two ints  
   {  
   }  
};  
  
// An array of Point objects can be declared as follows:  
Point aPoint[3] = {  
   Point( 3, 3 )     // Use int, int constructor.  
};  
  
int main()  
{  
}  
```  
  
 El primer elemento de `aPoint` se construye utilizando el constructor `Point( int, int )`; los dos elementos restantes se crean con el constructor predeterminado.  
  
 Matrices de miembros estáticos (si **const** o no) se pueden inicializar en sus definiciones (fuera de la declaración de clase). Por ejemplo:  
  
```  
// initializing_arrays2.cpp  
class WindowColors  
{  
public:  
    static const char *rgszWindowPartList[7];  
};  
  
const char *WindowColors::rgszWindowPartList[7] = {  
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",  
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [(NOTINBUILD) Funciones miembro especiales](http://msdn.microsoft.com/es-es/82223d73-64cb-4923-b678-78f9568ff3ca)