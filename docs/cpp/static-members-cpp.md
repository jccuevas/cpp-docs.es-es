---
title: "Miembros est&#225;ticos (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "instancias de clase [C++], miembros compartidos"
  - "instancias de clase [C++], miembros estáticos"
  - "miembros de clases [C++], compartidos"
  - "miembros de clases [C++], static"
  - "miembros de datos [C++], miembros de datos estáticos"
  - "constructores de instancias, miembros compartidos"
  - "constructores de instancias, miembros estáticos"
  - "miembros [C++], miembros de datos estáticos"
  - "miembros de datos estáticos [C++]"
  - "miembros estáticos [C++], miembros de datos"
ms.assetid: 9cc8cf0f-d74c-46f2-8e83-42d4e42c8370
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Miembros est&#225;ticos (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases pueden contener datos de miembro y funciones miembro estáticos.  Cuando un miembro de datos se declara como **static**, solo se conserva una copia de los datos para todos los objetos de la clase.  \(Para obtener más información, vea [Funciones miembro estáticas](../misc/static-member-functions.md)\).  
  
 Los miembros de datos estáticos no forman parte de los objetos de un tipo de clase determinado.  Por tanto, la declaración de un miembro de datos estático no se considera una definición.  El miembro de datos se declara en el ámbito de la clase, pero la definición se realiza en el ámbito de archivo.  Estos miembros estáticos tienen vinculación externa.  Esto se ilustra en el siguiente ejemplo:  
  
```  
// static_data_members.cpp  
class BufferedOutput  
{  
public:  
   // Return number of bytes written by any object of this class.  
   short BytesWritten()  
   {  
      return bytecount;  
   }  
  
   // Reset the counter.  
   static void ResetCount()  
   {  
      bytecount = 0;  
   }  
  
   // Static member declaration.  
   static long bytecount;  
};  
  
// Define bytecount in file scope.  
long BufferedOutput::bytecount;  
  
int main()  
{  
}  
```  
  
 En el código anterior, el miembro `bytecount` se declara en la clase `BufferedOutput`, pero debe definirse fuera de la declaración de clase.  
  
 Se puede hacer referencia a miembros de datos estáticos sin hacer referencia a un objeto de tipo de clase.  El número de bytes escritos mediante objetos de `BufferedOutput` puede obtenerse de la manera siguiente:  
  
```  
long nBytes = BufferedOutput::bytecount;  
```  
  
 Para que el miembro estático exista, no es necesario que exista ningún objeto del tipo de clase.  También se puede obtener acceso a los miembros estáticos mediante los operadores de selección de miembros \(**.** y **–\>**\).  Por ejemplo:  
  
```  
BufferedOutput Console;  
  
long nBytes = Console.bytecount;  
```  
  
 En el caso anterior, la referencia al objeto \(`Console`\) no se evalúa; el valor devuelto es el del objeto estático `bytecount`.  
  
 Los miembros de datos estáticos están sujetos a las reglas de acceso a miembros de clase, por lo que el acceso privado a miembros de datos estáticos solo se permite para las funciones miembro de clase y los elementos friend.  Estas reglas se describen en [Control de acceso a miembros](../cpp/member-access-control-cpp.md).  La excepción es que los miembros de datos estáticos se deben definir en el ámbito de archivo, independientemente de sus restricciones de acceso.  Si el miembro de datos se va a inicializar explícitamente, se debe proporcionar un inicializador con la definición.  
  
 El nombre de clase no califica el tipo de un miembro estático.  Por tanto, el tipo de `BufferedOutput::bytecount` es `long`.  
  
## Vea también  
 [Clases y structs](../cpp/classes-and-structs-cpp.md)