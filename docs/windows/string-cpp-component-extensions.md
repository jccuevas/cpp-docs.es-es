---
title: Cadena (extensiones de componentes de C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e988da5393e32871794a2a1e7565801b0b338c2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="string--c-component-extensions"></a>Cadena (Extensiones de componentes de C++)
El compilador de Visual C++ admite *cadenas*, que son objetos que representan texto como una secuencia de caracteres. Visual C++ admite variables de cadena, cuyo valor es implícito, y literales, cuyo valor es una cadena entre comillas explícita.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 Windows Runtime y Common Language Runtime representan cadenas como objetos cuya memoria asignada se administra automáticamente. Es decir, no es necesario descartar explícitamente la memoria de una cadena cuando la variable de cadena está fuera del ámbito o finaliza la aplicación. Para indicar que la duración de un objeto de cadena que se administrarán automáticamente, declare el tipo de cadena con el [identificador-a-objeto (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md) modificador.  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 La arquitectura de Windows en tiempo de ejecución requiere que Visual C++ implemente el tipo de datos `String` en el espacio de nombres `Platform`. Para su comodidad, Visual C++ también proporciona el tipo de datos `string`, que es un sinónimo de `Platform::String`, en el espacio de nombres `default`.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
// compile with /ZW  
using namespace Platform;  
using namespace default;  
   Platform::String^ MyString1 = "The quick brown fox";  
   String^ MyString2 = "jumped over the lazy dog.";  
   String^ MyString3 = "Hello, world!";  
  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información y ejemplos acerca de las cadenas, vea [Platform:: String, std:: wstring y literales (plataforma)](http://msdn.microsoft.com/en-us/ec92fbc6-edf3-4137-a85e-8e29bdb857a8)  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 Este tema describe cómo el compilador de Visual C++ procesa los literales de cadena cuando se ejecutan mediante el **/CLR** opción del compilador. Usar **/CLR**, también debe utilizar common language runtime (CLR), C + / sintaxis CLI y objetos administrados. Para obtener más información acerca de **/CLR**, consulte [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 Cuando se compila con **/CLR**, el compilador convertirá los literales de cadena a cadenas de tipo <xref:System.String>. Para mantener la compatibilidad con el código existente, existen dos excepciones a esto:  
  
-   Control de excepciones. Cuando se produce un literal de cadena, el compilador lo detectará como literal de cadena.  
  
-   Deducción de plantilla. Cuando un literal de cadena se pasa como argumento de plantilla, el compilador no lo convertirá a <xref:System.String>. Tenga en cuenta que los literales de cadena pasados como argumento genérico se promoverán a <xref:System.String>.  
  
 El compilador también tiene compatibilidad integrada para tres operadores, que puede invalidar para personalizar su comportamiento:  
  
-   Operador System::String ^ +( System::String, System::String);  
  
-   Operador System::String ^ +( System::Object, System::String);  
  
-   Operador System::String ^ +( System::String, System::Object);  
  
 Cuando se pasa <xref:System.String>, el compilador aplicará una conversión boxing, si fuera necesario, y después concatenará el objeto (con ToString) con la cadena.  
  
> [!NOTE]
>  El símbolo de intercalación (“^ ") indica que la variable declarada es un identificador para un objeto administrado de C++/CLI.  
  
 Para obtener más información, consulte [literales de cadena y carácter](../cpp/string-and-character-literals-cpp.md).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se muestra la concatenación y la comparación de cadenas.  
  
```cpp  
// string_operators.cpp  
// compile with: /clr  
// In the following code, the caret ("^") indicates that the   
// declared variable is a handle to a C++/CLI managed object.  
using namespace System;  
  
int main() {  
   String ^ a = gcnew String("abc");  
   String ^ b = "def";   // same as gcnew form  
   Object ^ c = gcnew String("ghi");  
  
   char d[100] = "abc";  
  
   // variables of System::String returning a System::String  
   Console::WriteLine(a + b);  
   Console::WriteLine(a + c);  
   Console::WriteLine(c + a);  
  
   // accessing a character in the string  
   Console::WriteLine(a[2]);  
  
   // concatenation of three System::Strings  
   Console::WriteLine(a + b + c);  
  
   // concatenation of a System::String and string literal  
   Console::WriteLine(a + "zzz");  
  
   // you can append to a System::String ^  
   Console::WriteLine(a + 1);  
   Console::WriteLine(a + 'a');  
   Console::WriteLine(a + 3.1);  
  
   // test System::String ^ for equality  
   a += b;  
   Console::WriteLine(a);  
   a = b;  
   if (a == b)  
      Console::WriteLine("a and b are equal");  
  
   a = "abc";  
   if (a != b)  
      Console::WriteLine("a and b are not equal");  
  
   // System:String ^ and tracking reference  
   String^% rstr1 = a;  
   Console::WriteLine(rstr1);  
  
   // testing an empty System::String ^  
   String ^ n;  
   if (n == nullptr)  
      Console::WriteLine("n is empty");  
}  
```  
  
 **Salida**  
  
```Output  
abcdef  
  
abcghi  
  
ghiabc  
  
c  
  
abcdefghi  
  
abczzz  
  
abc1  
  
abc97  
  
abc3.1  
  
abcdef  
  
a and b are equal  
  
a and b are not equal  
  
abc  
  
n is empty  
```  
  
 **Ejemplo**  
  
 En el ejemplo siguiente se muestra cómo sobrecargar los operadores proporcionados por el compilador, y cómo el compilador buscará una sobrecarga de función basada en el tipo <xref:System.String>.  
  
```cpp  
// string_operators_2.cpp  
// compile with: /clr  
using namespace System;  
  
// a string^ overload will be favored when calling with a String  
void Test_Overload(const char * a) {   
   Console::WriteLine("const char * a");   
}  
void Test_Overload(String ^ a) {   
   Console::WriteLine("String ^ a");   
}  
  
// overload will be called instead of compiler defined operator  
String ^ operator +(String ^ a, String ^ b) {  
   return ("overloaded +(String ^ a, String ^ b)");  
}  
  
// overload will be called instead of compiler defined operator  
String ^ operator +(Object ^ a, String ^ b) {  
   return ("overloaded +(Object ^ a, String ^ b)");  
}  
  
// overload will be called instead of compiler defined operator  
String ^ operator +(String ^ a, Object ^ b) {  
   return ("overloaded +(String ^ a, Object ^ b)");  
}  
  
int main() {  
   String ^ a = gcnew String("abc");  
   String ^ b = "def";   // same as gcnew form  
   Object ^ c = gcnew String("ghi");  
  
   char d[100] = "abc";  
  
   Console::WriteLine(a + b);  
   Console::WriteLine(a + c);  
   Console::WriteLine(c + a);  
  
   Test_Overload("hello");  
   Test_Overload(d);  
}  
```  
  
 **Salida**  
  
```Output  
overloaded +(String ^ a, String ^ b)   
  
overloaded +(String ^ a, Object ^ b)   
  
overloaded +(Object ^ a, String ^ b)   
  
String ^ a  
  
const char * a  
```  
  
 **Ejemplo**  
  
 En el ejemplo siguiente se muestra que el compilador distingue entre cadenas nativas y cadenas <xref:System.String>.  
  
```cpp  
// string_operators_3.cpp  
// compile with: /clr  
using namespace System;  
int func() {  
   throw "simple string";   // const char *  
};  
  
int func2() {  
   throw "string" + "string";   // returns System::String  
};  
  
template<typename T>  
void func3(T t) {  
   Console::WriteLine(T::typeid);  
}  
  
int main() {  
   try {  
      func();  
   }  
   catch(char * e) {  
      Console::WriteLine("char *");  
   }  
  
   try {  
      func2();  
   }  
   catch(String^ str) {  
      Console::WriteLine("String^ str");  
   }  
  
   func3("string");   // const char *  
   func3("string" + "string");   // returns System::String  
}  
```  
  
 **Salida**  
  
```Output  
char *  
  
String^ str  
  
System.SByte*  
  
System.String  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)   
 [Literales de cadena y carácter](../cpp/string-and-character-literals-cpp.md)   
 [/CLR (compilación de common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)