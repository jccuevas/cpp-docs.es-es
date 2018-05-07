---
title: 'Cómo: llamar a DLL nativas desde código administrado mediante PInvoke | Documentos de Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e82690e49daf324d0ff77f89710ecdd09b208c19
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>Cómo: Llamar a archivos DLL nativos desde el código administrado mediante PInvoke
Puede llamar a funciones que se implementan en archivos DLL no administradas desde código administrado mediante la funcionalidad de invocación de plataforma (P/Invoke). Si el código fuente para el archivo DLL no está disponible, P/Invoke es la única opción para interoperar. Sin embargo, a diferencia de otros lenguajes. NET, Visual C++ proporciona una alternativa a P/Invoke. Para obtener más información, consulte [uso de la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se utiliza Win32 [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385) función para recuperar la resolución actual de la pantalla en píxeles.  
  
 Para las funciones que usan solo los tipos intrínsecos como argumentos y valores devuelven, es necesario ningún trabajo adicional. Otros tipos de datos, como punteros de función, matrices y estructuras, requieren atributos adicionales para garantizar la serialización de datos adecuados.  
  
 Aunque no es necesario, es recomendable realizar los miembros estáticos de las declaraciones P/Invoke de una clase de valor para que no existen en el espacio de nombres global, como se muestra en este ejemplo.  
  
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