---
title: "Operadores sobrecargados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sobrecarga de operadores, en una clase de CLR"
  - "operadores [C++], sobrecargar"
ms.assetid: 30391426-afe7-4497-bf22-e4816c1e48c8
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores sobrecargados
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La sobrecarga de operadores ha cambiado significativamente de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 En la declaración de un tipo de referencia, por ejemplo, en lugar de utilizar la sintaxis `operator+` nativa, debe escribir explícitamente el nombre interno subyacente del operador; en este caso, `op_Addition`.  Además, la invocación de un operador debe realizarse de forma explícita mediante ese nombre, lo que elimina las dos ventajas principales de la sobrecarga de operadores: \(a\) la sintaxis intuitiva y \(b\) la posibilidad de combinar nuevos tipos con tipos existentes.  Por ejemplo:  
  
```  
public __gc __sealed class Vector {  
public:  
   Vector( double x, double y, double z );  
  
   static bool    op_Equality( const Vector*, const Vector* );  
   static Vector* op_Division( const Vector*, double );  
   static Vector* op_Addition( const Vector*, const Vector* );  
   static Vector* op_Subtraction( const Vector*, const Vector* );  
};  
  
int main()  
{  
   Vector *pa = new Vector( 0.231, 2.4745, 0.023 );  
   Vector *pb = new Vector( 1.475, 4.8916, -1.23 );   
  
   Vector *pc1 = Vector::op_Addition( pa, pb );  
   Vector *pc2 = Vector::op_Subtraction( pa, pc1 );  
   Vector *pc3 = Vector::op_Division( pc1, pc2->x );  
  
   if ( Vector::op_Equality( pc1, pc2 ))  
      ;  
}  
```  
  
 En la nueva sintaxis, se recuperan las expectativas usuales de un programador de C\+\+ nativo, tanto en la declaración como en el uso de operadores estáticos.  Ésta es la clase `Vector` traducida a la nueva sintaxis:  
  
```  
public ref class Vector sealed {  
public:  
   Vector( double x, double y, double z );  
  
   static bool    operator ==( const Vector^, const Vector^ );  
   static Vector^ operator /( const Vector^, double );  
   static Vector^ operator +( const Vector^, const Vector^ );  
   static Vector^ operator -( const Vector^, const Vector^ );  
};  
  
int main()  
{  
   Vector^ pa = gcnew Vector( 0.231, 2.4745, 0.023 );  
   Vector^ pb = gcnew Vector( 1.475,4.8916,-1.23 );  
  
   Vector^ pc1 = pa + pb;  
   Vector^ pc2 = pa - pc1;  
   Vector^ pc3 = pc1 / pc2->x;  
  
   if ( pc1 == pc2 )  
      ;  
}  
```  
  
## Vea también  
 [Declaraciones de miembros en una clase o interfaz \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)