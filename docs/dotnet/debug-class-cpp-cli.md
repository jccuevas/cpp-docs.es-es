---
title: Debug (clase) (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: eecda10f2fd88b902a54fe9f4dc4de8edc4bc1b0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413567"
---
# <a name="debug-class-ccli"></a>Debug (Clase) (C++/CLI)

Cuando se usa <xref:System.Diagnostics.Debug> en una aplicación de Visual C++, el comportamiento no cambia entre una depuración y una versión de lanzamiento.

## <a name="remarks"></a>Comentarios

El comportamiento de <xref:System.Diagnostics.Trace> es idéntico al comportamiento de la clase Debug, pero depende del símbolo TRACE que se está definiendo. Esto significa que hay que `#ifdef` cualquier código relacionado con el seguimiento para evitar el comportamiento de depuración en una versión de lanzamiento.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

El ejemplo siguiente ejecuta siempre las instrucciones de salida, independientemente de si se compila con **/DDEBUG** o **/DTRACE**.

### <a name="code"></a>Código

```cpp
// mcpp_debug_class.cpp
// compile with: /clr
#using <system.dll>
using namespace System::Diagnostics;
using namespace System;

int main() {
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );
   Trace::AutoFlush = true;
   Trace::Indent();
   Trace::WriteLine( "Entering Main" );
   Console::WriteLine( "Hello World." );
   Trace::WriteLine( "Exiting Main" );
   Trace::Unindent();

   Debug::WriteLine("test");
}
```

### <a name="output"></a>Salida

```Output
    Entering Main
Hello World.
    Exiting Main
test
```

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

Para obtener el comportamiento esperado (es decir, que no se imprima "probar" para una versión de lanzamiento), debe usar el `#ifdef` y `#endif` directivas. Para demostrar esta corrección, el anterior ejemplo de código se modifica a continuación:

### <a name="code"></a>Código

```cpp
// mcpp_debug_class2.cpp
// compile with: /clr
#using <system.dll>
using namespace System::Diagnostics;
using namespace System;

int main() {
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );
   Trace::AutoFlush = true;
   Trace::Indent();

#ifdef TRACE   // checks for a debug build
   Trace::WriteLine( "Entering Main" );
   Console::WriteLine( "Hello World." );
   Trace::WriteLine( "Exiting Main" );
#endif
   Trace::Unindent();

#ifdef DEBUG   // checks for a debug build
   Debug::WriteLine("test");
#endif   //ends the conditional block
}
```

## <a name="see-also"></a>Vea también

[Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)