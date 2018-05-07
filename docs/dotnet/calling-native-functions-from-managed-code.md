---
title: Llamar a funciones nativas desde código administrado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c0d7e69c95790122f44dc59d06f2843afbddfb2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="calling-native-functions-from-managed-code"></a>Llamar a funciones nativas desde código administrado
Common language runtime proporciona servicios de invocación de plataforma o PInvoke, que habilita el código administrado llame a funciones de estilo C en bibliotecas de vínculos dinámicos (DLL) nativas. Se utilizan los mismos datos que el cálculo de referencias para interoperabilidad de COM con el tiempo de ejecución y para el mecanismo "It Just Works" o IJW.  
  
 Para obtener más información, consulte:  
  
-   [Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
-   [Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [Aproximación a la invocación de plataforma](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
  
 Los ejemplos de esta sección solo se muestra cómo `PInvoke` puede utilizarse. `PInvoke` puede simplificar la serialización de datos personalizados porque proporciona información de serialización mediante declaración en atributos en lugar de escribir código de serialización de procedimiento.  
  
> [!NOTE]
>  La biblioteca de serialización proporciona una manera alternativa de calcular las referencias de datos entre los entornos nativos y administrados de forma optimizada. Vea [información general de serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de la biblioteca de serialización. La biblioteca de serialización es útil sólo para los datos y no para las funciones.  
  
## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke y DllImport (atributo)  
 En el ejemplo siguiente se muestra el uso de `PInvoke` en un programa de Visual C++. La función nativa puts se define en msvcrt.dll. El atributo DllImport se utiliza para la declaración de puts.  
  
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
  
 El ejemplo siguiente es equivalente al ejemplo anterior, pero utiliza IJW.  
  
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
  
### <a name="advantages-of-ijw"></a>Ventajas de IJW  
  
-   No es necesario escribir `DLLImport` atributo declaraciones de las API no administradas que utiliza el programa. Simplemente incluya el archivo de encabezado y el vínculo con la biblioteca de importación.  
  
-   El mecanismo IJW es ligeramente más rápido (por ejemplo, el código auxiliar IJW no necesita comprobar si la necesidad de pin o copia elementos de datos, puesto que se lleva a cabo explícitamente el desarrollador).  
  
-   Muestra claramente los problemas de rendimiento. En este caso, el hecho de que se está traduciendo desde una cadena Unicode en una cadena ANSI y que puede tener una asignación de memoria y desasignación. En este caso, un desarrollador que escribe en el código mediante IJW ¿tenga en cuenta que la llamada a `_putws` y el uso de `PtrToStringChars` sería mejor para el rendimiento.  
  
-   Si se llama a muchas API no administradas que utiliza los mismos datos, el cálculo de referencias, una vez y pasar la copia calculada es mucho más eficaz que volver a calcular las referencias cada vez.  
  
### <a name="disadvantages-of-ijw"></a>Desventajas de IJW  
  
-   El cálculo de referencias debe especificarse explícitamente en el código en lugar de atributos (que a menudo tienen valores predeterminados adecuados).  
  
-   El código de serialización es en línea, donde resulta más invasivo en el flujo de la lógica de aplicación.  
  
-   Dado que las API de cálculo de referencias explícito devuelven `IntPtr` tipos para la portabilidad de 32 bits a 64 bits, debe usar extra `ToPointer` llamadas.  
  
 El método concreto expuesto por C++ es el método explícito más eficaz, a costa de cierta complejidad adicional.  
  
 Si la aplicación usa principalmente tipos de datos no administrados o si llama a más API no administradas que la API de .NET Framework, se recomienda utilice la característica IJW. Para llamar a una API no administrada ocasional en una aplicación principalmente administrada, la opción es más sutil.  
  
## <a name="pinvoke-with-windows-apis"></a>PInvoke con las API de Windows  
 PInvoke también resulta adecuado para llamar a funciones en Windows.  
  
 En este ejemplo, un programa de Visual C++ interactúa con la función de cuadro de mensajes que forma parte de la API de Win32.  
  
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
  
 El resultado es un cuadro de mensaje que tiene el título PInvoke Test y contiene el texto Hello World!.  
  
 PInvoke también sirve la información de serialización para buscar las funciones del archivo DLL. En el archivo user32.dll no es de hecho ninguna función MessageBox, pero CharSet = CharSet:: ANSI permite a PInvoke usar MessageBoxA, la versión ANSI, en lugar de MessageBoxW, que es la versión Unicode. En general, se recomienda usar las versiones de Unicode de las API no administradas porque así se elimina la traducción de la sobrecarga del formato Unicode nativo de los objetos de cadena de .NET Framework a ANSI.  
  
## <a name="when-not-to-use-pinvoke"></a>Cuándo no usar PInvoke  
 Uso de PInvoke no es adecuado para todas las funciones de estilo C en archivos DLL. Por ejemplo, suponga que hay una función MakeSpecial en mylib.dll declarada como sigue:  
  
 `char * MakeSpecial(char * pszString);`  
  
 Si se utiliza PInvoke en una aplicación de Visual C++, se podría escribir algo similar a lo siguiente:  
  
 `[DllImport("mylib")]`  
  
 `extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);`  
  
 La dificultad aquí es que no podemos eliminar la memoria de la cadena no administrada devuelta por MakeSpecial. Otras funciones llamadas a través de PInvoke devuelven un puntero a un búfer interno que no tiene que ser desasignado por el usuario. En este caso, el uso de la característica IJW es la opción obvia.  
  
## <a name="limitations-of-pinvoke"></a>Limitaciones de PInvoke  
 No puede devolver el mismo puntero exacto de una función nativa que se tomó como un parámetro. Si una función nativa devuelve el puntero que se han calculado las referencias a él mediante PInvoke, pueden producirse excepciones y daños en la memoria.  
  
```  
__declspec(dllexport)  
char* fstringA(char* param) {  
   return param;  
}  
```  
  
 El ejemplo siguiente muestra este problema, y aunque el programa parece que da el resultado correcto, el resultado procede de la memoria que se ha liberado.  
  
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
  
## <a name="marshaling-arguments"></a>Serializar los argumentos  
 Con `PInvoke`, no se necesita ningún cálculo de referencias entre administrados y los tipos primitivos nativos de C++ con el mismo formato. Por ejemplo, no es necesaria la serialización entre Int32 e int, o entre Double y double  
  
 Sin embargo, deben calcular las referencias de tipos que no tienen el mismo formato. Esto incluye los tipos char, string y struct. La siguiente tabla muestra las asignaciones utilizadas por el contador de referencias para varios tipos:  
  
|archivo Wtypes.h|Visual C++|Visual C++ con /clr|Common Language Runtime|  
|--------------|------------------|-----------------------------|-----------------------------|  
|HANDLE|void *|void *|IntPtr, UIntPtr|  
|BYTE|unsigned char|unsigned char|Byte|  
|SHORT|short|short|Int16|  
|WORD|unsigned short|unsigned short|UInt16|  
|INT|int|int|Int32|  
|UINT|unsigned int|unsigned int|UInt32|  
|LONG|long|long|Int32|  
|BOOL|long|bool|Booleano|  
|DWORD|unsigned long|unsigned long|UInt32|  
|ULONG|unsigned long|unsigned long|UInt32|  
|CHAR|char|char|Char|  
|LPCSTR|char*|Cadena ^ [in], StringBuilder ^ [en, out]|Cadena ^ [in], StringBuilder ^ [en, out]|  
|LPCSTR|const char *|Cadena ^|String|  
|LPWSTR|wchar_t*|Cadena ^ [in], StringBuilder ^ [en, out]|Cadena ^ [in], StringBuilder ^ [en, out]|  
|LPCWSTR|const wchar_t *|Cadena ^|String|  
|FLOAT|float|float|Single|  
|DOUBLE|double|double|Doble|  
  
 El contador de referencias ancla automáticamente la memoria asignada en el montón en tiempo de ejecución si su dirección se pasa a una función no administrada. Fijar impide que el recolector de elementos no utilizados mueve el bloque de memoria asignado durante la compactación.  
  
 En el ejemplo mostrado anteriormente en este tema, el parámetro CharSet de DllImport especifica cómo administradas cadenas se deberían serializar; en este caso, se deben calcular como cadenas ANSI para la parte nativa.  
  
 Puede especificar información de cálculo de referencias para argumentos individuales de una función nativa mediante el atributo MarshalAs. Hay varias opciones de serialización de una cadena * argumento: BStr, ANSIBStr, TBStr, LPStr, LPWStr y LPTStr. El valor predeterminado es LPStr.  
  
 En este ejemplo, la cadena se serializa como una cadena de caracteres Unicode de doble byte, LPWStr. ¡El resultado es la primera letra de Hello World! Dado que el segundo byte de la cadena calculada es null y se coloca interpreta esto como el marcador de fin de cadena.  
  
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
  
 El atributo MarshalAs está en el espacio de nombres System::Runtime::InteropServices. El atributo se puede usar con otros tipos de datos, como matrices.  
  
 Como se mencionó anteriormente en este tema, la biblioteca de serialización proporciona un nuevo método optimizado de serialización de datos entre los entornos nativo y administrados. Para obtener más información, consulte [información general de serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md).  
  
## <a name="performance-considerations"></a>Consideraciones sobre el rendimiento  
 PInvoke tiene una sobrecarga de entre 10 y 30 x86 instrucciones por llamada. Además de este costo fijo, el cálculo de referencias crea una sobrecarga adicional. No hay ningún costo de cálculo de referencias entre los tipos de bits/bytes que tienen la misma representación en código no administrado y no administrado. Por ejemplo, no hay ningún costo para traducir entre int e Int32.  
  
 Para mejorar el rendimiento, tienen menos llamadas a PInvoke que las referencias a tantos datos como sea posible, en lugar de llamadas más que calcular las referencias de menos datos por llamada.  
  
## <a name="see-also"></a>Vea también  
 [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)