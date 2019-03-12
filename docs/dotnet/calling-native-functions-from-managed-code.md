---
title: Llamar a funciones nativas desde código administrado
ms.date: 11/04/2016
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
ms.openlocfilehash: 285bfabbd5935df303a39ada11c388713ae24f34
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743248"
---
# <a name="calling-native-functions-from-managed-code"></a>Llamar a funciones nativas desde código administrado

Common language runtime proporciona Platform Invocation Services, o PInvoke, que permite código administrado llame a funciones de estilo C en bibliotecas de vínculos dinámicos (DLL) nativas. Los mismos datos de serialización se utilizan para la interoperabilidad de COM con el tiempo de ejecución y para el mecanismo "It Just Works" o IJW.

Para obtener más información, consulte:

- [Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

Los ejemplos en esta sección solo muestran cómo `PInvoke` se puede usar. `PInvoke` puede simplificar el cálculo de referencias de datos personalizados ya proporcionan información de serialización declarativamente en atributos en lugar de escribir código de cálculo de referencias de procedimientos.

> [!NOTE]
>  La biblioteca de serialización proporciona una manera alternativa de calcular las referencias de datos entre los entornos nativos y administrados de forma optimizada. Consulte [Overview of Marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de la biblioteca de serialización. La biblioteca de serialización es útil sólo para los datos y no para funciones.

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke y el atributo DllImport

El ejemplo siguiente muestra el uso de `PInvoke` en un programa de Visual C++. La función nativa puts se define en msvcrt.dll. El atributo DllImport se usa para la declaración de puts.

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

- No hay ninguna necesidad de escribir `DLLImport` declaraciones para las API no administradas que utiliza el programa del atributo. Simplemente incluya el archivo de encabezado y vincúlelo con la biblioteca de importación.

- El mecanismo IJW es ligeramente más rápido (por ejemplo, el código auxiliar de IJW es necesario comprobar si se deben anclar o copiar elementos de datos porque eso lo realiza explícitamente el desarrollador).

- Muestra claramente los problemas de rendimiento. En este caso, el hecho de que esté convirtiendo una cadena Unicode en una cadena ANSI y que tiene una asignación de memoria y desasignación. En este caso, un desarrollador que escribe el código mediante IJW comprendería que al llamar a `_putws` y el uso de `PtrToStringChars` sería mejor para el rendimiento.

- Si se llama a muchas API no administradas que usan los mismos datos, el cálculo de referencias, una vez y pasar la copia calculada es mucho más eficaz que volver a calcular las referencias cada vez.

### <a name="disadvantages-of-ijw"></a>Desventajas de IJW

- El cálculo de referencias debe especificarse explícitamente en el código en lugar de los atributos (que a menudo tienen valores predeterminados adecuados).

- El código de serialización está en línea, donde resulta más invasivo en el flujo de la lógica de aplicación.

- Dado que las API de cálculo de referencias explícito devuelven `IntPtr` tipos para la portabilidad de 32 bits a 64 bits, debe usar extra `ToPointer` llamadas.

El método concreto expuesto por C++ es el método explícito más eficiente, a costa de una cierta complejidad adicional.

Si la aplicación usa principalmente tipos de datos no administrados o si llama a más API no administradas de .NET Framework, se recomienda use la característica IJW. Para llamar a una API no administrada ocasional en una aplicación principalmente administrada, la elección es más sutil.

## <a name="pinvoke-with-windows-apis"></a>PInvoke con las API de Windows

PInvoke también resulta adecuado para llamar a funciones en Windows.

En este ejemplo, un programa de Visual C++ interactúa con la función MessageBox que forma parte de la API de Win32.

```cpp
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

El resultado es un cuadro de mensaje que tiene el título PInvoke Test y que contiene el texto Hello World!.

La información de cálculo de referencias también se utiliza PInvoke para buscar las funciones en el archivo DLL. En user32.dll hay en realidad no hay función MessageBox, pero CharSet = CharSet:: ANSI permite a PInvoke usar MessageBoxA, la versión ANSI, en lugar de MessageBoxW, que es la versión de Unicode. En general, se recomienda usar las versiones Unicode de las API no administradas porque así elimina la traducción de la sobrecarga del formato Unicode nativo de los objetos de cadena de .NET Framework a ANSI.

## <a name="when-not-to-use-pinvoke"></a>Cuando no se debe utilizar PInvoke

Uso de PInvoke no es adecuado para todas las funciones de estilo C en archivos DLL. Por ejemplo, suponga que hay es una función MakeSpecial en mylib.dll se declara como sigue:

`char * MakeSpecial(char * pszString);`

Si se utiliza PInvoke en una aplicación de Visual C++, se podría escribir algo similar al siguiente:

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

La dificultad aquí es que no se puede eliminar la memoria para la cadena no administrada devuelta por MakeSpecial. Otras funciones llamadas a través de PInvoke devuelven un puntero a un búfer interno que no tiene que ser realizada por el usuario. En este caso, utilizar la característica IJW es la opción obvia.

## <a name="limitations-of-pinvoke"></a>Limitaciones de PInvoke

No puede devolver el mismo puntero exacto de una función nativa que se tomó como un parámetro. Si una función nativa devuelve el puntero que se han calculado las referencias a él mediante PInvoke, pueden producirse excepciones y daños en la memoria.

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

El ejemplo siguiente muestra este problema, y aunque el programa parece que da el resultado correcto, éste procede de la memoria que se ha liberado.

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

## <a name="marshaling-arguments"></a>Cálculo de referencias de argumentos

Con `PInvoke`, no se necesita ningún cálculo de referencias entre administrados y los tipos primitivos nativos de C++ con el mismo formulario. Por ejemplo, no es necesario entre Int32 e int, o entre Double y double ningún cálculo de referencias.

Sin embargo, debe calcular las referencias de tipos que no tienen el mismo formulario. Esto incluye los tipos char, string y struct. La siguiente tabla muestra las asignaciones utilizadas por el contador de referencias para los distintos tipos:

|wtypes.h|Visual C++|Visual C++ con /clr|Common Language Runtime|
|--------------|------------------|-----------------------------|-----------------------------|
|HANDLE|Void \*|Void \*|IntPtr, UIntPtr|
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
|LPCSTR|Char \*|String ^ [in], StringBuilder ^ [en, out]|String ^ [in], StringBuilder ^ [en, out]|
|LPCSTR|const char \*|String ^|String|
|LPWSTR|wchar_t \*|String ^ [in], StringBuilder ^ [en, out]|String ^ [in], StringBuilder ^ [en, out]|
|LPCWSTR|const wchar_t \*|String ^|String|
|FLOAT|float|float|Single|
|DOUBLE|double|double|Doble|

El contador de referencias ancla automáticamente la memoria asignada en el montón en tiempo de ejecución si su dirección se pasa a una función no administrada. Anclar impide que el recolector de elementos no utilizados mueva el bloque de memoria asignado durante consolidación.

En el ejemplo mostrado anteriormente en este tema, el parámetro CharSet de DllImport especifica cadenas administradas cómo se deben serializar; en este caso, se deben calcular como cadenas ANSI para el lado nativo.

Puede especificar la información de serialización para argumentos individuales de una función nativa mediante el atributo MarshalAs. Hay varias opciones para la serialización de una cadena \* argumento: BStr, ANSIBStr, TBStr, LPStr, LPWStr y LPTStr. El valor predeterminado es LPStr.

En este ejemplo, la cadena se serializa como una cadena de caracteres Unicode de doble byte, LPWStr. ¡El resultado es la primera letra de Hola a todos! Dado que el segundo byte de la cadena calculada es null y coloca interpreta esto como el marcador de final de cadena.

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

Como se mencionó anteriormente en este tema, la biblioteca de serialización proporciona un nuevo método optimizado de cálculo de referencias de datos entre los entornos nativos y administrados. Para obtener más información, consulte [Overview of Marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md).

## <a name="performance-considerations"></a>Consideraciones sobre el rendimiento

PInvoke tiene una sobrecarga de entre 10 y 30 x86 instrucciones por llamada. Además de este costo fijo, el cálculo de referencias crea una sobrecarga adicional. No hay ningún costo de cálculo de referencias entre tipos que tienen la misma representación en código administrado y no administrado. Por ejemplo, no hay ningún costo en traducir entre int e Int32.

Para mejorar el rendimiento, tiene menos llamadas a PInvoke que las referencias a tantos datos como sea posible, en lugar de llamadas más que calcular las referencias de menos datos por llamada.

## <a name="see-also"></a>Vea también

[Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)
