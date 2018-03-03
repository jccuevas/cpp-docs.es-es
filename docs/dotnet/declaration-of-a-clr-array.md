---
title: "Declaración de una matriz de CLR | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
ms.assetid: 36a8883c-2663-43f0-a90c-28f27035e036
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3f263227d437ddafb65ac3da0829414e4af05855
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="declaration-of-a-clr-array"></a>Declaración de una matriz de CLR
La sintaxis para declarar, crear instancias e inicializar una matriz administrada ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 La declaración de un objeto de matriz de CLR en Extensiones administradas era una extensión de la declaración de matriz estándar en la que se colocaba una palabra clave `__gc` entre el nombre del objeto de matriz y su dimensión posiblemente rellenada de comas, como en el siguiente par de ejemplos:  
  
```  
void PrintValues( Object* myArr __gc[]);  
void PrintValues( int myArr __gc[,,]);  
```  
  
 Esto se ha simplificado en la nueva sintaxis, en el que se utiliza una declaración de tipo plantilla similar a la biblioteca estándar de C++ `vector` declaración. El primer parámetro indica el tipo de elemento. El segundo parámetro especifica la dimensión de la matriz (con un valor predeterminado de 1, tan sólo varias dimensiones requieren un segundo argumento). El propio objeto de matriz es un controlador de seguimiento, por lo que se le debe agregar un acento circunflejo. Si el tipo de elemento también es un tipo de referencia, se debe marcar igualmente con un acento circunflejo. Por ejemplo, el ejemplo anterior, cuando se expresa en la nueva sintaxis, tiene la apariencia siguiente:  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
 Como un tipo de referencia es un controlador de seguimiento más que un objeto, es posible especificar una matriz de CLR como tipo de valor devuelto de una función. (Por el contrario, no es posible especificar la matriz nativa como tipo de valor devuelto de una función.) La sintaxis para esto en Extensiones administradas no era algo muy intuitivo. Por ejemplo:  
  
```  
Int32 f() [];  
int GetArray() __gc[];  
```  
  
 En Visual C++, la declaración es mucho más fácil. Por ejemplo,  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
 La inicialización rápida de una matriz administrada local se admite en ambas versiones del lenguaje. Por ejemplo:  
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = {   
      __box(26), __box(27), __box(28), __box(29), __box(30)  
   };  
   return a1;  
}  
```  
  
 se ha simplificado considerablemente en la nueva sintaxis (tenga en cuenta que, dado que la conversión boxing es implícita en la nueva sintaxis, la `__box` se ha eliminado el operador: vea [sus comportamientos y tipos de valor (C++ / CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md) para obtener una discusión):  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
   return a1;  
}  
```  
  
 Dado que una matriz es un tipo de referencia de CLR, la declaración de cada objeto de matriz es un controlador de seguimiento. Por lo tanto, deben asignarse objetos de matriz al montón CLR. (La notación rápida oculta la asignación del montón administrada.) A continuación aparece el formulario explícito de una inicialización de objeto de matriz en Extensiones administradas:  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 En la nueva sintaxis, la expresión `new` se ha reemplazado por `gcnew`. Los tamaños de la dimensión se pasan como parámetros a la expresión `gcnew`, tal como sigue:  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 En la nueva sintaxis, una lista de inicializaciones explícitas puede seguir a la expresión `gcnew`; esto no estaba admitido en Extensiones administradas. Por ejemplo:  
  
```  
// explicit initialization list following gcnew   
// was not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## <a name="see-also"></a>Vea también  
 [Tipos administrados (C++ / CL)](../dotnet/managed-types-cpp-cl.md)   
 [Matrices](../windows/arrays-cpp-component-extensions.md)