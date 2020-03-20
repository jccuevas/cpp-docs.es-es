---
title: 'Cómo: Llamar a archivos DLL nativos desde el código administrado mediante PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
ms.openlocfilehash: 1eb5d5669c49dd49a411c275f8845dbbab989df3
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545094"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>Cómo: Llamar a archivos DLL nativos desde el código administrado mediante PInvoke

Se puede llamar a las funciones que se implementan en archivos dll no administrados desde el código administrado mediante la funcionalidad de invocación de plataforma (P/Invoke). Si el código fuente del archivo DLL no está disponible, P/Invoke es la única opción para interoperar. Sin embargo, a diferencia de otros lenguajes C++ .net, visual proporciona una alternativa a P/Invoke. Para obtener más información, [vea C++ usar Interop (implicit PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se usa la función [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics) de Win32 para recuperar la resolución actual de la pantalla en píxeles.

En el caso de las funciones que usan solo tipos intrínsecos como argumentos y valores devueltos, no se requiere ningún trabajo adicional. Otros tipos de datos, como punteros de función, matrices y estructuras, requieren atributos adicionales para garantizar el cálculo de referencias de datos adecuado.

Aunque no es necesario, se recomienda crear declaraciones P/Invoke de miembros estáticos de una clase de valor para que no existan en el espacio de nombres global, como se muestra en este ejemplo.

```cpp
// pinvoke_basic.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value class Win32 {
public:
   [DllImport("User32.dll")]
   static int GetSystemMetrics(int);

   enum class SystemMetricIndex {
      // Same values as those defined in winuser.h.
      SM_CXSCREEN = 0,
      SM_CYSCREEN = 1
   };
};

int main() {
   int hRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CXSCREEN) );
   int vRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CYSCREEN) );
   Console::WriteLine("screen resolution: {0},{1}", hRes, vRes);
}
```

## <a name="see-also"></a>Consulte también

[Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
