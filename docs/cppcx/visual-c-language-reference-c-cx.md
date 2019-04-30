---
title: Referencia del lenguaje Visual C++ (C++/CX)
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: ce0272499b653b9077a891e39e9b29797e7e051d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384951"
---
# <a name="visual-c-language-reference-ccx"></a>Referencia del lenguaje Visual C++ (C++/CX)

C++ / c++ / CX es un conjunto de extensiones del lenguaje C++ que permiten la creación de aplicaciones de Windows y componentes de Windows en tiempo de ejecución en una locución que sea lo más parecido posible al modernas de C++. Usar C / c++ / CX para escribir aplicaciones de Windows y componentes en código nativo que interactúen fácilmente con Visual C#, Visual Basic y JavaScript y otros lenguajes compatibles con el tiempo de ejecución de Windows. En los pocos casos que requieren acceso directo a las interfaces COM sin procesar, o el código no excepcional, puede usar el [biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución](../windows/windows-runtime-cpp-template-library-wrl.md).

> [!NOTE]
> **[C++ / c++ / WinRT](/windows/uwp/cpp-and-winrt-apis/index) es la alternativa recomendada para C++ / c++ / CX**. Es una nueva, el estándar C ++ 17 proyección de lenguaje de Windows en tiempo de ejecución APIs, disponible en Windows 10 SDK más reciente de la versión 1803 en adelante. C++ / c++ / WinRT se implementa completamente en archivos de encabezado y ha diseñado para proporcionar acceso de primera clase a la API de Windows moderna.
>
> Con C / c++ / WinRT, puede consumir y crear con cualquier compilador de 17 C ++ conforme a los estándares de Windows en tiempo de ejecución APIs. C++ / c++ / WinRT normalmente funciona mejor y genera archivos binarios más pequeños que ninguna otra opción de idioma para el tiempo de ejecución de Windows. Se seguirá admitiendo C++ / c++ / CX y WRL, pero se recomienda encarecidamente que utilicen las nuevas aplicaciones C++ / c++ / WinRT. Para obtener más información, consulte [C++ / c++ / WinRT](/windows/uwp/cpp-and-winrt-apis/index).

Mediante el uso de C++ / c++ / CX, puede crear:

- Las aplicaciones de C++ Universal Windows Platform (UWP) que usan XAML para definir el usuario de la interfaz y la pila nativa. Para obtener más información, consulte [crear una aplicación "hello world" en C++ (UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- Componentes de tiempo de ejecución de Windows de C++ que pueden utilizarse en aplicaciones de Windows basadas en JavaScript. Para obtener más información, consulta [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Aplicaciones con numerosos gráficos y juegos DirectX de Windows. Para obtener más información, consulte [crear un juego para UWP simple con DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game).

## <a name="related-articles"></a>Artículos relacionados

|||
|-|-|
|[Referencia rápida](../cppcx/quick-reference-c-cx.md)|Tabla de palabras clave y operadores de C / c++ / CX.|
|[Sistema de tipos](../cppcx/type-system-c-cx.md)|Describe básico de C++ / c++ / CX tipos y construcciones de programación y cómo utilizar C++ / c++ / CX para consumir y crear tipos en tiempo de ejecución de Windows.|
|[Compilación de aplicaciones y bibliotecas](../cppcx/building-apps-and-libraries-c-cx.md)|Describe cómo utilizar el IDE para crear aplicaciones y vincular a bibliotecas estáticas y archivos DLL.|
|[Interoperación con otros lenguajes](../cppcx/interoperating-with-other-languages-c-cx.md)|Describe cómo los componentes que se escriben con C++ / c++ / CX puede usarse con los componentes que se escriben en JavaScript, cualquier administrado idioma o la biblioteca de plantillas C++ de Windows en tiempo de ejecución.|
|[Subprocesamiento y serialización](../cppcx/threading-and-marshaling-c-cx.md)|Describe cómo especificar el comportamiento de subprocesamiento y cálculo de referencias de los componentes que crees.|
|[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)|Hace referencia a documentación para el espacio de nombres predeterminado, el espacio de nombres Platform, Platform::Collections y los espacios de nombres relacionados.|
|[Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|Enumera las funciones de CRT que no se pueden usar en aplicaciones de Windows Runtime.|
|[Guías de procedimientos para las aplicaciones de Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|Proporcionan orientación de alto nivel sobre las aplicaciones de Windows 10 y vínculos a más información.|
|[C++ / c++ / CX parte 0 de \[n\]: Una introducción](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C++ / c++ / CX parte 1 de \[n\]: Una clase Simple](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C++ / c++ / CX parte 2 de \[n\]: Tipos que usan sombreros](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C++ / c++ / CX parte 3 de \[n\]: En obra](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C++ / c++ / CX parte 4 de \[n\]: Funciones miembro estáticas](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|Una serie de blog Introducción de Visual C++ en C++ / c++ / CX.|
