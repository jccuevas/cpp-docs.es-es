---
title: Esquema de cambios (C++ / CLI) | Documentos de Microsoft
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
ms.assetid: c0bbbd6b-c5c4-44cf-a6ca-c1010c377e9d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fdc0015bda5f0a6678b1d274c79445aba4e4aab0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="outline-of-changes-ccli"></a>Esquema de cambios (C++/CLI)
Este tema muestran ejemplos de algunos de los cambios en el lenguaje de extensiones administradas para C++ a Visual C++. Siga el vínculo que acompaña a cada elemento para obtener más información.  
  
## <a name="no-double-underscore-keywords"></a>No hay palabras clave de subrayado doble  
 Se quitó el carácter de subrayado doble delante de todas las palabras clave, con una excepción. Por lo tanto, `__value` se convierte en `value`, y `__interface` se convierte en `interface`, y así sucesivamente. Para evitar conflictos de nombres entre palabras clave y los identificadores del código de usuario, palabras clave se trata principalmente como contextuales.  
  
 Vea [palabras clave del lenguaje (C++ / CLI)](../dotnet/language-keywords-cpp-cli.md) para obtener más información.  
  
## <a name="class-declarations"></a>Declaraciones de clase  
 Sintaxis de extensiones administradas:  
  
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
  
 Vea [tipos administrados (C++ / CL)](../dotnet/managed-types-cpp-cl.md) para obtener más información.  
  
## <a name="object-declaration"></a>Declaración de objeto  
 Sintaxis de extensiones administradas:  
  
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
  
 Vea [declaración de un objeto de clase de referencia de CLR](../dotnet/declaration-of-a-clr-reference-class-object.md) para obtener más información.  
  
### <a name="managed-heap-allocation"></a>Asignación en el montón administrado  
 Sintaxis de extensiones administradas:  
  
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
  
 Vea [declaración de un objeto de clase de referencia de CLR](../dotnet/declaration-of-a-clr-reference-class-object.md) para obtener más información.  
  
### <a name="a-tracking-reference-to-no-object"></a>Una referencia de seguimiento a ningún objeto  
 Sintaxis de extensiones administradas:  
  
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
  
 Vea [declaración de un objeto de clase de referencia de CLR](../dotnet/declaration-of-a-clr-reference-class-object.md) para obtener más información.  
  
## <a name="array-declaration"></a>Declaración de matriz  
 Se ha rediseñado la matriz CLR. Es similar a la stl `vector` colección de plantilla, pero se asigna a subyacente `System::Array` clase; es decir, no es una implementación de plantilla.  
  
 Vea [declaración de una matriz de CLR](../dotnet/declaration-of-a-clr-array.md) para obtener más información.  
  
### <a name="array-as-parameter"></a>Matriz como parámetro  
 Sintaxis de matriz de extensiones administradas:  
  
```  
void PrintValues( Object* myArr __gc[]);   
void PrintValues( int myArr __gc[,,]);   
```  
  
 Nueva sintaxis de matriz:  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
### <a name="array-as-return-type"></a>Matriz como tipo de valor devuelto  
 Sintaxis de matriz de extensiones administradas:  
  
```  
Int32 f() [];   
int GetArray() __gc[];  
```  
  
 Nueva sintaxis de matriz:  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
### <a name="shorthand-initialization-of-local-clr-array"></a>Inicialización rápida de la matriz CLR Local  
 Sintaxis de matriz de extensiones administradas:  
  
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
  
### <a name="explicit-clr-array-declaration"></a>Declaración de matriz CLR explícita  
 Sintaxis de matriz de extensiones administradas:  
  
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
  
## <a name="scalar-properties"></a>Propiedades escalares  
 Sintaxis de la propiedad de extensiones administradas:  
  
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
   } // Note: no semi-colon  
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
  
 Vea [declaración de propiedad](../dotnet/property-declaration.md) para obtener más información.  
  
## <a name="indexed-properties"></a>Propiedades indizadas  
 Sintaxis de la propiedad habían indizada de extensiones administradas:  
  
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
  
 Nuevo en el lenguaje: propiedad indizada de nivel de clase  
  
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
  
 Vea [Property Index Declaration](../dotnet/property-index-declaration.md) para obtener más información.  
  
## <a name="overloaded-operators"></a>Operadores sobrecargados  
 Sintaxis de sobrecarga de operador de extensiones administradas:  
  
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
  
 Nueva sintaxis de sobrecarga de operador:  
  
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
  
 Vea [operadores sobrecargados](../dotnet/overloaded-operators.md) para obtener más información.  
  
## <a name="conversion-operators"></a>Operadores de conversión  
 Sintaxis de operador de conversión de extensiones administradas:  
  
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
  
 Vea [cambia a los operadores de conversión](../dotnet/changes-to-conversion-operators.md) para obtener más información.  
  
## <a name="explicit-override-of-an-interface-member"></a>Reemplazo explícito de un miembro de interfaz  
 Sintaxis de reemplazo explícita de extensiones administradas:  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 Nueva sintaxis de reemplazo explícito:  
  
```  
public ref class R : public ICloneable {  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R   
   virtual R^ Clone();  
};  
```  
  
 Vea [la invalidación explícita de un miembro de interfaz](../dotnet/explicit-override-of-an-interface-member.md) para obtener más información.  
  
## <a name="private-virtual-functions"></a>Funciones virtuales privadas  
 Sintaxis de función virtual privada de extensiones administradas:  
  
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
  
 Vea [Private Virtual Functions](../dotnet/private-virtual-functions.md) para obtener más información.  
  
## <a name="clr-enum-type"></a>Tipo de enumeración de CLR  
 Sintaxis de enumeración de extensiones administradas:  
  
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
  
 Aparte de este pequeño cambio sintáctico, el comportamiento del tipo de enumeración CLR se ha cambiado en una de varias maneras:  
  
-   Ya no se admite una declaración adelantada de una enumeración CLR.  
  
-   La resolución de sobrecarga entre los tipos aritméticos integrados y la jerarquía de clases de objeto se ha invertido entre extensiones administradas y Visual C++. Como efecto secundario, las enumeraciones CLR ya no es implícitamente se convierten en tipos aritméticos.  
  
-   En la nueva sintaxis, una enumeración de CLR mantiene su propio ámbito, que no es el caso en extensiones administradas. Anteriormente, los enumeradores estaban visibles dentro del ámbito contenedor de la enumeración; Ahora, los enumeradores se encapsulan dentro del ámbito de la enumeración.  
  
 Vea [tipo de enumeración de CLR](../dotnet/clr-enum-type.md) para obtener más información.  
  
## <a name="removal-of-box-keyword"></a>Eliminación de __box (palabra clave)  
 Sintaxis de conversión boxing de extensiones administradas:  
  
```  
Object *o = __box( 1024 ); // explicit boxing  
```  
  
 Nueva sintaxis de conversión boxing:  
  
```  
Object ^o = 1024; // implicit boxing  
```  
  
 Vea [A Tracking Handle en un valor a una conversión boxing](../dotnet/a-tracking-handle-to-a-boxed-value.md) para obtener más información.  
  
## <a name="pinning-pointer"></a>Puntero anclado  
 Sintaxis de puntero anclado de extensiones administradas:  
  
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
  
 Vea [la semántica de tipos de valor](../dotnet/value-type-semantics.md) para obtener más información.  
  
## <a name="typeof-keyword-becomes-typeid"></a>__typeof (palabra clave) se convierte en typeid  
 Sintaxis de typeof de extensiones administradas:  
  
```  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 Nueva sintaxis de typeid:  
  
```  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
 Vea [: typeid reemplaza typeof](../dotnet/typeof-goes-to-t-typeid.md) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [C++ / CLI manual de migraciones](../dotnet/cpp-cli-migration-primer.md)   
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)


