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
ms.openlocfilehash: 0cdd5db4fae8d9167fa9ab1aeb6a4e8cbfe76ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372509"
---
# <a name="calling-native-functions-from-managed-code"></a>Llamar a funciones nativas desde código administrado

Common Language Runtime proporciona Platform Invocation Services, o PInvoke, que permite que el código administrado llame a funciones de estilo C en bibliotecas nativas vinculadas dinámicas (DLL). El mismo cálculo de referencias de datos se utiliza para la interoperabilidad COM con el tiempo de ejecución y para el mecanismo "It Just Works", o IJW.

Para más información, consulte:

- [Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [Utilizar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

Los ejemplos de esta `PInvoke` sección solo ilustran cómo se pueden utilizar. `PInvoke`puede simplificar el cálculo de referencias de datos personalizado porque proporciona información de cálculo de referencias mediante declaración en atributos en lugar de escribir código de cálculo de referencias de procedimiento.

> [!NOTE]
> La biblioteca de cálculo de referencias proporciona una forma alternativa de calcular referencias de datos entre entornos nativos y administrados de forma optimizada. Consulte [Información general sobre el cálculo de referencias en C++](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de la biblioteca de cálculo de referencias. La biblioteca de cálculo de referencias solo se puede utilizar para datos y no para funciones.

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke y el atributo DllImport

En el ejemplo siguiente `PInvoke` se muestra el uso de un programa de Visual C++. La función nativa puts se define en msvcrt.dll. El atributo DllImport se utiliza para la declaración de puts.

```cpp
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

```cpp
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

- No es necesario `DLLImport` escribir declaraciones de atributo para las API no administradas que utiliza el programa. Simplemente incluya el archivo de encabezado y vincule con la biblioteca de importación.

- El mecanismo IJW es un poco más rápido (por ejemplo, los stubs IJW no necesitan comprobar la necesidad de anclar o copiar elementos de datos porque eso lo hace explícitamente el desarrollador).

- Ilustra claramente los problemas de rendimiento. En este caso, el hecho de que se está traduciendo de una cadena Unicode a una cadena ANSI y que tiene una asignación de memoria y desasignación de memoria de operador. En este caso, un desarrollador que escribe el `_putws` código `PtrToStringChars` con IJW se daría cuenta de que llamar y usar sería mejor para el rendimiento.

- Si llama a muchas API no administradas con los mismos datos, serializarlas una vez y pasar la copia serializada es mucho más eficaz que volver a calcular el cálculo de referencias cada vez.

### <a name="disadvantages-of-ijw"></a>Desventajas de IJW

- El cálculo de referencias debe especificarse explícitamente en el código en lugar de en los atributos (que a menudo tienen valores predeterminados adecuados).

- El código de cálculo de referencias está en línea, donde es más invasivo en el flujo de la lógica de la aplicación.

- Dado que las API `IntPtr` de cálculo de referencias explícitos devuelven tipos para `ToPointer` la portabilidad de 32 bits a 64 bits, debe usar llamadas adicionales.

El método específico expuesto por C++ es el método más eficiente y explícito, a costa de cierta complejidad adicional.

Si la aplicación usa principalmente tipos de datos no administrados o si llama a más API no administradas que las API de .NET Framework, se recomienda usar la característica IJW. Para llamar a una API no administrada ocasional en una aplicación administrada principalmente, la elección es más sutil.

## <a name="pinvoke-with-windows-apis"></a>PInvoke con las API de Windows

PInvoke es conveniente para llamar a funciones en Windows.

En este ejemplo, un programa de Visual C++ interopera con la función de cuadro de mensajes que forma parte de la API de Win32.

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

La salida es un cuadro de mensaje que tiene el título PInvoke Test y contiene el texto Hello World!.

PInvoke también utiliza la información de cálculo de referencias para buscar funciones en el archivo DLL. En user32.dll de hecho no hay ninguna función de cuadro de mensajes, pero CharSet-CharSet::Ansi permite a PInvoke utilizar MessageBoxA, la versión ANSI, en lugar de MessageBoxW, que es la versión Unicode. En general, se recomienda usar versiones Unicode de API no administradas porque esto elimina la sobrecarga de traducción del formato Unicode nativo de objetos de cadena de .NET Framework a ANSI.

## <a name="when-not-to-use-pinvoke"></a>Cuándo no usar PInvoke

El uso de PInvoke no es adecuado para todas las funciones de estilo C en los archivos DLL. Por ejemplo, supongamos que hay una función MakeSpecial en mylib.dll declarada de la siguiente manera:

`char * MakeSpecial(char * pszString);`

Si usamos PInvoke en una aplicación de Visual C++, podríamos escribir algo similar a lo siguiente:

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

La dificultad aquí es que no podemos eliminar la memoria de la cadena no administrada devuelta por MakeSpecial. Otras funciones a las que se llama a través de PInvoke devuelven un puntero a un búfer interno que no tiene que ser desasignado por el usuario. En este caso, el uso de la característica IJW es la opción obvia.

## <a name="limitations-of-pinvoke"></a>Limitaciones de PInvoke

No puede devolver el mismo puntero exacto de una función nativa que tomó como parámetro. Si una función nativa devuelve el puntero que PInvoke le ha serializado, pueden producirse daños en la memoria y excepciones.

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

El ejemplo siguiente muestra este problema, y aunque el programa puede parecer dar la salida correcta, la salida proviene de la memoria que se había liberado.

```cpp
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

## <a name="marshaling-arguments"></a>Argumentos de marshaling

Con `PInvoke`, no se necesita ningún cálculo de referencias entre los tipos primitivos nativos administrados y C+ + con la misma forma. Por ejemplo, no se requiere ningún cálculo de referencias entre Int32 e int, o entre Double y double.

Sin embargo, debe calcular las referencias de tipos que no tienen el mismo formulario. Esto incluye los tipos char, string y struct. En la tabla siguiente se muestran las asignaciones utilizadas por el serializador para varios tipos:

|wtypes.h|Visual C++|Visual C++ con /clr|Common Language Runtime|
|--------------|------------------|-----------------------------|-----------------------------|
|HANDLE|Vacío\*|Vacío\*|IntPtr, UIntPtr|
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
|LPSTR|Char\*|String á [in], StringBuilder á [in, out]|String á [in], StringBuilder á [in, out]|
|LPCSTR|const char\*|Cadena de la cadena de la cadena de|String|
|LPWSTR|Wchar_t\*|String á [in], StringBuilder á [in, out]|String á [in], StringBuilder á [in, out]|
|LPCWSTR|const wchar_t \*|Cadena de la cadena de la cadena de|String|
|FLOAT|FLOAT|FLOAT|Single|
|DOUBLE|double|double|Double|

El serializador ancla automáticamente la memoria asignada en el montón en tiempo de ejecución si su dirección se pasa a una función no administrada. El anclado impide que el recolector de elementos no utilizados mueva el bloque de memoria asignado durante la compactación.

En el ejemplo mostrado anteriormente en este tema, el parámetro CharSet de DllImport especifica cómo se deben calcular las referencias de las cadenas administradas; en este caso, deben serializarse en cadenas ANSI para el lado nativo.

Puede especificar información de cálculo de referencias para argumentos individuales de una función nativa mediante el atributo MarshalAs. Hay varias opciones para serializar un argumento String: \* BStr, ANSIBStr, TBStr, LPStr, LPWStr y LPTStr. El valor predeterminado es LPStr.

En este ejemplo, la cadena se calcula como una cadena de caracteres Unicode de doble byte, LPWStr. La salida es la primera letra de Hello World! porque el segundo byte de la cadena serializada es null y coloca esto como el marcador de fin de cadena.

```cpp
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

El atributo MarshalAs se encuentra en el espacio de nombres System::Runtime::InteropServices. El atributo se puede utilizar con otros tipos de datos, como matrices.

Como se mencionó anteriormente en el tema, la biblioteca de cálculo de referencias proporciona un nuevo método optimizado para calcular referencias de datos entre entornos nativos y administrados. Para obtener más información, consulte [Información general sobre el cálculo de referencias en C++](../dotnet/overview-of-marshaling-in-cpp.md).

## <a name="performance-considerations"></a>Consideraciones sobre el rendimiento

PInvoke tiene una sobrecarga de entre 10 y 30 instrucciones x86 por llamada. Además de este coste fijo, el cálculo de referencias crea gastos generales adicionales. No hay ningún costo de cálculo de referencias entre tipos que se pueden codificar y que tienen la misma representación en código administrado y no administrado. Por ejemplo, no hay ningún costo para traducir entre int y Int32.

Para un mejor rendimiento, tenga menos llamadas PInvoke que calculan referencias de tantos datos como sea posible, en lugar de más llamadas que calculan menos datos por llamada.

## <a name="see-also"></a>Consulte también

[Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)
