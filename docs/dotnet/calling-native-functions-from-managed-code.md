---
title: "Llamar a funciones nativas desde c&#243;digo administrado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "llamar a funciones nativas desde código administrado"
  - "interoperabilidad [C++], llamar a funciones nativas desde código administrado"
  - "interoperabilidad [C++], llamar a funciones nativas desde código administrado"
  - "código administrado [C++], interoperabilidad"
  - "funciones nativas llamadas desde código administrado [C++]"
  - "invocación de plataforma [C++], interoperabilidad"
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# Llamar a funciones nativas desde c&#243;digo administrado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Common Language Runtime proporciona Platform Invocation Services, o PInvoke, que permite al código administrado llamar a funciones del estilo de C en bibliotecas de vínculo dinámico \(DLL\) nativas.  El mismo cálculo de referencias de datos se utiliza en cuanto a la interoperabilidad COM con el tiempo de ejecución y para el mecanismo "It Just Works" o IJW.  
  
 Para obtener más información, vea:  
  
-   [Utilizar un elemento PInvoke explícito en C\+\+ \(Atributo DllImport\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
-   [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [A Closer Look at Platform Invoke](http://msdn.microsoft.com/es-es/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
  
 Los ejemplos de esta sección solo muestran cómo se puede usar `PInvoke`.  `PInvoke` puede simplificar el cálculo de referencias de datos personalizado, ya que la información de cálculo de referencias se proporciona declarativamente en atributos en lugar de escribir código de cálculo de referencias en forma de procedimiento.  
  
> [!NOTE]
>  La biblioteca de cálculo de referencias proporciona una manera alternativa de calcular referencias de los datos entre los entornos nativo y administrado de forma optimizada.  Para obtener más información sobre la biblioteca de cálculo de referencias, vea [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md).  La biblioteca de cálculo de referencias sólo se puede utilizar para datos, no para funciones.  
  
## PInvoke y el atributo DllImport  
 El ejemplo siguiente muestra el uso de `PInvoke`en un programa de Visual C\+\+.  La función nativa puts se define en msvcrt.dll.  El atributo DllImport se usa para la declaración de puts.  
  
```  
// platform_invocation_services.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[DllImport("msvcrt", CharSet=CharSet::Ansi)]  
extern "C" int puts(String ^);  
  
int main() {  
   String ^ pStr = "Hello World!";  
   puts(pStr);  
}  
```  
  
 El ejemplo siguiente equivale al ejemplo anterior, pero utiliza IJW.  
  
```  
// platform_invocation_services_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#include <stdio.h>  
  
int main() {  
   String ^ pStr = "Hello World!";  
   char* pChars = (char*)Marshal::StringToHGlobalAnsi(pStr).ToPointer();   
   puts(pChars);  
  
   Marshal::FreeHGlobal((IntPtr)pChars);  
}  
```  
  
### Ventajas de IJW  
  
-   No hay necesidad de escribir declaraciones del atributo `DLLImport` para las API no administradas que usa el programa.  Simplemente incluya el archivo de encabezado y vincúlelo a la biblioteca de importación.  
  
-   El mecanismo IJW es ligeramente más rápido \(por ejemplo, el código auxiliar de IJW no necesita comprobar si se deben anclar o copiar elementos de datos, ya que eso lo realiza explícitamente el desarrollador\).  
  
-   Muestra claramente los problemas de rendimiento.  En este caso, el hecho de que esté convirtiendo una cadena de Unicode en una cadena ANSI y que tenga una asignación y desasignación de memoria correspondiente.  En este caso, un desarrollador que escriba el código mediante IJW comprendería que sería mejor para el rendimiento llamar a `_putws` y utilizar `PtrToStringChars`.  
  
-   Si realiza llamadas a muchas API no administradas que usan los mismos datos, realizar previamente un cálculo de referencias una vez y pasar la copia calculada resulta mucho más eficaz que volver a realizar un cálculo de referencias cada vez.  
  
### Desventajas de IJW  
  
-   El cálculo de referencias se debe especificar explícitamente en el código en lugar de mediante atributos \(los cuales tienen a menudo valores predeterminados adecuados\).  
  
-   El código de cálculo de referencias se realiza en línea, donde resulta más invasivo en el flujo de la lógica de la aplicación.  
  
-   Como las API de cálculo de referencias explícito devuelven tipos `IntPtr` para portabilidad de 32 bits a 64 bits, se deberán utilizar llamadas adicionales a `ToPointer`.  
  
 El método concreto expuesto por C\+\+ es el método explícito más eficiente, a costa de una cierta complejidad adicional.  
  
 Si la aplicación usa principalmente tipos de datos no administrados, o si llama a más API no administradas que a API de .NET Framework, se recomienda utilizar la característica IJW.  Para llamar a una API no administrada ocasional en una aplicación principalmente administrada, la opción es más sutil.  
  
## PInvoke con las API de Windows  
 PInvoke también resulta adecuado para llamar a funciones en Windows.  
  
 En este ejemplo, un programa de Visual C\+\+ interactúa con la función MessageBox que forma parte de la API Win32.  
  
```  
// platform_invocation_services_4.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Runtime::InteropServices;  
typedef void* HWND;  
[DllImport("user32", CharSet=CharSet::Ansi)]  
extern "C" int MessageBox(HWND hWnd, String ^ pText, String ^ pCaption, unsigned int uType);  
  
int main() {  
   String ^ pText = "Hello World! ";  
   String ^ pCaption = "PInvoke Test";  
   MessageBox(0, pText, pCaption, 0);  
}  
```  
  
 El resultado es un cuadro de mensaje con el título PInvoke Test y que contiene el texto "Hello World\!".  
  
 PInvoke utiliza también la información de cálculo de referencias para buscar las funciones en el archivo DLL.  En user32.dll, de hecho no existe la función MessageBox, pero CharSet\=CharSet::Ansi permite a PInvoke usar MessageBoxA, la versión ANSI, en lugar de MessageBoxW, que es la versión Unicode.  En general, recomendamos utilizar las versiones Unicode de las API no administradas porque así se elimina la sobrecarga que conlleva convertir del formato Unicode nativo de los objetos de cadena de .NET Framework a ANSI.  
  
## Cuando no se debe utilizar PInvoke  
 El uso de  PInvoke no es apropiado para todas las funciones de estilo C en archivos DLL.  Por ejemplo, suponga que hay una función MakeSpecial en mylib.dll declarada del siguiente modo:  
  
 `char * MakeSpecial(char * pszString);`  
  
 Si se utiliza PInvoke en una aplicación de Visual C\+\+, se podría escribir algo similar a lo siguiente:  
  
 `[DllImport("mylib")]`  
  
 `extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);`  
  
 La dificultad aquí es que no se puede eliminar la memoria de la cadena no administrada devuelta por MakeSpecial.  Otras funciones a las que se llama a través de PInvoke devuelven un puntero a un búfer interno cuya desasignación no tiene que ser realizada por el usuario.  En este caso, utilizar la característica IJW es la opción obvia.  
  
## Limitaciones de PInvoke  
 No puede devolver el mismo puntero exacto de una función nativa que se tomó como un parámetro.  Si una función nativa devuelve el puntero para el que PInvoke ha calculado las referencias, pueden ocurrir daños en la memoria y excepciones.  
  
```  
__declspec(dllexport)  
char* fstringA(char* param) {  
   return param;  
}  
```  
  
 El siguiente ejemplo muestra este problema, y aunque el programa parece que da el resultado correcto, éste procede de una memoria que se ha liberado.  
  
```  
// platform_invocation_services_5.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Runtime::InteropServices;  
#include <limits.h>  
  
ref struct MyPInvokeWrap {  
public:  
   [ DllImport("user32.dll", EntryPoint = "CharLower", CharSet = CharSet::Ansi) ]  
   static String^ CharLower([In, Out] String ^);  
};  
  
int main() {  
   String ^ strout = "AabCc";  
   Console::WriteLine(strout);  
   strout = MyPInvokeWrap::CharLower(strout);  
   Console::WriteLine(strout);  
}  
```  
  
## Cálculo de referencias de argumentos  
 Con `PInvoke`, no se necesita ningún cálculo de referencias entre los tipos administrados y los tipos primitivos nativos de C\+\+ con el mismo formato.  Por ejemplo, no se requiere ningún cálculo de referencias entre Int32 e int, o entre Double y double.  
  
 Sin embargo, sí se debe hacer el cálculo de referencias para los tipos que no tienen el mismo formato.  Esto incluye los tipos char, string y struct.  La tabla siguiente muestra las asignaciones utilizadas por el contador de referencias para los distintos tipos:  
  
|wtypes.h|Visual C\+\+|Visual C\+\+ con \/clr|Common Language Runtime|  
|--------------|------------------|----------------------------|-----------------------------|  
|HANDLE|void\*|void\*|IntPtr, UIntPtr|  
|BYTE|unsigned char|unsigned char|Byte|  
|SHORT|short|short|Int16|  
|WORD|unsigned short|unsigned short|UInt16|  
|INT|int|int|Int32|  
|UINT|unsigned int|unsigned int|UInt32|  
|LONG|long|long|Int32|  
|BOOL|long|bool|Boolean|  
|DWORD|unsigned long|unsigned long|UInt32|  
|ULONG|unsigned long|unsigned long|UInt32|  
|CHAR|char|char|Char|  
|LPCSTR|char\*|String ^ \[in\], StringBuilder ^ \[in, out\]|String ^ \[in\], StringBuilder ^ \[in, out\]|  
|LPCSTR|const char \*|String ^|String|  
|LPWSTR|wchar\_t\*|String ^ \[in\], StringBuilder ^ \[in, out\]|String ^ \[in\], StringBuilder ^ \[in, out\]|  
|LPCWSTR|const wchar\_t \*|String ^|String|  
|FLOAT|float|float|Single|  
|DOUBLE|double|double|Double|  
  
 El contador de referencias ancla automáticamente la memoria asignada en el montón en tiempo de ejecución si su dirección se pasa a una función no administrada.  El anclaje evita que el recolector de elementos no utilizados mueva el bloque de memoria asignado durante consolidación.  
  
 En el ejemplo mostrado anteriormente en este tema, el parámetro CharSet de DllImport especifica cómo se deben calcular las referencias de tipos String administrados; en este caso se deben calcular como cadenas ANSI para la parte nativa.  
  
 La información de cálculo de referencias para los argumentos individuales de una función nativa se puede especificar mediante el atributo MarshalAs.  Hay varias opciones para el cálculo de referencias de un argumento String \*: BSTR, ANSIBStr, TBStr, LPStr, LPWStr y LPTStr.  El valor predeterminado es LPStr.  
  
 En este ejemplo, se calculan las referencias de la cadena como una cadena de caracteres Unicode de doble byte, LPWStr.  El resultado es la primera letra de Hola a todos ya que el segundo byte de la cadena cuyas referencias se han calculado es null, y la función puts interpreta esto como el marcador de fin de cadena.  
  
```  
// platform_invocation_services_3.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[DllImport("msvcrt", EntryPoint="puts")]  
extern "C" int puts([MarshalAs(UnmanagedType::LPWStr)] String ^);  
  
int main() {  
   String ^ pStr = "Hello World!";  
   puts(pStr);  
}  
```  
  
 El atributo MarshalAs está en el espacio de nombres System::Runtime::InteropServices.  El atributo se puede utilizar con otros tipos de datos, por ejemplo con las matrices.  
  
 Como ya se ha mencionado anteriormente en este tema, la biblioteca de cálculo de referencias proporciona un nuevo método optimizado de cálculo de referencia de datos entre los entornos nativo y administrado.  Para obtener más información, vea [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md).  
  
## Consideraciones sobre el rendimiento  
 PInvoke tiene una sobrecarga de entre 10 y 30 instrucciones x86 por la llamada.  Además de este costo fijo, el cálculo de referencias crea una sobrecarga adicional.  No hay ningún costo de cálculo de referencias entre tipos que pueden transferirse en bloque de bits que tengan la misma representación en código administrado y no administrado.  Por ejemplo, no hay ningún costo en traducir entre int e Int32.  
  
 Para lograr un mejor rendimiento, utilice menos llamadas a PInvoke y haga que calculen las referencias de la mayor cantidad de datos posible, en lugar de tener más llamadas a PInvoke que calculen las referencias de menos datos por llamada.  
  
## Vea también  
 [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)