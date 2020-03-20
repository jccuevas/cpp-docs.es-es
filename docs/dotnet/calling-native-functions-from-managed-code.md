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
ms.openlocfilehash: 50f40cc147daaa26a7fa4e607f0d4dd42cf22d61
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545370"
---
# <a name="calling-native-functions-from-managed-code"></a>Llamar a funciones nativas desde código administrado

El Common Language Runtime proporciona servicios de invocación de plataforma, o PInvoke, que permite al código administrado llamar a funciones de estilo C en bibliotecas nativas de vínculos dinámicos (dll). La misma serialización de datos se usa como para la interoperabilidad COM con el tiempo de ejecución y para el mecanismo "it Just Works" o IJW.

Para más información, consulte:

- [Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

Los ejemplos de esta sección solo muestran cómo se puede usar `PInvoke`. `PInvoke` puede simplificar el cálculo de referencias de datos personalizado, ya que la información de cálculo de referencias se proporciona mediante declaración en atributos en lugar de escribir código de serialización de procedimientos.

> [!NOTE]
>  La biblioteca de cálculo de referencias proporciona una forma alternativa de calcular las referencias de datos entre entornos nativos y administrados de una manera optimizada. Vea [información general sobre el cálculo C++ de referencias en](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información sobre la biblioteca de cálculo de referencias. La biblioteca de serialización solo se puede usar para datos y no para funciones.

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke y el atributo DllImport

En el ejemplo siguiente se muestra el uso de `PInvoke` en C++ un programa visual. La función nativa put se define en msvcrt. dll. El atributo DllImport se usa para la declaración de puts.

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

- No es necesario escribir `DLLImport` declaraciones de atributo para las API no administradas que utiliza el programa. Solo tiene que incluir el archivo de encabezado y vincular con la biblioteca de importación.

- El mecanismo IJW es ligeramente más rápido (por ejemplo, no es necesario que el código auxiliar de IJW busque la necesidad de anclar o copiar elementos de datos porque lo hace explícitamente el desarrollador).

- Ilustra claramente los problemas de rendimiento. En este caso, el hecho de trasladar una cadena Unicode a una cadena ANSI y tener una asignación y desasignación de memoria de operador. En este caso, un desarrollador que escribe el código mediante IJW darse de ejemplo que la llamada a `_putws` y el uso de `PtrToStringChars` sería mejor para el rendimiento.

- Si llama a muchas API no administradas utilizando los mismos datos, el cálculo de referencias de una vez y el paso de la copia calculada es mucho más eficaz que volver a calcular las referencias de cada vez.

### <a name="disadvantages-of-ijw"></a>Desventajas de IJW

- El cálculo de referencias se debe especificar explícitamente en el código en lugar de en los atributos (que suelen tener los valores predeterminados adecuados).

- El código de serialización está alineado, donde es más invasivo en el flujo de la lógica de la aplicación.

- Dado que las API de serialización explícita devuelven `IntPtr` tipos para la portabilidad de 32 bits a 64 bits, debe usar llamadas de `ToPointer` adicionales.

El método específico expuesto por C++ es el método explícito más eficaz, a costa de cierta complejidad adicional.

Si la aplicación usa principalmente tipos de datos no administrados o si llama a más API no administradas que .NET Framework API, se recomienda usar la característica IJW. Para llamar a una API no administrada ocasional en una aplicación mayoritariamente administrada, la elección es más sutil.

## <a name="pinvoke-with-windows-apis"></a>PInvoke con las API de Windows

PInvoke es práctico para llamar a funciones en Windows.

En este ejemplo, un programa C++ visual interopera con la función MessageBox que forma parte de la API Win32.

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

El resultado es un cuadro de mensaje que tiene el título PInvoke test y contiene el texto Hola mundo!.

PInvoke también utiliza la información de cálculo de referencias para buscar funciones en el archivo DLL. En user32. dll no hay ninguna función MessageBox, pero CharSet = CharSet:: ANSI permite a PInvoke usar MessageBoxA, la versión ANSI, en lugar de MessageBoxW, que es la versión Unicode. En general, se recomienda usar las versiones Unicode de las API no administradas, ya que elimina la sobrecarga de traducción del formato Unicode nativo de .NET Framework objetos de cadena a ANSI.

## <a name="when-not-to-use-pinvoke"></a>Cuándo no usar PInvoke

El uso de PInvoke no es adecuado para todas las funciones de estilo C en archivos dll. Por ejemplo, supongamos que hay una función MakeSpecial en MyLib. dll declarada de la siguiente manera:

`char * MakeSpecial(char * pszString);`

Si usamos PInvoke en una aplicación Visual C++ , podríamos escribir algo similar a lo siguiente:

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

La dificultad aquí es que no se puede eliminar la memoria de la cadena no administrada devuelta por MakeSpecial. Otras funciones llamadas a través de PInvoke devuelven un puntero a un búfer interno que no tiene que ser desasignado por el usuario. En este caso, el uso de la característica IJW es la opción obvia.

## <a name="limitations-of-pinvoke"></a>Limitaciones de PInvoke

No se puede devolver el mismo puntero exacto desde una función nativa que se tomó como parámetro. Si una función nativa devuelve el puntero en el que se han calculado las referencias de PInvoke, pueden producirse daños en la memoria y excepciones.

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

En el ejemplo siguiente se muestra este problema y, aunque el programa parezca proporcionar la salida correcta, la salida proviene de la memoria que se ha liberado.

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

## <a name="marshaling-arguments"></a>Calcular las referencias de argumentos

Con `PInvoke`, no se necesita ningún cálculo de referencias entre C++ tipos primitivos administrados y nativos con el mismo formato. Por ejemplo, no se requiere ningún cálculo de referencias entre Int32 e int, o entre Double y Double.

Sin embargo, debe serializar los tipos que no tienen el mismo formato. Esto incluye los tipos Char, String y struct. En la tabla siguiente se muestran las asignaciones utilizadas por el contador de referencias para varios tipos:

|Wtypes. h|Visual C++|Visual C++ con/CLR|Common Language Runtime|
|--------------|------------------|-----------------------------|-----------------------------|
|HANDLE|\* void|\* void|IntPtr, UIntPtr|
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
|LPCSTR|char \*|Cadena ^ [in], StringBuilder ^ [in, out]|Cadena ^ [in], StringBuilder ^ [in, out]|
|LPCSTR|const char \*|Cadena ^|String|
|LPWSTR|wchar_t \*|Cadena ^ [in], StringBuilder ^ [in, out]|Cadena ^ [in], StringBuilder ^ [in, out]|
|LPCWSTR|wchar_t const \*|Cadena ^|String|
|FLOAT|FLOAT|FLOAT|Single|
|DOUBLE|double|double|Double|

El serializador ancla automáticamente la memoria asignada en el montón en tiempo de ejecución si su dirección se pasa a una función no administrada. El anclaje evita que el recolector de elementos no utilizados mueva el bloque de memoria asignado durante la compactación.

En el ejemplo mostrado anteriormente en este tema, el parámetro CharSet de DllImport especifica cómo deben calcularse las referencias de las cadenas administradas. en este caso, se deben calcular las referencias a cadenas ANSI para el lado nativo.

Puede especificar la información de cálculo de referencias para argumentos individuales de una función nativa mediante el atributo MarshalAs. Hay varias opciones para calcular las referencias de una cadena \* argumento: BStr, ANSIBStr, TBStr, LPStr, LPWStr y LPTStr. El valor predeterminado es LPStr.

En este ejemplo, se calculan las referencias de la cadena como una cadena de caracteres Unicode de doble byte, LPWStr. La salida es la primera letra de Hola mundo. Dado que el segundo byte de la cadena serializada es null, y puts lo interpreta como el marcador de fin de cadena.

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

El atributo MarshalAs está en el espacio de nombres System:: Runtime:: InteropServices. El atributo se puede utilizar con otros tipos de datos, como las matrices.

Como se mencionó anteriormente en el tema, la biblioteca de cálculo de referencias proporciona un método nuevo y optimizado para calcular las referencias de datos entre entornos nativos y administrados. Para obtener más información, vea [información general sobre el C++cálculo de referencias en ](../dotnet/overview-of-marshaling-in-cpp.md).

## <a name="performance-considerations"></a>Consideraciones de rendimiento

PInvoke tiene una sobrecarga de entre 10 y 30 instrucciones x86 por llamada. Además de este costo fijo, la serialización crea una sobrecarga adicional. No hay ningún costo de serialización entre los tipos que se pueden repasar por bytes que tienen la misma representación en código administrado y no administrado. Por ejemplo, no hay ningún costo por traducir entre int e Int32.

Para mejorar el rendimiento, tenga menos llamadas PInvoke que calculen las referencias de los datos posibles, en lugar de más llamadas que calculen las referencias a menos datos por llamada.

## <a name="see-also"></a>Consulte también

[Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)
