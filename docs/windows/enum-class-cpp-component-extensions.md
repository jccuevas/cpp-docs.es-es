---
title: enum class (extensiones de componente de C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6c3da3529d9f2bc0bb45119c6850f14afe794051
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="enum-class--c-component-extensions"></a>enum class (Extensiones de componentes de C++)
Declara una enumeración en el ámbito de espacio de nombres, que es un tipo definido por el usuario que está compuesto de un conjunto de constantes con nombre llamadas enumeradores.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 **Comentarios**  
  
 C++/CX y C++/CLI admiten `public enum class` y `private enum class` que son similares a la `enum class` estándar de C++ pero con la adición del especificador de accesibilidad. En **/clr**, el tipo `enum class` de C++11 está permitido pero generará la advertencia C4472, que pretende garantizar que realmente desea el tipo de enumeración ISO y no el tipo C++/CX y C++/CLI. Para obtener más información sobre el estándar ISO C++ `enum` palabra clave, consulte [enumeraciones](../cpp/enumerations-cpp.md).  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 **Sintaxis**  
  
```  
  
      access  
      enum class  
      enumeration-identifier  
      [:underlying-type] { enumerator-list } [var];  
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];  
```  
  
 **Parámetros**  
  
 *access*  
 Accesibilidad de la enumeración, que puede ser `public` o `private`.  
  
 *enumeration-identifier*  
 Nombre de la enumeración.  
  
 *underlying-type*  
 (Opcional) Tipo de datos subyacente de la enumeración.  
  
 (Opcional. Windows en tiempo de ejecución solo) el tipo subyacente de la enumeración, que puede ser `bool`, `char`, `char16`, `int16`, `uint16`, `int`, `uint32`, `int64`, o `uint64`.  
  
 *enumerator-list*  
 Lista de nombres de enumerador separados con comas.  
  
 El valor de cada enumerador es una expresión constante definida implícitamente por el compilador o explícitamente mediante la notación, *enumerator*`=`*constant-expression*. De forma predeterminada, el valor del primer enumerador es cero si se define implícitamente. El valor de cada enumerador implícitamente definido subsiguiente es el valor del enumerador anterior + 1.  
  
 *var*  
 (Opcional) Nombre de una variable del tipo de enumeración.  
  
 **Comentarios**  
  
 Para obtener más información y ejemplos, vea [Enumeraciones](http://msdn.microsoft.com/%20library/windows/apps/hh755820.aspx).  
  
 Observe que el compilador emite mensajes de error si la expresión constante que define el valor de un enumerador no se puede representar mediante *underlying-type*.  Sin embargo, el compilador no indica un error para un valor que es inadecuado para el tipo subyacente. Por ejemplo:  
  
-   Si *underlying-type* es numérico y un enumerador especifica el valor máximo para ese tipo, el valor de la siguiente enumeración definida implícitamente no se puede representar.  
  
-   Si *underlying-type* es `bool`y hay más de dos enumeradores definidos implícitamente, no se pueden representar los enumeradores después de los dos primeros.  
  
-   Si *underlying-type* es `char16`y el valor de enumeración va de 0xD800 a 0xDFFF, el valor se puede representar. Sin embargo, el valor es lógicamente incorrecto porque representa la mitad del par suplente Unicode y no debe aparecer de forma aislada.  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Sintaxis**  
  
```  
  
      access  
      enum class  
      name [:type] { enumerator-list } var;  
accessenum structname [:type] { enumerator-list } var;  
```  
  
 **Parámetros**  
  
 `access`  
 Accesibilidad de la enumeración.  Puede ser **public** o `private`.  
  
 `enumerator-list`  
 Una lista delimitada por comas de los identificadores (enumeradores) en la enumeración.  
  
 `name`  
 Nombre de la enumeración.  Las enumeraciones administradas anónimas no se permiten.  
  
 `type` (opcional)  
 Tipo subyacente de los *identifiers*.  Puede tratarse de cualquier tipo escalar, como versiones con signo o sin signo de int, short o long.  También se permite`bool` o `char` .  
  
 `var` (opcional)  
 Nombre de una variable del tipo de enumeración.  
  
 **Comentarios**  
  
 **enum class** y **enum struct** son declaraciones equivalentes.  
  
 Hay dos tipos de enumeraciones: administrada o C++/CX y estándar.  
  
 Una enumeración administrada o C++/CX puede definirse como sigue,  
  
```cpp  
public enum class day {sun, mon };  
```  
  
 y es semánticamente equivalente a:  
  
```cpp  
ref class day {  
public:  
   static const int sun = 0;  
   static const int mon = 1;  
};  
```  
  
 Una enumeración estándar puede definirse como sigue:  
  
```cpp  
enum day2 { sun, mon };  
```  
  
 y es semánticamente equivalente a:  
  
```cpp  
static const int sun = 0;  
static const int mon = 1;  
```  
  
 Los nombres de enumerador administrados (*identifiers*) no se insertan en el ámbito en el que está definida la enumeración; todas las referencias a los enumeradores deben ser completas (*name*`::`*identifier*).  Por esta razón, no se puede definir una enumeración administrada anónima.  
  
 Los enumeradores de una enumeración estándar se insertan fuertemente en el ámbito de inclusión.  Es decir, si hay otro símbolo con el mismo nombre que un enumerador en el ámbito de inclusión, el compilador generará un error.  
  
 En Visual C++ 2002 y Visual C++ 2003, los enumeradores se insertaban de forma poco rigurosa (visibles en el ámbito de inclusión a menos que hubiera otro identificador con el mismo nombre).  
  
 Si se define una enumeración estándar de C++ (sin **class** o `struct`), la compilación con **/clr** hará que la enumeración se compile como una enumeración administrada.  La enumeración todavía tiene la semántica de una enumeración no administrada.  Nota: el compilador inserta un atributo, `Microsoft::VisualC::NativeEnumAttribute`, que el compilador de Visual C++ reconoce, para identificar la intención del programador de que la enumeración sea una enumeración nativa.  Otros compiladores verán simplemente la enumeración estándar como enumeración administrada.  
  
 Una enumeración con nombre, estándar compilada con /clr estará visible en el ensamblado como una enumeración administrada y se puede usar en cualquier otro compilador administrado.   Sin embargo, una enumeración estándar sin nombre no será visible de forma pública desde el ensamblado.  
  
 En Visual C++ 2002 y Visual C++ 2003, una enumeración estándar usada como el tipo de un parámetro de función:  
  
```cpp  
// mcppv2_enum.cpp  
// compile with: /clr  
enum E { a, b };  
void f(E) {System::Console::WriteLine("hi");}  
  
int main() {  
   E myi = b;  
   f(myi);  
}  
```  
  
 emitiría lo siguiente en MSIL para la signatura de la función:  
  
```  
void f(int32);  
```  
  
 Sin embargo, en las versiones actuales del compilador, la enumeración estándar se emite como enumeración administrada con [NativeEnumAttribute] y lo siguiente en MSIL para la signatura de la función:  
  
```  
void f(E)  
```  
  
 Para obtener más información sobre enumeraciones nativas, vea [Declaraciones de enumeración de C++](../cpp/enumerations-cpp.md).  
  
 Para obtener más información sobre las enumeraciones CLR, vea:  
  
-   [Tipo subyacente de una enumeración](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 desc  
  
```cpp  
// mcppv2_enum_2.cpp  
// compile with: /clr  
// managed enum  
public enum class m { a, b };  
  
// standard enum  
public enum n { c, d };  
  
// unnamed, standard enum  
public enum { e, f } o;  
  
int main()   
{  
   // consume managed enum  
   m mym = m::b;  
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);  
   System::Console::WriteLine("convert to int: {0}", (int)mym);  
  
   // consume standard enum  
   n myn = d;  
   System::Console::WriteLine(myn);  
  
   // consume standard, unnamed enum  
   o = f;  
   System::Console::WriteLine(o);  
}   
```  
  
 **Salida**  
  
```Output  
no automatic conversion to int: b  
  
convert to int: 1  
  
1  
  
1  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)