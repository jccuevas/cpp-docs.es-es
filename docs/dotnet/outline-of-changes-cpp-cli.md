---
title: "Esquema de cambios (C++/CLI) | Microsoft Docs"
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
ms.assetid: c0bbbd6b-c5c4-44cf-a6ca-c1010c377e9d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Esquema de cambios (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se muestran ejemplos de algunos de los cambios que ha sufrido el lenguaje de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  Para obtener más información, siga el vínculo que acompaña a cada producto.  
  
## Ninguna palabra clave con subrayado doble  
 Se ha quitado el subrayado doble que precedía a todas las palabras clave, con una sola excepción.  Así, `__value` se convierte en `value` y `__interface` se convierte en `interface`, etc.  Para evitar conflictos entre los nombres de las palabras clave y de los identificadores en el código de usuario, las palabras clave se tratan principalmente como contextuales.  
  
 Para obtener más información, vea [Palabras clave del lenguaje \(C\+\+\/CLI\)](../dotnet/language-keywords-cpp-cli.md).  
  
## Declaraciones de clase  
 Sintaxis de Extensiones administradas:  
  
```  
__gc class Block {};                           // reference class  
__value class Vector {};                       // value class  
__interface I {};                        // interface class  
__gc __abstract class Shape {};                // abstract class  
__gc __sealed class Shape2D : public Shape {}; // derived class  
```  
  
 Nueva sintaxis:  
  
```  
ref class Block {};                // reference class  
value class Vector {};             // value class  
interface class I {};        // interface class  
ref class Shape abstract {};       // abstract class  
ref class Shape2D sealed: Shape{}; // derived class  
```  
  
 Para obtener más información, vea [Tipos administrados \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md).  
  
## Declaración de objetos  
 Sintaxis de Extensiones administradas:  
  
```  
public __gc class Form1 : public System::Windows::Forms::Form {  
private:  
   System::ComponentModel::Container __gc *components;  
   System::Windows::Forms::Button   __gc *button1;  
   System::Windows::Forms::DataGrid __gc *myDataGrid;     
   System::Data::DataSet  __gc *myDataSet;  
};  
```  
  
 Nueva sintaxis:  
  
```  
public ref class Form1 : System::Windows::Forms::Form {  
   System::ComponentModel::Container^ components;  
   System::Windows::Forms::Button^ button1;  
   System::Windows::Forms::DataGrid^ myDataGrid;  
   System::Data::DataSet^ myDataSet;  
};  
```  
  
 Para obtener más información, vea [Declaración de un objeto de una clase de referencia de CLR](../dotnet/declaration-of-a-clr-reference-class-object.md).  
  
### Asignación del montón administrado  
 Sintaxis de Extensiones administradas:  
  
```  
Button* button1 = new Button; // managed heap  
int *pi1 = new int;           // native heap  
Int32 *pi2 = new Int32;       // managed heap  
```  
  
 Nueva sintaxis:  
  
```  
Button^ button1 = gcnew Button;        // managed heap  
int * pi1 = new int;                   // native heap  
Int32^ pi2 = gcnew Int32;              // managed heap  
```  
  
 Para obtener más información, vea [Declaración de un objeto de una clase de referencia de CLR](../dotnet/declaration-of-a-clr-reference-class-object.md).  
  
### Una referencia de seguimiento a ningún objeto  
 Sintaxis de Extensiones administradas:  
  
```  
// OK: we set obj to refer to no object  
Object * obj = 0;  
  
// Error: no implicit boxing  
Object * obj2 = 1;  
```  
  
 Nueva sintaxis:  
  
```  
// Incorrect Translation  
// causes the implicit boxing of both 0 and 1  
Object ^ obj = 0;  
Object ^ obj2 = 1;  
  
// Correct Translation  
// OK: we set obj to refer to no object  
Object ^ obj = nullptr;  
  
// OK: we initialize obj2 to an Int32^  
Object ^ obj2 = 1;  
```  
  
 Para obtener más información, vea [Declaración de un objeto de una clase de referencia de CLR](../dotnet/declaration-of-a-clr-reference-class-object.md).  
  
## Declaración de matrices  
 Se ha rediseñado la matriz CLR.  Es similar a la colección de plantillas stl `vector`, pero se asigna a la clase `System::Array` subyacente; es decir, no es una implementación de plantilla.  
  
 Para obtener más información, vea [Declaración de una matriz de CLR](../dotnet/declaration-of-a-clr-array.md).  
  
### Matriz como parámetro  
 Sintaxis de matriz de Extensiones administradas:  
  
```  
void PrintValues( Object* myArr __gc[]);   
void PrintValues( int myArr __gc[,,]);   
```  
  
 Nueva sintaxis de matriz:  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
### Matriz como tipo de devolución  
 Sintaxis de matriz de Extensiones administradas:  
  
```  
Int32 f() [];   
int GetArray() __gc[];  
```  
  
 Nueva sintaxis de matriz:  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
### Inicialización rápida de la matriz CLR local  
 Sintaxis de matriz de Extensiones administradas:  
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = { __box(26), __box(27), __box(28),  
                                 __box(29), __box(30) };  
  
   return a1;  
}  
```  
  
 Nueva sintaxis de matriz:  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
  
   return a1;  
}  
```  
  
### Declaración explícita de la matriz CLR  
 Sintaxis de matriz de Extensiones administradas:  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 Nueva sintaxis de matriz:  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 Nuevo en el lenguaje: inicialización explícita de la matriz que sigue a gcnew  
  
```  
// explicit initialization list follow gcnew   
// is not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## Propiedades escalares  
 Sintaxis de propiedad de Extensiones administradas:  
  
```  
public __gc __sealed class Vector {  
   double _x;  
  
public:  
   __property double get_x(){ return _x; }  
   __property void set_x( double newx ){ _x = newx; }  
};  
```  
  
 Nueva sintaxis de propiedad:  
  
```  
public ref class Vector sealed {   
   double _x;  
  
public:  
   property double x   
   {  
      double get()             { return _x; }  
      void   set( double newx ){ _x = newx; }  
   } // Note: no semi-colon …  
};  
```  
  
 Nuevo en el lenguaje: propiedades triviales  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   // backing store is not accessible  
   property double x;   
};  
```  
  
 Para obtener más información, vea [Declaración de propiedades](../dotnet/property-declaration.md).  
  
## Propiedades indizadas  
 Sintaxis de propiedad indizada de Extensiones administradas:  
  
```  
public __gc class Matrix {  
   float mat[,];  
  
public:   
   __property void set_Item( int r, int c, float value) { mat[r,c] = value; }  
   __property int get_Item( int r, int c ) { return mat[r,c]; }  
};  
```  
  
 Nueva sintaxis de propiedad indizada:  
  
```  
public ref class Matrix {  
   array<float, 2>^ mat;  
  
public:  
   property float Item [int,int] {  
      float get( int r, int c ) { return mat[r,c]; }  
      void set( int r, int c, float value ) { mat[r,c] = value; }  
   }  
};  
```  
  
 Nuevo en el lenguaje: propiedad indizada en el nivel de clase  
  
```  
public ref class Matrix {  
   array<float, 2>^ mat;  
  
public:  
   // ok: class level indexer now  
   //     Matrix mat;  
   //     mat[ 0, 0 ] = 1;   
   //  
   // invokes the set accessor of the default indexer  
  
   property float default [int,int] {  
      float get( int r, int c ) { return mat[r,c]; }  
      void set( int r, int c, float value ) { mat[r,c] = value; }  
   }  
};  
```  
  
 Para obtener más información, vea [Declaración de índices de propiedad](../dotnet/property-index-declaration.md).  
  
## Operadores sobrecargados  
 Sintaxis de sobrecarga de operadores de Extensiones administradas:  
  
```  
public __gc __sealed class Vector {  
public:  
   Vector( double x, double y, double z );  
  
   static bool    op_Equality( const Vector*, const Vector* );  
   static Vector* op_Division( const Vector*, double );  
};  
  
int main() {  
   Vector *pa = new Vector( 0.231, 2.4745, 0.023 );  
   Vector *pb = new Vector( 1.475, 4.8916, -1.23 );   
  
   Vector *pc = Vector::op_Division( pa, 4.8916 );  
  
   if ( Vector::op_Equality( pa, pc ))  
      ;  
}  
```  
  
 Nueva sintaxis de sobrecarga de operadores:  
  
```  
public ref class Vector sealed {  
public:  
   Vector( double x, double y, double z );  
  
   static bool    operator ==( const Vector^, const Vector^ );  
   static Vector^ operator /( const Vector^, double );  
};  
  
int main() {  
   Vector^ pa = gcnew Vector( 0.231, 2.4745, 0.023 );  
   Vector^ pb = gcnew Vector( 1.475, 4.8916, -1.23 );  
  
   Vector^ pc = pa / 4.8916;  
   if ( pc == pa )  
      ;  
}  
```  
  
 Para obtener más información, vea [Operadores sobrecargados](../dotnet/overloaded-operators.md).  
  
## Operadores de conversión  
 Sintaxis de operador de conversión de Extensiones administradas:  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 Nueva sintaxis de operador de conversión:  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 Para obtener más información, vea [Cambios en los operadores de conversión](../dotnet/changes-to-conversion-operators.md).  
  
## Reemplazo explícito de un miembro de interfaz  
 Sintaxis de reemplazo explícita de Extensiones administradas:  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 Nueva sintaxis de reemplazo explícita:  
  
```  
public ref class R : public ICloneable {  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R   
   virtual R^ Clone();  
};  
```  
  
 Para obtener más información, vea [Reemplazo explícito de un miembro de interfaz](../dotnet/explicit-override-of-an-interface-member.md).  
  
## Funciones virtuales privadas  
 Sintaxis de función virtual privada de Extensiones administradas:  
  
```  
__gc class Base {  
private:  
   // inaccessible to a derived class  
   virtual void g();   
};  
  
__gc class Derived : public Base {  
public:  
   // ok: g() overrides Base::g()  
   virtual void g();  
};  
```  
  
 Nueva sintaxis de función virtual privada  
  
```  
ref class Base {  
private:  
   // inaccessible to a derived class  
   virtual void g();   
};  
  
ref class Derived : public Base {  
public:  
   // error: cannot override: Base::g() is inaccessible  
   virtual void g() override;  
};  
```  
  
 Para obtener más información, vea [Funciones virtuales privadas](../dotnet/private-virtual-functions.md).  
  
## Tipo de enumeración de CLR  
 Sintaxis de enumeración de Extensiones administradas:  
  
```  
__value enum e1 { fail, pass };  
public __value enum e2 : unsigned short  {   
   not_ok = 1024,   
   maybe, ok = 2048   
};    
```  
  
 Nueva sintaxis de enumeración:  
  
```  
enum class e1 { fail, pass };  
public enum class e2 : unsigned short {   
   not_ok = 1024,  
   maybe, ok = 2048   
};  
```  
  
 Aparte de este pequeño cambio sintáctico, el comportamiento del tipo de enumeración CLR ha cambiado en muchos aspectos:  
  
-   Ya no se admite una declaración adelantada de una enumeración CLR.  
  
-   La resolución de sobrecarga entre los tipos aritméticos integrados y la jerarquía de clases Object se ha invertido entre Extensiones administradas y [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  Como efecto secundario, las enumeraciones CLR ya no se convierten implícitamente en tipos aritméticos.  
  
-   En la nueva sintaxis, una enumeración CLR mantiene su propio ámbito, que no es el caso en Extensiones administradas.  Previamente, los enumeradores estaban visibles dentro del ámbito contenedor de la enumeración; ahora, los enumeradores se encapsulan dentro del ámbito de la enumeración.  
  
 Para obtener más información, vea [Tipo de enumeración de CLR](../dotnet/clr-enum-type.md).  
  
## Eliminación de la palabra clave \_\_box  
 Sintaxis de conversión boxing de Extensiones administradas:  
  
```  
Object *o = __box( 1024 ); // explicit boxing  
```  
  
 Nueva sintaxis de conversión boxing:  
  
```  
Object ^o = 1024; // implicit boxing  
```  
  
 Para obtener más información, vea [Controlador de seguimiento de un valor al que se le ha aplicado la conversión boxing](../dotnet/a-tracking-handle-to-a-boxed-value.md).  
  
## Punteros anclados  
 Sintaxis de puntero anclado de Extensiones administradas:  
  
```  
__gc struct H { int j; };  
  
int main() {  
   H * h = new H;  
   int __pin * k = & h -> j;  
};  
```  
  
 Nueva sintaxis de puntero anclado:  
  
```  
ref struct H { int j; };  
  
int main() {  
   H^ h = gcnew H;  
   pin_ptr<int> k = &h->j;  
}  
```  
  
 Para obtener más información, vea [Semántica de los tipos de valor](../dotnet/value-type-semantics.md).  
  
## La palabra clave \_\_typeof se convierte en typeid  
 Sintaxis de typeof de Extensiones administradas:  
  
```  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 Nueva sintaxis de typeid:  
  
```  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
 Para obtener más información, vea [T::typeid reemplaza typeof](../dotnet/typeof-goes-to-t-typeid.md).  
  
## Vea también  
 [Manual de migraciones C\+\+\/CLI](../dotnet/cpp-cli-migration-primer.md)   
 [\(NOTINBUILD\)Managed Extensions for C\+\+ Syntax Upgrade Checklist](http://msdn.microsoft.com/es-es/edbded88-7ef3-4757-bd9d-b8f48ac2aada)   
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)