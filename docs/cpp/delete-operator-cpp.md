---
title: "delete (Operador) (C++) | Microsoft Docs"
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
  - "delete_cpp"
  - "delete"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "delete (palabra clave) [C++]"
  - "delete (palabra clave) [C++], desasignar objetos"
  - "delete (palabra clave) [C++], sintaxis"
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# delete (Operador) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Desasigna un bloque de memoria.  
  
## Sintaxis  
  
```  
[::] delete cast-expression  
[::] delete [ ] cast-expression  
```  
  
## Comentarios  
 El argumento de la expresión de conversión *cast\-expression* debe ser un puntero a un bloque de memoria asignado previamente para un objeto creado con el [operador new](../cpp/new-operator-cpp.md).  El operador **delete** tiene un resultado de tipo `void` y, por tanto, no devuelve ningún valor.  Por ejemplo:  
  
```  
CDialog* MyDialog = new CDialog;  
// use MyDialog  
delete MyDialog;  
```  
  
 El uso de **delete** en un puntero a un objeto no asignado con **new** tiene resultados impredecibles.  Sin embargo, se puede utilizar **delete** en un puntero con el valor 0.  Este aprovisionamiento significa que, cuando **new** devuelve 0 en caso de error, es inocuo eliminar el resultado de una operación **new** con errores.  Vea [Los operadores new y delete](../cpp/new-and-delete-operators.md) para obtener más información.  
  
 Los operadores **new** y **delete** también se pueden utilizar para tipos integrados, incluidas matrices.  Si `pointer` hace referencia a una matriz, ponga corchetes vacíos delante de `pointer`:  
  
```  
int* set = new int[100];  
//use set[]  
delete [] set;  
```  
  
 El uso del operador **delete** en un objeto desasigna su memoria.  Un programa que desreferencia un puntero después de eliminarse el objeto puede producir resultados impredecibles o bloquearse.  
  
 Cuando se utiliza **delete** para desasignar memoria para un objeto de clase de C\+\+, se llama al destructor del objeto antes de que se desasigne la memoria del objeto \(si el objeto tiene un destructor\).  
  
 Si el operando del operador **delete** es un valor L modificable, su valor está sin definir después de que se elimine el objeto.  
  
## Usar delete  
 Hay dos variantes sintácticas para el [operador delete](../cpp/delete-operator-cpp.md): uno para objetos únicos y otro para matrices de objetos.  En el fragmento de código siguiente se muestra cómo difieren entre sí:  
  
```  
// expre_Using_delete.cpp  
struct UDType   
{  
};  
  
int main()  
{  
   // Allocate a user-defined object, UDObject, and an object  
   //  of type double on the free store using the  
   //  new operator.  
   UDType *UDObject = new UDType;  
   double *dObject = new double;  
   // Delete the two objects.  
   delete UDObject;  
   delete dObject;   
   // Allocate an array of user-defined objects on the  
   // free store using the new operator.  
   UDType (*UDArr)[7] = new UDType[5][7];  
   // Use the array syntax to delete the array of objects.  
   delete [] UDArr;  
}  
```  
  
 Los dos casos siguientes generan resultados sin definir: usando la forma de matriz de \(delete \[ \]\) en un objeto y usando la forma no de matriz de delete en una matriz.  
  
## Ejemplo  
 Para obtener ejemplos del uso de **delete**, vea [new \(operador\)](../cpp/new-operator-cpp.md).  
  
## Cómo eliminar trabajos  
 El [operador delete](../cpp/delete-operator-cpp.md) invoca la función [operator delete](../misc/operator-delete-function.md).  
  
 Para los objetos que no son no de tipo de clase \([class](../cpp/class-cpp.md), [struct](../cpp/struct-cpp.md) o [union](../cpp/unions.md)\), se invoca el operador delete global.  Para los objetos de tipo de clase, el nombre de la función de desasignación se resuelve en el ámbito global si la expresión de eliminación comienza con el operador unario de resolución de ámbito \(::\).  Si no, el operador delete invoca el destructor de un objeto antes de la desasignación de memoria \(si el puntero no es nulo\).  El operador delete puede definirse clase por clase; si no existe esta definición para una clase determinada, se invoca el operador delete global.  Si la expresión de eliminación se utiliza para desasignar un objeto de clase cuyo de tipo estático tenga un destructor virtual, la función de desasignación se resuelve mediante el destructor virtual del tipo dinámico del objeto.  
  
## Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Operadores new y delete](../cpp/new-and-delete-operators.md)   
 [operator delete \(Función\)](../misc/operator-delete-function.md)