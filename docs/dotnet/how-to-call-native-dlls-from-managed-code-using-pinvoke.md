---
title: Procedimiento Llamar a DLL nativas desde código administrado mediante PInvoke
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
ms.openlocfilehash: e51e094cc013250fc254a09e279745f1f9c108ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222816"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>Procedimiento Llamar a DLL nativas desde código administrado mediante PInvoke

Funciones que se implementan en archivos DLL no administrado se pueden llamar desde código administrado mediante la funcionalidad de invocación de plataforma (P/Invoke). Si el código fuente para el archivo DLL no está disponible, P/Invoke es la única opción para interoperar. Sin embargo, a diferencia de otros lenguajes. NET, Visual C++ proporciona una alternativa a P/Invoke. Para obtener más información, consulte [utilizando interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se usa Win32 [GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics) función para recuperar la resolución actual de la pantalla en píxeles.

Para las funciones que usan solo tipos intrínsecos como argumentos y valores devuelven, no se requiere ningún trabajo adicional. Otros tipos de datos, como punteros de función, matrices y estructuras, requieren atributos adicionales para asegurarse de que el cálculo de referencias de datos adecuada.

Aunque no es necesario, es recomendable hacer que los miembros estáticos de las declaraciones P/Invoke de una clase de valor para que no existen en el espacio de nombres global, como se muestra en este ejemplo.

```
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

## <a name="see-also"></a>Vea también

[Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
